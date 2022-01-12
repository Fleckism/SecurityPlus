## EXAM OBJECTIVES COVERED

1.5 Explain different threat actors, vectors, and intelligence sources

As a security professional, you must continually refresh and expand your knowledge of both security technologies and practices and adversary tactics and techniques. As well as staying up-to-date on a personal level, you will also need to select and deploy threat intelligence platforms. You need to be able to identify and evaluate sources of threat intelligence and research and to use these resources to enhance security controls.

## THREAT RESEARCH SOURCES

Threat research is a counterintelligence gathering effort in which security companies and researchers attempt to discover the tactics, techniques, and procedures (TTPs) of modern cyber adversaries. There are many companies and academic institutions engaged in primary cybersecurity research. Security solution providers with firewall and anti-malware platforms derive a lot of data from their own customers' networks. As they assist customers with cybersecurity operations, they are able to analyze and publicize TTPs and their indicators. These organizations also operate honeynets to try to observe how hackers interact with vulnerable systems. 

Another primary source of threat intelligence is the dark web. The deep web is any part of the World Wide Web that is not indexed by a search engine. This includes pages that require registration, pages that block search indexing, unlinked pages, pages using nonstandard DNS, and content encoded in a nonstandard manner. Within the deep web, are areas that are deliberately concealed from "regular" browser access.

-   Dark net—a network established as an overlay to Internet infrastructure by software, such as The Onion Router (TOR), Freenet, or I2P, that acts to anonymize usage and prevent a third party from knowing about the existence of the network or analyzing any activity taking place over the network. Onion routing, for instance, uses multiple layers of encryption and relays between nodes to achieve this anonymity.
-   Dark web—sites, content, and services accessible only over a dark net. While there are dark web search engines, many sites are hidden from them. Access to a dark web site via its URL is often only available via "word of mouth" bulletin boards.

![Screenshot of AlphaBay Market showing "Tor circuit for this site" with 8 steps including IP addresses in Italy, Sweden, and Germany.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2941-1599771794384.png)

Using the TOR browser to view the AlphaBay market, now closed by law enforcement. (Screenshot used with permission from Security Onion.)

Investigating these dark web sites and message boards is a valuable source of counterintelligence. The anonymity of dark web services has made it easy for investigators to infiltrate the forums and webstores that have been set up to exchange stolen data and hacking tools. As adversaries react to this, they are setting up new networks and ways of identifying law enforcement infiltration. Consequently, dark nets and the dark web represent a continually shifting landscape.

## THREAT INTELLIGENCE PROVIDERS

The outputs from the primary research undertaken by security solutions providers and academics can take three main forms:

-   Behavioral threat research—narrative commentary describing examples of attacks and TTPs gathered through primary research sources.
-   Reputational threat intelligence—lists of IP addresses and domains associated with malicious behavior, plus signatures of known file-based malware.
-   Threat data—computer data that can correlate events observed on a customer's own networks and logs with known TTP and threat actor indicators.

Threat data can be packaged as feeds that integrate with a **security information and event management (SIEM)** platform. These feeds are usually described as cyber threat intelligence (CTI) data. The data on its own is not a complete security solution however. To produce actionable intelligence, the threat data must be correlated with observed data from customer networks. This type of analysis is often powered by artificial intelligence (AI) features of the SIEM.

Threat intelligence platforms and feeds are supplied as one of four different commercial models:

-   Closed/proprietary—the threat research and CTI data is made available as a paid subscription to a commercial threat intelligence platform. The security solution provider will also make the most valuable research available early to platform subscribers in the form of blogs, white papers, and webinars. Some examples of such platforms include:
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