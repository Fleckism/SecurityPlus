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
## Service Discovery and NMAP
