---
Define mitigating(To make less harsh or hostile)
---
# EXAM OBJECTIVES COVERED

1.2 Given a scenario, analyze #Ops potential indicators to determine the type of attack

4.4 Given an incident, apply mitigation techniques or controls to secure an environment 

[[Mitigation techniques]] are applied first to **contain**, and then to **eradicate** and recover from the effects of malicious activity. Incident response is a highly pressured activity, with the conflicting challenges of eliminating the intrusion without disrupting business workflows. You must be able to select and apply the appropriate technique for a given scenario.
# INCIDENT CONTAINMENT 

As incidents cover such a wide range of different scenarios, technologies, motivations, and degrees of seriousness, there is no standard approach to containment or incident isolation. Some of the many complex issues facing the [[CIRT]] are:

-   What damage or theft has occurred already? How much more could be inflicted and in what sort of time frame (loss control)?
-   What countermeasures are available? What are their costs and implications?
-   What actions could alert the attacker to the fact that the attack has been detected? What evidence of the attack must be gathered and preserved?

**When an incident has been identified, classified, and prioritized, the next phase of incident response is containment. Containment techniques can be classed as either isolation-based or segmentation-based.**

### Isolation-Based Containment 

**Isolation** involves removing an affected component from whatever larger environment it is a part of. This can be everything from removing a server from the network after it has been the target of a DoS attack, to placing an application in a [[Sandbox]] VM outside of the host environments it usually runs on. Whatever the circumstances may be, you'll want to make sure that there is **no longer an interface between the affected component and your production network or the Internet.**

A simple option is to disconnect the host from the network completely, either by pulling the network plug (**creating an air gap**) or **disabling its switch port**. This is the least stealthy option and will reduce opportunities to analyze #Ops the attack or malware. If a group of hosts is affected, you could use **routing infrastructure to isolate one or more infected virtual LANs (VLANs)** in a black hole that is not reachable from the rest of the network. **Another possibility is to use firewalls or other security filters to prevent infected hosts from communicating.**

Finally, isolation could also refer to **disabling a user account or application service**. Temporarily disabling users' network accounts may prove helpful in containing damage if an intruder is detected within the network. Without privileges to access resources, an intruder will not be able to further damage or steal information from the organization. Applications that you suspect may be the vector of an attack can be much less effective to the attacker if the application is prevented from executing on most hosts.

### Segmentation-Based Containment

Segmentation-based containment is a means of achieving the isolation of a host or group of hosts using network technologies and architecture #A_D. **Segmentation uses VLANs, routing/subnets, and firewall ACLs to prevent a host or group of hosts from communicating outside the protected segment**. As opposed to completely isolating the hosts, you might configure the protected segment as a sinkhole or honeynet and allow the attacker to continue to receive filtered (and possibly modified) output over the [[C&C]] channel to deceive him or her into thinking the attack is progressing successfully. **Analysis of the malware code by reverse engineering it could provide powerful deception capabilities. You could intercept the function calls made by malware to allow the adversary to believe an attack is proceeding while building detailed knowledge of their tactics and (hopefully) identity. Attribution of the attack to a particular group will allow an estimation of adversary capability.**
# INCIDENT ERADICATION AND RECOVERY 

After an incident has been contained, you can apply mitigation techniques and controls to **eradicate the intrusion tools and unauthorized configuration changes from your systems**. Eradicating malware, backdoors, and compromised accounts from individual hosts is not the last step in incident response. You should also consider **a recovery phase where the goal is restoration of capabilities and services. This means that hosts are fully reconfigured to operate the business workflow they were performing before the incident**. An essential part of recovery is the process of ensuring that the **system cannot be compromised through the same [[attack vector]] (or failing that, that the vector is closely monitored to provide advance warning of another attack)**.

Eradication of malware or other intrusion mechanisms and recovery from the attack will involve several steps:

If reinstalling from baseline template configurations or images, make sure that there is nothing in the baseline that allowed the incident to occur! If so, update the template before rolling it out again.

If your organization is subjected to a targeted attack, be aware that one incident may be very quickly followed by another.

1.  **Reconstitution of affected systems**—either remove the malicious files or tools from affected systems or restore the systems from secure backups/images.
2.  **Reaudit security controls**—ensure they are not vulnerable to another attack. This could be the same attack or from some new attack that the attacker could launch through information they have gained about your network.
3.  Ensure that affected parties are notified and provided with the means to remediate their own systems. For example, if customers' passwords are stolen, they should be advised to change the credentials for any other accounts where that password might have been used (not good practice, but most people do it).
# FIREWALL CONFIGURATION CHANGES

**Analysis of an attack should identify the vector exploited by the attacker**. This analysis is used to identify configuration changes that block that [[attack vector]]. A configuration change may mean the deployment of a new type of security control, or altering the settings of an existing control to make it more effective.

**Historically, many organizations focused on ingress filtering rules**, designed to prevent local network penetration from the Internet. In the current threat landscape, **it is imperative to also apply strict egress filtering rules to prevent malware that has infected internal hosts by other means from communicating out to C&C servers**. Egress filtering can be problematic in terms of interrupting authorized network activity, but it is an essential component of modern network defense. Some general guidelines for configuring egress filtering are:

-   **Allow only authorized application ports** and, if possible, restrict the destination addresses to authorized Internet hosts. Where authorized hosts cannot be identified or a default deny is too restrictive, use URL and content filtering to try to detect malicious traffic over authorized protocols.
-   **Restrict DNS lookups** to your own or your ISP's DNS services or authorized public resolvers, such as Google's or Quad9's DNS services.
-   **Block access to** "known bad" IP address ranges, as listed on don't route or peer ([[DROP]]) filter lists.
-   **Block access from** any IP address space that is not authorized for use on your local network.
-   **Block all Internet access from host subnets** that do not need to connect to the Internet, such as most types of internal server, workstations used to manage industrial control systems (ICSs), and so on.

**Even within these rules, there is a lot of scope for [[threat actor]]s to perform command signaling and exfiltration**. For example, cloud services, such as content delivery networks and social media platforms, can be used to communicate scripts and malware commands and to exfiltrate data over Hyper Text Transfer ProtocolTTPs]]S ([rhinosecuritylabs.com/aws/hiding-cloudcobalt-strike-beacon-c2-using-amazon-apis](https://rhinosecuritylabs.com/aws/hiding-cloudcobalt-strike-beacon-c2-using-amazon-apis/)).
# CONTENT FILTER CONFIGURATION CHANGES

The limitations of a basic packet filtering firewall (even if it is stateful) mean that some sort of **content filtering application proxy may provide better security**. These types of appliances are usually referred to as secure web gateways ([[SWGs]]). A [[SWG]] **mediates user access to Internet services, with the ability to block content from regularly updated URL/domain/IP block lists and perform intrusion detection/prevention on traffic based on matching content in application layer protocol headers and payloads.**

If a **SWG is already in place**, an attacker may have found a way to circumvent it via some sort of backdoor. The network configuration should be checked and updated to ensure that all client access to the Internet must pass through the SWG. Another possibility is that the attacker is using a protocol or [[C&C]] method that is not filtered. **The SWG should be updated with scripts and data, domains and IP addresses, that will block the exploit**.

### Data Loss Prevention (DLP)

**Data loss prevention** (DLP) performs a similar function, but instead of user access it **mediates the copying of tagged data to restrict it to authorized media and services**. An attack may reveal the necessity of investing in DLP as a security control if one is not already implemented. If DLP is enabled and configured in the correct way to enforce policy, the attacker may have been able to circumvent it using a backdoor method that the DLP software cannot scan. Alternatively, **the attacker may have been able to disguise the data so that it was not recognized.**

### Mobile Device Management (MDM) 

Mobile Device Management (MDM) provides execution control over apps and features of smartphones. Features include GPS, camera, and microphone. As with DLP, an intrusion might reveal a vector that allowed the [[[[threat actor]]]] to circumvent enrollment or a misconfiguration in the MDM's policy templates. 

### Update or Revoke Certificates

Compromise of the private key represented by a digital certificate or the ability to present spoofed certificates as trusted is a critical security vulnerability as it allows an attacker to impersonate trusted resources and potentially gain unauthorized access to secure systems.

-   **Remove compromised root certificates**—if an attacker has managed to install a root certificate, the attacker can make malicious hosts and services seem trusted. Suspicious root certificates must be removed from the client's cache.
-   **Revoke certificates on compromised hosts**—if a host is compromised, the private key it used for digital signatures or digital envelopes is no longer safe. The certificate associated with the key should be revoked using the Key Compromise property. The certificate can be rekeyed with a new key pair but the same subject and expiry information.
# ENDPOINT CONFIGURATION CHANGES

If [[endpoint security]] is breached, there are several classes of vector to consider for mitigation:

-   **[[Social engineering]]**—if the malware was executed by a user, use security education and awareness to reduce the risk of future attacks succeeding. Review permissions to see if the account could be operated with a lower privilege level.
-   **Vulnerabilities**—if the malware exploited a software fault, either install the patch or isolate the system until a patch can be developed.
-   **Lack of security controls**—if the attack could have been prevented by endpoint protection/A-V, host firewall, content filtering, DLP, or MDM, investigate the possibility of deploying them to the endpoint. If this is not practical, isolate the system from being exploited by the same vector.
-   **Configuration drift**—if the malware exploited an undocumented configuration change (shadow IT software or an unauthorized service/port, for instance), reapply the baseline configuration and investigate configuration management procedures to prevent this type of ad hoc change.
-   **Weak configuration**—if the configuration was correctly applied, but was exploited anyway, review the template to devise more secure settings. Make sure the template is applied to similar hosts. 

### Application Allow Lists and Block Lists

One element of [[endpoint]] configuration is an execution control policy that defines applications that can or cannot be run.

-   **An allow list** (or approved list) denies execution unless the process is explicitly authorized.
-   **A block list** (or deny list) generally allows execution, but explicitly prohibits listed processes.

You will need to update the contents of allow lists and block lists in response to incidents and as a result of ongoing [[threat hunting]] and monitoring. [[threat hunting]] may also provoke a strategic change. For example, if you rely principally on **explicit denies**, but your systems are subject to numerous intrusions, you will have to consider adopting a "**least privileges**" model and using a deny-unless-listed approach. This sort of change has the potential to be highly disruptive however, so it must be preceded by a [[risk assesment]] and business impact analysis.

Execution control can also be tricky to configure effectively, with many opportunities for [[threat actor]]s to evade the controls. Detailed analysis of the attack might show the need for changes to the existing mechanism, or the use of a more robust system.

### Quarantine

If mitigating techniques are not successful, or the results are uncertain, the endpoint will require careful management before being integrated back onto the network. If further evidence needs to be gathered, the best approach may be to **quarantine or [[Sandbox]] the endpoint or suspect process/file**. This allows for analysis of the attack or tool and collection of evidence using digital forensic techniques.
# SECURITY ORCHESTRATION, AUTOMATION, AND RESPONSE

[[Automation]] is the action of scripting a single activity, while [[orchestration]] is the action of coordinating multiple automations (and possibly manual activity) to perform a complex, multistep task. In the case of security orchestration, automation, and response ([[SOAR]]), this task is principally incident response, though the technologies can be used for tasks such as [[threat hunting]] too. SOAR is designed as a solution to the problem of the volume of alerts overwhelming analysts' ability to respond, measured as the mean time to respond ([[MTTR]]). A SOAR may be implemented as a standalone technology or integrated with a [[SIEM]]—often referred to as a next-gen SIEM. The basis of SOAR is to scan the organization's store of security and threat intelligence, analyze #Ops it using machine/deep learning techniques, and then use that data to automate and provide data enrichment for the workflows that drive incident response and [[threat hunting]]. It can also assist with provisioning tasks, such as creating and deleting user accounts, making shares available, or launching VMs from templates, to try to eliminate configuration errors. The SOAR will use technologies such as cloud and SDN/SDV APIs, orchestration tools, and cyberthreat intelligence (CTI) feeds to integrate the different systems that it is managing. It will also leverage technologies such as automated malware signature creation and user and entity behavior analytics ([[UEBA]]) to detect threats.

An incident response workflow is usually defined as a [[playbook]]. A playbook is a checklist of actions to perform to detect and respond to a specific type of incident. A playbook should be made highly specific by including the query strings and signatures that will detect a particular type of incident. A playbook will also account for compliance factors, such as whether an incident must be reported as a breach plus when and to whom notification must be made. Where a playbook is implemented with a high degree of automation from a [[SOAR]] system, it can be referred to as a **runbook**, though the terms are also widely used interchangeably. The aim of a runbook is to automate as many stages of the playbook as possible, leaving clearly defined interaction points for human analysis. These interaction points should try to present all the contextual information and guidance needed for the analyst to make a quick, informed decision about the best way to proceed with incident mitigation.

Rapid7 have produced an ebook demonstrating the uses of SOAR ([rapid7.com/info/security-orchestration-and-automation-playbook/?x=d67w-U](https://www.rapid7.com/info/security-orchestration-and-automation-playbook/?x=d67w-U)). A white paper by Demisto provides a useful overview of the role of SOAR across different organizations ([cdn2.hubspot.net/hubfs/5003120/Content%20Downloads/White%20Papers/Demisto%20-%20State%20of%20SOAR.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/Demisto%20-%20State%20of%20SOAR.pdf)).
# ADVERSARIAL ARTIFICIAL INTELLIGENCE

**Artificial Intelligence (AI)-type systems are used extensively for user and entity behavior analytics** ([[UEBA]]). A UEBA is trained on security data from customer systems and honeypots. This allows the AI to determine features of malicious code and account activity and to recognize those features in **novel data streams**. To make use of UEBA, host event data and network traffic is streamed to a cloud-based analytics service. **An attacker with undetected persistent access to the network, but with a low probability of effecting lateral movement or data exfiltration, may be in a position to inject traffic into this data stream with a long-term goal of concealing tools that could achieve actions on objectives**. The attacker may use his or her own AI resources as a means of generating samples, hence adversarial AI. Manipulated samples could also be uploaded to public repositories, such as virustotal.com.

For example, ML algorithms are highly sensitive to noise. This is demonstrated in image recognition cases, where given a doctored image of a turtle, an AI will identify it as a rifle ([theregister.com/2017/11/06/mit_fooling_ai](https://www.theregister.com/2017/11/06/mit_fooling_ai/)). To a human observer, the image appears to be that of a perfectly ordinary turtle. Similar techniques might be used to cause an AI to **miscategorize** an attack tool as a text editor.

Successful adversarial attacks mostly depend on knowledge of the algorithms used by the target AI. This is referred to as a white box attack. Keeping those algorithms secret forces the adversarial AI to use black box techniques, which are more difficult to develop. **Algorithm secrecy is security by obscurity, however, and difficult to ensure**. Other solutions include generating adversarial examples and training the system to recognize them. Another option is to develop a filter that can detect and block adversarial samples as they are submitted.

A Microsoft presentation at BlackHat illustrates some of the techniques that can be used to mitigate adversarial AI ([i.blackhat.com/us-18/Thu-August-9/us-18-Parikh-Protecting-the-Protector-Hardening-Machine-Learning-Defenses-Against-Adversarial-Attacks.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/us-18-Parikh-Protecting-the-Protector-Hardening-Machine-Learning-Defenses-Against-Adversarial-Attacks.pdf)).
