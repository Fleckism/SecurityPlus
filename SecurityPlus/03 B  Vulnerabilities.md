Security Concerns with General Vulnerability Types 3B 
 ## EXAM OBJECTIVES COVERED

1.6 Explain the security concerns associated with various types of #vulnerability  

Performing a security [[assessment]] effectively is not simply a matter of choosing appropriate tools. You need to understand the types of [[vulnerability|vulnerabilities]] that affect information systems and networks. You must also be able to evaluate and explain the impacts that can arise from [[vulnerability|vulnerabilities]], so that assessment and remediation activities can be given priority where they are most needed.

## SOFTWARE [[vulnerability|vulnerabilities]] AND PATCH MANAGEMENT
[[Software exploitation]] means an attack that targets a [[vulnerability]] in software code. An [[application vulnerability]] is a design flaw that can cause the security system to be circumvented or that will cause the application to crash. Typically, [[vulnerability|vulnerabilities]] can only be exploited in quite specific circumstances but because of the complexity of modern software and the speed with which new versions must be released to market, almost no software is free from [[vulnerability|vulnerabilities]]. As two contrasting examples, consider [[vulnerability|vulnerabilities]] affecting Adobe's PDF document reader versus a vulnerability in the server software underpinning transport security. The former could give a [[threat actor]]s a foothold on a corporate network via a workstation; the latter could expose the cryptographic keys used to provide secure web services to compromise. Both are potentially high impact for different reasons.

It is also important to realize that software [[vulnerability|vulnerabilities]] affect all types of code, not just applications:

-   Operating system (OS)—an application [[exploit]] will run with the permissions of the logged on user, which will hopefully be limited. A vulnerability in an OS kernel file or shared library is more likely to allow   **privilege escalation**, where the malware code runs with higher access rights (system or root). Dirty COW is one example of a Linux kernel vulnerability ([access.redhat.com/blogs/766093/posts/2757141](https://access.redhat.com/blogs/766093/posts/2757141)).
-   Firmware—[[vulnerability|vulnerabilities]] can exist in the BIOS/UEFI firmware that controls the boot process for PCs. There can also be bugs in device firmware, such as network cards and disk controllers. Finally, network appliances and Internet of Things (IoT) devices run OS code as a type of firmware. Like kernel [[vulnerability|vulnerabilities]], firmware exploits can be difficult to identify, because the exploit code can run with the highest level of privilege. The Intel AMT vulnerability illustrates the impacts of a firmware vulnerability ([blackhat.com/docs/us-17/thursday/us-17-Evdokimov-Intel-AMT-Stealth-Breakthrough-wp.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/us-17-Evdokimov-Intel-AMT-Stealth-Breakthrough-wp.pdf)).

Most [[vulnerability|vulnerabilities]] are discovered by software and security researchers, who notify the vendor to give them time to patch the vulnerability before releasing details to the wider public. **Improper or weak patch management** is an additional layer of vulnerability where these security patches are not applied to systems, leaving them vulnerable to exploits. Poor configuration management may mean that the organization is simply not documenting and managing its assets rigorously. Patches may be deployed to some systems, but not others. Patches may be applied and then removed because they cause performance issues.

## ZERO-DAY AND LEGACY PLATFORM [[vulnerability|vulnerabilities]]

Even if effective patch management procedures are in place, attackers may still be able to use software [[vulnerability|vulnerabilities]] as an [[attack vector]]. A [[vulnerability]] that is exploited before the developer knows about it or can release a patch is called a [[zero-day]]. These can be extremely destructive, as it can take the vendor some time to develop a patch, leaving systems vulnerable in the interim.

The term zero-day is usually applied to the vulnerability itself but can also refer to an attack or malware that exploits it. The EternalBlue zero-day exploit makes for an instructive case study ([wired.com/story/eternalblue-leaked-nsa-spy-tool-hacked-world](https://www.wired.com/story/eternalblue-leaked-nsa-spy-tool-hacked-world/)).

Zero-day [[vulnerability|vulnerabilities]] have significant financial value. A zero-day exploit for a mobile OS can be worth millions of dollars. Consequently, an adversary will only use a zero-day vulnerability for high value attacks. State security and law enforcement agencies are known to stockpile zero-days to facilitate the investigation of crimes.

**A legacy platform is one that is no longer supported with security patches by its developer or vendor.** This could be a PC/laptop/smartphone, networking appliance, peripheral device, Internet of Things device, operating system, database/programming environment, or software application. By definition, **legacy platforms are unpatchable**. Such systems are highly likely to be vulnerable to exploits and must be protected by [[security control]]s other than patching, such as isolating them to networks that an attacker cannot physically connect to.
## WEAK HOST CONFIGURATIONS
While ineffective patch and configuration management policies and procedures represent one type of [[vulnerability]], weak configurations can have similar impacts.

### [[Default Settings]]

Relying on the ( managerial) manufacturer default settings when deploying an appliance or software applications is one example of weak configuration. It is not sufficient to rely on the vendor to ship products in a default-secure configuration, though many now do. Default settings may leave unsecure interfaces enabled that allow an attacker to compromise the device. **Network appliances with weak settings can allow attackers to move through the network unhindered and snoop on traffic.**

### [[Unsecured Root Accounts]] 

**The root account, referred to as the default Administrator** account in Windows or generically as the superuser, has no restrictions set over system access. A superuser account is used to install the OS. An unsecured root account is one that an adversary is able to gain control of, either by guessing a weak password or by using some **local boot attack to set or change the password**. Software bugs can also allow root access, such as one affecting MacOS ([arstechnica.com/information-technology/2017/11/macos-bug-lets-you-log-in-as-admin-with-no-password-required](https://arstechnica.com/information-technology/2017/11/macos-bug-lets-you-log-in-as-admin-with-no-password-required/)). These [[vulnerability|vulnerabilities]] are extremely serious as they give the [[threat actor]] complete control of the system.

Effective user management and authorization policies should be enforced so that the superuser account is highly restricted and administration tasks are performed by least privilege management accounts or roles instead. The default root or Administrator account is usually disabled for login. Even if this type of account is enabled for local (interactive) login, it should not be accessible via remote login mechanisms.

### Open Permissions

[[Open permissions]] refers to provisioning data files or applications without differentiating access rights for user groups. Permissions systems can be complex and it is easy to make mistakes, such as permitting unauthenticated guests to view confidential data files, or allowing write access when only read access is appropriate. This issue is particularly prevalent on cloud storage, where administrators used to Windows and Linux directory access control lists may be unfamiliar with the cloud equivalents ([directdefense.com/how-to-prevent-exploitation-of-amazon-s3-buckets-with-weak-permissions](https://www.directdefense.com/how-to-prevent-exploitation-of-amazon-s3-buckets-with-weak-permissions/)).
## WEAK NETWORK CONFIGURATIONS

[[vulnerability|vulnerabilities]] can also arise from running unnecessary services or using weak encryption.

### [[Open Ports]] and Services

Network applications and services allow client connections via Transport Control Protocol ([[TCP]] or User Datagram Protocol [[UDP]] port numbers. The clients and servers are identified by Internet Protocol (IP) addresses. Servers must operate with at least some open ports, but security best practice dictates that these should be restricted to only necessary services. Running unnecessary open ports and services increases the attack surface. Some generic steps to harden services to meet a given role include:

-   If the service is security-critical (such as a remote administration interface), **restrict endpoints** that are allowed to access the service by IP address or address range. Alternatively, prevent suspect endpoints from connecting by adding them to the block list, but otherwise allow access.
-   **Disable services** that are installed by default but that are not needed. Ideally, disable the service on the server itself, but in some circumstances it may be necessary to block the port using a firewall instead.
-   For services that should only be available on the private network, **block access to ports at border firewalls** or segment the network so that the servers cannot be accessed from external networks.

### Unsecure Protocols

An [[unsecure protocol]] is one that transfers data as cleartext; that is, the protocol does not use encryption for data protection. Lack of encryption also means that there is no secure way to authenticate the endpoints. This allows an attacker to intercept and modify communications, acting as man-in-the-middle [[MITM]].

### [[Weak Encryption]]

Encryption algorithms protect data when it is stored on disk or transferred over a network. Encrypted data should only be accessible to someone with the correct decryption key. Weak encryption [[vulnerability|vulnerabilities]] allow unauthorized access to data. Such [[vulnerability|vulnerabilities]] arise in the following circumstances:

-   The key is generated from a simple password, making it vulnerable to guessing attempts by brute-force enumeration (if the password is too short) or dictionary enumeration (if the password is not complex).
-   The algorithm or cipher used for encryption has known weaknesses that allow brute-force enumeration.
-   The key is not distributed securely and can easily fall into the hands of people who are not authorized to decrypt the data.

### Errors

Weakly configured applications may display unformatted error messages under certain conditions. These error messages can be revealing to [[threat actor]]s probing for [[vulnerability|vulnerabilities]] and coding mistakes. Secure coding practices should ensure that if an application fails, it does so "gracefully" without revealing information that could assist the development of an exploit.
WEAK NETWORK CONFIGURATIONS

[[vulnerability|vulnerabilities]] can also arise from running unnecessary services or using weak encryption.


## IMPACTS FROM [[vulnerability|vulnerabilities]]

[[vulnerability|vulnerabilities]] can lead to various data breach and data loss scenarios. These events can have serious impacts in terms of costs and damage to the organization's reputation.

### Data Breaches and Data Exfiltration Impacts

All information should be collected, stored, and processed by authenticated users and hosts subject to the permissions (authorization) allocated to them by the data owner. [[Data breach]] and data exfiltration describe two types of event where unauthorized information use occurs:

-   A **data breach** event is where confidential data is read, transferred, modified, or deleted without authorization. A privacy breach is where personal data is not collected, stored, or processed in full compliance with the laws or regulations governing personal information. A breach can also be described as a data leak. A data breach can be intentional/malicious or unintentional/accidental.
-  **Data exfiltration** is the methods and tools by which an attacker transfers data without authorization from the victim's systems to an external network or media. Unlike a data breach, a **data exfiltration event is always intentional and malicious.** A data breach is a consequence of a data exfiltration event.

Data breach includes a wide range of scenarios with different levels of impact. The most severe data breaches compromise valuable intellectual property (IP) or the personal information of account holders.

### Identity Theft Impacts

A privacy breach may allow the [[threat actor]] to perform identity theft or to sell the data to other malicious actors. The [[threat actor]] may obtain account credentials or might be able to use personal details and financial information to make fraudulent credit applications and purchases.

### Data Loss and [[Availability]] Loss Impacts

Compared to data breaches, [[data loss]] is where information becomes unavailable, either permanently or temporarily. [[Availability]] is sometimes overlooked as a security attribute compared to confidentiality and integrity, but it can have severe impacts on business workflows. If processing systems are brought down by accidental or malicious disaster events, a company may not be able to perform crucial workflows like order processing and fulfillment. 

Some definitions of data breach focus on the unauthorized release of information, while others include loss of information, such as encryption of a database by ransomware. The events that constitute a data breach are often specified in legislation or regulations, which will also impose requirements to notify stakeholders.

### Financial and Reputation Impacts

All these impacts can have direct financial impacts due to damages, fines, and loss of business. Data/privacy breach and [[Availability]] loss events will also cause a company's reputation to drop with direct customers. Major events might cause widespread adverse publicity on social media and mainstream media. In anticipation of these impacts, incident handling teams should include public relations (PR) and marketing expertise to minimize reputational damage.
## [[THIRD-PARTY RISKS]]

High-profile breaches have led to a greater appreciation of the importance of the supply chain in vulnerability management. A product, or even a service, may have components created and maintained by a long chain of different companies. Each company in the chain depends on its suppliers or vendors performing due diligence on their vendors. A weak link in the chain could cause impacts on service [[Availability]] and performance, or in the worst cases lead to data breaches.

### Vendor Management

Vendor management is a process for selecting supplier companies and evaluating the risks inherent in relying on a third-party product or service. When it comes to data and cybersecurity, you must understand that risks cannot be wholly transferred to the vendor. If a data storage vendor suffers a data breach, you may be able to claim costs from them, but your company will still be held liable in terms of legal penalties and damage to reputation. If your webstore suffers frequent outages because of failures at a hosting provider, it is your company's reputation that will suffer and your company that will lose orders because customers look elsewhere.

A vendor may supply documentation and certification to prove that it has implemented a security policy robustly. You might be able to see evidence of security capabilities, such as a history of effective vulnerability management and product support. Larger companies will usually ask vendors to complete a detailed audit process to ensure that they meet the required standards.

Within vendor management, _system integration_ refers to the process of using components/services from multiple vendors to implement a business workflow. For example, a workflow allowing customers to make online purchases might involve the storefront product, a web application firewall, [[cloud]] data processing and analytics, plus integration with on-premises accounting and customer relationship management ([[CRM]]) and support ticketing systems. The contracting company may have a list of preferred vendors and ask a third-party systems integrator to build and support the solution. Alternatively, systems integration might be fully outsourced, with the third-party integrator also selecting their preferred vendors for the component parts. The principal risk in both these scenarios is that the contracting company does not have sufficient expertise to oversee the project and places too much trust in the third-party integrator.

When a vendor has become deeply embedded within a workflow, lack of vendor support can have serious impacts, as retooling the workflow to use a different vendor can be a long and complex process. Vendors may become unsupportive for any number of reasons. For example, their company might be growing too quickly and resources are spread too thinly, they may drop support for products that are not profitable, they may have overstated capabilities in terms of security, and so on. The key point for vendor management is to assess these risks when determining whether to outsource all or part of a workflow and to have contingency plans if a vendor does not perform as expected.

### Outsourced Code Development

The problem of effective oversight is particularly pertinent to outsourced code development. Many companies do not have in-house programming expertise, but without such expertise it is hard to ensure that contractors are delivering secure code. A solution is to use one vendor for development and a different vendor for vulnerability and penetration testing.

### Data Storage

There are two main scenarios for risks to data when using third parties. First, you may need to grant vendor access to your data, and second, you may use a vendor to host data or data backups and archives. The following general precautions should be taken:

-   Ensure the same protections for data as though it were stored on-premises, including authorization and access management and encryption.
-   Monitor and audit third-party access to data storage to ensure it is being used only in compliance with data sharing agreements and nondisclosure agreements.
-   Evaluate compliance impacts from storing personal data on a third-party system, such as a cloud provider or backup/archive management service.

### Cloud-Based versus On-Premises Risks

On-premises risks refer to software [[vulnerability|vulnerabilities]], weak configurations, and third-party issues arising from hosts, servers, routers, switches, [[access points]], and firewalls located on a private network installed to private offices or campus buildings. Many companies use cloud services to fully or partly support business workflows. The third-party vendor management, code, and data storage risks discussed previously apply directly to cloud as well as to on-premises. Software and weak configuration risks can also apply, however. They are not the sole responsibility of the cloud service provider ([[CSP]]). Clouds operate a shared responsibility model. This means that the cloud service provider is responsible for the security of the cloud, while the cloud consumer is responsible for security in the cloud. The types of software and configuration [[vulnerability|vulnerabilities]] that you must assess and monitor vary according to the nature of the service.