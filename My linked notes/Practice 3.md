The ping command can be used to detect the presence of a host on a particular IP address or that responds to a particular host name. This command is a fast and easy way to determine if a system can communicate over the network with another system.

The ipconfig command is used to report the configuration assigned to the network adapter in Windows.

The ifconfig command can be used to report the adapter configuration in Linux.

The ip command is a more powerful command in Linux and gives options for managing routes as well as the local interface configuration.

The traceroute command is used to probe a path from one end system to another, and lists the intermediate systems providing the link. The Nmap combined with Zenmap tools will give a visual of the network topology.

The ipconfig and ifconfig commands are used for looking at the configuration of a system's network adapter.

The primary difference between the ipconfig and ifconfig commands are the type of systems the network is using. The ipconfig is designed for Windows, while the ifconfig is designed for use on Linux systems.

The nslookup command is used to query the Domain Name System (DNS).

The correct syntax is nmap -O. When the -O switch is used with nmap, it displays open ports and running software, but does not show the version.

The netstat command checks the state of ports on the local machine. In Linux, the -a switch displays ports in the listening state, it does not enable software and version detection.

Using nmap -sS 10.1.0.0/24 is a fast technique also referred to as half-open scanning, as the scanning host requests a connection without acknowledging it. 

Netstat shows the state of TCP/UDP ports on the local machine. Netstat -n suppresses name resolution, so host IP addresses and numeric ports are shown in the output.

Wireshark and tcdump are packet sniffers. A sniffer is a tool that captures packets, or frames, moving over a network.

Wireshark is an open source graphical packet capture and analysis utility. Wireshark works with most operating systems, where tcpdump is a command line packet capture utility for Linux.

A packet analyzer works in conjunction with a sniffer to perform traffic analysis. Protocol analyzers can decode a captured frame to reveal its contents in a readable format, but they do not capture packets.

A packet injection involves sending forged or spoofed network traffic by inserting (or injecting) frames into the network stream. Packets are not captured with packet injection.

The initial exploitation phase (also referred to as weaponization) is not a reconnaissance technique. It is an exploit that is used to gain some sort of access to the target's network.

Open Source Intelligence (OSINT) refers to using web search tools and social media to obtain information about the target.

Social engineering refers to obtaining information, physical access to premises, or even access to a user account through the art of persuasion.

Scanning refers to using software tools to obtain information about a host or network topology. Scans may be launched against web hosts or against wired or wireless network segments, if the attacker can gain physical access to them.

A zero-day vulnerability is exploited before the developer knows about it or can release a patch. These can be extremely destructive, as it can take the vendor some time to develop a patch, leaving systems vulnerable in the interim.

A legacy platform is no longer supported with security patches by its developer or vendor. By definition, legacy platforms are not patchable.

Legacy systems are highly likely to be vulnerable to exploits and must be protected by security controls other than patching, such as isolating them to networks that an attacker cannot physically connect to.

Even if effective patch management procedures are in place, attackers may still be able to use zero-day software [[vulnerability|vulnerabilities]], before a vendor develops a patch.

A vulnerability in an OS kernel file or shared library can allow privilege escalation, where the malware code runs with higher access rights (system or root). Root or system accounts are considered superuser accounts with administrative privileges.

Software exploitation means an attack that targets a vulnerability in software code.

An application vulnerability is a design flaw that can cause the security system to be circumvented or that will cause the application to crash.

Security best practice for network configurations dictates that open ports should be restricted to only necessary services. Running unnecessary open ports and services increases the attack surface.

Weaknesses in products or services in a supply chain can impact service availability and performance, or lead to data breaches. Suppliers and vendors in the chain rely on each other to perform due diligence.

Relying on the manufacturer default settings when deploying an appliance or software applications is a weak configuration. Although many vendors ship products in secure default configurations, it is insufficient to rely on default settings.

Default settings may leave unsecure interfaces enabled that allow an attacker to compromise the device. Weak settings on network appliances can allow attackers to move through the network unhindered and snoop on traffic.

An unsecure protocol transfers data as cleartext. It does not use encryption for data protection.

An unsecured protocol is one that transfers data as cleartext—that is, the protocol does not use encryption for data protection.

Software [[vulnerability|vulnerabilities]] affect all types of code. Operating system and firmware [[vulnerability|vulnerabilities]] may allow escalated permissions and unauthorized access. Software and security researchers discover most [[vulnerability|vulnerabilities]] and release patches to remedy them.

Weak encryption [[vulnerability|vulnerabilities]] allow unauthorized access to data. An algorithm or cipher used for encryption has known weaknesses that allow brute-force enumeration.

If a decryption key is not distributed securely, it can easily fall into the hands of people who are not authorized to decrypt the data.

A privacy breach may allow the threat actor to perform identity theft or to sell the data to other malicious actors. Malicious actors may obtain account credentials or use personal details and financial information to make fraudulent credit applications and purchases.

  
A data breach can cause a data exfiltration event to occur. A data exfiltration event is always intentional and malicious.

  
A data breach event is where confidential data is read or transferred without authorization. A data breach, unlike data exfiltration, can be intentional/malicious or unintentional/accidental.

  
Availability means that information is accessible to those authorized to view or modify it. If a data breach brings down processing systems, a company may not be able to perform crucial workflows like order processing and fulfillment, compromising information availability.

Vulnerability scanning and penetration testing can use passive or active reconnaissance techniques. A passive approach tries to discover issues without causing an impact to systems, whereas an active approach may cause instability on a scanned system.

Penetration testing is non-malicious; therefore, it is a “white hat” activity, not “black hat.”

Penetration testing is considered “ethical hacking,” but vulnerability scanning is not. Vulnerability scanning is used to uncover system weaknesses, not to try to hack into the system.

Both vulnerability scanning and penetration testing are forms of reconnaissance, or information gathering. The hacker likely has to find some way of escalating the privileges available to them.

Where a pen test attempts to demonstrate a system’s weakness or achieve intrusion, threat hunting is based only on analysis of data within the system. It is potentially less disruptive than pen testing.

A credentialed scan has a user account with logon rights to hosts and permissions appropriate for the testing routines. Credentialed scans are intrusive and allow in-depth analysis and insight to what an insider attack might achieve.

A configuration review assesses the configuration of security controls and application settings & permissions compared to established benchmarks.

Penetration testing, an intrusive, active scanning technique, does not stop at detection, but attempts to gain access to a system.

A false positive is something that is identified by a scanner or other assessment tool as being a vulnerability, when in fact it is not.

False negatives are potential [[vulnerability|vulnerabilities]] that are not identified in a scan. This risk can be mitigated somewhat by running repeat scans periodically and by using scanners from more than one vendor.

Reviewing related system and network logs can enhance the vulnerability report validation process. Using relevant data, such as event logs, can help confirm the validity of [[vulnerability|vulnerabilities]] identified in a scan.

Some scanners measure systems and configuration settings against best practice frameworks. This is called a compliance scan, which might be necessary for regulatory compliance or voluntary conformance.

Scan intrusiveness is a measure of how much the scanner interacts with the target. Active scanning consumes more network bandwidth than passive scanning.

Active scanning means probing the device's configuration using some type of network connection with the target. This type of scanning runs the risk of crashing the target of the scan or causing some other sort of outage.

Active scanning has the possibility of failing due to any security settings that may prevent certain scans.

A non-credentialed scan proceeds by directing test packets at a host without being able to log on to the OS or application. A non-credentialed scan provides a view of what the host exposes to an unprivileged user on the network.

Non-credentialed scanning is often the most appropriate technique for external assessment of the network perimeter or when performing web application scanning.

A non-credentialed scan proceeds by directing test packets at a host without being able to log on to the OS or application. A non-credentialed scan provides a view of what the host exposes to an unprivileged user on the network.

A passive scan has the least impact on the network and on hosts but is less likely to identify [[vulnerability|vulnerabilities]] comprehensively.

Configuration reviews investigate how system misconfigurations make controls less effective or ineffective, such as antivirus software not being updated, or management passwords left configured to the default. Configuration reviews generally require a credentialed scan.

Two penetration test steps are being utilized by actively testing security controls and exploiting the [[vulnerability|vulnerabilities]]. Identifying weak passwords is actively testing security controls.

In addition, exploiting [[vulnerability|vulnerabilities]] is being used by proving that a vulnerability is high risk. The list of critical data obtained will prove that the weak passwords can allow access to critical information.

Bypassing security controls can be accomplished by going around controls that are already in place to gain access.

Verifying that a threat exists would have consisted of using surveillance, social engineering, network scanners, and/or vulnerability assessment tools to identify [[vulnerability|vulnerabilities]].

Black box (or blind) is when the pen tester receives no privileged information about the network and its security systems. Black box tests are useful for simulating the behavior of an external threat.

A sandbox is a test environment that accurately simulates a production environment. It is not a penetration testing strategy.

Gray box describes the penetration strategy where the pen tester receives some information. Typically, this would resemble the knowledge of junior or non-IT staff to model particular types of insider threats.

White box (or full disclosure) is when the pen tester receives complete access to information about the network. White box tests are useful for simulating the behavior of a privileged insider threat.

Persistence refers to the hacker’s ability to reconnect to the compromised host and use it as a Remote Access Tool (RAT) or backdoor. To do this, the hacker must establish a Command and Control (C2 or C&C) network.

Weaponization is an exploit used to gain some sort of access to a target's network, but it doesn't involve being able to reconnect.

Reconnaissance is the process of gathering information, it is not related to Command and Control networks.

Pivoting follows persistence. It involves a system and/or set of privileges that allow the hacker to compromise other network systems (lateral spread). The hacker likely has to find some way of escalating the privileges available to him/her.

A black box penetration tester receives no privileged information, while a white box tester has complete access. A white box test may follow up on a black box test.

In a black box pen test, the consultant receives no privileged information about the network and its security systems. A gray box pen tester has partial access and must perform some reconnaissance.

A red team performs an offensive role to try to infiltrate the target. A blue team defends a target system by operating monitoring and alerting controls to detect and prevent the infiltration.

White box tests are useful for simulating the behavior of a privileged insider threat. Gray box tests are useful for simulating the behavior of an unprivileged insider threat.

A white team sets the rules of engagement and monitors the exercise, providing arbitration and guidance, and if necessary, halt the exercise. If the red team is third party, the white team will include a representative of the consultancy company.

The red team acts offensively to try to infiltrate the target system.

The blue team performs the defensive role by operating monitoring and alerting controls to detect and prevent the infiltration.

The confrontational structure in a typical red team/blue team test does not always promote constructive development and improvement. In a purple team exercise, the red and blue teams meet for regular debriefs while the exercise is ongoing.