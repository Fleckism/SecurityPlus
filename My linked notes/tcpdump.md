#tool tcpdump is a command line packet capture [[Network#Network packet | network packet]] utility for Linux ([linux.die.net/man/8/tcpdump](https://linux.die.net/man/8/tcpdump)). The basic syntax of the command is tcpdump -i eth0, where eth0 is the interface to listen on. The utility will then display captured packets until halted manually (Ctrl+C). Frames can be saved to a .pcap file using the -w option. Alternatively, you can open a pcap file using the -r option.
[[tool]]
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