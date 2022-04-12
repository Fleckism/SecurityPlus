---
tags: [,section]
---
# LESSON INTRODUCTION

Where incident response emphasizes the swift eradication of malicious activity, digital forensics requires patient capture, preservation, and analysis of evidence using verifiable methods. You may be called on to assist with an investigation into the details of a security incident and to identify [[threat actor]]s. To assist these investigations, you must be able to **summarize the basic concepts of collecting and processing forensic evidence** that could be used in legal action or for strategic counterintelligence.

Lesson Objectives

In this lesson, you will:

-   Explain key aspects of digital forensics documentation.
-   Explain key aspects of digital forensics evidence acquisition.
# EXAM OBJECTIVES COVERED

4.5 Explain the key aspects of digital forensics

Documentation is critical to collecting, preserving, and presenting valid digital proofs. Mistakes or gaps in the record of the process can lead to the evidence being dismissed. You should be able to explain key aspects of forensics documentation so that you give effective assistance to investigators.
# KEY ASPECTS OF DIGITAL FORENSICS 

**Digital forensics is the practice of collecting evidence from computer systems to a standard that will be accepted in a court of law**. Forensics investigations are most likely to be launched against crimes arising from insider threats, notably fraud or misuse of equipment (to download or store obscene material, for instance). Prosecuting external threat sources is often difficult, as the [[[[threat actor]]]] may well be in a different country or have taken effective steps to disguise his or her location and identity. Such prosecutions are normally initiated by law enforcement agencies, where the threat is directed against military or governmental agencies or is linked to organized crime. 

### Evidence, Documentation, and Admissibility

Like DNA or fingerprints, digital evidence is latent. **Latent means that the evidence cannot be seen with the naked eye**; rather, it must be interpreted using a machine or process. This means that great care must be taken to ensure the admissibility of digital evidence. As well as the physical evidence (a hard drive, for instance), digital forensics requires documentation showing how the evidence was collected and analyzed without tampering or bias.

Due process is a term used in US and UK common law to require that people only be convicted of crimes following the fair application of the laws of the land. More generally, **due process can be understood to mean having a set of procedural safeguards to ensure fairness**. This principle is central to forensic investigation. If a forensic investigation is launched (or if one is a possibility), it is important that technicians and managers are aware of the processes that the investigation will use. It is vital that they are able to assist the investigator and that they not do anything to compromise the investigation. In a trial, defense counsel will try to exploit any uncertainty or mistake regarding the integrity of evidence or the process of collecting it.

The first response period following detection and notification is often critical. To gather evidence successfully, it is vital that staff do not panic or act in a way that would compromise the investigation. 

### Legal Hold

Legal hold refers to the fact that information that may be relevant to a **court case must be preserved**. Information subject to legal hold might be defined by regulators or industry best practice, or there may be a litigation notice from law enforcement or lawyers pursuing a civil action. This means that computer systems may be taken as evidence, with all the obvious disruption to a network that entails. 

### Chain of Custody

Chain of custody documentation reinforces the integrity and proper handling of evidence from collection, to analysis, to storage, and finally to presentation. When security breaches go to trial, the chain of custody protects an organization against accusations that evidence has either been tampered with or is different than it was when it was collected. Every person in the chain who handles evidence must log the methods and tools they used.
# DIGITAL FORENSICS REPORTS

A digital forensics report summarizes the significant contents of the digital data and the conclusions from the investigator's analysis. It is important to note that strong ethical principles must guide forensics analysis.

-   **Analysis must be performed without bias**. Conclusions and opinions should be formed only from the direct evidence under analysis.
-   **Analysis methods must be repeatable by third parties with access to the same evidence.**
-   **Ideally, the evidence must not be changed or manipulated**. If a device used as evidence must be manipulated to facilitate analysis (disabling the lock feature of a mobile phone or preventing a remote wipe for example), the reasons for doing so must be sound and the process of doing so must be recorded.

Defense counsel may try to use any deviation of good ethical and professional behavior to have the forensics investigator's findings dismissed.
# E-DISCOVERY

A forensic examination of a device such as a fixed drive that contains Electronically Stored Information (ESI) entails a search of the whole drive (including both allocated and unallocated sectors, for instance). E-discovery is a means of filtering the relevant evidence produced from all the data gathered by a forensic examination and storing it in a database in a format such that it can be used as evidence in a trial. E-discovery software tools have been produced to assist this process. Some of the functions of e-discovery suites are:

-   **Identify and deduplicate files and metadata**—many files on a computer system are "standard" installed files or copies of the same file. E-discovery filters these types of files, reducing the volume of data that must be analyzed.
-   **Search**—allow investigators to locate files of interest to the case. As well as keyword search, software might support semantic search. Semantic search matches keywords if they correspond to a particular context.
-   **Tags**—apply standardized keywords or labels to files and metadata to help **organize** the evidence. Tags might be used to indicate relevancy to the case or part of the case or to show confidentiality, for instance.
-   **Security**—at all points evidence must be shown to have been stored, transmitted, and analyzed without tampering.
-   **Disclosure**—an important part of trial procedure is that the same evidence be made available to both plaintiff and defendant. E-discovery can fulfill this requirement. Recent court cases have required parties to a court case to provide searchable ESI rather than paper records.
# VIDEO AND WITNESS INTERVIEWS

The first phase of a forensics investigation is to document the scene. The crime scene must be recorded using photographs and ideally audio and video. Investigators must capture every action they take in identifying, collecting, and handling evidence.

Remember that if the matter comes to trial, the trial could take place months or years after the event. It is vital to record impressions and actions in notes. Also consider that in-place CCTV systems or webcams might have captured valuable evidence.

If possible, evidence is gathered from the live system using forensic software tools. It is vital that these tools do as little to modify the digital data that they capture as possible.

As well as digital evidence, an investigator should interview witnesses to establish what they were doing at the scene, whether they observed any suspicious behavior or activity, and also to gather information about the computer system. An investigator might ask questions informally and record the answers as notes to gain an initial understanding of the circumstances surrounding an incident. **An investigator must ask questions carefully, to ensure that the witness is giving reliable information and to avoid leading the witness to a particular conclusion**. Making an audio or video recording of witness statements produces a more reliable record but may make witnesses less willing to make a statement. If a witness needs to be compelled to make a statement, there will be legal issues around employment contracts (if the witness is an employee) and right to legal representation.
# TIMELINES

A significant part of a forensic investigation will involve tying events to specific times to establish a consistent and verifiable narrative. The visual representation of events happening in chronological order is called a timeline.

Operating systems and file systems use a variety of methods to identify the time at which something occurred. The benchmark time is **Coordinated Universal Time** (UTC), which is essentially the time at the Greenwich meridian. Local time is the time within a particular time zone, which will be offset from UTC by several hours (or in some cases, half hours). The local time offset may also vary if a seasonal daylight saving time is in place.

**NT File System** (NTFS) uses UTC "internally", but many OS and file systems record time stamps as the **local system time**. When collecting evidence, it is vital to establish how a time stamp is calculated and note the offset between the local system time and UTC.

Forensics also needs to consider that a host's system clock may not be properly synchronized to a valid time source or may have been tampered with. Most computers are configured to synchronize the clock to a **Network Time Protocol** (NTP) server. Closely synchronized time is important for authentication and audit systems to work properly. The right to modify a computer's time would normally be restricted to administrator-level accounts (on enterprise networks) and time change events should be logged.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5310-1599771811654.png)

Using Autopsy to generate a timeline of events from a disk image. (Screenshot Autopsy—the Sleuth Kit [sleuthkit.org/autopsy](http://www.sleuthkit.org/autopsy/).)
# EVENT LOGS AND NETWORK TRAFFIC

Digital evidence is not just drawn from analysis of host system memory and data drives. An investigation may also obtain the event logs for one or more network appliances and/or server hosts. Similarly, network packet captures and traces/flows might provide valuable evidence. On a typical network, sensor and logging systems are not configured to record all network traffic, as this would generate a very considerable amount of data. On the other hand, an organization with sufficient IT resources could choose to preserve a huge amount of data. A **Retrospective Network Analysis** (RNA) solution provides the means to record [[network events at either a packet header or payload level.]]

For forensics, data records that are not supported by physical evidence (a data drive) must meet many tests to be admissible in court. For event logs, the drives might not be accessible or might no longer hold the original logs; for network traffic, there is no physical evidence. Where logs and network traffic are captured in a [[SIEM]], the SIEM should demonstrate accuracy (that all relevant data was captured) and integrity (that neither party could have tampered with the data).
# STRATEGIC INTELLIGENCE AND COUNTERINTELLIGENCE

In some cases, an organization may conduct a forensics investigation without the expectation of legal action. As well as being used in a legal process, forensics has a role to play in cybersecurity. It enables the detection of past intrusions or ongoing but unknown intrusions by close examination of available digital evidence. A famous quote attributed to former Cisco CEO John Chambers illustrates the point: "There are two types of companies: those that have been hacked, and those who don't know they have been hacked."

Digital forensics can be used for information gathering to protect against espionage and hacking. This intelligence is deployed in two different ways:

-   [[Counterintelligence]]—identification and analysis of specific adversary tactics, techniques, and procedures (TTP) provides information about how to configure and audit active logging systems so that they are most likely to capture evidence of attempted and successful intrusions.
-   [[Strategic intelligence]]—data and research that has been analyzed to produce actionable insights. These insights are used to inform risk management and security control provisioning to build mature cybersecurity capabilities.
