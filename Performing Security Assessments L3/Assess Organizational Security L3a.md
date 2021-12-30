#Security_Assessment
Does the mind map include this entire note I'm guessing yes
## Security Assessment refers to the process and tools that evaluate the attack surface. With knowledge of adversary tactics and capabilities, you can assess whether points on the attack surface are potentially vulnerable attack vectors.  The output of assessment is recommendations for deploying, enhancing, or reconfiguring security controls to mitigate the risk that vulnerabilities are exploitable by threat actors.

#Attack_surface the process of mapping it out is referred to as network reconnaissance and discovery.

- Topology discovery ( footprinting ) scanning hosts, IP ranges, and routes between networks to map out the structure of the target network.
	- Can also be used to build an asset database and to identify non-authorized hosts(rogue system detection) or network configuration errors
#Command_Line_Tools
	-	ipconfig (win):  Show the configuration assigned to network interface(s) 
	-	ifconfig (linux): "                  "
	-   ping:  probe a host on a particular IP address or host name using Internet Control Message Protocol (ICMP)
	-	arp: Display the local machines Address Resolution Protocol(ARP) cache
	
	
	
	
	
	





## Route and Traceroute, the following tools can be used to test the routing configuration and connectivity with remote hosts and networks.
-	route(linux?): View and configure the host's local routing table.
-	tracert(win):  uses ICMP probes to report the round trip time (RTT) for hops between the local host and a host on a remote network.
-	traceroute(Linux): Performs route discovery from a Linux host. Users UDP probes rather than ICMP, by default.
-	pathping(win):  Provides statistics for latency and packet loss along a router over longer measuring period.
-	mtr(Linux): "                     "

**In Linux, commands such as ifconfig, arp, route, and traceroute are deprecated and the utilities have not been updated for some years. The iproute2 suite of tools supply replacements for these commands**

## IP Scanners and NMAP, IP scanners perform host discovery and identifies how the hosts are connected together in an internetwork.
- is a stealthy and detailed way to scan networks.
- Microsoft's System Center Products are used for auditing.  
	- Can be provided credentials to perform authorized scans and obtain detailed host information via management protocols, such as the Simple Network Management Protocol (SNMP).

-	Nmap(Linux & Win):  Can defeat security mechanisms(firewalls and intrusion detection) GUI version Zenmap.
-	The basic syntax of an Nmap command is to give the IP subnet (or IP host address) to scan. When used without switches like this, the default behavior of Nmap is to ping and send a TCP ACK packet to ports 80 and 443 to determine whether a host is present. On a local network segment, Nmap will also perform ARP and ND (Neighbor Discovery) sweeps. If a host is detected, Nmap performs a port scan against that host to determine which services it is running.

![Screenshot of 7 IP addresses in the left pane that begin with 10.1.0; the right pane lists the MAC address for each host and whether the host is up.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1833-1599771794816.png)

Nmap default scan listing open ports from within the default range. (Screenshot Nmap [nmap.org](https://nmap.org/).)

This OS fingerprinting can be time-consuming on a large IP scope and is also non-stealthy. If you want to perform only host discovery, you can use Nmap with the -sn switch (or -sP in earlier versions) to suppress the port scan.
## Service Discovery and NMAP after identifying active IP hosts on network and gaining an idea of the network topology, the 2nd step in network reconnaissance is to work out which operating systems are in use, and which network services each host is running, and if possible which application software is underpinning those services. Service discovery can also be used defensively, to probe potential rogue systems and identify the presence of unauthorized network service ports. 
- Nmap options against active IP addresses
	-   TCP SYN (-sS)—this is a fast technique also referred to as half-open scanning, as the scanning host requests a connection without acknowledging it. The target's response to the scan's SYN packet identifies the port state.
	-   UDP scans (-sU)—scan UDP ports. As these do not use ACKs, Nmap needs to wait for a response or timeout to determine the port state, so UDP scanning can take a long time. A UDP scan can be combined with a TCP scan.
	-   Port range (-p)—by default, Nmap scans 1000 commonly used ports, as listed in its configuration file. Use the -p argument to specify a port range.

### Service and Version Detection and OS Fingerprinting with Nmap.  Detailed analysis of services on a particular host is called fingerprinting.  Different software responds differently to probes in a unique way.  The scanning software can make an educated guess at the software type and version, without having any privileged access to the host. Aka banner grabbing, where the banner is the header of the response returned by the application.
When services are discovered, you can use Nmap with the -sV or -A switch to probe a host more intensively to discover the following information:

-   Protocol—do not assume that a port is being used for its "well known" application protocol. Nmap can scan traffic to verify whether it matches the expected signature (HTTP, DNS, SMTP, and so on).
-   Application name and version—the software operating the port, such as Apache web server or Internet Information Services (IIS) web server.
-   OS type and version—use the -O switch to enable OS fingerprinting (or -A to use both OS fingerprinting and version discovery).
-   Device type—not all network devices are PCs. Nmap can identify switches and routers or other types of networked devices, such as NAS boxes, printers, and webcams.