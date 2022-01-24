[[tcpdump]] is a command line packet capture utility for Linux

A protocol analyzer (or packet analyzer) works in conjunction with a sniffer to perform traffic analysis. You can either analyze a live capture or open a saved capture (.pcap) file. Protocol analyzers can decode a captured frame to reveal its contents in a readable format. You can choose to view a summary of the frame or choose a more detailed view that provides information on the OSI layer, protocol, function, and data.

[[Wireshark]]

[[hping]] is an open-source spoofing tool that provides a penetration tester with the ability to craft network packets to exploit vulnerable firewalls and IDSs. hping can perform the following types of test **(Used for fingerprinting)**:

[[tcpreplay]] As the name suggests, tcpreplay takes previously captured traffic that has been saved to a .pcap file and replays it through a network interface ([linux.die.net/man/1/tcpreplay](https://linux.die.net/man/1/tcpreplay)). Optionally, fields in the capture can be changed, such as substituting MAC or IP addresses. tcpreplay is useful for analysis purposes. If you have captured suspect traffic, you can replay it through a monitored network interface to test intrusion detection rules malicious raffic sample.