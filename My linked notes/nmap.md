The traceroute command is used to probe a path from one end system to another, and lists the intermediate systems providing the link. The Nmap combined with Zenmap tools will give a visual of the network topology.

**nmap -sn --traceroute 192.168.1.1**

The [[Nmap]] Security Scanner ([nmap.org](https://nmap.org/)) is one of the most popular open-source IP scanners. Nmap can use diverse methods of host discovery, some of which can operate stealthily and serve to defeat security mechanisms such as firewalls and intrusion detection. The tool is open-source software with packages for most versions of Windows, Linux, and macOS. It can be operated with a command line or via a GUI (Zenmap) **(Used for fingerprinting)**.

The basic syntax of an Nmap command is to give the IP subnet (or IP host address) to scan. When used without switches like this, the default behavior of Nmap is to ping and send a TCP ACK packet to ports 80 and 443 to determine whether a host is present. On a local network segment, Nmap will also perform ARP and ND (Neighbor Discovery) sweeps. If a host is detected, Nmap performs a port scan against that host to determine which services it is running.

![Screenshot of 7 IP addresses in the left pane that begin with 10.1.0; the right pane lists the MAC address for each host and whether the host is up.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1833-1599771794816.png)

Nmap default scan listing open ports from within the default range. (Screenshot Nmap [nmap.org](https://nmap.org/).)
#assessment 
This OS fingerprinting can be time-consuming on a large IP scope and is also non-stealthy. If you want to perform only host discovery, you can use Nmap with the -sn switch (or -sP in earlier versions) to suppress the port scan.