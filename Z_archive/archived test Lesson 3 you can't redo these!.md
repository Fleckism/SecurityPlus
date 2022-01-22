# q1
In which of these situations might a non-credentialed vulnerability scan be more advantageous than a credentialed scan? **(Select all that apply.)**

1.  When active scanning poses no risk to system stability
2.  External assessments of a network perimeter
3.  Detection of security setting misconfiguration
4.  ==Web application scanning==

Solution

Non-credentialed scanning is often the most appropriate technique for external assessment of the network perimeter or when performing web application scanning.

A non-credentialed scan proceeds by directing test packets at a host without being able to log on to the OS or application. A non-credentialed scan provides a view of what the host exposes to an unprivileged user on the network.

A passive scan has the least impact on the network and on hosts but is less likely to identify vulnerabilities comprehensively.

Configuration reviews investigate how system misconfigurations make controls less effective or ineffective, such as antivirus software not being updated, or management passwords left configured to the default. Configuration reviews generally require a credentialed scan

# q2
Which of the following statements summarizes a disadvantage to performing an active vulnerability scan? **(Select all that apply.)**

1.  ==Active scanning consumes more network bandwidth.
2.  ==Active scanning runs the risk of causing an outage.==
3.  Active scanning may fail to identify all of a system’s known vulnerabilities.
4.  Active scanning techniques do not use system login.

Solution

Scan intrusiveness is a measure of how much the scanner interacts with the target. Active scanning consumes more network bandwidth than passive scanning.

Active scanning means probing the device's configuration using some type of network connection with the target. This type of scanning runs the risk of crashing the target of the scan or causing some other sort of outage.

Passive scanning has the least impact on the network and on hosts but is less likely to identify vulnerabilities comprehensively.

A non-credentialed scan proceeds by directing test packets at a host without being able to log on to the OS or application. A non-credentialed scan provides a view of what the host exposes to an unprivileged user on the network.

# q3
Encryption vulnerabilities allow unauthorized access to protected data. Which component is subject to brute-force enumeration?

1.  An unsecured protocol
2.  A software vulnerability
==3.  A weak cipher==
4.  A lost decryption key

Solution

An unsecured protocol is one that transfers data as cleartext—that is, the protocol does not use encryption for data protection.

Software vulnerabilities affect all types of code. Operating system and firmware vulnerabilities may allow escalated permissions and unauthorized access. Software and security researchers discover most vulnerabilities and release patches to remedy them.

Weak encryption vulnerabilities allow unauthorized access to data. An algorithm or cipher used for encryption has known weaknesses that allow brute-force enumeration.

If a decryption key is not distributed securely, it can easily fall into the hands of people who are not authorized to decrypt the data.

# q4
Following a **data breach** at a large retail company, their public relations team issues a statement emphasizing the company’s commitment to consumer privacy. Identify the true statements concerning this event. **(Select all that apply.)**

1.  The data breach must be an intentional act of corporate sabotage.
2.  ==The privacy breach may allow the threat actor to sell the data to other malicious actors.==
3.  ==Data exfiltration by a malicious actor may have caused the data breach==.
4.  The data breach event may compromise data integrity, but not information availability.

Solution

A privacy breach may allow the threat actor to perform identity theft or to sell the data to other malicious actors. Malicious actors may obtain account credentials or use personal details and financial information to make fraudulent credit applications and purchases.

A data breach is a consequence of a data exfiltration event. A data exfiltration event is always intentional and malicious.

A data breach event is where confidential data is read or transferred without authorization. A data breach, unlike data exfiltration, can be intentional/malicious or unintentional/accidental.

Availability means that information is accessible to those authorized to view or modify it. If a data breach brings down processing systems, a company may not be able to perform crucial workflows like order processing and fulfillment, compromising information availability.

# q5
Which statement best explains the differences between black box, white box, and gray box attack profiles used in penetration testing?

1.  A black box pen tester acts as a privileged insider and must perform no reconnaissance. A white box pen tester has no access, and reconnaissance is necessary. A gray box actor is a third-party actor who mediates between a black box and white box pen tester.
2.  A black box pen tester acts as the adversary in the test, while the white box pen tester acts in a defensive role. A gray box pen tester is a third-party actor who mediates between a black box pen tester and a white box pen tester.
3.  ==In a black box pen test, the contractor receives no privileged information, so they must perform reconnaissance. In contrast, a white box pen tester has complete access and skips reconnaissance. A gray box tester has some, but not all information, and requires partial reconnaissance.==
4.  In a white box pen test, the contractor receives no privileged information, so they must perform reconnaissance. In contrast, a black box pen tester has complete access and skips reconnaissance. A gray box tester has some, but not all information, and requires partial reconnaissance.

Solution

A black box penetration tester receives no privileged information, while a white box tester has complete access. A white box test may follow up on a black box test.

In a black box pen test, the consultant receives no privileged information about the network and its security systems. A gray box pen tester has partial access and must perform some reconnaissance.

A red team performs an offensive role to try to infiltrate the target. A blue team defends a target system by operating monitoring and alerting controls to detect and prevent the infiltration.

White box tests are useful for simulating the behavior of a privileged insider threat. Gray box tests are useful for simulating the behavior of an unprivileged insider threat.
# q
A contractor has been hired to conduct penetration testing on a company's network. They have decided to try to crack the passwords on a percentage of systems within the company. They plan to annotate the type of data that is on the systems that they can successfully crack to prove the ease of access to data. Evaluate the penetration steps and determine which are being utilized for this task. **(Select all that apply.)**

1.  ==Test security controls==
2.  Bypass security controls
3.  Verify a threat exists
4.  ==Exploit vulnerabilities==

Solution

Two penetration test steps are being utilized by actively testing security controls and exploiting the vulnerabilities. Identifying weak passwords is actively testing security controls.

In addition, exploiting vulnerabilities is being used by proving that a vulnerability is high risk. The list of critical data obtained will prove that the weak passwords can allow access to critical information.

Bypassing security controls can be accomplished by going around controls that are already in place to gain access.

Verifying that a threat exists would have consisted of using surveillance, social engineering, network scanners, and/or vulnerability assessment tools to identify vulnerabilities.

# q 
During a penetration test, systems administrators for a large company are tasked to play on the white team for an affiliated company. Examine each of the following roles and determine which role the systems admins will fill.

1.  ==The systems admins will arbitrate the exercise, setting rules of engagement and guidance.==
2.  The systems admins will try to infiltrate the target system.
3.  The systems admins will operate monitoring and alerting controls to detect and prevent the infiltration.
4.  The systems admins will collaborate with attackers and defenders to promote constructive developments.

Solution

A white team sets the rules of engagement and monitors the exercise, providing arbitration and guidance, and if necessary, halt the exercise. If the red team is third party, the white team will include a representative of the consultancy company.

The red team acts offensively to try to infiltrate the target system.

The blue team performs the defensive role by operating monitoring and alerting controls to detect and prevent the infiltration.

The confrontational structure in a typical red team/blue team test does not always promote constructive development and improvement. In a purple team exercise, the red and blue teams meet for regular debriefs while the exercise is ongoing.
# q 
Select the statement which best describes the difference between a zero-day vulnerability and a legacy platform vulnerability.

1.  ==A legacy platform vulnerability is unpatchable, while a zero-day vulnerability may be exploited before a developer can create a patch for it.==
2.  A zero-day vulnerability is unpatchable, while a legacy platform vulnerability can be patched, once detected.
3.  A zero-day vulnerability can be mitigated by responsible patch management, while a legacy platform vulnerability cannot be patched.
4.  A legacy platform vulnerability can be mitigated by responsible patch management, while a zero-day vulnerability does not yet have a patch solution.

Solution

A zero-day vulnerability is exploited before the developer knows about it or can release a patch. These can be extremely destructive, as it can take the vendor some time to develop a patch, leaving systems vulnerable in the interim.

A legacy platform is no longer supported with security patches by its developer or vendor. By definition, legacy platforms are not patchable.

Legacy systems are highly likely to be vulnerable to exploits and must be protected by security controls other than patching, such as isolating them to networks that an attacker cannot physically connect to.

Even if effective patch management procedures are in place, attackers may still be able to use zero-day software vulnerabilities, before a vendor develops a patch.
# q 
A manufacturing company hires a pentesting firm to uncover any vulnerabilities in their network with the understanding that the pen tester receives no information about the company’s system. Which of the following penetration testing strategies is the manufacturing company requesting?

==1.  Black box==
2.  Sandbox
3.  Gray box
4.  White box

Solution

A sandbox is a test environment that accurately simulates a production environment. It is not a penetration testing strategy.

Black box (or blind) is when the pen tester receives no privileged information about the network and its security systems. Black box tests are useful for simulating the behavior of an external threat.

Gray box describes the penetration strategy where the pen tester receives some information. Typically, this would resemble the knowledge of junior or non-IT staff to model particular types of insider threats.

White box (or full disclosure) is when the pen tester receives complete access to information about the network. White box tests are useful for simulating the behavior of a privileged insider threat.
# q 
A hacker set up a Command and Control network to control a compromised host. What is the ability of the hacker to use this remote connection method as needed known as?

1.  Weaponization
2.  ==Persistence==
3.  Reconnaissance
4.  Pivoting

Solution

Persistence refers to the hacker’s ability to reconnect to the compromised host and use it as a Remote Access Tool (RAT) or backdoor. To do this, the hacker must establish a Command and Control (C2 or C&C) network.

Weaponization is an exploit used to gain some sort of access to a target's network, but it doesn't involve being able to reconnect.

Reconnaissance is the process of gathering information, it is not related to Command and Control networks.

Pivoting follows persistence. It involves a system and/or set of privileges that allow the hacker to compromise other network systems (lateral spread). The hacker likely has to find some way of escalating the privileges available to him/her.
# q 
Examine each attack vector. Which is most vulnerable to escalation of privileges?

1.  Software
==2.  Operating System (OS)==3.  Applications
4.  Ports

Solution

A vulnerability in an OS kernel file or shared library can allow privilege escalation, where the malware code runs with higher access rights (system or root). Root or system accounts are considered superuser accounts with administrative privileges.

Software exploitation means an attack that targets a vulnerability in software code.

An application vulnerability is a design flaw that can cause the security system to be circumvented or that will cause the application to crash.

Security best practice for network configurations dictates that open ports should be restricted to only necessary services. Running unnecessary open ports and services increases the attack surface.
# q 
An outside security consultant updates a company’s network, including data cloud storage solutions. The consultant leaves the manufacturer’s default settings when installing network switches, assuming the vendor shipped the switches in a default-secure configuration. Examine the company’s network security posture and select the statements that describe key vulnerabilities in this network. **(Select all that apply.)**

1.  **The network is open to third-party risks from using an outside contractor to configure cloud storage settings.**
2.  **The default settings in the network switches represent a weak configuration.**
3.  The use of network switches leaves numerous unused ports open.
4.  The default settings in the network switches represent unsecured protocols.

Solution

Weaknesses in products or services in a supply chain can impact service availability and performance, or lead to data breaches. Suppliers and vendors in the chain rely on each other to perform due diligence.

Relying on the manufacturer default settings when deploying an appliance or software applications is a weak configuration. Although many vendors ship products in secure default configurations, it is insufficient to rely on default settings.

Default settings may leave unsecure interfaces enabled that allow an attacker to compromise the device. Weak settings on network appliances can allow attackers to move through the network unhindered and snoop on traffic.

An unsecure protocol transfers data as cleartext. It does not use encryption for data protection.
# q 
A network administrator uses two different automated vulnerability scanners. They regularly update with the latest vulnerability feeds. If the system regularly performs active scans, what type of error is the system most likely to make?

**1.  False positive**
2.  False negative
3.  Validation error
4.  Configuration error

Solution

A false positive is something that is identified by a scanner or other assessment tool as being a vulnerability, when in fact it is not.

False negatives are potential vulnerabilities that are not identified in a scan. This risk can be mitigated somewhat by running repeat scans periodically and by using scanners from more than one vendor.

Reviewing related system and network logs can enhance the vulnerability report validation process. Using relevant data, such as event logs, can help confirm the validity of vulnerabilities identified in a scan.

Some scanners measure systems and configuration settings against best practice frameworks. This is called a compliance scan, which might be necessary for regulatory compliance or voluntary conformance.
# q 
Select the appropriate methods for packet capture. **(Select all that apply.)**

1.  **Wireshark**
2.  Packet analyzer
3.  Packet injection
4.  **tcpdump**

Solution

Wireshark and tcdump are packet sniffers. A sniffer is a tool that captures packets, or frames, moving over a network.

Wireshark is an open source graphical packet capture and analysis utility. Wireshark works with most operating systems, where tcpdump is a command line packet capture utility for Linux.

A packet analyzer works in conjunction with a sniffer to perform traffic analysis. Protocol analyzers can decode a captured frame to reveal its contents in a readable format, but they do not capture packets.

A packet injection involves sending forged or spoofed network traffic by inserting (or injecting) frames into the network stream. Packets are not captured with packet injection.
# q 
Analyze and eliminate the item that is NOT an example of a reconnaissance technique.

1.  **Initial exploitation**
2.  Open Source Intelligence (OSINT)
3.  Social engineering
4.  Scanning

Solution

The initial exploitation phase (also referred to as weaponization) is not a reconnaissance technique. It is an exploit that is used to gain some sort of access to the target's network.

Open Source Intelligence (OSINT) refers to using web search tools and social media to obtain information about the target.

Social engineering refers to obtaining information, physical access to premises, or even access to a user account through the art of persuasion.

Scanning refers to using software tools to obtain information about a host or network topology. Scans may be launched against web hosts or against wired or wireless network segments, if the attacker can gain physical access to them.
# q 
A system administrator must scan the company’s web-based application to identify which ports are open and which operating system can be seen from the outside world. Determine the syntax that should be used to yield the desired information if the administrator will be executing this task from a Linux command line.

1.  netstat -a
2.  **nmap -O webapp.company.com**
3.  nmap -sS 10.1.0.0/24
4.  netstat -n

Solution

The correct syntax is nmap -O webapp.company.com. When the -O switch is used with nmap, it displays open ports and running software, but does not show the version.

The netstat command checks the state of ports on the local machine. In Linux, the -a switch displays ports in the listening state, it does not enable software and version detection.

Using nmap -sS 10.1.0.0/24 is a fast technique also referred to as half-open scanning, as the scanning host requests a connection without acknowledging it. 

Netstat shows the state of TCP/UDP ports on the local machine. Netstat -n suppresses name resolution, so host IP addresses and numeric ports are shown in the output.
# q 
Identify the command that can be used to detect the presence of a host on a particular IP address.

1.  ipconfig
2.  ifconfig
3.  ip
4.  **ping**

Solution

The ping command can be used to detect the presence of a host on a particular IP address or that responds to a particular host name. This command is a fast and easy way to determine if a system can communicate over the network with another system.

The ipconfig command is used to report the configuration assigned to the network adapter in Windows.

The ifconfig command can be used to report the adapter configuration in Linux.

The ip command is a more powerful command in Linux and gives options for managing routes as well as the local interface configuration.
# q 
An IT director reads about a new form of malware that targets a system widely utilized in the company’s network. The director wants to discover whether the network has been targeted, but also wants to conduct the scan without disrupting company operations or tipping off potential attackers to the investigation. Evaluate vulnerability scanning techniques and determine the best tool for the investigation.

1.  Credentialed scan
2.  Configuration review
3.  Penetration testing
4.  **Threat hunting**

Solution

Where a pen test attempts to demonstrate a system’s weakness or achieve intrusion, threat hunting is based only on analysis of data within the system. It is potentially less disruptive than pen testing.

A credentialed scan has a user account with logon rights to hosts and permissions appropriate for the testing routines. Credentialed scans are intrusive and allow in-depth analysis and insight to what an insider attack might achieve.

A configuration review assesses the configuration of security controls and application settings & permissions compared to established benchmarks.

Penetration testing, an intrusive, active scanning technique, does not stop at detection, but attempts to gain access to a system.
# q 
Compare and contrast vulnerability scanning and penetration testing. Select the true statement from the following options.

1.  Vulnerability scanning is conducted by a “white hat” and penetration testing is carried out by a “black hat.”
2.  **Vulnerability scanning by eavesdropping is passive, while penetration testing with credentials is active.**
3.  Penetration testing and vulnerability scanning are considered “black hat” practices.
4.  Vulnerability scanning is part of network reconnaissance, but penetration testing is not.

Solution

Vulnerability scanning and penetration testing can use passive or active reconnaissance techniques. A passive approach tries to discover issues without causing an impact to systems, whereas an active approach may cause instability on a scanned system.

Penetration testing is non-malicious; therefore, it is a “white hat” activity, not “black hat.”

Penetration testing is considered “ethical hacking,” but vulnerability scanning is not. Vulnerability scanning is used to uncover system weaknesses, not to try to hack into the system.

Both vulnerability scanning and penetration testing are forms of reconnaissance, or information gathering. The hacker likely has to find some way of escalating the privileges available to them.
# q 
A network manager needs a map of the network's topology. The network manager is using Network Mapper (Nmap) and will obtain the visual map with the Zenmap tool. If the target IP address is 192.168.1.1, determine the command within Nmap that will return the necessary data to build the visual map of the network topology.

1.  nmap -sn --ipconfig 192.168.1.1
2.  nmap -sn --ifconfig 192.168.1.1
3.  **nmap -sn --traceroute 192.168.1.1**
4.  nmap -sn --nslookup 192.168.1.1

Solution

The traceroute command is used to probe a path from one end system to another, and lists the intermediate systems providing the link. The Nmap combined with Zenmap tools will give a visual of the network topology.

The ipconfig and ifconfig commands are used for looking at the configuration of a system's network adapter.

The primary difference between the ipconfig and ifconfig commands are the type of systems the network is using. The ipconfig is designed for Windows, while the ifconfig is designed for use on Linux systems.

The nslookup command is used to query the Domain Name System (DNS).
# q 
# q 
# q 
# q 
# q 
# q 
# q 
# q 
# q 

# q 
# q 
# q 
# q 
# q 

