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

Threat research is a counterintelligence gathering effort in which security companies and researchers attempt to discover the tactics, techniques, and procedures (TTPs) of modern cyber adversaries. There are many companies and academic institutions engaged in primary cybersecurity research. Security solution providers with firewall and anti-malware platforms derive a lot of data from their own customers' networks. As they assist customers with cybersecurity operations, they are able to analyze and publicize TTPs and their indicators. These organizations also operate honeynets to try to observe how hackers interact with vulnerable systems. 

Another primary source of threat intelligence is the dark web. The deep web is any part of the World Wide Web that is not indexed by a search engine. This includes pages that require registration, pages that block search indexing, unlinked pages, pages using nonstandard DNS, and content encoded in a nonstandard manner. Within the deep web, are areas that are deliberately concealed from "regular" browser access.

-   Dark net—a network established as an overlay to Internet infrastructure by software, such as The Onion Router (TOR), Freenet, or I2P, that acts to anonymize usage and prevent a third party from knowing about the existence of the network or analyzing any activity taking place over the network. Onion routing, for instance, uses multiple layers of encryption and relays between nodes to achieve this anonymity.
-   Dark web—sites, content, and services accessible only over a dark net. While there are dark web search engines, many sites are hidden from them. Access to a dark web site via its URL is often only available via "word of mouth" bulletin boards.

![Screenshot of AlphaBay Market showing "Tor circuit for this site" with 8 steps including IP addresses in Italy, Sweden, and Germany.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2941-1599771794384.png)

Using the TOR browser to view the AlphaBay market, now closed by law enforcement. (Screenshot used with permission from Security Onion.)

Investigating these dark web sites and message boards is a valuable source of counterintelligence. The anonymity of dark web services has made it easy for investigators to infiltrate the forums and webstores that have been set up to exchange stolen data and hacking tools. As adversaries react to this, they are setting up new networks and ways of identifying law enforcement infiltration. Consequently, dark nets and the dark web represent a continually shifting landscape.