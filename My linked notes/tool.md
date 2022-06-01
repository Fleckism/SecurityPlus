#IR #Ops 
[[tcpdump]] is a command line packet capture utility for Linux

A protocol analyzer (or packet analyzer) works in conjunction with a sniffer to perform traffic analysis. You can either analyze a live capture or open a saved capture (.pcap) file. Protocol analyzers can decode a captured frame to reveal its contents in a readable format. You can choose to view a summary of the frame or choose a more detailed view that provides information on the OSI layer, protocol, function, and data.

[[Wireshark]]

[[hping]] is an open-source spoofing tool that provides a penetration tester with the ability to craft network packets to exploit vulnerable firewalls and IDSs. hping can perform the following types of test **(Used for fingerprinting)**:

[[tcpreplay]] As the name suggests, tcpreplay takes previously captured traffic that has been saved to a .pcap file and replays it through a network interface ([linux.die.net/man/1/tcpreplay](https://linux.die.net/man/1/tcpreplay)). Optionally, fields in the capture can be changed, such as substituting MAC or IP addresses. tcpreplay is useful for analysis purposes. If you have captured suspect traffic, you can replay it through a monitored network interface to test intrusion detection rules malicious raffic sample.

Metasploit framework

[[Netcat]] One simple but effective [[tool]] for testing connectivity is Netcat (nc), available for both Windows and Linux. Netcat is a computer networking utility for reading and writing raw data over a network connection, and can be used for port scanning and fingerprinting. For example, the following command attempts to connect to the HTTP port on a server and return any banner by sending the "head" HTTP keyword: **(To check for if it's possible to open a network connection to a remote host over a given port#)** 

[[ipconfig]]
[[ifconfig]] show the configuration assigned to network interface(s) in Linux.
[[ping]] probe a host on a particular IP address or host name using Internet Control Message Protocol (ICMP)**. You can use ping with a simple script to perform a sweep of all the IP addresses in a subnet. The following example will scan the 10.1.0.0/24 subnet from a Windows machine:**
+++ Is ARP a tool?+++
[[arp]]—display the local machine's Address Resolution Protocol ([[ARP]]) cache. The ARP cache shows the MAC address of the interface associated with each IP address the local host has communicated with recently. This can be useful if you are investigating a suspected spoofing attack. For example, a sign of a man-in-the-middle attack is where the MAC address of the default gateway IP listed in the cache is not the legitimate router's MAC address.

[[tracert]]—uses [[ICMP]] probes to report the round trip time (RTT) for hops between the local host and a host on a remote network. tracert is the Windows version of the tool.

[[traceroute]]—performs route discovery from a Linux host. traceroute uses [[UDP]] probes rather than ICMP, by default.

[[pathping]]—provides statistics for latency and packet loss along a route over a longer measuring period. pathping is a Windows tool; the equivalent on Linux is mtr  **( Rogue host is modifying traffic before forwarding it, with the side effect of increasing network latency)**.

[[Nmap]] Security Scanner ([nmap.org](https://nmap.org/)) is one of the most popular open-source IP scanners. Nmap can use diverse methods of host discovery, some of which can operate stealthily and serve to defeat security mechanisms such as firewalls and intrusion detection. The tool is open-source software with packages for most versions of Windows, Linux, and macOS. It can be operated with a command line or via a GUI (Zenmap) **(Used for fingerprinting)**.

[[Nikto]]