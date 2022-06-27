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

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 

- 
