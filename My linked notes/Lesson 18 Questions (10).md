# 1
A systems breach occurs at a financial organization. The system in question contains highly valuable data. When performing data acquisition for an investigation, which component does an engineer acquire first?

4.  Disk controller cache

Solution

The order of volatility outlines a general list of which components the engineer should examine for data. The engineer should first examine CPU registers and cache memory (including the cache on disk controllers and GPUs).

The engineer should acquire contents of nonpersistent system memory (RAM), including routing tables, ARP caches, process tables, and kernel statistics after any cache memory.

The engineer performs data acquisition on persistent mass storage devices after any available system caches or memory. This includes temporary files, such as those found in a browser cache.

The engineer performs data acquisition on persistent mass storage devices (such as HDDs or SSDs) after any available system caches or memory.
# 2
A cloud server has been breached. The organization realizes that data acquisition differs in the cloud when compared to on-premises. What roadblocks may the organization have to consider when considering data? **(Select all that apply.)**

1.  On-demand services
2.  Jurisdiction
3.  Chain of custody

Solution

The on-demand nature of cloud services means that instances are often created and destroyed again, with no real opportunity for forensic recovery of any data.

Jurisdiction and data sovereignty may restrict what evidence the CSP is willing to release to the organization.

Chain of custody issues are complex as it may have to rely on the CSP to select and package data for the organization.

If the CSP is a data processor, it will be bound by data breach notification laws and regulations. This issue does not relate to the acquisition of data.
# 3
Which term defines the practice of collecting evidence from computer systems to an accepted standard in a court of law?

1.  Forensics

Solution

Computer forensics is the practice of collecting evidence from computer systems to an accepted standard in a court of law.

Due Process is a common law term used in the US and the UK which requires that people only be convicted of crimes following the fair application of the laws of the land.

eDiscovery is a means of filtering the relevant evidence produced from all the data gathered by a forensic examination and storing it in a database in a format to use as evidence in a trial.

Legal hold refers to the fact that information that may be relevant to a court case must be preserved.
# 4
A systems breach occurs at a manufacturer. The system in question contains highly valuable data. An engineer plans a live acquisition, but ultimately, is not successful. What reason may be stopping the engineer?

2.  The tools are not preinstalled or running


Solution

A specialist hardware or software tool can capture the contents of memory while the host is running (live acquisition). This type of tool needs to be pre-installed or a standalone executable needs to be run, as it requires a kernel mode driver to dump any data of interest.

When a Windows host is in a sleep state, the system creates a hibernation file on disk in the root folder of the boot volume. This file is not a prerequisite for a live acquisition.

When Windows encounters an unrecoverable kernel error, it can write contents of memory to a dump file. This file is not a prerequisite for a live acquisition.

The pagefile/swap file/swap partition stores pages of memory in use that exceed the capacity of the host's RAM modules. This file is not a prerequisite for a live acquisition.
# 5
An engineer retrieves data for a legal investigation related to an internal fraud case. The data in question is from an NTFS volume. What will the engineer have to consider with NTFS when documenting a data timeline?

1.  UTC time

Solution

NTFS uses UTC "internally." When collecting evidence, it is vital to establish the procedure to calculate a timestamp and note the difference between the local system time and UTC.

Devices might be pointed towards an NTP server to synchronize time, but the engineer will need to record the times that the actual device itself is registering. 

Most computers have the clock configured to synchronize to a Network Time Protocol (NTP) server. Closely synchronized time is important for authentication and audit systems to work properly.

A Dynamic Host Configuration Protocol (DHCP) server is not associated with time. A DHCP server distributes IP addresses to clients on the network. These logs could be helpful though during the investigation.
# 6
A security expert archives sensitive data that is crucial to a legal case involving a data breach. The court is holding this data due to its relevance. The expert fully complies with any procedures as part of what legal process?

4.  Legal hold

Solution

Legal hold refers to information that the security expert must preserve, which may be relevant to a court case. Regulators or the industry's best practice may define the information that is subject to legal hold.

Chain of custody reinforces the integrity and proper handling of evidence from collection, to analysis, to storage, and finally to presentation. When security breaches go to trial, the chain of custody protects an organization against accusations of tampering with the evidence.

Due process is a common law term used in the US and UK to require that people only be convicted of crimes following the fair application of the laws of the land.

Forensics is the practice of collecting evidence from computer systems to a standard that a court of law will accept.
# 7
An engineer plans to acquire data from a disk. The disk is connected to the forensics workstation and is ready for the engineer. Which steps indicate a correct order of acquisition as they relate to integrity and non-repudiation?

1.  1. A hash of the disk is made 2. A bit-by-bit copy is made 3. A second hash is made 4. A copy is made of the reference image

Solution

In the correct first step, the engineer makes a cryptographic hash of the disk media, using either the MD5 or SHA hashing function. The output of the function is a checksum.

In the correct second step, the engineer makes a bit-by-bit copy of the media using the imaging utility.

In the correct third step, the engineer then makes a second hash of the image, which should match the original hash of the media.

In the correct fourth step, the engineer makes a copy of the reference image and then validates it again by the checksum. The engineer then performs an analysis on the copy.
# 8
A system breach occurs at a retail distribution center. Data from a persistent disk is required as evidence. No write blocker technology is available. Which approach does a security analyst use to acquire the disk?

3.  Snapshot


Solution

A snapshot is a live acquisition image of a persistent disk. It may have less validity than an image taken from a device using a write blocker technology.

Fragments on a disk might represent deleted or overwritten files. The process of recovering them is carving.

Cache can refer either to hardware components or software. The system uses a software-based cache in the file system, and when needed, the admin can acquire it as part of a disk image.

Artifacts refer to any type of data that is not part of the mainstream data structures of an operating system.
# 9
An engineer utilizes digital forensics for information gathering. While doing so, the first focus is counterintelligence. Which concepts does the engineer pursue? **(Select all that apply.)**

1.  Identification and analysis of specific adversary tactics

3.  Configure and audit active logging systems


Solution

Counterintelligence includes the identification and analysis of specific adversary tactics, techniques, and procedures (TTP). This information furthers the betterment of understanding adversary approaches that counterintelligence can note for monitoring.

Counterintelligence provides information about how to configure and audit active logging systems so that they are most likely to capture evidence of attempted and successful intrusions.

Strategic intelligence is data and research that security specialists have analyzed to produce actionable insights that help to build mature cybersecurity capabilities.

Strategic intelligence is information that security specialists have gathered through research and provides insights used to inform risk management and security control provisioning.
# 10
Which of the following is an example of the process of identifying and de-duplicating files and metadata to be stored for evidence in a trial?

3.  eDiscovery

Solution

eDiscovery is a means of filtering the relevant evidence produced from all the data gathered by a forensic examination and storing it in a database in a format to use as evidence in a trial.

Legal hold refers to the fact that information that may be relevant to a court case must be preserved.

Forensics is the practice of collecting evidence from computer systems to an accepted standard in a court of law.

Due process is a term used in common law to require that people only be convicted of crimes following the fair application of the laws of the land.
