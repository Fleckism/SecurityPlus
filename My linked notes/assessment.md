Security #assessment refers to processes and tools that **evaluate the attack surface**.

 **Reconnaissance is a type of assessment activity that maps the potential attack surface by identifying the nodes and connections that make up the network**. You will often need to run scans using both command line and GUI topology discovery tools. You will need to report host configurations using [[fingerprinting]] tools and capture and analyze network traffic. You should also understand how tools can be used to operate backdoor connections to a host and to covertly exfiltrate data.
 #z
 The process of mapping out the attack surface is referred to as network **reconnaissance** and discovery
 #tool
-   [[ipconfig]]—show the configuration assigned to network interface(s) in Windows, including the hardware or media access control (MAC) address, IPv4 and IPv6 addresses.
-   [[ifconfig]]—show the configuration assigned to network interface(s) in Linux.
-   [[ping]]—
-   arp—display the local machine's Address Resolution Protocol ([[ARP]]) cache.
-   
host discovery scan

next step in network reconnaissance is to work out which operating systems are in use, which network services each host is running, and, if possible, which application software is underpinning those services.

Are these all the steps in an assessment?
- security assessments, network reconnaissance, vulnerability scanning, and penetration testing
- Network reconnaissance and discovery is used to identify hosts, network topology, and open services/ports, establishing an overall attack surface.

# Dump
**vulnerability assessment, threat hunting, and penetration testing**
 
 Vulnerability scanning and penetration testing can use passive or active reconnaissance techniques. A passive approach tries to discover issues without causing an impact to systems, whereas an active approach may cause instability on a scanned system
 
 **Vulnerability scanning by eavesdropping is passive, while penetration testing with credentials is active.**
 
 
 1.
 **Reconnaissance** is a type of assessment activity that maps the potential attack surface by identifying the nodes and connections that make up the network.
 
 **[[Topology discovery]]** (or "footprinting") means scanning for hosts, IP ranges, and routes between networks to map out the structure of the target network. Topology discovery can also be used to build an asset database and to identify non-authorized hosts (rogue system detection) or network configuration errors.
 
 OS fingerprinting
 
 Packet and protocol analysis is another crucial security #assessment and monitoring process:
 -   Packet analysis refers to deep-down frame-by-frame scrutiny of captured frames.
-   Protocol analysis means using statistical tools to analyze a sequence of packets, or packet trace.

A **protocol analyzer** (or packet analyzer) works in conjunction with a sniffer to perform traffic analysis. You can either analyze a live capture or open a saved capture (.pcap) file. Protocol analyzers can decode a captured frame to reveal its contents in a readable format. You can choose to view a summary of the frame or choose a more detailed view that provides information on the OSI layer, protocol, function, and data.

[[packet injection]]: Some reconnaissance techniques and tests depend on sending forged or spoofed network traffic. Often, network sniffing software libraries allow frames to be inserted (or injected) into the network stream. There are also tools that allow for different kinds of packets to be crafted and manipulated. Well-known tools used for 