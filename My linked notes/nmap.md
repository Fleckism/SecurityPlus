The traceroute command is used to probe a path from one end system to another, and lists the intermediate systems providing the link. The Nmap combined with Zenmap tools will give a visual of the network topology.

**nmap -sn --traceroute 192.168.1.1**

The [[Nmap]] Security Scanner ([nmap.org](https://nmap.org/)) is one of the most popular open-source IP scanners. Nmap can use diverse methods of host discovery, some of which can operate stealthily and serve to defeat security mechanisms such as firewalls and intrusion detection. The tool is open-source software with packages for most versions of Windows, Linux, and macOS. It can be operated with a command line or via a GUI (Zenmap) **(Used for fingerprinting)**.

The basic syntax of an Nmap command is to give the IP subnet (or IP host address) to scan. When used without switches like this, the default behavior of Nmap is to ping and send a TCP ACK packet to ports 80 and 443 to determine whether a host is present. On a local network segment, Nmap will also perform ARP and ND (Neighbor Discovery) sweeps. If a host is detected, Nmap performs a port scan against that host to determine which services it is running.

![Screenshot of 7 IP addresses in the left pane that begin with 10.1.0; the right pane lists the MAC address for each host and whether the host is up.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1833-1599771794816.png)

Nmap default scan listing open ports from within the default range. (Screenshot Nmap [nmap.org](https://nmap.org/).)
 
This OS fingerprinting can be time-consuming on a large IP scope and is also non-stealthy. If you want to perform only host discovery, you can use Nmap with the -sn switch (or -sP in earlier versions) to suppress the port scan.

# Options
- A: Enable OS detection, version detection, script scanning, and traceroute
#  PORT SPECIFICATION AND SCAN ORDER:
  -p (port ranges): Only scan specified ports
    Ex: -p22; -p1-65535; -p U:53,111,137,T:21-25,80,139,8080,S:9
  --exclude-ports (port ranges): Exclude the specified ports from scanning
  -F: Fast mode - Scan fewer ports than the default scan
  -r: Scan ports consecutively - don't randomize
  --top-ports (number): Scan (number) most common ports
  --port-ratio (ratio): Scan ports more common than (ratio) 
	

	
# SCAN TECHNIQUES:
  -sS/sT/sA/sW/sM: TCP SYN/Connect()/ACK/Window/Maimon scans
  -sU: UDP Scan
  -sN/sF/sX: TCP Null, FIN, and Xmas scans
  --scanflags <flags>: Customize TCP scan flags
  -sI <zombie host[:probeport]>: Idle scan
  -sY/sZ: SCTP INIT/COOKIE-ECHO scans
  -sO: IP protocol scan
  -b <FTP relay host>: FTP bounce scan
	

	
	# Port 