---
tags: [Implementation, secondTag]
---
# EXAM OBJECTIVES COVERED

2.5 Given a scenario, implement cybersecurity resilience

No [[cybersecurity program]] is complete without an effective and tested system for backing up and restoring critical data and system configurations. As a security professional, you need to be able to select appropriate backup types and media for different scenarios and explain how [[nonpersistence]] can achieve more secure system configurations, as well as maintaining high availability.
# BACKUPS AND RETENTION POLICY

Every business continuity and disaster recovery plan makes use of backups, of one type or another. The execution and frequency of backups must be carefully planned and guided by policies. Data retention needs to be considered in the short and long term:

-   In the short term, files that change frequently might need retaining for version control. Short-term retention is also important in recovering from malware infection. Consider the scenario where a backup is made on Monday, a file is infected with a virus on Tuesday, and when that file is backed up later on Tuesday, the copy made on Monday is overwritten. This means that there is no good means of restoring the uninfected version of the file. Short-term retention is determined by how often the youngest media sets are overwritten.
-   In the long term, data may need to be stored to meet legal requirements or to comply with company policies or industry standards. Any data that must be retained in a particular version past the oldest sets should be moved to archive storage.

![Screenshot shows Items to backup, including Local folder and Network folder.  Specify folder pane shows A: and a list of folders under C:](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7461-1599771812358.png)

Performing a backup using Acronis Backup. (Screenshot used with permission from Acronis.)

For these reasons, backups are kept back to certain points in time. As backups take up a lot of space, and there is never limitless storage capacity, this introduces the need for storage management routines to reduce the amount of data occupying backup storage media while giving adequate coverage of the required recovery window. The recovery window is determined by the recovery point objective ([[RPO]]), which is determined through business continuity planning. Advanced backup software can prevent media sets from being overwritten in line with the specified retention policy.

![Screenshot shows Backup menu with Machines with agents option selected. The applied backup plan is shown for the selected machine.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4161-1599771812431.png)

Backing up a [[domain controller]] using Acronis backup—The How Long to Keep field specifies the retention period. (Screenshot used with permission from Acronis.)
# BACKUP TYPES

Utilities that support enterprise [[backup]] operations come with features to support retention policies and media rotation. When considering a backup made against an original copy of data, the backup can usually be performed using one of three main types: **full, incremental, and differential**. In Windows, a full backup includes all selected files and directories while incremental and differential backups check the status of the archive attribute before including a file. The archive attribute is set whenever a file is modified. This allows backup software to determine which files have been changed and therefore need to be copied.

**Linux doesn't support a file archive attribute. Instead, a date stamp is used to determine whether the file has changed.**

### Full, Incremental, and Differential Backup Types

The following table summarizes the three different backup types.

Type

Data Selection

Backup/Restore Time

Archive Attribute

Full

All selected data regardless of when it was previously backed up

High/low (one tape set)

Cleared

Incremental

New files, as well as files modified since the last backup

Low/high (multiple tape sets)

Cleared

Differential

All new and modified files since the last full backup

Moderate/moderate (no more than two sets)

Not Cleared

Differential and incremental backup and restore operations.

The factors that determine which method to use are the time it takes to restore versus the time it takes to back up. Assuming a backup is performed every working day, an incremental backup only includes files changed during that day, while a differential backup includes all files changed since the last full backup. Incremental backups save backup time but can be more time-consuming when the system must be restored. The system must be restored from the last full backup set and then from each incremental backup that has subsequently occurred. A differential backup system only involves two tape sets when restoration is required. 

Do not combine differential and incremental backups. Use full backups interspersed with differential backups or full backups interspersed with incremental backups.

### Copy Backups

Most software also has the capability to do copy backups. These are made outside the [[tape rotation system]] and do not affect the archive attribute.
# SNAPSHOTS AND IMAGES

**Snapshots**

Snapshots are a means of getting around the problem of open files. If the data that you're considering backing up is part of a database, such as SQL data or an [[Exchange messaging system]], then the data is probably being used all the time. Often copy-based mechanisms will be unable to back up open files. Short of closing the files, and so too the database, a copy-based system will not work. A snapshot is a point-in-time copy of data maintained by the file system. A backup program can use the snapshot rather than the live data to perform the backup. In Windows, snapshots are provided for on NTFS volumes by the Volume Shadow Copy Service ([[VSS]]). They are also supported on Sun's ZFS file system, and under some distributions of Linux.

![Screenshot shows Volume Shadow Copy Service (VSS) settings. Use VSS when taking snapshots and Automatically select snapshot provider are set.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7057-1599771812666.png)

Configuring VSS settings in Acronis Backup. (Screenshot used with permission from Acronis.)

Virtual system managers can usually take snapshot or cloned copies of VMs. A snapshot remains linked to the original VM, while a clone becomes a separate VM from the point that the cloned image was made.

**Images**

An [[image]] backup is made by duplicating an OS installation. This can be done either from a physical hard disk or from a VM's virtual hard disk. Imaging allows the system to be redeployed quickly, without having to reinstall third-party software, patches, and configuration settings. A system image should generally not contain any user data files, as these will quickly become out of date.
# BACKUP STORAGE ISSUES 

Backed up and archived data need to be stored as securely as live data. A data backup has the same confidentiality and integrity requirements as its source. It also has its own availability requirement. Typically, backup media is physically secured against theft or snooping by keeping it in a restricted part of the building, with other server and network equipment. Many backup solutions use encryption to ensure data confidentiality should the media be stolen.

### Offsite Storage

Additionally, you must plan for events that could compromise both the live data and the backup set. Natural disasters, such as fires, earthquakes, and floods, could leave an organization without a data backup, unless they have kept a copy offsite. Distance consideration is a calculation of how far offsite the backup needs to be kept, given different disaster scenarios. On the one hand, the media must be kept far away enough not to be damaged by the disaster; on the other, media access should not slow down a recovery operation too much.

Without a network that can support the required bandwidth, the offsite media must be physically brought onsite (and if there is no second set of offsite media, data is at substantial risk at this time), the latest backup performed, and then removed to offsite storage again. Quite apart from the difficulty and expense of doing this, there are data confidentiality and security issues in transporting the data. In recent years, high-bandwidth Internet and high-capacity cloud storage providers have made offsite backup solutions much more affordable and easy to implement.

### Online versus Offline Backups

As well as the onsite/offsite consideration, you should also be aware of a distinction between online and offline backups. An online backup system is instantly available to perform a backup or restore operation without an administrator having to transport and connect a device or load some backup media. An offline backup is disconnected from the host and must be connected manually.

An online system is faster, but an offline backup offers better security. ==Consider the case of cryptoransomware, for instance. If the backup system is connected to the infected host, the ransomware will encrypt the backup, rendering it useless.== Some cryptoransomware is configured to try to access cloud accounts and encrypt the cloud storage ([f-secure.com/v-descs/articles/crypto-ransomware.shtml](https://www.f-secure.com/v-descs/articles/crypto-ransomware.shtml)).

**The 3-2-1 rule states that you should have three copies of your data, across two media types, with one copy held offline and offsite**.
# BACKUP MEDIA TYPES

A backup operation can use several media types. Each type has advantages and disadvantages that make it more or less suitable for given scenarios.

### Disk

Individual removable hard drives are an excellent low-cost option for small office/home office ([[SOHO]]) network backups, but they do not have sufficient capacity or flexibility to be used within an automated enterprise backup solution.

### Network Attached Storage (NAS)

A network attached storage ([[NAS]]) [[appliance]] is a specially configured type of server that makes RAID storage available over common network protocols, such as Windows File Sharing ([[SMB]]) or [[FTP]]. A NAS appliance is accessed via an IP address and backup takes place at file-level. A NAS can be another good option for SOHO backup, but as a single device, it provides no offsite option. As it is normally kept online, it can be vulnerable to cryptoransomware as well.

### Tape

**Digital tape systems are a popular choice for institutions with multi-terabyte storage requirements.** Tape is very cost effective and, given a media rotation system, tapes can be transported offsite. The latest generation of tape will store about 10-12 terabytes per cartridge or up to about 30 TB with compression. The main drawback of tape is that it is slow, compared to disk-based solutions, especially for restore operations.

### Storage Area Network (SAN) and Cloud

A RAID array or tape drive/autoloader can be provisioned as direct attached storage, where a server hosts the backup devices, usually over serial attached [[SCSI]] ([[SAS]]). Direct attached storage has limited scalability, so enterprise and cloud storage solutions often use storage area networks (SAN) as a layer of abstraction between the file system objects presented to servers and the configuration of the actual storage media. Where NAS uses file-level access to storage, a SAN is based on block-level addressing. A SAN can incorporate RAID arrays and tape systems within the same network. SANs can achieve offsite storage through replication.
# RESTORATION ORDER

If a site suffers an uncontrolled outage, in ideal circumstances processing will be switched to an alternate site and the outage can be resolved without any service interruption. If an alternate processing site is not available, then the main site must be brought back online as quickly as possible to minimize service disruption. This does not mean that the process can be rushed, however. A complex facility such as a data center or campus network must be reconstituted according to a carefully designed order of [[restoration]]. If systems are brought back online in an uncontrolled way, there is the serious risk of causing additional power problems or of causing problems in the network, OS, or application layers because dependencies between different appliances and servers have not been met.

In very general terms, the order of restoration will be as follows:

1.  Enable and test power delivery systems (grid power, power distribution units [PDUs], UPS, secondary generators, and so on).
2.  Enable and test switch infrastructure, then routing appliances and systems.
3.  Enable and test network security appliances (firewalls, IDS, proxies).
4.  Enable and test critical network servers (DHCP, DNS, NTP, and directory services).
5.  Enable and test back-end and middleware (databases and business logic). Verify data integrity.
6.  Enable and test front-end applications.
7.  Enable client workstations and devices and client browser access.
# NONPERSISTENCE

When recovering systems, it may be necessary to ensure that any artifacts from the disaster, such as malware or backdoors, are removed when reconstituting the production environment. This can be facilitated in an environment designed for nonpersistence. [[Nonpersistence]] describes a computing environment (e.g., virtual machine instance) that is static in terms of processing function. Storing data elsewhere allows the instance to be destroyed and rebuilt with the same functionality without suffering configuration problems. There are various mechanisms for ensuring nonpersistence:

-   Snapshot/revert to known state—this is a saved system state that can be reapplied to the instance.
-   Rollback to known configuration—a physical instance might not support snapshots but has an "internal" mechanism for restoring the baseline system configuration, such as Windows System Restore.
-   Live boot media—another option is to use an instance that boots from read-only storage to memory rather than being installed on a local read/write hard disk.

When provisioning a new or replacement instance automatically, the automation system may use one of two types of mastering instructions:

-   Master image—this is the "gold" copy of a server instance, with the OS, applications, and patches all installed and configured. This is faster than using a template, but keeping the image up to date can involve more work than updating a template.
-   Automated build from a template—similar to a master image, this is the build instructions for an instance. Rather than storing a master image, the software may build and provision an instance according to the template instructions.

Another important process in automating resiliency strategies is to provide configuration validation. This process ensures that a recovery solution is working at each layer (hardware, network connectivity, data replication, and application). An automation solution for incident and disaster recovery will have a dashboard of key indicators and may be able to evaluate metrics such as compliance with recovery point objective (RPO) and recovery time objective (RTO) from observed data.
