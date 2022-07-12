# Session multiple should have started sooner
You are investigating a client workstation that has not obtained updates to its endpoint protection software for days. On the workstation you discover thousands of executable files with random names. The local endpoint log reveals that all of them have been scanned and identified as malware. You can find no evidence of any further intrusion on the network. What is the likely motive of the threat actor?

- This could be an offline tainted data attack against the endpoint software's identification engine.

MitB attack (Man-in-the-Browser attack)
- An attack when the web browser is compromised by installing malicious plug-ins or scripts, or intercepting API calls between the browser process and DLLs.

vulnerability feed
- A synchronizable list of data and scripts used to check for vulnerabilities. Also referred to as plug-ins or network vulnerability tests (NVTs).

blockchain
- A concept in which an expanding list of transactional records listed in a public ledger is secured using cryptography.

What countermeasures can you use against the threat of malicious firmware code?
- Only use reputable suppliers for peripheral devices and strictly controlled sources for firmware updates. Consider use of a sheep dip sandboxed system to observe a device before allowing it to be attached to a host in the enterprise network. Use execution control software to allow only approved USB vendors.

white team
- Staff administering, evaluating, and supervising a penetration test or incident response exercise.

active defense
- The practice of responding to a threat by destroying or deceiving a threat actor's capabilities.

password cracking
- Password guessing software can attempt to crack captured hashes of user credentials by running through all possible combinations (brute force). This can be made less computationally intensive by using a dictionary of standard words or phrases.

When using S/MIME, which key is used to encrypt a message?
- The recipient's public key (principally). The public key is used to encrypt a symmetric session key and (for performance reasons) the session key does the actual data encoding. The session key and, therefore, the message text can then only be recovered by the recipient, who uses the linked private key to decrypt it.


True or false? A virtual IP is a means by which two appliances can be put in a fault tolerant configuration to respond to requests for the same IP address?
- True

Which security property is assured by symmetric encryption?
- Confidentiality—symmetric ciphers are generally fast and well suited to bulk encrypting large amounts of data.

NAT (network address translation)
- A routing mechanism that conceals internal addressing schemes from the public Internet by translating between a single public address on the external side of a router and private, non-routable addresses internally.

extranet
- A private network that provides some access to outside parties, particularly vendors, partners, and select customers.

CE (cryptographic erase)
- A method of sanitizing a self-encrypting drive by erasing the media encryption key.

What areas of a business or workflow must you examine to assess multiparty risk?
- You need to examine supply chain dependencies to identify how problems with one or more suppliers would impact your business. You also need to examine customer relationships to determine what liabilities you have in the event of an incident impacting your ability to supply a product or service and what impact disruption of important customer accounts would have, should cyber incidents disrupt their business.

public key
- During asymmetric encryption, this key is freely distributed and can be used to perform the reverse encryption or decryption operation of the linked private key in the pair.

USB data blocker (Universal Serial Bus data blocker)
- Hardware plug to prevent malicious data transfer when a device is plugged into a USB charging point.

zero trust
- Security design paradigm where any request (host-to-host or container-to-container) must be authenticated before being allowed.

STIX (Structured Threat Information eXpression)
- A framework for analyzing cybersecurity incidents.

MMS (multimedia messaging service)
- Extension to SMS allowing digital data (picture, video, or audio) to be sent over a cellular data connection.


CSR (certificate signing request)
- A Base64 ASCII file that a subject sends to a CA to get a certificate.

CBT (computer-based training)
- Training and education programs delivered using computer devices and e-learning instructional models and design.

FTPS
- A type of FTP using TLS for confidentiality.

#zFleck stream cipher
- A type of symmetric encryption that combines a stream of plaintext bits or bytes with a pseudorandom stream initialized by a secret key.


SSH (Secure Shell)
- A remote administration and file-copy program that supports VPNs by using port forwarding, and that runs on TCP port 22.


deidentification
- In data protection, methods and technologies that remove identifying information from data before it is distributed.


You are writing a shell script to display the last 5 lines of a log file at /var/log/audit in a dashboard. What is the Linux command to do this?
- tail /var/log/audit -n 5

cryptographic primitive
- A single hash function, symmetric cipher, or asymmetric cipher.


Is Cuckoo a type of malware or a security product?
- Cuckoo is a security product designed to analyze malware as it runs in an isolated sandbox environment.

What are the properties of a public/private key pair?
- Each key can reverse the cryptographic operation performed by its pair but cannot reverse an operation performed by itself. The private key must be kept secret by the owner, but the public key is designed to be widely distributed. The private key cannot be determined from the public key, given a sufficient key size.


sinkhole
- A DoS attack mitigation strategy that directs the traffic that is flooding a target IP address to a different network for analysis.


packet crafting
- A method of manually generating packets (instead of modifying existing network traffic) to test the behavior of network devices, enabling a hacker to enumerate firewall or intrusion detection rules that are in place.


router
- A network device that links dissimilar networks and can support multiple alternate paths between location-based parameters such as speed, traffic loads, and price.


SCAP (Security Content Automation Protocol)
- A NIST framework that outlines various accepted practices for automating vulnerability scanning.


UEM (unified endpoint management)
- Enterprise software for controlling device settings, apps, and corporate data storage on all types of fixed, mobile, and IoT computing devices.


algorithm
- Any defined method of performing a process, but in encryption, the term specifically refers to the technique used to encrypt a message. Also referred to as Cipher


onboarding
- The process of bringing in a new employee, contractor, or supplier.


session hijacking
- A type of spoofing attack where the attacker disconnects a host then replaces it with his or her own machine, spoofing the original host's IP address.


TOTP (Time-based One-time Password)
- An improvement on HOTP that forces one-time passwords to expire after a short period of time.



You are preparing a solution overview on privacy enhancing technologies based on CompTIA Security+ syllabus objectives. You have completed notes under the following headings—which other report section do you need? Data minimization, Anonymization, Pseudo-anonymization, Data masking, Aggregation/Banding
- Tokenization—replacing data with a randomly generated token from a separate token server or vault. This allows reconstruction of the original data if combined with the token vault.



cloud service model
- Classifying the provision of cloud services and the limit of the cloud service provider's responsibility as software, platform, infrastructure, and so on.


Cloud Security Alliance
- Industry body providing security guidance to CSPs, including enterprise reference architecture and security controls matrix.


#zFleck You are providing security consultancy to assist a company with improving incident response procedures. The business manager wants to know why an out-of-band contact mechanism for responders is necessary. What do you say?
- The response team needs a secure channel to communicate over without alerting the threat actor. There may also be availability issues with the main communication network, if it has been affected by the incident.


You are consulting with a medium-size company about endpoint security solutions. What advantages does a cloud-based analytics platform have over an on-premises solution that relies on signature updates?
- Advanced persistent threat (APT) malware can use many techniques to evade signature-based detection. A cloud analytics platform, backed by machine learning, can apply more effective behavioral-based monitoring and alerting.


RBAC (role-based access control)
- An access control model where resources are protected by ACLs that are managed by administrators and that provide user permissions based on job functions.



A threat actor gained access to a remote network over a VPN. Later, you discover a video recording of a hacked user's work phone screen showing the user logging on to a company SharePoint site from a company-owned smartphone. What type of endpoint security solution might have prevented this security breach?
- A mobile device management (MDM) suite can prevent use of the camera function of a smartphone.



deception and disruption
- Cybersecurity resilience tools and techniques to increase the cost of attack planning for the threat actor.


SAML (Security Assertion Markup Language)
- An XML-based data format used to exchange authentication information between a client and a service.


Nessus
- One of the best-known commercial vulnerability scanners, produced by Tenable Network Security. Also referred to as Tenable.


supply chain attack
- An attack that targets the end-to-end process of manufacturing, distributing, and handling goods and services.


You are assisting a customer with implementing data loss prevention (DLP) software. Of the two products left in consideration, one supports steganalysis of image data, but the other does not. What is the risk of omitting this capability?
- A threat actor could conceal information within an image file and use that to bypass the DLP system. One thing to note is that attackers could find other ways to implement covertexts (audio or video, for instance) or abuse protocol coding. There are many things that steganalysis needs to be able to scan for! You might also note that steganography is not only a data exfiltration risk. It can also be used to smuggle malicious code into a host system.


MSA (measurement systems analysis)
- Evaluates the data collection and statistical methods used by a quality management process to ensure they are robust.


persistence (load balancing)
- In load balancing, the configuration option that enables a client to maintain a connection with a load-balanced server over the duration of the session. Also referred to as sticky sessions.


Why should an organization design role-based training programs?
- Employees have different levels of technical knowledge and different work priorities. This means that a "one size fits all" approach to security training is impractical.


data ownership
- The process of identifying the person responsible for the confidentiality, integrity, availability, and privacy of information assets.


east-west traffic
- Design paradigm accounting for the fact that data center traffic between servers is greater than that passing in and out (north-south).


post-quantum
- Anticipating challenges to current cryptographic implementations and general security issues in a world where threat actors have accesss to significant quantum processing capability.


content filter
- A software application or gateway that filters client requests for various types of internet content (web, FTP, IM, and so on).


What is the principal use of grep in relation to log files?
- grep is used to search the content of files.


Why should an Internet service provider (ISP) be informed before pen testing on a hosted website takes place?
- ISPs monitor their networks for suspicious traffic and may block the test attempts. The pen test may also involve equipment owned and operated by the ISP.


network monitoring
- Auditing software that collects status and configuration information from network devices. Many products are based on the Simple Network Management Protocol (SNMP).



compute
- In cloud architecture, the resources that provide processing functionality and services, often in the context of an isolated container or VM.


stateless
- A type of firewall that does not preserve information about the connection between two hosts. Often used to describe packet-filtering firewalls.


ISSO (Information Systems Security Officer)
- Organizational role with technical responsibilities for implementation of security policies, frameworks, and controls.


cloud deployment model
- Classifying the ownership and management of a cloud as public, private, community, or hybrid.


RDP (Remote Desktop Protocol)
- Microsoft's protocol for operating remote connections to a Windows machine (Terminal Services), allowing specified users to log onto the Windows computer over the network and work remotely. The protocol sends screen data from the remote host to the client and transfer mouse and keyboard input from the client to the remote host. It uses TCP port 3389.


PFX (personal information exchange)
- Windows file format for storing a private key and certificate data. The file can be password-protected.


#zFleck black hole
- A means of mitigating DoS or intrusion attacks by silently dropping (discarding) traffic.


You have been asked to produce a summary of pros and cons for the products Chef and Puppet. What type of virtualization or cloud computing technology do these support?
- These are orchestration tools. Orchestration facilitates "automation of automation," ensuring that scripts and API calls are made in the right order and at the right time to support an overall workflow.


PPTP (Point-to-Point Tunneling Protocol)
- Developed by Cisco and Microsoft to support VPNs over PPP and TCP/IP. PPTP is highly vulnerable to password cracking attacks and considered obsolete.


orchestration
- The automation of multiple steps in a deployment process.


What tools are used for OSINT?
- Open-source intelligence is a reconnaissance activity to gather information about the target from any public source. The basic tool is web searches/queries plus sites that scan/scrape/monitor vulnerabilities in Internet-facing services and devices. There are also specialist OSINT tools, such as theHarvester, that aggregate data from queries of different resources.

PLC (programmable logic controller)
- A type of computer designed for deployment in an industrial or outdoor setting that can automate and monitor mechanical systems.

key stretching
- A technique that strengthens potentially weak input for cryptographic key generation, such as passwords or passphrases created by people, against bruteforce attacks.

group account
- A group account is a collection of user accounts that are useful when establishing file permissions and user rights because when many individuals need the same level of access, a group could be established containing all the relevant users.

How does a specially configured compiler inhibit attacks through software diversity?

- The compiler can apply obfuscation routines to make the code difficult for a threat actor to reverse engineer and analyze for vulnerabilities.

logs

- OS and applications software can be configured to log events automatically. This provides valuable troubleshooting information. Security logs provide an audit trail of actions performed on the system as well as warning of suspicious activity. It is important that log configuration and files be made tamper-proof.

[[ca]]

- A server that guarantees subject identities by issuing signed digital certifcate wrappers for their public keys.

What type of bulk encryption cipher mode of operation offers the best security?

- Generally, counter modes implementing Authenticated Encryption with Additional Data (AEAD). Specific examples include AES-GCM and ChaCha20-Poly1305.
hybrid cloud

- A cloud deployment that uses both private and public elements.

proxy [[server]]

- A server that mediates the communications between a client and another server. It can filter and often modify communications, as well as provide caching services to improve performance. Also referred to as forward proxy.

[[authentication]]

- A method of validating a particular entity's or individual's unique credentials.

[[dump file]]

- File containing data captured from system memory.

Why should detailed vendor and product assessments be required before allowing the use of IoT devices in the enterprise?

- As systems with considerable computing and networking functionality, these devices are subject to the same sort of vulnerabilities and exploits as ordinary workstations and laptops. It is critical to assess the vendor's policies in terms of the security design for the product and support for identifying and mitigating any vulnerabilities discovered in its use.

NOS firewall (network operating system firewall)

- A software-based firewall running on a network server OS, such as Windows or Linux, so that the server can function as a gateway or proxy for a network segment.

birthday [[Attack]]

- A type of password attack that exploits weaknesses in the mathematical algorithms used to encrypt passwords, in order to take advantage of the probability of different password inputs producing the same encrypted output.

purple [[team]] #zFleck 

- A mode of penetration testing where red and blue teams share information and collaborate throughout the engagement.

[[DSA]]

- public key encryption standard used for digital signatures that provides authentication and integrity verification for messages.

SDK

- Coding resources provided by a vendor to assist with development projects that use their platform or API.

You are consulting on threat intelligence solutions for a supplier of electronic voting machines. What type of threat intelligence source would produce the most relevant information at the lowest cost?

- For critical infrastructure providers, threat data sharing via an Information Sharing and Analysis Center (ISAC) is likely to be the best option.

implicit deny

- A basic principle of security stating that unless something has explicitly been granted access, it should be denied access.

 [[BIA]] (business impact analysis)

- A systematic activity that identifies organizational risks and determines their effect on ongoing, mission critical operations.

Other than cost, which factor primarily constrains embedded systems in terms of compute and networking?

- Power—many embedded systems must operate on battery power, and changing the batteries is an onerous task, so power-hungry systems like processing and high bandwidth or long-range networking are constrained.

In the context of penetration testing, what is persistence?

- Persistence refers to the tester's ability to reconnect to the compromised host and use it as a remote access tool (RAT) or backdoor.

Zero day

- A vulnerability in software that is unpatched by the developer or an attack that exploits such a vulnerability.

digital signature

- A message digest encrypted using the sender's private key that is appended to a message to authenticate the sender and prove message integrity.

[[OTG]]

- USB specification allowing a mobile device to act as a host when a device such as an external drive or keyboard is attached.

obfuscation 

- A technique that essentially "hides" or "camouflages" code or other information so that it is harder to read by unauthorized users.

Your consultancy includes a training segment. What type of incident response exercise will best represent a practical incident handling scenario?

- A simulation exercise creates an actual intrusion scenario, with a red team performing the intrusion and a blue team attempting to identify, contain, and eradicate it.

[[syslog]]

- A protocol enabling different appliances and software applications to transmit logs or event records to a central server.

A company has installed motion-activated floodlighting on the grounds around its premises. What class and function is this security control?

- It would be classed as a physical control and its function is both detecting and deterring.

You are assisting with writing an attack surface assessment report for a small company. Following the CompTIA syllabus, which two potential attack vectors have been omitted from the following headings in the report? Direct access, Email, Remote and wireless, Web and social media, Cloud.

- Removable media and supply chain.

RA (registration authority)

- In PKI, an authority that accepts requests for digital certificates and authenticates the entities making those requests.

full backup

- A backup type in which all selected files, regardless of prior state, are backed up.

CVE (Common Vulnerabilities and Exposures)

- Scheme for identifying vulnerabilities developed by MITRE and adopted by NIST.

regex (regular expression)

- A group of characters that describe how to execute a specific search pattern on a given text.

Antivirus software has reported the presence of malware but cannot remove it automatically. Apart from the location of the affected file, what information will you need to remediate the system manually?

- The string identifying the malware. You can use this to reference the malware on the A-V vendor's site and, hopefully, obtain manual removal and prevention advice.

stateful inspection

- A technique used in firewalls to analyze packets down to the application layer rather than filtering packets only by header information, enabling the firewall to enforce tighter and more security.

ISSO (Information Systems Security Officer)

- Organizational role with technical responsibilities for implementation of security policies, frameworks, and controls.

persistence (load balancing)

- In load balancing, the configuration option that enables a client to maintain a connection with a load-balanced server over the duration of the session. Also referred to as sticky sessions.

Which response header provides protection against SSL stripping attacks?

- HTTP Strict Transport Security (HSTS).

HMI (human-machine interface)

- Input and output controls on a PLC to allow a user to configure and monitor the system.

What type of physical destruction media sanitization method is not suitable for USB thumb drives?

- Degaussing is ineffective against all types of flash media, including thumb drives, SSDs, hybrid drives, and memory cards.

An employee's car was recently broken into, and the thief stole a company tablet that held a great deal of sensitive data. You've already taken the precaution of securing plenty of backups of that data. What should you do to be absolutely certain that the data doesn't fall into the wrong hands?

- Remotely wipe the device, also referred to as a kill switch.

lateral movement
(This doesn't seem correct.  unless up and down is described as something else?)
- The process by which an attacker is able to move from one part of a computing environment to another.

reverse shell

- A maliciously spawned remote command shell where the victim host opens the connection to the attacking host.

jump [[server]]

- A hardened server that provides access to other hosts. Also referred to as a jumpbox.

GDPR (General Data Protection Regulation)

- Provisions and requirements protecting the personal data of European Union (EU) citizens. Transfers of personal data outside the EU Single Market are restricted unless protected by like-for-like regulations, such as the US's Privacy Shield requirements.

# Sessions 2
CSR (certificate signing request)

- A Base64 ASCII file that a subject sends to a CA to get a certificate.

OTA (over the air)

- A firmware update delivered on a cellular data connection.

code signing

- The method of using a digital signature to ensure the source and integrity of programming code.

cleartext

- Unencrypted data that is meant to be encrypted before it is transmitted, or the result of decryption of encrypted data. Also referred to as plaintext.

cryptography

- The science and practice of altering data to make it unintelligible to unauthorized parties.

HTML5 VPN

- Using features of HTML5 to implement remote desktop/VPN connections via browser software (clientless).

geographic dispersal

- Resiliency mechanism where processing and data storage resources are replicated between physically distant sites.

NTLM authentication (NT LAN Manager authentication)

- A challenge-response authentication protocol created by Microsoft for use in its products.

AI (artificial intelligence)

- The science of creating machines with the ability to develop problem solving and analysis strategies without significant human direction or intervention.

You receive an email with a screenshot showing a command prompt at one of your application servers. The email suggests you engage the hacker for a day's consultancy to patch the vulnerability. How should you categorize this threat?

- This is either gray hat (semi-authorized) hacking or black hat (non-authorized) hacking. If the request for compensation via consultancy is an extortion threat (if refused, the hacker sells the exploit on the dark web), then the motivation is purely financial gain and can be categorized as black hat. If the consultancy is refused and the hacker takes no further action, it can be classed as gray hat.

ICMP (Internet Control Message Protocol)

- IP-level protocol for reporting errors and status information supporting the function of troubleshooting utilities such as ping.

RIP (Routing Information Protocol)

- A distance vector-based routing protocol that uses a hop count to determine the distance to the destination network.

logger command

- Linux utility that writes data to the system log.

DRP (disaster recovery plan)

- A documented and resourced plan showing actions and responsibilities to be used in response to critical incidents.

IR (incident response)

- Procedures and guidelines covering appropriate priorities, actions, and responsibilities in the event of security incidents, divided into preparation, detection/analysis, containment, eradication/recovery, and post-incident stages.

enumeration

- When an attacker tries to get a list of resources on the network, host, or system as a whole to identify potential targets for further attack

# Session 3

CVSS (Common Vulnerability Scoring System)A risk management approach to quantifying vulnerability data and then taking into account the degree of risk to different types of systems or information.

- A risk management approach to quantifying vulnerability data and then taking into account the degree of risk to different types of systems or information.

stapling

- Mechanism used to mitigate performance and privacy issues when requesting certificate status from an OCSP responder.stapling

SOX (Sarbanes-Oxley Act)

- A law enacted in 2002 that dictates requirements for the storage and retention of documents relating to an organization's financial and business operations.SOX (Sarbanes-Oxley Act)

data sovereignty

- In data protection, the principle that countries and states may impose individual requirements on data collected or stored within their jurisdiction.data sovereignty

SID (security identifier)

- The value assigned to an account by Windows and that is used by the operating system to identify that account.SID (security identifier)

Which port(s) and security methods should be used by a mail client to submit messages for delivery by an SMTP server?

- Port 587 with STARTTLS (explicit TLS) or port 465 with implicit TLS.

service discovery

- The practice of using network scans to discover open TCP and UDP ports, plus information about the servers operating them.

DHE (Diffie-Hellman Ephemeral)

- A cryptographic protocol that is based on Diffie-Hellman and that provides for secure key exchange by using ephemeral keys.

TAXII (Trusted Automated eXchange of Indicator Information)

- A protocol for supplying codified information to automate incident detection and analysis.

HSM (hardware security module)

- An appliance for generating and storing cryptographic keys. This sort of solution may be less susceptible to tampering and insider threats than software-based storage.

You need to correlate intrusion detection data with web server log files. What component must you deploy to collect IDS alerts in a SIEM?

- You need to deploy a sensor to send network packet captures or intrusion detection alerts to the SIEM.

CAN bus (controller area network bus)

- A serial network designed to allow communications between embedded programmable logic controllers.

SAE (Simultaneous Authentication of Equals)

- Personal authentication mechanism for Wi-Fi networks introduced with WPA3 to address vulnerabilities in the WPA-PSK method.

How does a subject go about obtaining a certificate from a CA?

- In most cases, the subject generates a key pair then adds the public key along with subject information and certificate type in a certificate signing request (CSR) and submits it to the CA. If the CA accepts the request, it generates a certificate with the appropriate key usage and validity, signs it, and transmits it to the subject.

MTTF (mean time to failure)

- The average time a device or component is expected to be in operation.

#zFleck Why is subnetting useful in secure network design?

- Subnet traffic is routed, allowing it to be filtered by devices such as a firewall. An attacker must be able to gather more information about the configuration of the network and overcome more barriers to launch successful attacks.

If you suspect a process of being used for data exfiltration but the process is not identified as malware by A-V software, what types of analysis tools will be most useful?

- You can use a sandbox with monitoring tools to see which files the process interacts with and a network monitor to see if it opens (or tries to open) a connection with a remote host.

stored procedure

- One of a set of pre-compiled database statements that can be used to validate input to a database.

Netflow

- A Cisco-developed means of reporting network flow information to a structured database. NetFlow allows better understanding of IP traffic flows as used by different network applications and hosts.

SLE (single loss expectancy)

- The amount that would be lost in a single occurrence of a particular risk factor.

Which software tool is most appropriate for forwarding Windows event logs to a Syslog-compatible server?

- NXlog is designed as a multi-platform logging system.

smart meter

- A utility meter that can submit readings to the supplier without user intervention.

Which protocol protects the contents of a VoIP conversation from eavesdropping?

- Encrypted VoIP data is carried over the Secure Real-time Transport Protocol (SRTP).

brute force attack


- A type of password attack where an attacker uses an application to exhaustively try every possible alphanumeric combination to crack encrypted passwords.

[[KEK]] (key encryption key)

- In storage encryption, the private key that is used to encrypt the symmetric bulk media encryption key (MEK). This means that a user must authenticate to decrypt the MEK and access the media.

private cloud

- A cloud that is deployed for use by a single entity.

What tools are used for OSINT?

- Open-source intelligence is a reconnaissance activity to gather information about the target from any public source. The basic tool is web searches/queries plus sites that scan/scrape/monitor vulnerabilities in Internet-facing services and devices. There are also specialist OSINT tools, such as theHarvester, that aggregate data from queries of different resources.

Recently, attackers were able to compromise the account of a user whose employment had been terminated a week earlier. They used this account to access a network share and delete important files. What account vulnerability enabled this attack?

- While it's possible that lax password requirements and incorrect privileges may have contributed to the account compromise, the most glaring problem is that the terminated employee's account wasn't disabled. Since the account was no longer being used, it should not have been left active for a malicious user to exploit.

EAP (Extensible Authentication Protocol)

- Framework for negotiating authentication methods that enables systems to use hardware-based identifiers, such as fingerprint scanners or smart card readers, for authentication.

Why might enforcement policies be used to prevent USB tethering when a smartphone is brought to the workplace?

- This would allow a PC or laptop to connect to the Internet via the smartphone's cellular data connection. This could be used to evade network security mechanisms, such as data loss prevention or content filtering.

ip command

- A Linux-based utility used to gather information about the IP configuration of the network adapter or to configure the network adapter. Replaces the older ifconfig command.

What is a tabletop exercise?

- A discussion-based drill of emergency response procedures. Staff may role-play and discuss their responses but actual emergency conditions are not simulated.

What does it mean if a certificate extension attribute is marked as critical?

- That the application processing the certificate must be able to interpret the extension correctly. Otherwise, it should reject the certificate.

L2TP (Layer 2 Tunneling Protocol)

- VPN protocol for tunneling PPP sessions across a variety of network protocols such as IP, Frame Relay, or ATM.

MAC Address Table

- The table on a switch keeping track of MAC addresses associated with each port. As the switch uses a type of memory called Content Addressable Memory (CAM), this is sometimes called the CAM table.

Why should an Internet service provider (ISP) be informed before pen testing on a hosted website takes place?

- ISPs monitor their networks for suspicious traffic and may block the test attempts. The pen test may also involve equipment owned and operated by the ISP.

You are writing a shell script to display the last 5 lines of a log file at /var/log/audit in a dashboard. What is the Linux command to do this?

- tail /var/log/audit -n 5

#zFleck SDV (software defined visibility)

- APIs for reporting configuration and state data for automated monitoring and alerting.

#  Session 

What type of deployment model(s) allow users to select the mobile device make and model?

- Bring Your Own Device (BYOD) and Choose Your Own Device (CYOD).

What range of information classifications could you implement in a data labeling project?

- One set of tags could indicate the degree of confidentiality (public, confidential/secret, or critical/top secret). Another tagging schema could distinguish proprietary from private/sensitive personal data.

MSA (measurement systems analysis)

- Evaluates the data collection and statistical methods used by a quality management process to ensure they are robust.

bluejacking

- Sending an unsolicited message or picture message using a Bluetooth connection.

key stretching

- A technique that strengthens potentially weak input for cryptographic key generation, such as passwords or passphrases created by people, against bruteforce attacks.

You are consulting with a medium-size company about endpoint security solutions. What advantages does a cloud-based analytics platform have over an on-premises solution that relies on signature updates?

- Advanced persistent threat (APT) malware can use many techniques to evade signature-based detection. A cloud analytics platform, backed by machine learning, can apply more effective behavioral-based monitoring and alerting.



- 



- 



- 




CVSS (Common Vulnerability Scoring System)