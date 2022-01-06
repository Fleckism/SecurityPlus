## LESSON INTRODUCTION

Security assessment refers to processes and tools that evaluate the attack surface. With knowledge of adversary tactics and capabilities, you can assess whether points on the attack surface are potentially vulnerable attack vectors. The output of assessment is recommendations for deploying, enhancing, or reconfiguring security controls to mitigate the risk that vulnerabilities are exploitable by threat actors. 

Lesson Objectives

In this lesson, you will:

-   Assess organizational security with network reconnaissance tools.
-   Explain security concerns with general vulnerability types.
-   Summarize vulnerability scanning techniques.
-   Explain penetration testing concepts.

EXAM OBJECTIVES COVERED

4.1 Given a scenario, use the appropriate tool to assess organizational security

Reconnaissance is a type of assessment activity that maps the potential attack surface by identifying the nodes and connections that make up the network. You will often need to run scans using both command line and GUI topology discovery tools. You will need to report host configurations using fingerprinting tools and capture and analyze network traffic. You should also understand how tools can be used to operate backdoor connections to a host and to covertly exfiltrate data.
## ipconfig, ping, and ARP
The process of mapping out the attack surface is referred to as network reconnaissance and discovery. Reconnaissance techniques are used by threat actors, but they can also be used by security professionals to probe and test their own security systems, as part of a security assessment and ongoing monitoring.

_Topology discovery_ (or "footprinting") means scanning for hosts, IP ranges, and routes between networks to map out the structure of the target network. Topology discovery can also be used to build an asset database and to identify non-authorized hosts (rogue system detection) or network configuration errors. 

Basic topology discovery tasks can be accomplished using the command line tools built into Windows and Linux. The following tools report the IP configuration and test connectivity on the local network segment or subnet.

-   ipconfig—show the configuration assigned to network interface(s) in Windows, including the hardware or media access control (MAC) address, IPv4 and IPv6 addresses, default gateway, and whether the address is static or assigned by DHCP. If the address is DHCP-assigned, the output also shows the address of the DHCP server that provided the lease.
-   ifconfig—show the configuration assigned to network interface(s) in Linux.
-   ping—probe a host on a particular IP address or host name using Internet Control Message Protocol (ICMP). You can use ping with a simple script to perform a sweep of all the IP addresses in a subnet. The following example will scan the 10.1.0.0/24 subnet from a Windows machine:

for /l %i in (1,1,255) do @ping -n 1 -w 100 10.1.0.%i | find /i "reply"

![Screenshot shows 6 reply lines; the first line is "Reply from 10.1.0.1: bytes=32 time<1ms TTL=128". The IP address for each reply begins with 10.1.0.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9493-1599771794671.png)

Performing a ping sweep in Windows with a For loop—Searching multiple octets requires nested loops. Note that not all hosts respond to ICMP probes. (Screenshot used with permission from Microsoft.)

-   arp—display the local machine's Address Resolution Protocol (ARP) cache. The ARP cache shows the MAC address of the interface associated with each IP address the local host has communicated with recently. This can be useful if you are investigating a suspected spoofing attack. For example, a sign of a man-in-the-middle attack is where the MAC address of the default gateway IP listed in the cache is not the legitimate router's MAC address.

For more information about commands, including syntax usage, look up the command in an online resource for Windows ([docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands)) or Linux ([linux.die.net/man](https://linux.die.net/man/)).

In Linux, commands such as ifconfig, arp, route, and traceroute are deprecated and the utilities have not been updated for some years. The iproute2 suite of tools supply replacements for these commands ([digitalocean.com/community/tutorials/how-to-use-iproute2-tools-to-manage-network-configuration-on-a-linux-vps](https://www.digitalocean.com/community/tutorials/how-to-use-iproute2-tools-to-manage-network-configuration-on-a-linux-vps)).

## ROUTE AND TRACEROUTE

The following tools can be used to test the routing configuration and connectivity with remote hosts and networks.

-   route—view and configure the host's local routing table. Most end systems use a default route to forward all traffic for remote networks via a gateway router. If the host is not a router, additional entries in the routing table could be suspicious.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8872-1599771794749.png)

Output from the route command on a Linux host. Most endpoints have a simple routing table, similar to this. It shows the default route (0.0.0.0/0) via the host configured as the default gateway (10.1.0.254) over the network interface eth0. The second line of the table shows the subnet for local traffic (10.1.0.0/24). This network is directly connected, represented by the 0.0.0.0 gateway.

-   tracert—uses ICMP probes to report the round trip time (RTT) for hops between the local host and a host on a remote network. tracert is the Windows version of the tool.
-   traceroute—performs route discovery from a Linux host. traceroute uses UDP probes rather than ICMP, by default.
-   pathping—provides statistics for latency and packet loss along a route over a longer measuring period. pathping is a Windows tool; the equivalent on Linux is mtr.

In a security context, high latency at the default gateway compared to a baseline might indicate a man-in-the-middle attack. High latency on other hops could be a sign of denial of service, or could just indicate network congestion.

In Linux, commands such as ifconfig, arp, route, and traceroute are deprecated and the utilities have not been updated for some years. The iproute2 suite of tools supply replacements for these commands ([digitalocean.com/community/tutorials/how-to-use-iproute2-tools-to-manage-network-configuration-on-a-linux-vps](https://www.digitalocean.com/community/tutorials/how-to-use-iproute2-tools-to-manage-network-configuration-on-a-linux-vps)).
## IP SCANNERS AND NMAP

Scanning a network using tools such as ping is time consuming and non-stealthy, and does not return detailed results. Most topology discovery is performed using a dedicated IP scanner tool. An IP scanner performs host discovery and identifies how the hosts are connected together in an internetwork. For auditing, there are enterprise suites, such as Microsoft's System Center products. Such suites can be provided with credentials to perform authorized scans and obtain detailed host information via management protocols, such as the Simple Network Management Protocol (SNMP).

The Nmap Security Scanner ([nmap.org](https://nmap.org/)) is one of the most popular open-source IP scanners. Nmap can use diverse methods of host discovery, some of which can operate stealthily and serve to defeat security mechanisms such as firewalls and intrusion detection. The tool is open-source software with packages for most versions of Windows, Linux, and macOS. It can be operated with a command line or via a GUI (Zenmap).

The basic syntax of an Nmap command is to give the IP subnet (or IP host address) to scan. When used without switches like this, the default behavior of Nmap is to ping and send a TCP ACK packet to ports 80 and 443 to determine whether a host is present. On a local network segment, Nmap will also perform ARP and ND (Neighbor Discovery) sweeps. If a host is detected, Nmap performs a port scan against that host to determine which services it is running.

![Screenshot of 7 IP addresses in the left pane that begin with 10.1.0; the right pane lists the MAC address for each host and whether the host is up.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1833-1599771794816.png)

Nmap default scan listing open ports from within the default range. (Screenshot Nmap [nmap.org](https://nmap.org/).)

This OS fingerprinting can be time-consuming on a large IP scope and is also non-stealthy. If you want to perform only host discovery, you can use Nmap with the -sn switch (or -sP in earlier versions) to suppress the port scan.
## SERVICE DISCOVERY AND NMAP

Having identified active IP hosts on the network and gained an idea of the network topology, the next step in network reconnaissance is to work out which operating systems are in use, which network services each host is running, and, if possible, which application software is underpinning those services. This process is described as service discovery. Service discovery can also be used defensively, to probe potential rogue systems and identify the presence of unauthorized network service ports.

### Service Discovery with Nmap

When Nmap completes a host discovery scan, it will report on the state of each port scanned for each IP address in the scope. At this point, you can run additional service discovery scans against one or more of the active IP addresses. Some of the principal options for service discovery scans are:

-   TCP SYN (-sS)—this is a fast technique also referred to as half-open scanning, as the scanning host requests a connection without acknowledging it. The target's response to the scan's SYN packet identifies the port state.
-   UDP scans (-sU)—scan UDP ports. As these do not use ACKs, Nmap needs to wait for a response or timeout to determine the port state, so UDP scanning can take a long time. A UDP scan can be combined with a TCP scan.
-   Port range (-p)—by default, Nmap scans 1000 commonly used ports, as listed in its configuration file. Use the -p argument to specify a port range.

### Service and Version Detection and OS Fingerprinting with Nmap

The detailed analysis of services on a particular host is often called fingerprinting. This is because each OS or application software that underpins a network service responds to probes in a unique way. This allows the scanning software to guess at the software name and version, without having any sort of privileged access to the host. This can also be described as banner grabbing, where the banner is the header of the response returned by the application.

When services are discovered, you can use Nmap with the -sV or -A switch to probe a host more intensively to discover the following information:

-   Protocol—do not assume that a port is being used for its "well known" application protocol. Nmap can scan traffic to verify whether it matches the expected signature (HTTP, DNS, SMTP, and so on).
-   Application name and version—the software operating the port, such as Apache web server or Internet Information Services (IIS) web server.
-   OS type and version—use the -O switch to enable OS fingerprinting (or -A to use both OS fingerprinting and version discovery).
-   Device type—not all network devices are PCs. Nmap can identify switches and routers or other types of networked devices, such as NAS boxes, printers, and webcams.

Nmap fingerprinting scan results.

Nmap comes with a database of application and version fingerprint signatures, classified using a standard syntax called Common Platform Enumeration (CPE). Unmatched responses can be submitted to a web URL for analysis by the community .
## NETSTAT AND NSLOOKUP

Basic service discovery tasks can also be performed using tools built into the Windows and Linux operating systems:

-   netstat—show the state of TCP/UDP ports on the local machine. The same command is used on both Windows and Linux, though with different options syntax. You can use netstat to check for service misconfigurations (perhaps a host is running a web or FTP server that a user installed without authorization). You may also be able to identify suspect remote connections to services on the local host or from the host to remote IP addresses. If you are attempting to identify malware, the most useful netstat output is to show which process is listening on which ports. 

![The first 2 items in the list are "TCP 10.1.0.1:80 ROGUE:1415 TIME_WAIT" and "TCP 10.1.0.1:80 GATEWAY:49161 ESTABLISHED"; 9 similar items follow.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7383-1599771794926.png)

netstat command running on Windows showing activity during an nmap scan. The findstr function is being used to filter the output (to show only connections from IPv4 hosts on the same subnet). (Screenshot used with permission from Microsoft.)

Command line output from netstat –ano.

On Linux, use of netstat is deprecated in favor of the ss command from the iptools2 suite ([linux.com/topic/networking/introduction-ss-command](https://www.linux.com/topic/networking/introduction-ss-command/)).

-   nslookup/dig—query name records for a given domain using a particular DNS resolver. Under Windows (nslookup) or Linux (nslookup/dig). An attacker may test a network to find out if the DNS service is misconfigured. A misconfigured DNS may allow a zone transfer, which will give the attacker the complete records of every host in the domain, revealing a huge amount about the way the network is configured. 

![Screenshot shows "*** Can't list domain comptia.org: Query refused".](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9882-1599771794985.png)
## OTHER RECONNAISSANCE AND DISCOVERY TOOLS

There are hundreds of tools relevant to security assessments, network reconnaissance, vulnerability scanning, and penetration testing. Security distributions specialize in bundling these tools for Linux—notably KALI ([kali.org](https://www.kali.org/)) plus ParrotOS ([parrotlinux.org](https://parrotlinux.org/))—and Windows ([fireeye.com/blog/threat-research/2019/03/commando-vm-windows-offensive-distribution.html](https://www.fireeye.com/blog/threat-research/2019/03/commando-vm-windows-offensive-distribution.html)).

### theHarvester

theHarvester is a tool for gathering open-source intelligence (OSINT) for a particular domain or company name ([github.com/laramies/theHarvester](https://github.com/laramies/theHarvester)). It works by scanning multiple public data sources to gather emails, names, subdomains, IPs, URLs and other relevant data.

### dnsenum

While you can use tools such as dig and whois to query name records and hosting details and to check that external DNS services are not leaking too much information, a tool such as dnsenum packages a number of tests into a single query ([github.com/fwaeytens/dnsenum](https://github.com/fwaeytens/dnsenum)). As well as hosting information and name records, dnsenum can try to work out the IP address ranges that are in use.

### scanless

Port scanning is difficult to conceal from detection systems, unless it is performed slowly and results are gathered over an extended period. Another option is to disguise the source of probes. To that end, scanless is a tool that uses third-party sites ([github.com/vesche/scanless](https://github.com/vesche/scanless)). This sort of tool is also useful in a defensive sense, by scanning for ports and services that are open but shouldn't be.

### curl

curl is a command line client for performing data transfers over many types of protocol ([curl.haxx.se](https://curl.haxx.se/)). This tool can be used to submit HTTP GET, POST, and PUT requests as part of web application vulnerability testing. curl supports many other data transfer protocols, including FTP, IMAP, LDAP, POP3, SMB, and SMTP.

### Nessus

The list of services and version information that a host is running can be cross-checked against lists of known software vulnerabilities. This type of scanning is usually performed using automated tools. Nessus, produced by Tenable Network Security ([tenable.com/products/nessus/nessus-professional](https://www.tenable.com/products/nessus/nessus-professional)), is one of the best-known commercial vulnerability scanners. It is available in on-premises (Nessus Manager) and cloud (Tenable Cloud) versions, as well as a Nessus Professional version, designed for smaller networks. The product is free to use for home users but paid for on a subscription basis for enterprises. As a previously open-source program, Nessus also supplies the source code for many other scanners.
## PACKET CAPTURE AND TCPDUMP 

Packet and protocol analysis is another crucial security assessment and monitoring process:

-   Packet analysis refers to deep-down frame-by-frame scrutiny of captured frames.
-   Protocol analysis means using statistical tools to analyze a sequence of packets, or packet trace.

Packet and protocol analysis depends on a sniffer tool to capture and decode the frames of data. Network traffic can be captured from a host or from a network segment. Using a host means that only traffic directed at that host is captured. Capturing from a network segment can be performed by a switched port analyzer (SPAN) port (or mirror port). This means that a network switch is configured to copy frames passing over designated source ports to a destination port, which the packet sniffer is connected to. Sniffing can also be performed over a network cable segment by using a test access port (TAP). This means that a device is inserted in the cabling to copy frames passing over it. There are passive and active (powered) versions.

Typically, sniffers are placed inside a firewall or close to a server of particular importance. The idea is usually to identify malicious traffic that has managed to get past the firewall. A single sniffer can generate an exceptionally large amount of data, so you cannot just put multiple sensors everywhere in the network without provisioning the resources to manage them properly. Depending on network size and resources, one or just a few sensors will be deployed to monitor key assets or network paths.

tcpdump is a command line packet capture utility for Linux ([linux.die.net/man/8/tcpdump](https://linux.die.net/man/8/tcpdump)). The basic syntax of the command is tcpdump -i eth0, where eth0 is the interface to listen on. The utility will then display captured packets until halted manually (Ctrl+C). Frames can be saved to a .pcap file using the -w option. Alternatively, you can open a pcap file using the -r option.

tcpdump is often used with some sort of filter expression to reduce the number of frames that are captured:

-   Type—filter by host, net, port, or portrange.
-   Direction—filter by source (src) or destination (dst) parameters (host, network, or port).
-   Protocol—filter by a named protocol rather than port number (for example, arp, icmp, ip, ip6, tcp, udp, and so on).

Filter expressions can be combined by using Boolean operators:

-   and (&&)
-   or (||)
-   not (!)

Filter syntax can be made even more detailed by using parentheses to group expressions. A complex filter expression should be enclosed by quotes. For example, the following command filters frames to those with the source IP 10.1.0.100 and destination port 53 or 80:

tcpdump -i eth0 "src host 10.1.0.100 and (dst port 53 or dst port 80)"