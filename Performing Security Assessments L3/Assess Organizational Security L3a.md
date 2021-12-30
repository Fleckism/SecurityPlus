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
	- Can be provided credentials to perform authorized scans and obtain detailed host information.