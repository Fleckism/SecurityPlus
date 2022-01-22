## First Fold
attacks
threats
	- structured(targeted) or unstructured(opportunistic)
	- Malicious intent or accidental or unintentional threat actor and agents. 
	- Unintentional
		- Accidents, oversights, and other mistakes.
	
	
vulnerabilities
architecture and design
threat actor
attack vectors
Threat types:   viruses or rootkits, Trojans, botnets, and specific software vulnerabilities

Capability:  Script kiddie using a commodity attack tool that are widely available on the web or dark web.  More capable threat actors take advantage of zero-day exploits.

Hacker: describes an individual who has the skills to gain access to computer systems through unauthorized or unapproved mean

A script kiddie is someone who uses hacker tools without necessarily understanding how they work or having the ability to craft new attack

Advanced Persistent Threat (APT) APT refers to the ongoing ability of an adversary to compromise network security—to obtain and maintain access—using a variety of tools and techniques.

 shadow IT, where users purchase or introduce computer hardware or software to the workplace without the sanction of the IT department and without going through a procurement and security analysis process.
 
  attack vector is the path that a threat actor uses to gain access to a secure system
  
  access means being able to run malicious code on the target.
  
  deep web is any part of the World Wide Web that is not indexed by a search engine
  
  A tactic, technique, or procedure (TTP) is a generalized statement of adversary behavior. 2A
  	- TTPs describe what and how an adversary acts and Indicators describe how to recognize what those actions might look like.
  
  As a military term, Army [doctrine](http://armypubs.army.mil/doctrine/DR_pubs/dr_a/pdf/adrp1_02.pdf) is defined as the fundamental principles by which the military forces or elements thereof guide their actions in support of national objectives. 2A
  
  indicator of compromise (IoC) is a residual sign that an asset or network has been successfully attacked or is continuing to be attacked. Put another way, an IoC is evidence of a TTP.

-   ipconfig—show the configuration assigned to network interface(s) in Windows, including the hardware or media access control (MAC) address, IPv4 and IPv6 addresses, default gateway, and whether the address is static or assigned by DHCP. If the address is DHCP-assigned, the output also shows the address of the DHCP server that provided the lease.
-   ifconfig—show the configuration assigned to network interface(s) in Linux.
-   ping—probe a host on a particular IP address or host name using Internet Control Message Protocol (ICMP). You can use ping with a simple script to perform a sweep of all the IP addresses in a subnet. The following example will scan the 10.1.0.0/24 subnet from a Windows machine:
-   arp—display the local machine's Address Resolution Protocol (ARP) cache. The ARP cache shows the MAC address of the interface associated with each IP address the local host has communicated with recently. This can be useful if you are investigating a suspected spoofing attack. For example, a sign of a man-in-the-middle attack is where the MAC address of the default gateway IP listed in the cache is not the legitimate router's MAC address.

  -   route—view and configure the host's local routing table. Most end systems use a default route to forward all traffic for remote networks via a gateway router. If the host is not a router, additional entries in the routing table could be suspicious.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8872-1599771794749.png)

Output from the route command on a Linux host. Most endpoints have a simple routing table, similar to this. It shows the default route (0.0.0.0/0) via the host configured as the default gateway (10.1.0.254) over the network interface eth0. The second line of the table shows the subnet for local traffic (10.1.0.0/24). This network is directly connected, represented by the 0.0.0.0 gateway.

-   tracert—uses ICMP probes to report the round trip time (RTT) for hops between the local host and a host on a remote network. tracert is the Windows version of the tool.
-   traceroute—performs route discovery from a Linux host. traceroute uses UDP probes rather than ICMP, by default.
-   pathping—provides statistics for latency and packet loss along a route over a longer measuring period. pathping is a Windows tool; the equivalent on Linux is mtr.

(.pcap) file


-   Open Vulnerability and Assessment Language (OVAL)—an XML schema for describing system security state and querying vulnerability reports and information.


Tactics:  A plan for attaining a particular goal
- Describe the way the threat actor operates.
Technique: A method( A systematic way of doing something implies an orderly logical arrangement)
Procedure:  A particular course of action.
- A set of techniques is a procedure.

#fleck Function: Are what controls tell you to do.?
	What something does or is used for
#fleck Control:  Are the processes you have in place.

Cipher: An encrypted algorithm
unsecured protocol: is one that transfers data as cleartext—that is, the protocol does not use encryption for data protection.
#fleck 
#F_detect : To discover or find by careful search.
#F_respond : A reaction
#F_identify : To establish the identity of someone or something.
#threat :  A source of danger
#C_managerial :Policies, procedures, rules of behavior

# IoA/C
#IoA_C : Definition
IoA:  Indicator of an attack that is currently happening.
IoC:  are “pieces of forensic data, such as data found in system log entries or files, that identify potentially malicious activity on a system or network.” Indicators of compromise aid information security and IT professionals in detecting data breaches, malware infections, or other threat activity. By monitoring for indicators of compromise, organizations can detect attacks and act quickly to prevent breaches from occurring or limit damages by stopping attacks in earlier stages.
				
				There are several indicators of compromise that organizations should monitor. In an [article for DarkReading](http://www.darkreading.com/attacks-breaches/top-15-indicators-of-compromise/d/d-id/1140647?), Ericka Chickowski highlights 15 key indicators of compromise:

-   Unusual Outbound Network Traffic
-   Anomalies in Privileged User Account Activity
-   Geographical Irregularities
-   Log-In Red Flags
-   Increases in Database Read Volume
-   HTML Response Sizes
-   Large Numbers of Requests for the Same File
-   Mismatched Port-Application Traffic
-   Suspicious Registry or System File Changes
-   Unusual DNS Requests
-   Unexpected Patching of Systems
-   Mobile Device Profile Changes
-   Bundles of Data in the Wrong Place
-   Web Traffic with Unhuman Behavior
-   Signs of DDoS Activity

# threat
#threat : a **threat** is a potential negative action or event facilitated by a [vulnerability] that results in an unwanted impact to a computer system or application.

# vulnerability
#vulnerability : is a weakness which can be exploited by a threat actor

# implement
#implementations:  Put a decision or plan into effect

# zero-day vulnerability
#threat  zero-day vulnerability is exploited before the developer knows about it or can release a patch. These can be extremely destructive, as it can take the vendor some time to develop a patch, leaving systems vulnerable in the interim.

# Organized
#fleck Function: Are what controls tell you to do.?
	What something does or is used for
#fleck Control:  Are the processes you have in place.

Cipher: An encrypted algorithm
unsecured protocol: is one that transfers data as cleartext—that is, the protocol does not use encryption for data protection.
#fleck 
#F_detect : To discover or find by careful search.
#F_respond : A reaction
#F_identify : To establish the identity of someone or something.
#threat :  A source of danger
#C_managerial :Policies, procedures, rules of behavior