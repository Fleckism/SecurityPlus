---
tags: [implementation, secondTag]
---
# EXAM OBJECTIVES COVERED

2.1 Explain the importance of security concepts in an enterprise environment

3.2 Given a scenario, implement host or application security solutions

5.5 Explain privacy and sensitive data concepts in relation to security

Policies and procedures are essential for effective data governance, but they can be supported by technical controls too. As a security professional, you need to be aware of the capabilities of data loss prevention (DLP) systems and privacy enhancing database controls, and how they can be used to protect data anywhere it resides, on hosts, in email systems, or in the cloud.
# DATA PROTECTION

Data stored within a trusted OS can be subject to authorization mechanisms where the OS mediates access using some type of ACL. The presence of a trusted OS cannot always be assumed, however. Other data protection mechanisms, notably encryption, can be used to mitigate the risk that an authorization mechanism can be countermanded. When deploying a cryptographic system to protect data assets, consideration must be given to all the ways that information could potentially be intercepted. This means thinking beyond the simple concept of a data file stored on a disk. Data can be described as being in one of three states:

-   Data at rest—this state means that the data is in some sort of persistent storage media. Examples of types of data that may be at rest include financial information stored in databases, archived audiovisual media, operational policies and other management documents, system configuration data, and more. In this state, it is usually possible to encrypt the data, using techniques such as whole disk encryption, database encryption, and file- or folder-level encryption. It is also possible to apply permissions—access control lists (ACLs)—to ensure only authorized users can read or modify the data. ACLs can be applied only if access to the data is fully mediated through a trusted OS.
-   Data in transit (or data in motion)—this is the state when data is transmitted over a network. Examples of types of data that may be in transit include website traffic, remote access traffic, data being synchronized between cloud repositories, and more. In this state, data can be protected by a transport encryption protocol, such as TLS or IPSec. 

With data at rest, there is a greater encryption challenge than with data in transit as the encryption keys must be kept secure for longer. Transport encryption can use ephemeral (session) keys.

-   Data in use (or data in processing)—this is the state when data is present in volatile memory, such as system RAM or CPU registers and cache. Examples of types of data that may be in use include documents open in a word processing application, database data that is currently being modified, event logs being generated while an operating system is running, and more. When a user works with data, that data usually needs to be decrypted as it goes from in rest to in use. The data may stay decrypted for an entire work session, which puts it at risk. However, trusted execution environment (TEE) mechanisms, such as Intel Software Guard Extensions ([software.intel.com/content/www/us/en/develop/topics/software-guard-extensions/details.html](https://software.intel.com/content/www/us/en/develop/topics/software-guard-extensions/details.html)) are able to encrypt data as it exists in memory, so that an untrusted process cannot decode the information.
# DATA EXFILTRATION

In a workplace where mobile devices with huge storage capacity proliferate and high bandwidth network links are readily available, attempting to prevent the loss of data by controlling the types of storage devices allowed to connect to PCs and networks can be impractical. Unauthorized copying or retrieval of data from a system is referred to as data exfiltration. Data exfiltration attacks are one of the primary means for attackers to retrieve valuable data, such as personally identifiable information (PII) or payment information, often destined for later sale on the black market. Data exfiltration can take place via a wide variety of mechanisms, including:

-   Copying the data to removable media or other device with storage, such as USB drive, the memory card in a digital camera, or a smartphone.
-   Using a network protocol, such as HTTP, FTP, SSH, email, or Instant Messaging (IM)/chat. A sophisticated adversary might use a Remote Access Trojan (RAT) to perform transfer of data over a nonstandard network port or a packet crafter to transfer data over a standard port in a nonstandard way. The adversary may also use encryption to disguise the data being exfiltrated.
-   By communicating it orally over a telephone, cell phone, or Voice over IP (VoIP) network. Cell phone text messaging is another possibility.
-   Using a picture or video of the data—if text information is converted to an image format it is very difficult for a computer-based detection system to identify the original information from the image data.

While some of these mechanisms are simple to mitigate through the use of security tools, others may be much less easily defeated. You can protect data using mechanisms and security controls that you have examined previously:

-   Ensure that all sensitive data is encrypted at rest. If the data is transferred outside the network, it will be mostly useless to the attacker without the decryption key.
-   Create and maintain offsite backups of data that may be targeted for destruction or ransom.
-   Ensure that systems storing or transmitting sensitive data are implementing access controls. Check to see if access control mechanisms are granting excessive privileges to certain accounts.
-   Restrict the types of network channels that attackers can use to transfer data from the network to the outside. Disconnect systems storing archived data from the network.
-   Train users about document confidentiality and the use of encryption to store and transmit data securely. This should also be backed up by HR and auditing policies that ensure staff are trustworthy.

Even if you apply these policies and controls diligently, there are still risks to data from insider threats and advanced persistent threat (APT) malware. Consequently, a class of security control software has been developed to apply access policies directly to data, rather than just the host or network on which data is located.
# DATA LOSS PREVENTION

To apply data guardianship policies and procedures, smaller organizations might classify and type data manually. An organization that creates and collects large amounts of personal data will usually need to use automated tools to assist with this task, however. There may also be a requirement to protect valuable intellectual property (IP) data. Data loss prevention (DLP) products automate the discovery and classification of data types and enforce rules so that data is not viewed or transferred without a proper authorization. Such solutions will usually consist of the following components:

-   Policy server—to configure classification, confidentiality, and privacy rules and policies, log incidents, and compile reports.
-   Endpoint agents—to enforce policy on client computers, even when they are not connected to the network.
-   Network agents—to scan communications at network borders and interface with web and messaging servers to enforce policy.

DLP agents scan content in structured formats, such as a database with a formal access control model or unstructured formats, such as email or word processing documents. A file cracking process is applied to unstructured data to render it in a consistent scannable format. The transfer of content to removable media, such as USB devices, or by email, instant messaging, or even social media, can then be blocked if it does not conform to a predefined policy. Most DLP solutions can extend the protection mechanisms to cloud storage services, using either a proxy to mediate access or the cloud service provider's API to perform scanning and policy enforcement. 

![Screenshot of Office 365 Security and Compliance window with Data loss prevention menu option expanded and Policy selected." aria-label="In the New DLP policy submenu, Policy settings is selected, where you can customize the type of content you want to protect. Options include Find content that contains: U.S. Individual Taxpayer Identification Number (ITIN), U.S. Social Security Number (SSN), U.S. / U.K. Passport Number. An Edit link is shown below these options. Below that, the box for Detect when this content is shared (with people outside my organization) is checked.  There is also an option to use advanced settings.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/782-1599771810848.png)

Creating a DLP policy in Office 365. (Screenshot used with permission from Microsoft.)

Remediation is the action the DLP software takes when it detects a policy violation. The following remediation mechanisms are typical:

-   Alert only—the copying is allowed, but the management system records an incident and may alert an administrator.
-   Block—the user is prevented from copying the original file but retains access to it. The user may or may not be alerted to the policy violation, but it will be logged as an incident by the management engine.
-   Quarantine—access to the original file is denied to the user (or possibly any user). This might be accomplished by encrypting the file in place or by moving it to a quarantine area in the file system.
-   Tombstone—the original file is quarantined and replaced with one describing the policy violation and how the user can release it again.

When it is configured to protect a communications channel such as email, DLP remediation might take place using client-side or server-side mechanisms. For example, some DLP solutions prevent the actual attaching of files to the email before it is sent. Others might scan the email attachments and message contents, and then strip out certain data or stop the email from reaching its destination.

Some of the leading vendors include McAfee ([skyhighnetworks.com/cloud-data-loss-prevention](https://www.skyhighnetworks.com/cloud-data-loss-prevention/)), Symantec/Broadcom ([broadcom.com/products/cyber-security/information-protection/data-loss-prevention](https://www.broadcom.com/products/cyber-security/information-protection/data-loss-prevention)), and Digital Guardian ([digitalguardian.com](https://digitalguardian.com/)). A DLP and compliance solution is also available with Microsoft's Office 365 suite ([docs.microsoft.com/en-us/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide](https://docs.microsoft.com/en-us/microsoft-365/compliance/data-loss-prevention-policies?view=o365-worldwide)).
# RIGHTS MANAGEMENT SERVICES

As another example of data protection and information management solutions, Microsoft provides an Information Rights Management (IRM) feature in their Office productivity suite, SharePoint document collaboration services, and Exchange messaging server. IRM works with the Active Directory Rights Management Services (RMS) or the cloud-based Azure Information Protection. These technologies provide administrators with the following functionality:

-   Assign file permissions for different document roles, such as author, editor, or reviewer.
-   Restrict printing and forwarding of documents, even when sent as file attachments.
-   Restrict printing and forwarding of email messages.

![On the Rights tab for “gtslearning - reviewers” above a list of users, text reads “The author of a protected document always has Full Control rights”](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1031-1599771810950.png)

Configuring a rights management template. (Screenshot used with permission from Microsoft.)

Rights management is built into other secure document solutions, such as Adobe Acrobat.
# PRIVACY ENHANCING TECHNOLOGIES

Data minimization is the principle that data should only be processed and stored if that is necessary to perform the purpose for which it is collected. In order to prove compliance with the principle of data minimization, each process that uses personal data should be documented. The workflow can supply evidence of why processing and storage of a particular field or data point is required. Data minimization affects the data retention policy. It is necessary to track how long a data point has been stored for since it was collected and whether continued retention supports a legitimate processing function. Another impact is on test environments, where the minimization principle forbids the use of real data records.

Counterintuitively, the principle of minimization also includes the principle of sufficiency or adequacy. This means that you should collect the data required for the stated purpose in a single transaction to which the data subject can give clear consent. Collecting additional data later would not be compliant with this principle.

Large data sets are often shared or sold between organizations and companies, especially within the healthcare industry. Where these data sets contain PII or PHI, steps can be taken to remove the personal or identifying information. These deidentification processes can also be used internally, so that one group within a company can receive data for analysis without unnecessary risks to privacy. Deidentification methods may also be used where personal data is collected to perform a transaction but does not need to be retained thereafter. This reduces compliance risk when storing data by applying minimization principles. For example, a company uses a customer's credit card number to take payment for an order. When storing the order details, it only keeps the final 4 digits of the card as part of the transaction log, rather than the full card number.

A fully anonymized data set is one where individual subjects can no longer be identified, even if the data set is combined with other data sources. Identifying information is permanently removed. Ensuring full anonymization and preserving the utility of data for analysis is usually very difficult, however. Consequently, pseudo-anonymization methods are typically used instead. Pseudo-anonymization modifies or replaces identifying information so that reidentification depends on an alternate data source, which must be kept separate. With access to the alternated data, pseudo-anonymization methods are reversible.

It is important to note that given sufficient contextual information, a data subject can be reidentified, so great care must be taken when applying deidentification methods for distribution to different sources. A reidentification attack is one that combines a deidentified data set with other data sources, such as public voter records, to discover how secure the deidentification method used is.

K-anonymous information is data that can be linked to two or more individuals. This means that the data does not unambiguously reidentify a specific individual, but there is a significant risk of reidentification, given the value of K. For example, if k=5, any group that can be identified within the data set contains at least five individuals. NIST has produced an overview of deidentification issues, in draft form at the time of writing ([csrc.nist.gov/CSRC/media/Publications/sp/800-188/draft/documents/sp800_188_draft2.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/sp800_188_draft2.pdf)).
# DATABASE DEIDENTIFICATION METHODS

Deidentification methods are usually implemented as part of the database management system (DBMS) hosting the data. Sensitive fields will be tagged for deidentification whenever a query or report is run.

### Data Masking

Data masking can mean that all or part of the contents of a field are redacted, by substituting all character strings with "x" for example. A field might be partially redacted to preserve metadata for analysis purposes. For example, in a telephone number, the dialing prefix might be retained, but the subscriber number redacted. Data masking can also use techniques to preserve the original format of the field. Data masking is an irreversible deidentification technique.

### Tokenization

Tokenization means that all or part of data in a field is replaced with a randomly generated token. The token is stored with the original value on a token server or token vault, separate to the production database. An authorized query or app can retrieve the original value from the vault, if necessary, so tokenization is a reversible technique. Tokenization is used as a substitute for encryption, because from a regulatory perspective an encrypted field is the same value as the original data.

### Aggregation/Banding

Another deidentification technique is to generalize the data, such as substituting a specific age with a broader age band. 

### Hashing and Salting

A cryptographic hash produces a fixed-length string from arbitrary-length plaintext data using an algorithm such as SHA. If the function is secure, it should not be possible to match the hash back to a plaintext. Hashing is mostly used to prove integrity. If two sources have access to the same plaintext, they should derive the same hash value. Hashing is used for two main purposes within a database:

-   As an indexing method to speed up searches and provide deidentified references to records.
-   As a storage method for data such as passwords where the original plaintext does not need to be retained.

A salt is an additional value stored with the hashed data field. The purpose of salt is to frustrate attempts to crack the hashes. It means that the attacker cannot use pre-computed tables of hashes using dictionaries of plaintexts. These tables have to be recompiled to include the salt value.
