# Lesson 20

#Implementation  Cybersecurity Resilience

## 

LESSON INTRODUCTION

Cybersecurity resilience means that even successful intrusions by [[threat actor]]s have limited impact on [[confidentiality]], [[integrity]], and [[Availability]]. **Provisioning redundancy in storage, power, and network systems, plus effective backup procedures**, site resiliency, and effective procedures for change control and configuration management are crucial in maintaining high [[Availability]]. 

## 

LESSON OBJECTIVES

In this lesson, you will:

-   Implement redundancy strategies.
-   Implement backup strategies.
-   Implement cybersecurity resiliency strategies.
# EXAM OBJECTIVES COVERED

2.5 Given a scenario, implement cybersecurity resilience

The output of [[risk assessment]]s and business impact analysis will identify vulnerable business processes. To reduce risks in these processes, you can make the IT systems and other business systems that support them resilient to failure. You must be able to install and configure the systems that provide redundancy for power supply, networking, and storage systems.
# HIGH [[Availability]]

One of the key properties of a [[resilient]] system is high [[Availability]]. [[Availability]] is the percentage of time that the system is online, measured over the defined period, typically one year. The corollary of [[Availability]] is downtime, or the amount of time for which the system is unavailable. The maximum tolerable downtime (MTD) metric expresses the [[Availability]] requirement for a particular business function. High [[Availability]] is usually loosely described as 24x7 (24 hours per day, 7 days per week) or 24x365 (24 hours per day, 365 days per year). For a critical system, [[Availability]] will be described as "two-nines" (99%) up to five- or six-nines (99.9999%):

[[Availability]]

Annual Downtime (hh:mm:ss)

99.9999%

00:00:32

99.999%

00:05:15

99.99%

00:52:34

99.9%

08:45:36

99%

87:36:00

Downtime is calculated from the sum of scheduled service intervals plus unplanned outages over the period.

System [[Availability]] can refer to an overall process, but also to [[Availability]] at the level of a server or individual component.

### Scalability and Elasticity

High [[Availability]] also means that a system is able to cope with rapid growth in demand. Two properties of high [[Availability]] that have to do with this are referred to as scalability and elasticity. Scalability is the capacity to increase resources to meet demand within similar cost ratios. This means that if service demand doubles, costs do not more than double. There are two types of [[scalability]]:

-   To scale **out** is to add more resources in parallel with existing resources.
-   To scale **up** is to increase the power of existing resources.

**Elasticity** refers to the system's ability to handle these changes on demand **in real time**. A system with high elasticity will not experience loss of service or performance if demand suddenly increases rapidly.

### Fault Tolerance and Redundancy 

A system that can **experience failures** and continue to provide the same (or nearly the same) level of service is said to be fault tolerant. Fault tolerance is often achieved by provisioning redundancy for critical components and single points of failure. **A redundant component is one that is not essential** to the normal function of a system but that allows the system to recover from the failure of another component.
# POWER REDUNDANCY

All types of computer systems require a stable power supply to operate. **Electrical events, such as voltage spikes or surges**, can crash computers and network appliances, while loss of power from brownouts or blackouts will cause equipment to fail. Power management means deploying systems to ensure that equipment is protected against these events and that network operations can either continue uninterrupted or be recovered quickly. 

### Dual Power Supplies 

An enterprise-class server or appliance enclosure is likely to feature two or more power supply units (PSUs) for redundancy. A hot plug [[PSU]] can be replaced (in the event of failure) without powering down the system. 

### Managed Power Distribution Units (PDUs)

The power circuits supplying grid power to a **rack, network closet, or server room** must be enough to meet the load capacity of all the installed equipment, plus room for growth. Consequently, circuits to a server room will typically be higher capacity than domestic or office circuits (**30 or 60** amps as opposed to 13 amps, for instance). These circuits may be run through a power distribution unit (PDU). These come with circuitry to "clean" the power signal, provide protection against spikes, surges, and brownouts, and can integrate with uninterruptible power supplies (UPSs). Managed PDUs support remote power monitoring functions, such as reporting load and status, switching power to a [[socket]] on and off, or switching sockets on in a particular sequence. 

### Battery Backups and Uninterruptible Power Supplies (UPSs)

If there is loss of power, system operation can be sustained for a few minutes or hours (depending on load) using battery backup. Battery backup can be provisioned at the component level for disk drives and [[RAID arrays]]. The battery protects any read or write operations cached at the time of power loss. At the system level, an uninterruptible power supply (UPS) will provide a temporary power source in the event of a blackout (complete power loss). This may range from a few minutes for a desktop-rated model to hours for an enterprise system. In its simplest form, a UPS comprises a bank of batteries and their charging circuit plus an inverter to generate AC voltage from the DC voltage supplied by the batteries.

The time allowed by a UPS should be sufficient to failover to an alternative power source, such as a standby generator. If there is no secondary power source, UPS will at least allow the administrator to shut down the server or appliance properly—users can save files, and the OS can complete the proper shut down routines.

### Generators

A backup power generator can provide power to the whole building, often for several days. Most generators use diesel, propane, or natural gas as a fuel source. With diesel and propane, the main drawback is safe storage (diesel also has a shelf-life of between 18 months and two years); with natural gas, the issue is the reliability of the gas supply in the event of a natural disaster. Data centers are also investing in renewable power sources, such as solar, wind, geothermal, hydrogen fuel cells, and hydro. The ability to use renewable power is a strong factor in determining the best site for new data centers. Large-scale battery solutions, such as Tesla's Powerpack ([tesla.com/powerpack](https://www.tesla.com/powerpack)), may be able to provide an alternative to backup power generators. There are also emerging technologies to use all the battery resources of a data center as a microgrid for power storage ([scientificamerican.com/article/how-big-batteries-at-data-centers-could-replace-power-plants](https://www.scientificamerican.com/article/how-big-batteries-at-data-centers-could-replace-power-plants)).

A UPS is always required to protect against any interruption to computer services. A backup generator cannot be brought online fast enough to respond to a power failure.
# NETWORK REDUNDANCY

Networking is another [[critical resource]] where a single point of failure could cause significant service disruption. 

### Network Interface Card (NIC) Teaming

Network interface card ([[NIC]]) teaming, or adapter teaming, means that the server is installed with multiple NICs, or NICs with multiple ports, or both. Each port is connected to separate network cabling. During normal operation, this can provide a high-bandwidth link. For example, four 1 Gb ports gives an overall bandwidth of 4 Gb. If there is a problem with one cable, or one NIC, the network connection will continue to work, though at just 3 Gb.

For the system to be fault tolerant, the higher bandwidth must not be critical to the function.

### Switching and Routing

Network cabling should be designed to allow for multiple paths between the various switches and routers, so that during a failure of one part of the network, the rest remains operational.

Multiple switching paths **require** use of Spanning Tree Protocol ([[STP]]) to prevent loops.

### Load Balancers

NIC teaming provides load balancing at the [[adapter level]]. Load balancing and clustering can also be provisioned at a [[service level]]:

-   A load balancing switch distributes workloads between available servers.
-   A load balancing cluster enables multiple redundant servers to share data and session information to maintain a consistent service if there is failover from one server to another.
# DISK REDUNDANCY

Disk and storage resources are critically dependent on redundancy. While **backup provides integrity for when a disk fails**, to restore from backup would require installing a new storage unit, restoring the data, and testing the system configuration. **Disk redundancy ensures that a server can continue to operate** ==(Is this faster that using the backup?)==
if one, or possibly more, storage devices fail.

### Redundant Array of Independent Disks (RAID)

When a storage system is configured as a Redundant Array of Independent Disks ([[RAID]]), many disks can act as backups for each other to increase reliability and fault tolerance. If one disk fails, the data is not lost, and the server can keep functioning. The RAID advisory board defines **RAID levels, numbered from 0 to 6**, where each level corresponds to a specific type of fault tolerance. There are also proprietary and nested RAID solutions. Some of the most commonly implemented types of RAID are listed in the following table.

[[RAID Level]]

Fault Tolerance

Level 1

Mirroring means that data is written to two disks simultaneously, providing redundancy (if one disk fails, there is a copy of data on the other). The main drawback is that storage efficiency is only 50%.

Level 5

Striping with parity means that data is written across three or more disks, but additional information ([[parity]]) is calculated. This allows the volume to continue if one disk is lost. This solution has better storage efficiency than RAID 1.

Level 6

Double parity, or level 5 with an additional parity stripe, allows the volume to continue when two devices have been lost.

Nested (0+1, 1+0, or 5+0)

Nesting RAID sets generally improves performance or redundancy. For example, some nested RAID solutions can support the failure of more than one disk.

RAID level 0 refers to striping without parity. Data is written in blocks across several disks simultaneously, but with no redundancy. This can improve performance, but if one disk fails, so does the whole volume, and data on it will be corrupted. There are some use cases for RAID 0, but typically striping without parity is only implemented to improve performance in a nested RAID solution.

### Multipath

Where RAID provides redundancy for the storage devices, multipath is focused on the [[bus]] between the server and the storage devices or RAID array. A storage system is accessed via some type of [[controller]]. The controller might be connected to disk units locally installed in a server, or it might connect to storage devices within a storage area network ([[SAN]]). Multipath input/output (I/O) ensures that there is controller redundancy and/or multiple network paths to the storage devices.
# GEOGRAPHICAL REDUNDANCY AND REPLICATION

Data replication is technology that maintains exact copies of data at more than one location. RAID mirroring and parity implements types of replication between local storage devices. Data replication can be applied in many other contexts:

-   Storage Area Network ([[SAN]])—most enterprise storage is configured as a SAN. A SAN is a high-speed fiber optic network of storage devices built from technologies such as Fibre Channel, Small Computer System Interface (SCSI), or Infiniband. Redundancy can be provided within the SAN, and replication can also take place between SANs using WAN links.
-   [[Database]]—much data is stored within a database. Where a database is replicated between multiple servers or sites, it is very important to maintain consistency between the replicas. Database management systems come with specific tools to implement different kinds of replication.
-   Virtual Machine ([[VM]])—the same VM instance may need to be deployed in multiple locations. This can be achieved by replicating the VM's disk image and configuration settings. 

### Geographical Dispersal

[[Geographical dispersal]] refers to data replicating hot and warm sites that are physically distant from one another. This means that data is protected against a natural disaster wiping out storage at one of the sites. This is also [[described as a geo-redundant]] solution.

### Asynchronous and Synchronous Replication

[[Synchronous replication]] is designed to write data to all replicas simultaneously. Therefore, all replicas should always have the same data all of the time. [[Asynchronous replication]] writes data to the primary storage first, and then copies data to the replicas at scheduled intervals.

Asynchronous replication isn't a good choice for a solution that requires data in multiple locations to be consistent, such as data from product inventory lists accessed in different regions. Many geo-redundant replication services rely on asynchronous replication due to the distances between data centers in multiple regions. In some cases, business solutions work around the limitations of asynchronous replication. For example, an online retailer may choose only to show inventory from their local regional warehouse.

### On-Premises versus Cloud

High [[Availability]] through redundancy and replication is resource-intensive, especially when configuring multiple [[hot or warm sites does this actually mean temperature?]]. For on-premises sites, provisioning the storage devices and [[high-bandwidth, low-latency WAN]] links required between two geographically dispersed hot sites could incur unaffordable costs. This cost is one of the big drivers of cloud services, where local and geographic redundancy are built into the system, if you trust the CSP to operate the cloud effectively. For example, in the cloud, geo-redundancy replicates data or services between data centers physically located in two different regions. Disasters that occur at the regional level, like earthquakes, hurricanes, or floods, should not impact [[Availability]] across multiple zones.
