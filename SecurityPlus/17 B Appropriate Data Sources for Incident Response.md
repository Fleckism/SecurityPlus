
# EXAM OBJECTIVES COVERED

4.3 Given an incident, utilize appropriate data sources to support an investigation #IR

Security monitoring produces a very large amount of data, and automated detection systems can generate a large volume of alerts. Prioritizing and investigating the most urgent events as incidents and resolving them quickly is a significant challenge for all types of organization. As a security professional, you must be able to utilize appropriate data sources to perform incident identification as efficiently as possible.
# INCIDENT IDENTIFICATION 

[[Identification]] **is the process of collating events and determining whether any of them should be managed as incidents or as possible precursors to an incident; that is, an event that makes an incident more likely to happen**. There are multiple channels by which events or precursors may be recorded:

-   Using log files, error messages, IDS alerts, firewall alerts, and other resources to **establish baselines and identifying those parameters that indicate a possible security incident**.
-   Comparing **deviations** to established metrics to recognize incidents and their scopes.
-   **Manual or physical inspections** of site, premises, networks, and hosts.
-   **Notification** by an employee, customer, or supplier.
-   **Public reporting** of new [[vulnerability|vulnerabilities]] or threats by a system vendor, regulator, the media, or other outside party.

It is wise to provide for **confidential reporting** so that employees are not afraid to report insider threats, such as fraud or misconduct. It may also be necessary to use an "**out-of-band**" method of communication so as not to alert the intruder that his or her attack has been detected. 

### First Responder

When a suspicious event is detected, it is critical that the appropriate person on the [[CIRT]] be notified so that they can take charge of the situation and formulate the appropriate response. This person is referred to as the first responder. This means that employees at all levels of the organization must be trained to recognize and respond appropriately to actual or suspected security incidents. A good level of security awareness across the whole organization will reduce the incidence of false positives and negatives. For the most serious incidents, the entire CIRT may be involved in formulating an effective response. 

### Analysis and Incident Identification

When notification has taken place, the CIRT or other responsible person(s) must analyze #Ops the event to determine whether a genuine incident has been identified and what level of priority it should be assigned. **Analysis will depend on identifying the type of incident and the data or resources affected (its scope and impact)**. At this point, the incident management database should have a record of the event indicators, the nature of the incident, its impact, and the incident investigator responsible. The next phase of incident management is to determine an appropriate response.
# SECURITY INFORMATION AND EVENT MANAGEMENT

Coupled with an attack framework, notification will provide a general sense of where to look for or expect indicators of malicious activity. Incident analysis is greatly facilitated by a security information and event management ([[SIEM]]) system. A SIEM parses network traffic and log data from multiple sensors, appliances, and hosts and normalizes the information to standard field types. 

### Correlation

The SIEM can then run correlation rules on indicators extracted from the data sources to detect events that should be investigated as potential incidents. You can also filter or query the data based on the type of incident that has been reported.

Correlation means interpreting the relationship between individual data points to diagnose incidents of significance to the security team. A SIEM correlation rule is a statement that matches certain conditions. These rules use **logical expressions**, such as AND and OR, and operators, such as == (matches), < (less than), > (greater than), and in (contains). For example, a single-user logon failure is not a condition that should raise an alert. Multiple user logon failures for the same account, taking place within the space of one hour, is more likely to require investigation and is a candidate for detection by a correlation rule.

Error.LogonFailure > 3 AND LogonFailure.User AND Duration < 1 hour

As well as correlation between indicators observed on the network, a [[SIEM]] is likely to be **configured with a threat intelligence feed**. This means that data points observed on the network can be associated with known [[threat actor]] indicators, such as IP addresses and domain names. AI-assisted analysis enables more sophisticated alerting and detection of anomalous behavior.

### Retention

A SIEM can enact a retention policy so that historical log and network traffic data is kept for a defined period. This allows for r**etrospective incident and [[threat hunting]]**, and can be a valuable source of **forensic evidence**.
# SIEM DASHBOARDS 

SIEM dashboards are one of the main sources of automated alerts. A SIEM **dashboard provides a console to work from for day-to-day incident response**. Separate dashboards can be **created to suit many different purposes**. An incident handler's dashboard will contain uncategorized events that have been assigned to their account, plus visualizations (graphs and tables) showing key status metrics. A manager's dashboard would show overall status indicators, such as number of unclassified events for all event handlers.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2047-1599771811551.png)

The SGUIL console in Security Onion. A SIEM can generate huge numbers of alerts that need to be manually assessed for priority and investigation. (Screenshot courtesy of Security Onion [securityonion.net](https://securityonion.net/).)

### Sensitivity and Alerts 

One of the greatest challenges in operating a SIEM is **tuning the system sensitivity to reduce false positive indicators** being reported as an event. This is difficult firstly because there isn't a simple dial to turn for overall sensitivity, and secondly because reducing the number of rules that produce events increases the risk of false negatives. A false negative is where indicators that should be correlated as an event and raise an alert are ignored.

The correlation rules are likely to assign a criticality level to each match. For example:

-   **Log only**—an event is produced and added to the SIEM's database, but it is automatically classified.
-   **Alert**—the event is listed on a dashboard or incident handling system for an agent to assess. The agent classifies the event and either dismisses it to the log or escalates it as an incident.
-   **Alarm**—the event is automatically classified as critical and a priority alarm is raised. This might mean emailing an incident handler or sending a text message.

### Sensors

A sensor is a **network tap or port mirror** that performs **packet capture and intrusion detection**. One of the key uses of a SIEM is to aggregate data from multiple sensors and log sources, but it might also be appropriate to configure dashboards that show output from a single sensor or source host.
# TREND ANALYSIS 

[[Trend analysis]] is the process of detecting patterns or indicators within a data set over a time series and using those patterns to make predictions about future events. A trend is difficult to spot by examining each event in a log file. Instead, you need software to visualize the incidence of types of event and show how the number or frequency of those events changes over time. Trend analysis can apply to **frequency, volume, or statistical deviation**:

-   **Frequency**-based trend analysis establishes a baseline for a metric, such as number of NXERROR DNS log events per hour of the day. If the frequency exceeds (or in some cases undershoots) the threshold for the baseline, then an alert is raised.
-   **Volume**-based trend analysis can be performed with simpler indicators. For example, one simple metric for determining threat level is log volume. If logs are growing much faster than they were previously, there is a good chance that something needs investigating. Volume-based analysis also applies to network traffic. You might also measure endpoint disk usage. Client workstations don’t usually need to store data locally, so if a host's disk capacity has suddenly diminished, it could be a sign that it is being used to stage data for exfiltration.
-   **Statistical deviation** analysis can show when a data point should be treated as suspicious. For example, a cluster graph might show activity by standard users and privileged users, invoking analysis of behavioral metrics of what processes each type runs, which systems they access, and so on. A data point that appears outside the two clusters for standard and administrative users might indicate some suspicious activity by that account.
# LOGGING PLATFORMS

Log data from network appliances and hosts can be aggregated by a SIEM either by installing a local agent to collect and parse the log data or by using a forwarding system to transmit logs directly to the SIEM server. Also, organizations may not operate a SIEM, but still use a logging platform to aggregate log data in a central location.

### Syslog 

Syslog ([tools.ietf.org/html/rfc3164](https://tools.ietf.org/html/rfc3164)) provides an open format, protocol, and server software for logging event messages. It is used by a very wide range of host types. For example, syslog messages can be generated by Cisco routers and switches, as well as servers and workstations. It usually uses **UDP port 514**.

A syslog message comprises a [[PRI]] code, a header containing a timestamp and host name, and a message part. The PRI code is **calculated from the facility and a severity level**. The message part contains a tag showing the source process plus content. **The format of the content is application-dependent. It might use space- or comma-delimited fields or name/value pairs, such as JSON data.**

RFC 5424 ([tools.ietf.org/html/rfc5424](https://tools.ietf.org/html/rfc5424)) adjusts the structure slightly to split the tag into app name, process ID, and message ID fields, and to make them part of the header.

### Rsyslog and Syslog-ng

There have been two updates to the original syslog specification:

-   **Rsyslog** uses the same configuration file syntax, but can work over **TCP** and use a secure connection. Rsyslog can use more types of filter expressions in its configuration file to customize message handling.
-   Syslog-ng uses a different configuration file syntax, but can also use **TCP/secure** communications and more advanced options for message filtering. 

### journalctl

In [[Linux]], text-based log files of the sort managed by syslog can be viewed using commands such as cat, tail, and head. Most modern Linux distributions now use systemd to initialize the system and to start and manage background services. Rather than writing events to syslog-format text files, logs from processes managed by systemd are written to a binary-format file called journald. Events captured by journald can be forwarded to syslog. To view events in journald directly, you can use the journalctl command to print the entire journal log, or you can issue various options with the command to filter the log in a variety of ways, such as matching a service name or only printing messages matching the specified severity level.

### NXlog

NXlog ([nxlog.co](https://nxlog.co/)) is an open-source log normalization tool. One principal use for it is to collect Windows logs, which use an XML-based format, and normalize them to a syslog format.
# NETWORK, OS, AND SECURITY LOG FILES 

Log file data is a critical resource for investigating security incidents. As well as the log format, you must also consider the range of sources for log files and know how to determine what type of log file will best support any given **investigation scenario**.

### System and Security Logs 

One source of security information is the **event log from each network server or client**. Systems such as Microsoft Windows, Apple macOS, and Linux keep a variety of logs to record events as users and software interact with the system. The format of the logs varies depending on the system. Information contained within the logs also varies by system, and in many cases, the type of information that is captured can be configured.

When events are generated, they are placed into log categories. These categories describe the general nature of the events or what areas of the OS they affect. The five main categories of **Windows event logs** are:

-   **Application**—events generated by applications and services, such as when a service cannot start.
-   **Security**—Audit events, such as a failed logon or access to a file being denied.
-   **System**—events generated by the operating system and its services, such as storage volume health checks.
-   **Setup**—events generated during the installation of Windows.
-   **Forwarded Events**—events that are sent to the local log from other hosts.

### Network Logs

**Network logs are generated by appliances such as routers, firewalls, switches, and access points**. Log files will record the operation and status of the appliance itself—the system log for the appliance—plus traffic and access logs recording network behavior, such as a host trying to use a port that is blocked by the firewall, or an endpoint trying to use multiple MAC addresses when connected to a switch.

### Authentication Logs

Authentication attempts for each host are likely to be written to the **security log**. You might also need to inspect logs from the servers authorizing logons, such as [[RADIUS]] and TACACS+ servers or Windows Active Directory (AD) servers.

### Vulnerability Scan Output

A vulnerability scan report is another important source when determining how an attack might have been made. The scan engine might log or alert when a scan report contains [[vulnerability|vulnerabilities]]. The report can be analyzed to identify [[vulnerability|vulnerabilities]] that have not been patched or configuration weaknesses that have not been remediated. These can be correlated to recently developed exploits.

Windows Defender event within Windows event viewer. (Screenshot used with permission from Microsoft.)

Decoding contents of iptables firewall messages written to syslog.
# APPLICATION LOG FILES

An application log file is simply one that is managed by the application rather than the OS. The application may use Event Viewer or syslog to write event data using a standard format, or it might write log files to its own application directories in whatever format the developer has selected.

### DNS Event Logs

A [[DNS server]] may log an event each time it handles a request to convert between a domain name and an IP address. DNS event logs can hold a variety of information that may supply useful security intelligence, such as:

-   The types of **queries a host** has made to DNS.
-   Hosts that are in communication with **suspicious IP address ranges or domains**.
-   **Statistical anomalies** such as spikes or consistently large numbers of DNS lookup failures, which may point to computers that are infected with malware, misconfigured, or running obsolete or faulty applications.

### Web/Hyper Text Transfer ProtocolTTPs]] Access Logs 

Web servers are typically configured to log Hyper Text Transfer ProtocolTTPs]] traffic that encounters an **error or traffic that matches some predefined rule set**. Most web servers use the common log format ([[CLF]]) or W3C extended log file format to record the relevant information.

The [[status code]] of a response can reveal quite a bit about both the request and the server's behavior. Codes in the 400 range indicate client-based errors, while codes in the 500 range indicate server-based errors. For example, repeated 403 ("Forbidden") responses may indicate that the server is rejecting a client's attempts to access resources they are not authorized to. A 502 ("Bad Gateway") response could indicate that communications between the target server and its upstream server are being blocked, or that the upstream server is down.

In addition to status codes, some web server software also logs Hyper Text Transfer ProtocolTTPs]] **header information for both requests and responses**. This can provide you with a better picture of the makeup of each request or response, such as cookie information and [[MIME]] types. Another header field of note is the User-Agent field, which identifies the type of application making the request. In most cases, this is the version of the browser that the client is using to access a site, as well as the client's operating system. However, this can be misleading, as even a browser like **Microsoft Edge includes versions of Google Chrome and Safari in its User-Agent string**. Therefore, the User-Agent field may not be a reliable indicator of the client's environment.

### VoIP and Call Managers and Session Initiation Protocol (SIP) Traffic

Many VoIP systems use the Session Initiation Protocol ([[SIP]]) to identify endpoints and setup calls. The call content is transferred using a separate protocol, typically the Real-time Transport Protocol ([[RTP]]). VoIP protocols are vulnerable to most of the same [[vulnerability|vulnerabilities]] and exploits as web communications. Both SIP and RTP should use the secure protocol forms, where **endpoints are authenticated** and communications protected by Transport Layer Security (TLS).

The call manager is a gateway that connects endpoints within the local network and over the Internet. The call manager is also likely to implement a media gateway to connect VoIP calls to cellphone and landline telephone networks. SIP produces similar logs to [[SMTP]], typically in the common log format. A SIP log will identify the endpoints involved in a call request, plus the type of connection (voice only or voice with video, for instance), and status messaging. When handling requests, the call manager and any other intermediate servers add their IP address in a Via header, similar to per-hop SMTP headers. Inspecting the logs might reveal evidence of a man-in-the-middle [[MITM]] attack where an **unauthorized proxy** is intercepting traffic. VoIP systems connected to telephone   networks are also targets for toll fraud. The call manager's access log can be audited for suspicious connections.

### Dump Files

System memory contains volatile [[data]]. A system memory dump creates an image file that can be analyzed to identify the processes that are running, the contents of temporary [[file systems]], registry data, network connections, cryptographic keys, and more. It can also be a means of accessing data that is encrypted when stored on a mass storage device.
# METADATA

[[Metadata]] **is the properties of data as it is created by an application**, stored on media, or transmitted over a network. A number of metadata sources are likely to be useful when investigating incidents, because they can establish timeline questions, such as when and where, as well as containing other types of evidence. 

### File

File metadata is stored as **attributes**. The file system tracks when a file was created, accessed, and modified. A file might be assigned a security attribute, such as marking it as read-only or as a hidden or system file. The [[ACL]] attached to a file showing its permissions represents another type of attribute. Finally, the file may have extended attributes recording an author, copyright information, or tags for indexing/searching. In Linux, the ls command can be used to report file system metadata. 

### Web

When a client requests a resource from a web server, the server returns the resource plus **headers setting or describing its properties**. Also, the client can include headers in its request. One key use of headers is to **transmit authorization information**, in the form of cookies. Headers describing the type of data returned (text or binary, for instance) can also be of interest. The contents of headers can be inspected using the standard tools built into web browsers. Header information may also be logged by a web server. 

### Email

An email's Internet header contains address information for the recipient and sender, plus details of the servers handling transmission of the message between them. When an email is created, the mail user agent ([[MUA]]) creates an initial header and forwards the message to a mail delivery agent ([[MDA]]). The MDA should perform checks that the sender is authorized to issue messages from the domain. Assuming the email isn't being delivered locally at the same domain, the MDA adds or amends its own header and then transmits the message to a message transfer agent ([[MTA]]). The MTA routes the message to the recipient, with the message passing via one or more additional MTAs, such as [[SMTP]] servers operated by ISPs or mail security gateways. Each MTA adds information to the header.

Headers aren't exposed to the user by most email applications, which is why they're usually not a factor in an average user's judgment. You can view and copy headers from a mail client via a message properties/options/source command. MTAs can add a lot of information in each received header, such as the results of spam checking. If you use a plaintext editor to view the header, it can be difficult to identify where each part begins and ends. Fortunately, there are plenty of tools available to parse headers and display them in a more structured format. One example is the Message Analyzer tool, available as part of the Microsoft Remote Connectivity Analyzer ([testconnectivity.microsoft.com/tests/o365](https://testconnectivity.microsoft.com/tests/o365)). This will lay out the hops that the message took more clearly and break out the headers added by each MTA. 

### Mobile

Mobile phone metadata comprises call detail records ([[CDRs]]) of incoming, outgoing, and attempted calls and SMS text time, duration, and the opposite party's number. Metadata will also record data transfer volumes. The location history of the device can be tracked by the list of cell towers it has used to connect to the network. If you are investigating a suspected insider attack, this metadata could prove a suspect's whereabouts. Furthermore, AI-enabled analysis (or patient investigation) can correlate the opposite party numbers to businesses and individuals through other public records.

CDRs are generated and stored by the **mobile operator**. The retention period for CDRs is determined by national and state laws, but is typically around **18 months**. CDRs are directly available for corporate-owned devices, where you can request them from the communications provider as the owner of the device. Metadata for personally owned devices would only normally be accessible by law enforcement agencies by subpoena or with the consent of the account holder. An employment contract might require an employee to give this consent for bring your own device ([[BYOD]]) mobiles used within the workplace.

Metadata such as current location and time is also added to media such as photos and videos, though this is true for all types of computing device. When these files are uploaded to social media sites, they can reveal more information than the uploader intended.
# NETWORK DATA SOURCES

[[Network data]] is typically analyzed in detail at the level of **individual frames** or using summary statistics of **traffic flows and protocol usage**.

### Protocol Analyzer Output

A [[SIEM]] will store details from [[sensors]] at different points on the network. Information captured from network packets can be aggregated and summarized to show overall protocol usage and endpoint activity. The contents of packets can also be recorded for analysis. Recording the full data of every packet—referred to as retrospective network analysis ([[RNA]])—is too costly for most organizations. Typically, packet contents are only retained when indicators from the traffic are correlated as an event. The SIEM software will provide the ability to [[pivot from the event]] or alert summary to the underlying packets. Detailed analysis of the packet contents can help to reveal the tools used in an attack. It is also possible to extract binary files such as potential malware for analysis.

### Netflow/IPFIX 

A flow collector is a means of **recording metadata and statistics about network traffic rather than recording each frame**. Network traffic and flow data may come from a wide variety of #zFleck  [[sources]] (or probes), such as switches, routers, firewalls, web proxies, and so forth. Flow analysis tools can provide features such as:

-   **Highlighting** of trends and patterns in traffic generated by particular applications, hosts, and ports.
-   **Alerting** based on detection of anomalies, flow analysis patterns, or custom triggers.
-   **Visualization** tools that enable you to quickly create a map of network connections and interpret patterns of traffic and flow data.
-   **Identification of traffic** patterns revealing rogue user behavior, malware in transit, tunneling, applications exceeding their allocated bandwidth, and so forth.
-   **Identification of attempts** by malware to contact a handler or command & control ([[C&C]]) channel.

NetFlow is a Cisco-developed means of reporting network flow information to a structured database. NetFlow has been redeveloped as the IP Flow Information Export ([[IPFIX]]) IETF standard ([tools.ietf.org/html/rfc7011](https://tools.ietf.org/html/rfc7011)). **A particular traffic flow can be defined by packets sharing the same characteristics, referred to as keys,** such as IP source and destination addresses and protocol type. A selection of keys is called a flow label, while traffic matching a flow label is called a flow record.  ==Does this only appy to NetFlow?==

You can use a variety of NetFlow monitoring tools to capture data for point-in-time analysis and to diagnose any security or operational issues the network is experiencing. There are plenty of commercial NetFlow suites, plus products offering similar functionality to NetFlow. The SiLK suite ([tools.netsa.cert.org/silk/](https://tools.netsa.cert.org/silk/)) and nfdump/nfsen ([nfsen.sourceforge.net/](http://nfsen.sourceforge.net/)) are examples of open-source implementations. Another popular tool is Argus ([openargus.org](https://openargus.org/)). This uses a different data format to NetFlow, but the client tools can read and translate NetFlow data. 

### sFlow

sFlow, developed by HP and subsequently adopted as a web standard ([tools.ietf.org/html/rfc3176](https://tools.ietf.org/html/rfc3176)), uses sampling to measure traffic statistics at **any layer of the OSI model for a wider range of protocol types than the IP-based Netflow. sFlow can also capture the entire packet header for samples.** 

### Bandwidth Monitor

Bandwidth usage can be a key indicator of suspicious behavior, if you have reliable baselines for comparison. Unexpected bandwidth consumption could be evidence of a data exfiltration attack, for instance. Bandwidth usage can be reported by flow collectors. Firewalls and web security gateways are also likely to support bandwidth monitoring and alerting.
