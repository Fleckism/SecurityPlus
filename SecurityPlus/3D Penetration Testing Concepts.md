---
tags: [section]
---

## EXAM OBJECTIVES COVERED

1.8 Explain the techniques used in penetration testing
#Ops 
Automated vulnerability scanning does not test what a highly capable [[threat actor]] might be able to achieve. Penetration testing is a type of assessment that adopts known tactics and techniques to attempt intrusions. Devising, planning, and leading penetration tests is a specialized security role, but at a junior level you are likely to participate in this type of engagement, so you should be able to explain the fundamental principles.

## PENETRATION TESTING

A penetration test—often shortened to [[pen test]]—uses authorized hacking techniques to discover exploitable weaknesses in the target's security systems. Pen testing is also referred to as _ethical hacking._ A pen test might involve the following steps:

-   **Verify a threat exists**—use surveillance, [[[[Social engineering]]]], network scanners, and vulnerability assessment tools to identify a vector by which vulnerabilities could be exploited.
-   **Bypass security controls**—look for easy ways to attack the system. For example, if the network is strongly protected by a firewall, is it possible to gain physical access to a computer in the building and run malware from a USB stick?
-   **Actively test security controls**—probe controls for configuration weaknesses and errors, such as weak passwords or software vulnerabilities.
-   **Exploit vulnerabilities**—prove that a vulnerability is high risk by exploiting it to gain access to data or install [[backdoor]]s. i.e. annotate the data that has been accessed

The key difference from passive vulnerability assessment is that an attempt is made to actively test [[security control]]s and exploit any vulnerabilities discovered. Pen testing is an intrusive assessment technique. For example, a vulnerability scan may reveal that an SQL Server has not been patched to safeguard against a known exploit. A penetration test would attempt to use the exploit to perform code injection and compromise and "own" (or "pwn" in hacker idiom) the server. This provides active testing of security controls. Even though the potential for the exploit exists, in practice the permissions on the server might prevent an attacker from using it. This would not be identified by a vulnerability scan, but should be proven or not proven to be the case by penetration testing.

## RULES OF ENGAGEMENT 

[[security assesment]]s might be performed by employees or may be contracted to consultants or other third parties. Rules of engagement specify what activity is permitted or not permitted. These rules should be made explicit in a contractual agreement. For example, a pen test should have a concrete objective and scope rather than a vague type of "Break into the network" aim. There may be systems and data that the penetration tester should not attempt to access or exploit. Where a pen test involves third-party services (such as a cloud provider), authorization to conduct the test must also be sought from the third party.

The Pentest-Standard website provides invaluable commentary on the conduct of pen tests ([pentest-standard.readthedocs.io/en/latest/tree.html](https://pentest-standard.readthedocs.io/en/latest/tree.html)).

### Attack Profile

Attacks come from different sources and motivations. You may wish to test both resistance to external (targeted and untargeted) and insider threats. You need to determine how much information about the network to provide to the consultant:

-    **Black box (or unknown environment)**—the consultant is given no privileged information about the network and its security systems. This type of test would require the tester to perform a [[reconnaissance]] phase. Black box tests are useful for simulating the behavior of an external threat.
-   **White box (or known environment)**—the consultant is given complete access to information about the network. This type of test is sometimes conducted as a follow-up to a black box test to fully evaluate flaws discovered during the black box test. The tester skips the [[reconnaissance]] phase in this type of test. White box tests are useful for simulating the behavior of a privileged insider threat.
-   **Gray box (or partially known environment)**—the consultant is given some information; typically, this would resemble the knowledge of junior or non-IT staff to model particular types of insider threats. This type of test requires partial [[reconnaissance]] on the part of the tester. Gray box tests are useful for simulating the behavior of an unprivileged insider threat.

A test where the attacker has no knowledge of the system but where staff are informed that a test will take place is referred to as a _blind_ (or _single-blind_) test. A test where staff are not made aware that a pen test will take place is referred to as a _double-blind test._

### Bug Bounty

A bug bounty is a program operated by a software vendor or website operator where rewards are given for reporting vulnerabilities. Where a pen test is performed on a contractual basis, costed by the consultant, a bug bounty program is a way of **crowd sourcing detection of vulnerabilities**. Some bug bounties are operated as internal programs, with rewards for employees only. Most are open to public submissions ([tripwire.com/state-of-security/security-data-protection/cyber-security/essential-bug-bounty-programs](https://www.tripwire.com/state-of-security/security-data-protection/cyber-security/essential-bug-bounty-programs/)).
## EXERCISE TYPES

Some of the techniques used in penetration testing may also be employed as an exercise between two competing teams:

-   **Red team**—performs the **offensive** role to try to infiltrate the target.
-   **Blue team**—performs the **defensive** role by operating monitoring and alerting controls to detect and prevent the infiltration.

There will also often be a **white team**, which **sets the rules of engagement** and monitors the exercise, providing arbitration and guidance, if necessary. If the red team is third party, the white team will include a representative of the consultancy company. One critical task of the white team is to halt the exercise should it become too risky. For example, an actual [[threat actor]] may attempt to piggyback a backdoor established by the red team.

In a red versus blue team exercise, the typical process is for the red team to attempt the intrusion and either succeed or fail, and then to write a summary report. This confrontational structure does not always promote constructive development and improvement. In a purple team exercise, the red and blue teams meet for regular debriefs while the exercise is ongoing. The red team might reveal where they have been successful and collaborate with the blue team on working out a detection mechanism. This process might be assisted by purple team members acting as facilitators. The drawback of a purple team exercise is that without blind or double-blind conditions, there is no simulation of a hostile adversary and the stresses of dealing with that.
## PASSIVE AND ACTIVE [[reconnaissance]]

Analysis of adversary [[TTPs]] has established various "[[kill chain]]" models of the way modern cyber-attacks are conducted. A penetration testing engagement will generally use the same sort of techniques.

In the first [[reconnaissance]] phase for black box testing, the pen tester establishes a profile of the target of investigation and surveys the attack surface for weaknesses. [[reconnaissance]] activities can be classed as passive or active. Passive [[reconnaissance]] is not likely to alert the target of the investigation as it means querying publicly available information. Active [[reconnaissance]] has more risk of detection. Active techniques might involve gaining physical access to premises or using scanning tools on the target's web services and other networks.

-   Open Source Intelligence ([[OSINT]])—using web search tools, social media, and sites that scan for vulnerabilities in Internet-connected devices and services ([securitytrails.com/blog/osint-tools](https://securitytrails.com/blog/osint-tools)) to obtain information about the target. OSINT aggregation tools, such as theHarvester ([github.com/laramies/theHarvester](https://github.com/laramies/theHarvester)), collect and organize this data from multiple sources. OSINT requires almost no privileged access as it relies on finding information that the company makes publicly available, whether intentionally or not. This is a passive technique.
-   [[[[Social engineering]]]]—this refers to obtaining information, physical access to premises, or even access to a user account through the art of persuasion. While the amount of interaction may vary, this can be classed as an active technique.
-   **Footprinting**—using software tools, such as Nmap ([nmap.org](https://nmap.org/)), to obtain information about a host or network topology. Scans may be launched against web hosts or against wired or wireless network segments, if the attacker can gain physical access to them. While passive footprinting is possible (by limiting it to packet sniffing), most scan techniques require active network connections with the target that can be picked up by detection software.
-   [[War driving]]—mapping the location and type (frequency channel and security method) of wireless networks operated by the target. Some of these networks may be accessible from outside the building. Simply sniffing the presence of wireless networks is a passive activity, though there is the risk of being observed by security guards or cameras. An attacker might be able to position rogue access points, such as the Hak5 Pineapple ([shop.hak5.org/products/wifi-pineapple](https://shop.hak5.org/products/wifi-pineapple)), or perform other wireless attacks using intelligence gathered from war driving.
-   Drones/unmanned aerial vehicle (UAV)—allow the tester to reconnoiter campus premises, and even to perform war driving from the air (war flying). A tool such as the Wi-Fi Pineapple can easily be incorporated on a drone ([hackaday.com/2018/05/27/watch-dogs-inspired-hacking-drone-takes-flight](https://hackaday.com/2018/05/27/watch-dogs-inspired-hacking-drone-takes-flight/)). Drones also provide a vector for one enduringly popular [[Social engineering]] technique; dropping infected USB media around premises, with the expectation that at least some of them will be picked up and used ([blackhat.com/docs/us-16/materials/us-16-Bursztein-Does-Dropping-USB-Drives-In-Parking-Lots-And-Other-Places-Really-Work.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/us-16-Bursztein-Does-Dropping-USB-Drives-In-Parking-Lots-And-Other-Places-Really-Work.pdf)).
## PEN TEST ATTACK LIFE CYCLE

In the [[kill chain]] attack life cycle, [[reconnaissance]] is followed by an initial exploitation phase where a software tool is used to gain some sort of access to the target's network. This foothold might be accomplished using a phishing email and payload or by obtaining credentials via [[Social engineering]]. Having gained the foothold, the pen tester can then set about securing and widening access. A number of techniques are required:

-    **[[Persistence]]**—the tester's ability to reconnect to the compromised host and use it as a remote access tool ([[[[IoC]]]]) or backdoor. To do this, the tester must establish a command and control (C2 or C&C) network to use to control the compromised host, upload additional attack tools, and download exfiltrated data. The connection to the compromised host will typically require a malware executable to run after shut down/log off events and a connection to a network port and the attacker's IP address to be available.
- [[Privilege escalation]]—persistence is followed by further [[reconnaissance]], where the pen tester attempts to map out the internal network and discover the services running on it and accounts configured to access it. Moving within the network or accessing data assets are likely to require higher privilege levels. For example, the original malware may have run with local administrator privileges on a client workstation or as the Apache user on a web server. Another exploit might allow malware to execute with system/root privileges, or to use network administrator privileges on other hosts, such as application servers.
-   **[[Lateral movement]]**—gaining control over other hosts. This is done partly to discover more opportunities to widen access (harvesting credentials, detecting software vulnerabilities, and gathering other such "loot"), partly to identify where valuable data assets might be located, and partly to evade detection. **Lateral movement usually involves executing the attack tools over remote process shares or using scripting tools, such as PowerShell.**
-   [[Pivoting]]—hosts that hold the most valuable data are not normally able to access external networks directly. If the pen tester achieves a foothold on a perimeter server, a pivot allows them to **bypass a network boundary** and compromise servers on an inside network. A pivot is normally accomplished using remote access and tunneling protocols, such as Secure Shell (SSH), virtual private networking (VPN), or remote desktop.
-   [[Actions on Objectives]]—for a [[[[threat actor]]]], this means stealing data from one or more systems (data exfiltration). From the perspective of a pen tester, it would be a matter of the scope definition whether this would be attempted. In most cases, it is usually sufficient to show that actions on objectives could be achieved.
-   Cleanup—for a [[threat actor]], this means removing evidence of the attack, or at least evidence that could implicate the [[threat actor]]. For a pen tester, this phase means removing any backdoors or tools and ensuring that the system is not less secure than the pre-engagement state.