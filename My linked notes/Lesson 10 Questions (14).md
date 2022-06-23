# 1
Analyze the following scenarios and determine which best simulates a content filter in action. **(Select all that apply.)**


2.  A high school student is using the school library to do research for an assignment and cannot access certain websites due to the subject matter.

4.  A system administrator blocks access to social media sites after the CEO complains that work performance has decreased due to excessive social media usage at work.

Solution

A content filter restricts web use to only authorized sites. Examples of content filter uses can be schools restricting access to only sites that are .edu or to not allow sites that have adult-level content.

Another example of a content filter can be the workplace, only allowing sites that are for work purposes.

A proxy server works on a store-and-forward model and deconstructs each packet, performs analysis, then rebuilds the packet and forwards it on. A part of this process is removing suspicious content in the process of rebuilding the packet.

A system admin configures packet filtering firewalls by specifying a group of rules that define the type of data packet, and the appropriate action to take when the packet matches the rule.
# 2
Compare and analyze the types of firewalls available to differentiate between them. Choose the answer with the most correct description.

4.  An application firewall can analyze the HTTP headers to identify code that matches a pattern, while an appliance firewall monitors all traffic passing into and out of a network segment.

Solution

An application firewall can inspect the contents of packets at the application layer and can analyze the HTTP headers. It also analyzes the HTML code present in HTTP packets, to try to identify code that matches a pattern in its threat database.

Packet filtering firewalls operate at level 3 of the OSI model while circuit-level stateful inspection firewalls operate at layer 5 of the model.

An application aware firewall is also known as a stateful multilayer inspection or a deep packet inspection. An appliance firewall is a stand-alone hardware firewall that performs the function of a firewall only.

A packet filtering firewall is stateless, and an application firewall is a software application running on a single host.
# 3
Compare and contrast the characteristics of the various types of firewalls and select the correct explanation of a packet filtering firewall.

1.  An administrator configures an Access Control List (ACL) to deny access to IP addresses


Solution

An administrator configures a packet filtering firewall by specifying a group of rules, called an Access Control List (ACL). Each rule defines a specific type of data packet and the appropriate action to take when a packet matches the rule.

Packet filtering firewalls do not maintain stateful information about the connection between two hosts. The firewall analyzes each packet independently, with no record of previously processed packets.

Application aware firewalls can inspect the contents of packets at the application layer, which includes analyzing the HTTP headers and the HTML code.

An appliance firewall is a stand-alone hardware firewall that monitors all traffic passing into and out of a network segment
# 4
A network administrator wants to use a proxy server to prevent external hosts from connecting directly with application servers. Which proxy server implementation will best fit this need?

4.  Reverse proxy server

Solution

A transparent (or forced or intercepting) proxy intercepts client traffic without the client having to reconfigure with the proxy server address. The network admin may implement a transparent proxy on a switch, router, or other inline network appliance.

The network admin may configure the client with a non-transparent proxy server address and port number to use it (often configured as port 8080.).

A caching server that does not require a client-side configuration is called a transparent proxy server. In this type of server, the client is unaware of a proxy server, which redirects client requests without modification.

Deployed on the network edge, reverse proxy servers protect servers from direct contact with client requests from a public network (the Internet).
# 5
A system administrator wants to install a mechanism to conceal the internal IP addresses of hosts on a private network. What tool can the administrator use to accomplish this security function?

1.  NAT gateway


Solution

A NAT gateway translates between a local and public network by substituting private IPs for a public IP and forwarding the requests to the public Internet, thereby concealing private addressing schemes.

Deployed on the network edge, reverse proxy servers protect servers from direct contact with client requests from a public network (the Internet).

Virtual firewalls often enact east-west security and zero-trust microsegmentation design paradigms. Virtual firewalls can inspect traffic as it passes from host-to-host or between virtual networks, rather than routing that traffic up to a firewall appliance and back.

Firewall access control lists (ACLs) are configured on the principle of least access/least privilege.
# 6
Evaluate the functions of a Network-Based Intrusion Detection System (NIDS) and conclude which statements are accurate. **(Select all that apply.)**

2.  A NIDS will identify and log hosts and application activity that the administrator can use to analyze and take further action.
3.  Training and tuning are complex, and there is a high chance of false positive and negative rates.


Solution

A NIDS can identify and log hosts and applications and detect attack signatures and other indicators of attack. An administrator can analyze logs to tune firewall rulesets, remove or block suspect hosts and processes, or deploy additional security controls to mitigate threats identified.

One of the main disadvantages of NIDS is that training and tuning are complex, which results in high false positive and false negative rates, especially during initial deployment.

NIDS training and tuning are complex, with high initial false positive and false negative rates.

A NIDS will not block the traffic during an attack, which is a disadvantage. If an administrator does not immediately review logs during an attack, a delay will occur and the attack will continue.
# 7
A network administrator conducts a network assessment to determine where to implement a network intrusion detection system (NIDS). Which sensor deployment option is most ideal if the admin is concerned about system overloads and resiliency in the event of power loss?

1.  Passive test access point (TAP)


Solution

With a passive TAP, the monitor port receives every frame—corrupt, malformed, or not—and load does not affect copying.

Because it performs an active function, an active TAP becomes a point of failure for the links in the event of power loss. When deploying an active TAP, it is important to use a model with backup power options.

Aggregation TAPs rebuild the upstream and downstream channels into a single channel, but these can drop frames under very heavy load.

SPAN/mirror port sensor is not completely reliable, as frames with errors will not be mirrored and frames may be dropped under heavy load.
# 8
Which of the following considerations is most important when employing a signature-based intrusion detection system?


3.  Signatures and rules must be kept up to date to protect against emerging threats.


Solution

Network behavior and anomaly detection (NBAD) engines use heuristics to generate a statistical model of baseline normal traffic. The system generates false positives and false negatives until, over time, it improves its statistical model of normal activity. A false positive is where legitimate behavior generates an alert.

Behavioral-based detection engines are trained to recognize baseline "normal" traffic or events. Anything that deviates from this baseline generates an incident.

The signatures and rules (often called plug-ins or feeds) powering intrusion detection need updating regularly to provide protection against the latest threat types.

Behavioral-based detection software attempts to identify zero-day attacks, insider threats, and other malicious activity, for which there is a single signature that deviates from the baseline.
# 9
Which of the following solutions best addresses data availability concerns that may arise with the use of application-aware next-generation firewalls (NGFW) and unified threat management (UTM) solutions?


2.  Secure web gateway (SWG)
3. 
Solution

While complex NGFW and UTM solutions provide high confidentiality and integrity, lower throughput reduces availability. One solution to this is to treat security solutions for server traffic differently from that for user traffic. An SWG acts as a content filter, which applies user-focused filtering rules and also conducts threat analysis.

A signature-based detection (or pattern-matching) engine is loaded with a database of attack patterns or signatures. If traffic matches a pattern, then the engine generates an incident.

Intrusion prevention systems (IPS), positioned like firewalls at borders between network zones, provide an active response to network threats.

A TAP is a hardware device inserted into a cable to copy frames for analysis.
# 10
A networking administrator is reviewing available security products to further fine-tune the existing firewall and appliance settings. What system allows an administrator to tune firewall rulesets and remove or block suspect hosts and processes from the network?

1.  Network-based intrusion detection system (NIDS)


Solution

Analyzing NIDS logs allows an administrator to tune firewall rulesets, remove or block suspect hosts and processes from the network, or deploy additional security controls to mitigate any identified threats.

A Unified threat management (UTM) product centralizes many types of security controls into a single appliance. A UTM might not perform as well as software or a device with a single dedicated security function.

Compared to the passive function of an IDS, an intrusion prevention system (IPS) can provide an active response to any network threats that it matches.

An NBAD engine uses heuristics to generate a statistical model baseline normal traffic. The system generates false positives and false negatives until it improves its statistical model of what is "normal."
# 11
Which of the following are types of log collection for SIEM? **(Select all that apply.)**

3.  Agent-based
4.  Listener/Collector

Solution

With the agent-based approach, one must install an agent service on each host. As events occur on the host, logging data is filtered, aggregated, and normalized at the host, then sent to the SIEM server for analysis and storage.

With the listener/collector approach, rather than installing an agent, hosts can be configured to push updates to the SIEM server using a protocol such as _syslog_ or SNMP. A process runs on the management server to parse and normalize each log/monitoring source.

Log aggregation refers to normalizing data from different sources so that it is consistent and searchable and does not refer to a type of log collection

Firewalls are a source of logs that are often sent into a SIEM but is not a type of log collection for SIEMs.
# 12
Artificial intelligence (AI) and machine learning are especially important during which security information and event management (SIEM) task?


2.  Analysis and report review


Solution

Data captured from network sensors/sniffers plus netflow sources provide both summary statistics about bandwidth and protocol usage and the opportunity for detailed frame analysis.

SIEM software can link individual events or data points (observables) into a meaningful indicator of risk, or Indicator of Compromise (IOC). Many SIEM solutions use artificial intelligence (AI) and machine learning as the basis for automated analysis.

As distinct from collection, aggregation refers to normalizing data from different sources so that it is consistent and searchable.

The first task for SIEM is to collect data inputs from multiple sources, including agent-based log collection, sensor or sniffer data, and listener/collector protocols, such as syslog and Simple Network Management Protocol (SNMP).
# 13
Analyze each statement and determine which describes a fundamental improvement on traditional log management that security information and event management (SIEM) offers.


3.  SIEM can perform correlation, linking observables into meaningful indicators of risk or compromise.


Solution

While SIEM can automate many functions of log collection and review, security managers may also have to manually prepare data using a Linux command line.

Logs typically associate an action with a particular user, satisfying non-repudiation.

SIEM correlates individual events or data points (observables) into a meaningful indicator of risk, or Indicator of Compromise (IOC). Correlation is the principal factor distinguishing it from basic log management.

Security orchestration, automation, and response (SOAR) is a solution to the problem of the volume of alerts overwhelming analysts' ability to respond. A security engineer may implement SOAR as a standalone technology or integrate it with a SIEM, using machine/deep learning techniques to enrich data for use in incident response and threat hunting.
# 14
Security information and event management (SIEM) collect data inputs from multiple sources. Which of the following is NOT one of the main types of log collection for SIEM?

4.  Artificial intelligence (AI)

Solution

With an agent-based approach, data managers must install an agent service on each host. As events occur on the host, logging data is filtered, aggregated, and normalized at the host, then sent to the SIEM server for analysis and storage.

A listener/collector appliance gathers or receives log and/or state data from other network systems, using a protocol, such as syslog or simple network management protocol (SNMP).

As well as log data, the SIEM might collect packet captures and traffic flow data from sniffers/sensors.

AI and machine learning can drive correlation efforts for automated analysis.
