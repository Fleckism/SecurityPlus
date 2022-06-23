# 1
An administrator uses data from a Security Information and Event Management (SIEM) system to identify potential malicious activity. Which feature does the administrator utilize when implementing rules to interpret relationships between datapoints to diagnose incidents?

4.  Correlation

Solution

Correlation means interpreting the relationship between individual data points to diagnose incidents of significance to the security team. A SIEM correlation rule is a statement that matches certain conditions.

A SIEM can enact a retention policy to keep historical log and network traffic data for a defined period. This allows for a retrospective incident and threat hunting.

Trend analysis is the process of detecting patterns or indicators within a data set over a time series and using those patterns to make predictions about future events.

A baseline is a point of reference that provides a record of settings and configurations for comparison purposes.
# 2
A system compromise prompts the IT department to harden all systems. The technicians look to block communications to potential command and control servers. Which solutions apply to working with egress filtering? **(Select all that apply.)**

2.  Restrict DNS lookups
4.  Allow only authorized application ports

Solution

A recommended filtering approach would be to restrict DNS lookups to an ISP's DNS services or authorized public resolvers, such as Google's, helps to prevent lookups of malicious hosts.

A recommended filtering approach would be to allow only authorized application ports and, if possible, restricting the destination addresses to authorized Internet hosts helps to avoid contact with malicious servers.

Data loss prevention (DLP) pertains to protecting sensitive information by mediating the copying of tagged data to restrict it to authorized media and services.

If an attacker has managed to install a root certificate on a system, the attacker can make malicious hosts and services seem trusted. Admin must remove suspicious root certificates from the client's cache. This is not an egress filtering solution.

# 3
An engineer needs to review systems metadata to conclude what may have occurred during a breach. The first step the engineer takes in the investigation is to review MTA information in an Internet header. Which data type does the engineer review?


2.  Email

Solution

An email's Internet header contains address information for the recipient and sender, plus details of the servers or message Transfer Agents (MTA) handling transmission of the message between them.

When a client requests a resource from a web server, the server returns the resource plus headers setting, or describes its properties.

File metadata is stored as attributes. The file system tracks when a user creates, accesses, and modifies a file. The user might assign a file with a security attribute, such as marking it as read-only or as a hidden or system file.

Mobile phone metadata comprises call detail records (CDRs) of incoming, outgoing, and attempted calls and other data, such as SMS text time.
# 4
An engineer creates a set of tasks that queries information and runs some PowerShell commands to automate several stages of the process, including the identification of threats and other malicious activity on multiple servers. The engineer defines these tasks using which of the following?

1.  Runbook

Solution

A runbook aims to automate as many stages of the playbook as possible, while leaving clearly defined interaction points for human analysis.

  
A playbook is a type of list usually referred to as an incident response workflow. A playbook is a checklist of actions to perform, to detect and respond to a specific type of incident.

  
Orchestration is the action of coordinating multiple automations (and possibly manual activity) to perform a complex, multistep task.

  
Automation, unlike orchestration, is the action of scripting a single activity.
# 5
A security expert needs to review systems information to conclude what may have occurred during a breach. The expert reviews NetFlow data. What samples does the expert review?

3.  Statistics about network traffic


Solution

A flow collector is a means of recording metadata and statistics about network traffic rather than recording each frame. Network traffic and flow data may come from a wide variety of sources.

A SIEM collects data from sensors. The information captured from network packets can be aggregated and summarized to show overall protocol usage and endpoint activity.

sFlow, developed by HP and subsequently adopted as a web standard, uses sampling to measure traffic statistics at any layer of the OSI model for a wide range of protocol types.

If one has reliable baselines for comparison, bandwidth usage can be a key indicator of suspicious behavior. Unexpected bandwidth consumption could be evidence of a data exfiltration attack.
# 6
Incident management relies heavily on the efficient allocation of resources. Which of the following factors should an IT manager consider as it relates to the overall scope of dealing with an incident? **(Select all that apply.)**

2.  Downtime
3.  Detection time
4.  Recovery time

Solution

Downtime is a critical factor to consider to the degree to which an incident disrupts business processes. An incident can either degrade (reduce performance) or interrupt (completely stop) the availability of an asset, system, or business process.

Detection time is an important consideration requiring that the systems used to search for intrusions are thorough, and the response to detections must be fast.

Recovery time must be considered, as some incidents that need to have complex system changes require lengthy remediation. This extended recovery period should trigger heightened alertness for continued or new attacks.

Planning time can refer to the expected time for completing a project plan, or a period of time scheduled for an IT team to work together to plan out projects. It is not a consideration for incident remediation efforts.
# 7
The first responder to a security incident decides the issue requires escalation. Consider the following and select the scenario that best describes escalation in this issue.


3.  The first responder calls senior staff to get them involved.

Solution

Escalation is the process of involving additional senior staff to assist in incident management when the first responder feels the situation is too complex to manage alone.

“Pulling the plug” on an affected system is an option to contain an attack, but it is not the definition of escalation.

Although it is important to have access to legal expertise, who can evaluate the incident response from the perspective of compliance with laws and industry regulations, contacting the legal department is not an example of escalation.

The term escalation can describe when a user gains additional privileges without authorization. However, this is within the context of privilege management, not incident response.
# 8
When endpoint security experiences a breach, there are several classes of vector to consider for mitigation. Which type relates to exploiting an unauthorized service port change?

1.  Configuration drift

Solution

Configuration drift applies when malware exploits an undocumented configuration change (shadow IT software or an unauthorized service/port, for instance).

A weak configuration is correctly applied, but exploited anyway. Review of the settings is recommended to ensure the highest level of security.

If endpoint protection/A-V, host firewall, content filtering, DLP, or MDM could have prevented an attack, then investigate the possibility of the lack of security controls.

Social engineering means that a user executed an exploit. Use security education and awareness to reduce the risk of future attacks succeeding.
# 9
A systems administrator suspects that a virus has infected a critical server. In which step of the incident response process does the administrator notify stakeholders of the issue?

2.  Identification

Solution

In the identification phase, it is important to determine whether an incident has taken place, assess how severe it might be (triage), and notify stakeholders.

The recovery phase reintegrates the system into the environment and may involve the restoration of data from backup and security testing. The systems administrator must monitor the systems more closely for a period to detect and prevent any reoccurrence of the attack.

The containment phase aims to limit the scope and magnitude of the incident. The goal is to secure data while limiting the immediate impact on customers and business partners.

In the eradication phase, the admin removes the cause and restores the system to a secure state by applying secure configuration settings and installing patches.
# 10
A user calls the help desk to report that Microsoft Excel continues to crash when used. The technician would like to review the logs in an attempt to determine the cause. Analyze the types of logs to determine which would contain the information the technician needs.

1.  Event log

Solution

An event log records events that occur within an operating system or a software application. These logs diagnose errors and performance problems.

An audit log records the use of system privileges, such as creating a user account or modifying a file. Security logging needs to be configured carefully as over-logging can reduce the effectiveness of auditing by obscuring genuinely important events with thousands of routine notifications.

A security log is another way of describing an audit log. The audit log in Windows Event Viewer is called the Security log.

An access log is for server applications, such as Apache, which can log each connection or request for a resource.
# 11
Arrange the following stages of the incident response life cycle in the correct order.

1.  Preparation; Identification; Containment, Eradication, and Recovery; Lessons Learned

Solution

Stage 1. Preparation requires making the system resilient to attack in the first place (hardening systems, writing policies and procedures, and establishing confidential lines of communication).

Stage 2. Identification involves determining whether an incident has taken place and assessing how severe it might be, followed by notification of the incident to stakeholders.

Stage 3. Containment, Eradication, and Recovery are limiting the scope and impact of the incident. Once the incident is contained, the cause can then be removed and the system brought back to a secure state.

Stage 4. Lessons learned consists of analyzing the incident and responses to identify whether procedures or systems could be improved. It is imperative to document the incident.
# 12
A security analyst needs to contain a compromised system. The analyst would be most successful using which containment approach?


4.  Airgap

Solution

A simple option is to disconnect the host from the network completely (creating an air gap) or disabling its switch port. This is the least stealthy option and may reduce opportunities to analyze the attack or malware due to the isolation.

The analyst can implement a routing infrastructure to isolate one or more infected virtual LANs (VLANs) in a black hole that is not reachable from the rest of the network.

Segmentation-based containment is a means of achieving the isolation of a host or group of hosts using network technologies and architecture such as VLANs.

ACLs can prevent a host or group of hosts from communicating outside of a protected segment.
# 13
A security team desires to modify event logging for several network devices. One team member suggests using the configuration files from the current logging system with another open format that uses TCP with a secure connection. Which format does the team member suggest?

2.  Rsyslog

Solution

Rsyslog can work over TCP and use a secure connection. It uses the same configuration file syntax as Syslog. Rsyslog can use more types of filter expressions in its configuration file to customize message handling.

Syslog-ng is an update to Syslog that can use TCP secure communications, but it uses a different configuration file syntax than Syslog.

Syslog provides an open format, protocol, and server software for logging event messages. A very wide range of host types use Syslog, as well as UDP for communications.

NXlog is an open-source log normalization tool. One common use for it is to collect Windows logs, which use an XML-based format and then normalize them to a standard syslog format.
# 14
Successful adversarial attacks mostly depend on knowledge of the algorithms used by the target AI. In an attempt to keep an algorithm secret, which method does an engineer use when hiding the secret?

2.  Obscurity

Solution

Algorithm secrecy is secrecy by obscurity (hiding). This approach can partially mitigate risks from less motivated threat actors, who will simply move to the next, easier target.

A solution to prevent AI attacks is to generate adversarial examples and to train the AI system to recognize them.

An option for preventing or reducing AI attacks is to develop a filter that can detect and block adversarial samples as they are submitted.

Engineers use Artificial Intelligence (AI)-type systems extensively for user and entity behavior analytics (UEBA).
# 15
During weekly scans, a system administrator identifies a system that has software installed that goes against security policy. The system administrator removes the system from the network in an attempt to limit the effect of the incident on the remainder of the network. Apply the Computer Security Incident Handling Guide principles to determine which stage of the incident response life cycle the administrator has entered.


3.  Containment, eradication and recovery

Solution

The system administrator has entered the containment, eradication, and recovery stage by removing the system from the network. This action contains the incident and protects the other network resources. This is also the stage where the administrator will repair the system and bring it back online or replace it.

Preparation is the stage where the admin puts controls in place to prevent the software from being installed.

The identification stage was completed when the scan was conducted and the unauthorized software identified.

The lessons learned stage will occur after the containment, eradication, and recovery stage is completed and lessons learned will be utilized to improve the security of the network.
