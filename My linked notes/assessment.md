---
tags: [Implementation, OIR, vulnerability, threat, ]

---
See pdf on desktop!

These assessments involve 
- [[vulnerability]]
- [[threat]]
- [[risk]]


The main types of security [[assessment]]  are usually classed as 
- **vulnerability assessment, 
- **threat hunting**, and 
- **penetration testing**. 


Threat hunting and security monitoring must use **behavioral-based techniques** to identify infections. This means close analysis of the processes running in system memory on a host. To perform abnormal process behavior analysis effectively, you should build up a sense of what is "normal" in a system and spot deviations in a potentially infected system.

A vulnerability assessment is an evaluation of a system's security and ability to meet compliance requirements based on the configuration state of the system. Essentially, the vulnerability assessment determines if the current configuration matches the ideal configuration (the baseline). Vulnerability assessments might involve manual inspection of security controls, but are more often accomplished through automated vulnerability scanners.
vulnerabilities, threats, and risk: 

The process of identifying, estimating, and prioritizing risks to organizational operations (including mission, functions, image, reputation), organizational assets, individuals, other organizations, and the Nation, resulting from the operation of an information system. Part of risk management, incorporates threat and vulnerability analyses, and considers mitigations provided by security controls planned or in place. Synonymous with risk analysis

Taken From
([nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-30r1.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/nistspecialpublication800-30r1.pdf)).

Security assessment refers to processes and tools that **evaluate the attack surface**.:

 The process of mapping out the attack surface is referred to as network [[reconnaissance]] and discovery

Where [[vulnerability]] scanning uses lists of patches and standard definitions of baseline configurations, [[threat hunting]] is an assessment technique that utilizes insights gained from threat intelligence to proactively discover whether there is evidence of [[TTPs]] already present within the network or system. This contrasts with a reactive process that is only triggered when alert conditions are reported through an incident management system. You can also contrast threat hunting with penetration testing. Where a pen test attempts to achieve some sort of system intrusion or concrete demonstration of weakness, threat hunting is based only on analysis of data within the system. To that extent, it is less potentially disruptive than pen testing.

 

 
-   [[ipconfig]]—show the configuration assigned to network interface(s) in Windows, including the hardware or media access control (MAC) address, IPv4 and IPv6 addresses.
-   [[ifconfig]]—show the configuration assigned to network interface(s) in Linux.
-   [[ping]]—
-   arp—display the local machine's Address Resolution Protocol ([[ARP]]) cache.
-   host discovery scan

next step in network reconnaissance is to work out which operating systems are in use, which network services each host is running, and, if possible, which application software is underpinning those services.

Are these all the steps in an assessment?
- security assessments, network reconnaissance, vulnerability scanning, and penetration testing
- ==Network reconnaissance and discovery is used to identify hosts, network topology, and open services/ports, establishing an overall attack surface.==

- Network [[reconnaissance]]... is it the same as Evaluate attack surface 
	- Identify active IP hosts
	- Host discovery scan vs service discovery:  To see which operating systems are in use, which network services, which application software.


# Dump
**vulnerability assessment, threat hunting, and penetration testing**
 
 Vulnerability scanning and penetration testing can use passive or active reconnaissance techniques. A passive approach tries to discover issues without causing an impact to systems, whereas an active approach may cause instability on a scanned system
 
 **Vulnerability scanning by eavesdropping is passive, while penetration testing with credentials is active.**
 
 
 1.
 **Reconnaissance** is a type of assessment activity that maps the potential attack surface by identifying the nodes and connections that make up the network.
 
 **[[Topology discovery]]** (or "footprinting") means scanning for hosts, IP ranges, and routes between networks to map out the structure of the target network. Topology discovery can also be used to build an asset database and to identify non-authorized hosts (rogue system detection) or network configuration errors.
 
 OS fingerprinting
 
 Packet and protocol analysis is another crucial security assessment and monitoring process:
 -   Packet analysis refers to deep-down frame-by-frame scrutiny of captured frames.
-   Protocol analysis means using statistical tools to analyze a sequence of packets, or packet trace.

A **protocol analyzer** (or packet analyzer) works in conjunction with a sniffer to perform traffic analysis. You can either analyze a live capture or open a saved capture (.pcap) file. Protocol analyzers can decode a captured frame to reveal its contents in a readable format. You can choose to view a summary of the frame or choose a more detailed view that provides information on the OSI layer, protocol, function, and data.

[[packet injection]]: Some reconnaissance techniques and tests depend on sending forged or spoofed network traffic. Often, network sniffing software libraries allow frames to be inserted (or injected) into the network stream. There are also tools that allow for different kinds of packets to be crafted and manipulated. Well-known tools used for 

[[3C  Vulnerability Scanning Technics]]