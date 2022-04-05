---
tags: [firstTag, secondTag]
---
# EXAM OBJECTIVES COVERED

2.1 Explain the importance of security concepts in an enterprise environment

2.5 Given a scenario, implement cybersecurity resilience

5.3 Explain the importance of policies to organizational security

Effective site management and cybersecurity resilience depend on change control and configuration management. If this crucial documentation is not kept up to date, the response to incident and disaster events will suffer from confusion, errors, and lost time.

As part of a cybersecurity program, you must also be able to implement techniques that make things difficult for threat actors. [[Defense in depth and control diversity are crucial in designing resilient systems]]. Deception and disruption tactics help to increase the cost of attacks and so deter them.
# CONFIGURATION MANAGEMENT 

Response and recovery controls refer to the whole set of policies, procedures, and resources created for incident and disaster response and recovery. These controls are critical to cybersecurity, but they become increasingly difficult to provision at scale. Effective response and recovery depend heavily on how well-organized IT systems are at the site level. Without effective organizational policies to govern change and configuration management, response and recovery is much harder.

Configuration management ensures that each component of ICT infrastructure is in a trusted state that has not diverged from its documented properties. Change control and change management reduce the risk that changes to these components could cause service disruption. 

ITIL® is a popular documentation of good and best practice activities and processes for delivering IT services. Under [[ITIL]], configuration management is implemented using the following elements:

-   Service assets are things, processes, or people that contribute to the delivery of an IT service.
-   A Configuration Item ([[CI]]) is an asset that requires specific management procedures for it to be used to deliver the service. Each CI must be identified by some sort of label, ideally using a standard naming convention. CIs are defined by their attributes and relationships, which are stored in a configuration management database ([[CMDB]]).
-   A baseline configuration is the template of settings that a device, VM instance, or other CI was configured to, and that it should continue to match. You might also record performance baselines, such as the throughput achieved by a server, for comparison with monitored levels.
-   A configuration management system ([[CMS]]) is the tools and databases that collect, store, manage, update, and present information about CIs and their relationships. A small network might capture this information in spreadsheets and diagrams; there are dedicated applications for enterprise CMS. 
-   Diagrams are the best way to capture the complex relationships between network elements. Diagrams can be used to show how CIs are involved in business workflows, logical (IP) and physical network topologies, and network rack layouts. Remember, it is not sufficient simply to create the diagram, you must also keep the diagram up to date.
# ASSET MANAGEMENT

An asset management process tracks all the organization's critical systems, components, devices, and other objects of value in an inventory. It also involves collecting and analyzing information about these assets so that personnel can make more informed changes or otherwise work with assets to achieve business goals.

There are many software suites and associated hardware solutions available for tracking and managing assets. An asset management database can be configured to store as much or as little information as is deemed necessary, though typical data would be type, model, serial number, asset ID, location, user(s), value, and service information.

We are focusing on assets that require some degree of configuration (CIs). An organization will also have many assets with no configuration requirement, such as furniture.

### Asset Identification and Standard Naming Conventions

Tangible assets can be identified using a barcode label or radio frequency ID ([[RFID]]) tag attached to the device (or more simply, using an identification number). An RFID tag is a chip programmed with asset data. When in range of a scanner, the chip activates and signals the scanner. The scanner alerts management software to update the device's location. As well as asset tracking, this allows the management software to track the location of the device, making theft more difficult.

A standard naming convention for hardware assets, and for digital assets such as accounts and virtual machines, makes the environment more consistent. This means that errors are easier to spot and that it is easier to automate through scripting. The naming strategy should allow administrators to identify the type and function of any particular resource or location at any point in the CMDB or network directory. Each label should conform to rules for host and DNS names ([support.microsoft.com/en-us/help/909264/naming-conventions-in-active-directory-for-computers-domains-sites-and](https://support.microsoft.com/en-us/help/909264/naming-conventions-in-active-directory-for-computers-domains-sites-and)). As well as an ID attribute, the location and function of tangible and digital assets can be recorded using attribute tags and fields or DNS CNAME and TXT resource records.

### Internet Protocol (IP) Schema

The division of the IP address space into subnets should be carefully planned and documented in an Internet Protocol (IP) [[schema]]. Using a consistent addressing methodology makes it easier to apply firewall access control lists ([[ACL]]s) and perform security monitoring ([tools.cisco.com/security/center/resources/security_ip_addressing.html](https://tools.cisco.com/security/center/resources/security_ip_addressing.html)). It also makes configuration errors less likely and easier to detect. Within each subnet, the schema should identify IP addresses reserved for manual or static allocation versus DHCP address pools. IP address management (IPAM) software suites can be used to monitor IP usage.
# CHANGE CONTROL AND CHANGE MANAGEMENT 

Service management standards distinguish change control as distinct procedures for requesting and approving changes within an overall change management process.

### Change Control

A change control process can be used to request and approve changes in a planned and controlled way. Change requests are usually generated when something needs to be corrected, when something changes, or when there is room for improvement in a process or system currently in place. The need to change is often described either as reactive, where the change is forced on the organization, or as proactive, where the need for change is initiated internally. Changes can also be categorized according to their potential impact and level of risk (major, significant, minor, or normal, for instance). In a formal change management process, the need or reasons for change and the procedure for implementing the change is captured in a request for change ([[RFC]]) document and submitted for approval.

The RFC will then be considered at the appropriate level and affected stakeholders will be notified. This might be a supervisor or department manager if the change is normal or minor. Major or significant changes might be managed as a separate project and require approval through a change advisory board ([[CAB]]). 

### Change Management

The implementation of changes should be carefully planned, with consideration for how the change will affect dependent components. For most significant or major changes, organizations should attempt to trial the change first. **Every change should be accompanied by a rollback (or remediation) plan, so that the change can be reversed if it has harmful or unforeseen consequences**. Changes should also be scheduled sensitively if they are likely to cause system downtime or other negative impact on the workflow of the business units that depend on the IT system being modified. Most networks have a scheduled maintenance window period for authorized downtime. When the change has been implemented, its impact should be assessed, and the process reviewed and documented to identify any outcomes that could help future change management projects.
# SITE RESILIENCY 
#zFleck
Enterprise-level networks often provision resiliency at the site level. An alternate processing or recovery site is a location that can provide the same (or similar) level of service. An alternate processing site might always be available and in use, while a recovery site might take longer to set up or only be used in an emergency.

Operations are designed to failover to the new site until the previous site can be brought back online. Failover is a technique that ensures a redundant component, device, application, or site can quickly and efficiently take over the functionality of an asset that has failed. For example, load balancers provide failover in the event that one or more servers or sites behind the load balancer are down or are taking too long to respond. Once the load balancer detects this, it will redirect inbound traffic to an alternate processing server or site. Thus, redundant servers in the load balancer pool ensure there is no or minimal interruption of service.

Site resiliency is described as hot, warm, or cold:

-   A hot site can failover almost immediately. It generally means that the site is already within the organization's ownership and is ready to deploy. For example, a hot site could consist of a building with operational computer equipment that is kept updated with a live data set.
-   A warm site could be similar, but with the requirement that the latest data set will need to be loaded.
-   A cold site takes longer to set up. A cold site may be an empty building with a lease agreement in place to install whatever equipment is required when necessary.

Clearly, providing redundancy on this scale can be very expensive. Sites are often leased from service providers. However, in the event of a nationwide emergency, demand for the services is likely to exceed supply! Another option is for businesses to enter into reciprocal arrangements to provide mutual support. This is cost effective but complex to plan and set up.

Another issue is that creating a duplicate of anything doubles the complexity of securing that resource properly. The same security procedures must apply to redundant sites, spare systems, and backup data as apply to the main copy.

For many companies, the most cost-effective solution is to move processing and data storage to the cloud.
# DIVERSITY AND DEFENSE IN DEPTH

Layered security is typically seen as improving cybersecurity resiliency because it provides defense in depth. The idea is that to fully compromise a system, the attacker must get past multiple security controls, providing control diversity. These layers reduce the potential attack surface and make it much more likely that an attack will be deterred or prevented, or at least detected and then prevented by manual intervention. 

### Technology and Control Diversity

Allied with defense in depth is the concept of security through (or with) diversity. Technology diversity refers to environments that are a mix of operating systems, applications, coding languages, virtualization solutions, and so on. Control diversity means that the layers of controls should combine different classes of technical and administrative controls with the range of control functions: prevent, detect, correct, and deter.

Consider the scenario where Alan from marketing is sent a USB stick containing designs for a new billboard campaign from an agency. Without defense in depth, Alan might find the USB stick on his desk in the morning, plug it into his laptop without much thought, and from that point is potentially vulnerable to compromise. There are many opportunities in this scenario for an attacker to tamper with the media: at the agency, in the post, or at Alan's desk.

Defense in depth, established by deploying a diverse range of security controls, could mitigate the numerous risks inherent in this scenario:

-   User training (administrative control) could ensure that the media is not left unattended on a desk and is not inserted into a computer system without scanning it first.
-   Endpoint security (technical control) on the laptop could scan the media for malware or block access automatically.
-   Security locks inserted into USB ports (physical control) on the laptop could prevent attachment of media without requesting a key, allowing authorization checks to be performed first.
-   Permissions restricting Alan's user account (technical control) could prevent the malware from executing successfully.
-   The use of encrypted and digitally signed media (technical control) could prevent or identify an attempt to tamper with it.
-   If the laptop were compromised, intrusion detection and logging/alerting systems (technical control) could detect and prevent the malware spreading on the network. 

### Vendor Diversity

As well as deploying multiple types of controls, you should consider the advantages of leveraging vendor diversity. Vendor diversity means that security controls are sourced from multiple suppliers. A single vendor solution is a tempting choice for many organizations, as it provides interoperability and can reduce training and support costs. Some disadvantages could include the following:

-   Not obtaining best-in-class performance—one vendor might provide an effective firewall solution, but the bundled malware scanning is found to be less effective.
-   Less complex attack surface—a single vulnerability in a supplier's code could put multiple appliances at risk in a single vendor solution. A threat actor will be able to identify controls and possible weaknesses more easily.
-   Less innovation—dependence on a single vendor might make the organization invest too much trust in that vendor's solutions and less willing to research and test new approaches. 

### Crypto Diversity

This concept can be extended to the selection of algorithms and implementations of cryptography. Adoption of methods such as blockchain-based Identity and Access Management (IAM) ([ibm.com/blogs/blockchain/2018/10/decentralized-identity-an-alternative-to-password-based-authentication](https://www.ibm.com/blogs/blockchain/2018/10/decentralized-identity-an-alternative-to-password-based-authentication/)) or selecting ChaCha in place of Advanced Encryption Standard (AES) as a preferred cipher suite ([blog.cloudflare.com/it-takes-two-to-chacha-poly](https://blog.cloudflare.com/it-takes-two-to-chacha-poly/)) forces threat actors to develop new attack methods.
# DECEPTION AND DISRUPTION STRATEGIES

The practice of cybersecurity is often described as asymmetric warfare; the defenders have to win every encounter and be ready all the time. The threat actors can choose when to attack and only have to win once. Some cybersecurity tactics aim to reduce that asymmetry by increasing the attack cost. This means that a threat actor has to commit more resources to even plan an attack.

Active defense means an engagement with the adversary, but this can be interpreted in several different ways. One type of active defense involves the deployment of decoy assets to act as lures or bait. It is much easier to detect intrusions when an attacker interacts with a decoy resource, because you can precisely control baseline traffic and normal behavior in a way that is more difficult to do for production assets.

### Honeypots, Honeynets, and Honeyfiles

A honeypot is a computer system set up to attract threat actors, with the intention of analyzing attack strategies and tools, to provide early warnings of attack attempts, or possibly as a decoy to divert attention from actual computer systems. Another use is to detect internal fraud, snooping, and malpractice. A honeynet is an entire decoy network. This may be set up as an actual network or simulated using an emulator.

Deploying a honeypot or honeynet can help an organization to improve its security systems, but there is the risk that the attacker can still learn a great deal about how the network is configured and protected from analyzing the honeypot system. Many honeypots are set up by security researchers investigating malware threats, software exploits, and spammers' abuse of open relay mail systems. These systems are generally fully exposed to the Internet. On a production network, a honeypot is more likely to be located in a DMZ, or on an isolated segment on the private network (if the honeypot is seeking to draw out insider threats). This provides early warning and evidence of whether an attacker has been able to penetrate to a given security zone. This can help the security team find the source of the attack and take more comprehensive steps to completely eradicate the threat from the organization.

A honeypot or honeynet can be combined with the concept of a honeyfile, which is convincingly useful, but actually fake, data. This honeyfile can be made trackable, so that when a threat actor successfully exfiltrates it, the attempts to reuse or exploit it can be traced.

For example, an organization constructs a database full of benign or meaningless data disguised as important financial records. This deception strategy might involve breadcrumbs inserted into the production environment to subtly guide a threat actor toward the spoofed "loot" ([fidelissecurity.com/threatgeek/deception/breadcrumbs-intelligent-deception](https://fidelissecurity.com/threatgeek/deception/breadcrumbs-intelligent-deception/)). The database is placed behind a subnet with lowered defenses, which baits an attacker into trying to exfiltrate this useless data. Identifying the attacker also allows an organization to pursue an attribution strategy. Attribution means the organization publicizes the attacker's role and publishes the methods used as threat intelligence.

### Disruption Strategies

Another type of active defense uses disruption strategies. These adopt some of the obfuscation strategies used by malicious actors. The aim is to raise the attack cost and tie up the adversary's resources. Some examples of disruption strategies include:

-   Using bogus DNS entries to list multiple hosts that do not exist.
-   Configuring a web server with multiple decoy directories or dynamically generated pages to slow down scanning.
-   Using port triggering or spoofing to return fake telemetry data when a host detects port scanning activity. This will result in multiple ports being falsely reported as open and will slow down the scan. Telemetry can refer to any type of measurement or data returned by remote scanning. Similar fake telemetry could be used to report IP addresses as up when they are not, for instance.
-   Using a DNS sinkhole to route suspect traffic to a different network, such as a honeynet, where it can be analyzed.
