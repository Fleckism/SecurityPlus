# LESSON INTRODUCTION
[[IR]]    
From a day-to-day perspective, incident response means investigating the alerts produced by monitoring systems and issues reported by users. This activity is guided by policies and procedures and assisted by various technical controls.

Incident response is a critical security function and very large part of your work as a security professional will be taken up with it. You must be able to summarize the phases of incident handling, utilize appropriate data sources to assist an investigation, and apply mitigation techniques to secure the environment after an event.

Lesson Objectives

In this lesson, you will:

-   Summarize incident response procedures.
-   Utilize appropriate data sources for incident response.
-   Apply mitigation controls.
# EXAM OBJECTIVES COVERED

4.2 Summarize the importance of policies, processes, and procedures for incident response
#IR 
Effective incident response is governed by formal policies and procedures, setting out roles and responsibilities for an incident response team. You must understand the importance of following these procedures and performing your assigned role within the team to the best of your ability.
# INCIDENT RESPONSE PROCESS 

Incident response policy sets the resources, processes, and guidelines for dealing with security incidents. **Incident management is vital to mitigating risk**. As well as controlling the immediate or specific threat to security, effective incident management preserves an organization's reputation.

**Incident response follows a well-structured process, such as that set out in the NIST Computer Security Incident Handling Guide special publication** ([nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/NIST.SP.800-61r2.pdf)). The following are the principal stages in an [[incident response life cycle]]:

1.  **Preparation**—make the system resilient to attack in the first place. This includes hardening systems, writing policies and procedures, and setting up confidential lines of communication. It also implies creating incident response resources and procedures.
2.  **Identification**—from the information in an alert or report, determine whether an incident has taken place, assess how severe it might be (triage), and notify stakeholders.
3.  **Containment**—limit the scope and magnitude of the incident. The principal aim of incident response is to secure data while limiting the immediate impact on customers and business partners.
4.  **Eradication**—once the incident is contained, remove the cause and restore the affected system to a secure state by wiping a system and applying secure configuration settings.
5.  **Recovery**—with the cause of the incident eradicated, the system can be reintegrated into the business process that it supports. Applying patches and updates to a system to help prevent future incidents is important as well. This recovery phase may involve restoration of data from backup and security testing. Systems must be monitored more closely for a period to detect and prevent any reoccurrence of the attack. The response process may have to iterate through multiple phases of identification, containment, eradication, and recovery to effect a complete resolution.
6.  **Lessons learned**—analyze #Ops the incident and responses to identify whether procedures or systems could be improved. It is imperative to document the incident. The outputs from this phase feed back into a new preparation phase in the cycle.

Incident response is likely to require coordinated action and authorization from several different departments or managers, which adds further levels of complexity.

Phases in incident response.
# CYBER INCIDENT RESPONSE TEAM

Preparing for incident response means establishing the policies and procedures for dealing with security breaches and the personnel and resources to implement those policies.

One of the first challenges lies in **defining and categorizing types of incidents**. An incident is generally described as an event where security is breached or there is an attempted breach. NIST describes an **incident as "the act of violating an explicit or implied security policy."** In order to identify and manage incidents, you should develop some method of reporting, categorizing, and prioritizing them (**triage**), in the same way that troubleshooting support incidents can be logged and managed.

As well as investment in **appropriate detection and analysis software**, incident response requires expert staffing. Large organizations will provide a dedicated team as a **single point-of-contact for the notification of security incidents**. This team is variously described as a **cyber incident response team** ([[CIRT]]), **computer security incident response team** ([[CSIRT]]), or **computer emergency response team** ([[CERT]]). Incident response might also involve or be wholly located within a **security operations center** ([[SOC]]). However it is set up, the team needs a **mixture of senior management decision-makers** (up to director level) who can **authorize actions following the most serious incidents, managers, and technicians who can deal with minor incidents on their own initiative.**

Another important consideration is [[Availability]]. Incident response will typically require 24/7 [[Availability]], which will be expensive to provide. It is also worth considering that members of the [[CIRT]] should be rotated periodically to preclude the possibility of **infiltration**. For major incidents, expertise and advice from other business divisions will also need to be called upon:

-   **Legal**—it is important to have access to legal expertise, so that the team can evaluate incident response from the perspective of compliance with laws and industry regulations. It may also be necessary to liaise closely with law enforcement professionals, and this can be daunting without expert legal advice.
-   **Human Resources** (HR)—incident prevention and remediation actions may affect employee contracts, employment law, and so on. Incident response requires the right to intercept and monitor employee communications.
-   **Marketing**—the team is likely to require marketing or public relations input, so that any negative publicity from a serious incident can be managed.

Some organizations may prefer to outsource some of the CIRT functions to third-party agencies by retaining an incident response provider. External agents are able to deal more effectively with insider threats.
# COMMUNICATION PLAN AND STAKEHOLDER MANAGEMENT

Incident response policies should establish clear lines of communication, both for reporting incidents and for notifying affected parties as the management of an incident progresses. It is vital to have essential contact information readily available. 

You must prevent the inadvertent release of information beyond the team authorized to handle the incident. Status and event details should be circulated on a need-to-know basis and only to trusted parties identified on a call list.

### Communication Plan

**Secure communication** between the trusted parties of the CIRT is essential for managing incidents successfully. It is imperative that adversaries not be alerted to detection and remediation measures about to be taken against them. It may not be appropriate for all members of the CSIRT to be informed about all incident details.

**The team requires an "out-of-band" or "off-band" communication method that cannot be intercepted**. Using corporate email or VoIP runs the risk that the adversary will be able to intercept communications. One obvious method is cell phones but these only support voice and text messaging. For file and data exchange, there should be a messaging system with **end-to-end encryption**, such as **Off-the-Record** ([[OTR]]), Signal, or WhatsApp, or an external email system with message encryption (S/MIME or PGP). These **need to use digital signatures and encryption keys from a system that is completely separate from the identity management processes of the network being defended**.

### Stakeholder Management

Trusted parties might include both internal and external stakeholders. It is not helpful for an incident to be publicized in the press or through social **media outside of planned communications**. Ensure that parties with privileged information do not release this information to untrusted parties, whether intentionally or inadvertently.

You need to consider obligations to report the attack. **It may be necessary to inform affected parties during or immediately after the incident so that they can perform their own remediation**. It may be necessary to report to regulators or law enforcement. You also need to consider the marketing and PR impact of an incident. This can be highly damaging and you will need to demonstrate to customers that security systems have been improved.
# INCIDENT RESPONSE PLAN

An incident response plan ([[IRP]]) lists the procedures, contacts, and resources available to responders for various incident categories. The CSIRT should develop profiles or scenarios of [[typical incidents]] (**DDoS attack, virus/worm outbreak, data exfiltration by an external adversary, data modification by an internal adversary, and so on**). This will guide investigators in determining priorities and remediation plans. **A playbook (or runbook)** is a data-driven standard operating procedure (SOP) to assist junior analysts in detecting and responding to specific [[cyberthreat scenarios]], such as phishing attempts, SQL injection data exfiltration, connection to a block-listed IP range, and so on. The playbook starts with a [[SIEM]] report and query designed to detect the incident and identify the **key detection, containment, and eradication** steps to take.

**Incident categories and definitions** ensure that all response team members and other organizational personnel all have a common base of understanding of the meaning of t**erms, concepts, and descriptions**. The categories, types, and definitions might vary according to industry. For a listing of the US federal agency incident categories, you can visit [us-cert.cisa.gov/sites/default/files/publications/Federal_Incident_Notification_Guidelines.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/Federal_Incident_Notification_Guidelines.pdf).

One challenge in incident management is to allocate resources efficiently. This means that identified incidents must be assessed for severity and prioritized for remediation. There are several factors that can affect this process:

-   **Data integrity**—the most important factor in prioritizing incidents will often be the value of data that is at risk.
-   **Downtime**—another very important factor is the degree to which an incident disrupts business processes. An incident can either degrade (reduce performance) or interrupt (completely stop) the [[Availability]] of an asset, system, or business process. If you have completed an asset inventory and a thorough [[risk assessment]] of business processes (showing how assets and computer systems assist each process), then you can easily identify critical processes and quantify the impact of an incident in terms of the cost of downtime.
-   **Economic/publicity**—both data integrity and downtime will have important economic effects, both in the short term and the long term. Short-term costs involve incident response itself and lost business opportunities. Long-term economic costs may involve damage to reputation and market standing.
-   **Scope**—the scope of an incident (broadly the number of systems affected) is not a direct indicator of priority. A large number of systems might be infected with a type of malware that degrades performance, but is not a data breach risk. This might even be a masking attack as the adversary seeks to compromise data on a single database server storing top-secret information.
-   **Detection time**—research has shown that the existence of more than half of data breaches are not detected for weeks or months after the intrusion occurs, while in a successful intrusion, data is typically breached within minutes. This demonstrates that the systems used to search for intrusions must be thorough and the response to detection must be fast.
-   **Recovery time**—some incidents require lengthy remediation as the system changes required are complex to implement. This extended recovery period should trigger heightened alertness for continued or new attacks.
# CYBER KILL CHAIN ATTACK FRAMEWORK

Effective incident response depends on threat intelligence. Threat research provides insight into adversary tactics, techniques, and procedures ([[TTPs]]s). Insights from threat research can be used to develop specific tools and playbooks to deal with event scenarios. A key tool for threat research is a framework to use to describe the **stages of an attack**. These stages are often referred to as a cyber kill chain, following the influential white paper Intelligence-Driven Computer Network Defense commissioned by Lockheed Martin ([lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/LM-White-Paper-Intel-Driven-Defense.pdf)).

**Stages in the kill chain**.

The Lockheed Martin kill chain identifies the following phases:

1.  **[[reconnaissance]]**—in this stage the attacker determines what methods to use to complete the phases of the attack and gathers information about the target's personnel, computer systems, and supply chain.
2.  **Weaponization**—the attacker couples payload code that will enable access with exploit code that will use a vulnerability to execute on the target system.
3.  **Delivery**—the attacker identifies a vector by which to transmit the weaponized code to the target environment, such as via an email attachment or on a USB drive.
4.  **Exploitation**—the weaponized code is executed on the target system by this mechanism. For example, a phishing email may trick the user into running the code, while a drive-by-download would execute on a vulnerable system without user intervention.
5.  **Installation**—this mechanism enables the weaponized code to run a remote access tool and achieve persistence on the target system.
6.  **Command and control** (C2 or C&C)—the weaponized code establishes an outbound channel to a remote server that can then be used to control the remote access tool and possibly download additional tools to progress the attack.
7.  **Actions on objectives**—in this phase, the attacker typically uses the access he has achieved to covertly collect information from target systems and transfer it to a remote system (data exfiltration). An attacker may have other goals or motives, however.
# OTHER ATTACK FRAMEWORKS

Other types of attack framework have been implemented to provide a means of categorizing features of adversary behaviors to make it easier to identify indicators of such attacks.

### MITRE ATT&CK

As an alternative to the life cycle analysis implied by a kill chain, the [[MITRE]] Corporation's Adversarial Tactics, Techniques, and Common Knowledge ([[ATT&CK]]) matrices provide access to a database of known [[TTPs]]s. This freely available resource ([attack.mitre.org](https://attack.mitre.org/)) tags each technique with a unique ID and places it in one or more tactic categories, such as initial access, persistence, lateral movement, or command and control. The sequence in which attackers may deploy any given tactic category is not made explicit. This means analysts must interpret each attack life cycle from local evidence. The framework makes [[TTPs]]s used by different adversary groups directly comparable, without assuming how any particular adversary will run a campaign at a strategic level.

There is a matrix for enterprise, which can also be viewed as [[TTPs]]s [[directed against Linux, macOS, and Windows hosts]], and a second matrix for mobile. For example, Drive by Compromise is given the ID T1189 and categorized as an Initial Access tactic that can target Windows, Linux, and macOS hosts. Clicking through to the page accesses information about detection methods, mitigation methods, and examples of historic uses and analysis.

### The Diamond Model of Intrusion Analysis

The [[Diamond Model of Intrusion Analysis]] suggests a framework to analyze #Ops an intrusion event (**E**) by exploring the relationships between four core features: adversary, capability, infrastructure, and victim. These four features are represented by the four vertices of a diamond shape. Each event may also be described by meta-features, such as date/time, kill chain phase, result, and so on. Each feature is also assigned a confidence level (**C**), indicating data accuracy or the reliability of a conclusion or assumption assigned to the value by analysis.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9011-1599771811317.png)

Intrusion event represented in the Diamond Model. (Image: Released to public domain by Sergio Caltagirone, Andrew Pendergast, and Christopher Betz [[activeresponse.org/wp-content/uploads/2013/07/diamond.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/diamond.pdf)].)
# INCIDENT RESPONSE EXERCISES

The procedures and tools used for incident response are difficult to master and execute effectively. You do not want to be in the situation where first-time staff members are practicing them in the high-pressure environment of an actual incident. Running test exercises helps staff develop competencies and can help to identify deficiencies in the procedures and tools. **Training on specific incident response scenarios can use three forms:**

-   **Tabletop**—this is the least costly type of training. The facilitator presents a scenario and the responders explain what action they would take to identify, contain, and eradicate the threat. The training does not use computer systems. The scenario data is presented as flashcards.
-   **Walkthroughs**—in this model, a facilitator presents the scenario as for a tabletop exercise, but the incident responders demonstrate what actions they would take in response. Unlike a tabletop exercise, the responders perform actions such as running scans and analyzing sample files, typically on sandboxed versions of the company's actual response and recovery tools.
-   **Simulations**—a simulation is a team-based exercise, where the red team attempts an intrusion, the blue team operates response and recovery controls, and a white team moderates and evaluates the exercise. This type of training requires considerable investment and planning.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8382-1599771811430.jpg)

Members of Kentucky and Alabama National and Air Guard participating in a simulated network attack exercise. (Image © 2017 Kentucky National Guard.) 

MITRE have published a white paper that discusses preparing and facilitating incident response exercises ([mitre.org/sites/default/files/publications/pr_14-3929-cyber-exercise-playbook.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/pr_14-3929-cyber-exercise-playbook.pdf)).
# INCIDENT RESPONSE, DISASTER RECOVERY, AND RETENTION POLICY

Incident response fits into overall planning for enterprise risk management and cybersecurity resilience.

### Incident Response versus Disaster Recovery and Business Continuity

You should distinguish specific incident response planning from other types of planning for disaster recovery and business continuity:

-   **Disaster recovery plan**—a disaster can be seen as a special class of incident where the organization's primary business function is disrupted. Disaster recovery requires considerable resources, such as shifting processing to a secondary site. Disaster recovery will involve a wider range of stakeholders than less serious incidents.
-   **Business continuity plan** (BCP)—this identifies how business processes should deal with both minor and disaster-level disruption. During an incident, a system may need to be isolated. Continuity planning ensures that there is processing redundancy supporting the workflow, so that when a server is taken offline for security remediation, processing can failover to a separate system. If systems do not have this sort of planned resilience, incident response will be much more disruptive.
-   **Continuity of Operation Planning** (COOP)—this terminology is used for government facilities, but is functionally similar to business continuity planning. In some definitions, COOP refers specifically to backup methods of performing mission functions without IT support.

### Incident Response, Forensics, and Retention Policy

The **incident response process emphasizes containment, eradication, and recovery**. These aims are not entirely compatible with forensics. **Digital forensics describes techniques to collect and preserve evidence that demonstrate that there has been no tampering or manipulation**. **Forensics procedures are detailed and time-consuming, where the aims of incident response are usually urgent**. If an investigation must use forensic collection methods so that evidence is retained, this must be specified early in the response process.

Retention policy is also important for retrospective incident handling, or [[threat hunting]]. A retention policy for historic logs and data captures sets the period over which these are retained. You might discover indicators of a breach months or years after the event. Without a retention policy to keep logs and other digital evidence, it will not be possible to make any further investigation.
