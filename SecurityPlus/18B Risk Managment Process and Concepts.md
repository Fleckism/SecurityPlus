---
tags: [firstTag, secondTag]
---
# EXAM OBJECTIVES COVERED

4.1 Given a scenario, use the appropriate tool to assess organizational security

4.5 Explain the key aspects of digital forensics

There are many processes and tools for acquiring different kinds of digital evidence from computer hosts and networks. These processes must demonstrate exactly how the evidence was acquired and that it is a true copy of the system state at the time of the event. While you may not be responsible for leading evidence acquisition, you should be familiar with the processes and tools used, so that you can provide assistance as required.
# DATA ACQUISITION AND ORDER OF VOLATILITY

Acquisition is the process of obtaining a forensically clean copy of data from a device held as evidence. If the computer system or device is not owned by the organization, there is the question of whether search or seizure is legally valid. This impacts bring-your-own-device (BYOD) policies. For example, if an employee is accused of fraud you must verify that the employee's equipment and data can be legally seized and searched. Any mistake may make evidence gained from the search inadmissible.

Data acquisition is also complicated by the fact that it is **more difficult to capture evidence from a digital crime scene** than it is from a physical one. **Some evidence will be lost if the computer system is powered off; on the other hand, some evidence may be unobtainable until the system is powered off. Additionally, evidence may be lost depending on whether the system is shut down or "frozen" by suddenly disconnecting the power.**

Data acquisition usually proceeds by using a tool to make an image from the data held on the target device. An [[image]] can be acquired from either **volatile or nonvolatile storage**. The general principle is to capture evidence in the order of volatility, from more volatile to less volatile. The [[ISOC]] best practice guide to evidence collection and archiving, published as [tools.ietf.org/html/rfc3227](https://tools.ietf.org/html/rfc3227), sets out the general order as follows:

1.  CPU registers and cache memory (including cache on disk controllers, GPUs, and so on).
2.  Contents of nonpersistent system memory (RAM), including routing table, ARP cache, process table, kernel statistics.
3.  Data on persistent mass storage devices (HDDs, SSDs, and flash memory devices):

-   Partition and file system blocks, slack space, and free space.
-   System memory caches, such as swap space/virtual memory and hibernation files.
-   Temporary file caches, such as the browser cache.
-   User, application, and OS files and directories.

4.  Remote logging and monitoring data.
5.  Physical configuration and network topology.
6.  Archival media and printed documents.

The Windows registry is mostly stored on disk, but there are keys—notably HKLM\Hardware—that only ever exist in memory. The contents of the registry can be analyzed via a memory dump.
# DIGITAL FORENSICS SOFTWARE

Digital forensics software is designed to assist with the acquisition, documentation, and analysis of digital evidence. Most of the commercial forensics [[tools]] are available for the **Windows platform only**.

-   EnCase Forensic is a digital forensics case management product created by Guidance Software ([guidancesoftware.com/encase-forensic?cmpid=nav_r](https://www.guidancesoftware.com/encase-forensic?cmpid=nav_r)). Case management is assisted by built-in pathways, or workflow templates, showing the key steps in diverse types of investigation. In addition to the core forensics suite, there are separate products for e-discovery (digital evidence management) and Endpoint Investigator (for over-the-network analysis of corporate desktops and servers).
-   The Forensic Toolkit (FTK) from AccessData ([accessdata.com/products-services/forensic-toolkit-ftk](https://accessdata.com/products-services/forensic-toolkit-ftk)) is another commercial investigation suite designed to run on Windows Server (or server cluster).
-   The Sleuth Kit ([sleuthkit.org](https://sleuthkit.org/)) is an open-source collection of command line tools and programming libraries for disk imaging and file analysis. Autopsy is a graphical front-end for these tools and acts as a case management/workflow tool. The program can be extended with plug-ins for various analysis functions. Autopsy is available for Windows and can be compiled from the source code to run on Linux.
-   WinHex from X-Ways ([x-ways.net/winhex](https://www.x-ways.net/winhex/)) is a commercial tool for forensic recovery and analysis of binary data, with support for a range of file systems and memory dump types (depending on version).
-   The Volatility Framework ([github.com/volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)) is widely used for system memory analysis.
# SYSTEM MEMORY ACQUISITION

[[System memory]] is volatile data held in Random Access Memory ([[RAM]]) modules. [[Volatile]] means that the data is lost when power is removed. A system memory dump creates an image file that can be analyzed to identify the processes that are running, the contents of temporary file systems, registry data, network connections, cryptographic keys, and more. It can also be a means of accessing data that is encrypted when stored on a mass storage device. There are various methods of collecting the contents of system memory.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/217-1599771811747.png)

Viewing the process list in a memory dump using the Volatility Framework. (Screenshot Volatility Framework [volatilityfoundation.org](https://www.volatilityfoundation.org/).)

### Live Acquisition

A specialist hardware or software tool can **capture the contents of memory while the host is running**. Unfortunately, this type of tool needs to be preinstalled as it requires a kernel mode driver to dump any data of interest. Some examples for Windows include WinHex ([x-ways.net/winhex](https://www.x-ways.net/winhex/)), Memoryze from FireEye ([fireeye.com/services/freeware/memoryze.html](https://www.fireeye.com/services/freeware/memoryze.html)), and F-Response TACTICAL ([f-response.com/software/tac](https://www.f-response.com/software/tac)).

On Linux, a user mode tool, such as memdump ([porcupine.org/forensics/tct.html](http://www.porcupine.org/forensics/tct.html)) or dd, can be run against the /dev/mem device file. However, on most modern distributions, access to this file is blocked. The Volatility Framework ([github.com/volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)) includes a tool to install a kernel driver (pmem). The fmem and LiME kernel utilities provide similar functionality.

### Crash Dump

When Windows encounters an **unrecoverable kernel error**, it can write contents of memory to a dump file at C:\Windows\MEMORY.DMP. On modern systems, there is unlikely to be a complete dump of all the contents of memory, as these could take up a lot of disk space. However, even mini dump files, stored in C:\Windows\Minidumps, may be a valuable source of information.

### Hibernation File and Pagefile

A **hibernation file** is created on disk in the root folder of the boot volume when a **Windows host is put into a sleep state**. If it can be recovered, the data can be decompressed and loaded into a software tool for analysis. The drawback is that network connections will have been closed, and **malware may have detected the use of a sleep state and performed anti-forensics**.

The pagefile/swap file/swap partition stores pages of memory in use that exceed the capacity of the host's RAM modules. The pagefile is not structured in a way that analysis tools can interpret, but it is possible to search for strings.
# DISK IMAGE ACQUISITION

Disk image acquisition refers to acquiring data from nonvolatile storage. Nonvolatile storage includes hard disk drives (HDDs), solid state drives (SSDs), firmware, other types of flash memory (USB thumb drives and memory cards), and optical media (CD, DVD, and Blu-Ray). This can also be referred to as device acquisition, meaning the SSD storage in a smartphone or media player. Disk acquisition will also capture the OS installation, if the boot volume is included.

There are three device states for persistent storage acquisition:

-   Live acquisition—this means copying the data while the host is still running. This may capture more evidence or more data for analysis and reduce the impact on overall services, but the data on the actual disks will have changed, so this method may not produce legally acceptable evidence. It may also alert the adversary and allow time for them to perform anti-forensics.
-   Static acquisition by shutting down the host—this runs the risk that the malware will detect the shutdown process and perform anti-forensics to try to remove traces of itself.
-   Static acquisition by pulling the plug—this means disconnecting the power at the wall socket (not the hardware power-off button). This is most likely to preserve the storage devices in a forensically clean state, but there is the risk of corrupting data.

Given sufficient time at the scene, you may decide to perform both a live and static acquisition. Whichever method is used, it is imperative to document the steps taken and supply a timeline for your actions.

There are many GUI imaging utilities, including those packaged with suites such as the Forensic Toolkit and its FTK Imager. You should note that the EnCase forensics suite uses a vendor file format (.e01) compared to the raw file format used by Linux tools like dd. The file format is important when it comes to selecting a tool for analyzing the image. The .eo1 format allows image metadata (such as the checksum, drive geometry, and acquisition time) to be stored within the same file. The open-source Advanced Forensic Format (AFF) provides similar features.

If no specialist tool is available, on a Linux host you can use the dd command to make a copy of an input file (if=) to an output file (of=) and apply optional conversions to the file data. In the following sda is the fixed drive:

dd if=/dev/sda of=/mnt/usbstick/backup.img

A more recent fork of dd is dcfldd, which provides additional features like multiple output files and exact match verification.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3914-1599771811833.png)

Using dcfldd (a version of dd with additional forensics functionality created by the DoD) and generating a hash of the source-disk data (sda).
# PRESERVATION AND INTEGRITY OF EVIDENCE

It is vital that the evidence collected at the crime scene conform to a valid timeline. Digital information is susceptible to tampering, so access to the evidence must be tightly controlled. Recording the whole process establishes the provenance of the evidence as deriving directly from the crime scene.

To obtain a forensically sound image from nonvolatile storage, you need to ensure that nothing you do alters data or metadata (properties) on the source disk or file system. A write blocker assures this process by preventing any data on the disk or volume from being changed by filtering write commands at the driver and OS level. Data acquisition would normally proceed by attaching the target device to a forensics workstation or field capture device equipped with a write blocker.

### Data Acquisition with Integrity and Non-Repudiation

Once the target disk has been safely attached to the forensics workstation, data acquisition proceeds as follows:

1.  A cryptographic hash of the disk media is made, using either the MD5 or SHA hashing function. The output of the function can be described as a checksum.
2.  A bit-by-bit copy of the media is made using the imaging utility.
3.  A second hash is then made of the image, which should match the original hash of the media.
4.  A copy is made of the reference image, validated again by the checksum. Analysis is performed on the copy.

This proof of integrity ensures non-repudiation. If the provenance of the evidence is certain, the threat actor identified by analysis of the evidence cannot deny their actions. The checksums prove that no modification has been made to the image.

In practical terms, the image acquisition software will perform the verification steps as part of the acquisition process, but in theory you could use separate tools to perform each stage individually.

### Preservation of Evidence

The host devices and media taken from the crime scene should be labeled, bagged, and sealed, using tamper-evident bags. It is also appropriate to ensure that the bags have antistatic shielding to reduce the possibility that data will be damaged or corrupted on the electronic media by electrostatic discharge (ESD). Each piece of evidence should be documented by a chain of custody form which records where, when, and who collected the evidence, who subsequently handled it, and where it was stored. 

The evidence should be stored in a secure facility; this not only means access control, but also environmental control, so that the electronic systems are not damaged by condensation, ESD, fire, and other hazards. Similarly, if the evidence is transported, the transport must also be secure.
# ACQUISITION OF OTHER DATA

There are other potential sources of forensic data within computer systems and networks, though they can be hard to acquire or to prove as admissible.

### Network

Packet captures and traffic flows can contain very valuable evidence, if the capture was running at the right time and in the right place to record the incident. As with memory forensics, the issue for forensics lies in establishing the integrity of the data. Most network data will come from a SIEM.

### Cache

Cache can refer either to hardware components or software. Software-based cache is stored in the file system and can be acquired as part of a disk image. For example, each browser has a cache of temporary files, and each user profile has a cache of temp files. Some cache artifacts generated by the OS and applications are held in memory only, such as portions of the registry, cryptographic keys, password hashes, some types of cookies, and so on. The contents of hardware cache (CPU registers and disk controller read/write cache, for instance) is not generally recoverable.

### Artifacts and Data Recovery

Artifacts refers to any type of data that is not part of the mainstream data structures of an operating system. For example, the Windows Alternate Data Streams (ADS) feature is often used to conceal file data, and various caches, such as prefetch and Amcache, can be used to find indicators of suspicious process behavior.

Data recovery refers to analyzing a disk (or image of a disk) for file fragments stored in slack space. These fragments might represent deleted or overwritten files. The process of recovering them is referred to as carving. 

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/6862-1599771811926.png)

Using Autopsy for file carving a disk image. The selected Courses folder and the PDF files in it were deleted and so are flagged as unallocated. Because this image was captured soon after deletion, the file contents are easily recoverable, however. (Screenshot Autopsy—the Sleuth Kit [sleuthkit.org/autopsy](http://www.sleuthkit.org/autopsy/).)

### Snapshot

A snapshot is a live acquisition image of a persistent disk. While this may have less validity than an image taken from a device using a write blocker, it may be the only means of acquiring data from a virtual machine or cloud process.

### Firmware

Firmware is usually implemented as flash memory. Some types, such as the PC firmware, can potentially be extracted from the device or from system memory using an imaging utility. It likely will be necessary to use specialist hardware to attach the device to a forensic workstation, however.
# DIGITAL FORENSICS FOR CLOUD

With an on-premises investigation, the right to seize and analyze devices is usually fairly unproblematic. There may be availability issues with taking a system out of service, and bring-your-own-device policies can be more complex, but essentially as all the equipment is the company's property, there are no third-party obstacles.

While companies can operate private clouds, forensics in a public cloud are complicated by the right to audit permitted to you by your service level agreement (SLA) with the cloud provider. Two more issues with forensics investigations of cloud-hosted processing and data services are as follows:

-   The on-demand nature of cloud services means that instances are often created and destroyed again, with no real opportunity for forensic recovery of any data. Cloud providers can mitigate this to some extent with extensive logging and monitoring options. A CSP might also provide an option to generate file system and memory snapshots from containers and VMs in response to an alert condition generated by a SIEM.
-   Chain of custody issues are complex and might have to rely on the CSP to select and package data for you. The process should be documented and recorded as closely as is possible.
-   Jurisdiction and data sovereignty may restrict what evidence the CSP is willing to release to you.
-   If the CSP is a data processor, it will be bound by data breach notification laws and regulations. Coordinating the timing of notification and contact with the regulator between your organization and the CSP can be extremely complex, especially if there is an ongoing incident requiring confidentiality.
