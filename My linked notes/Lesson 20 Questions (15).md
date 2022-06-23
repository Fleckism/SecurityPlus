# 1
A hurricane has affected a company in Florida. What is the first step in the order of restoration?

2.  Enable and test power delivery systems

Solution

The first step in the order of restoration is to enable and test power delivery systems such as grid power, Power Distribution Units (PDUs), and secondary generators.

The second step in the order of restoration is to enable and test switch infrastructure, followed by routing appliances and systems.

The third step in the order of restoration is to enable and test network security appliances, such as firewalls and proxies.

The fourth step in the order of restoration is to enable and test critical network servers, such as directory services. The back-end and middleware will be next, followed by the front-end. The final step is to enable client workstations and devices.
# 2
Management has reason to believe that someone internal to the organization is committing fraud. To confirm their suspicion, and to collect evidence, they need to set up a system to capture the events taking place. Evaluate which option will best fit the organization's needs.


2.  Honeypot

Solution

A system that is placed on the network with the intent of attracting attackers or to detect internal fraud, snooping and malpractice is called a honeypot. This system will be placed within the current network.

An entire decoy network is called a honeynet. A honeynet can be an actual network or simulated.

An exploitation framework is a means of running intrusive scanning and uses the vulnerabilities identified by a scanner and launches scripts or software to attempt to exploit selected vulnerabilities.

Metasploit is the best-known exploit framework.
# 3
A Redundant Array of Independent Disks (RAID) is installed with data written to two disks with 50% storage efficiency. Which RAID level has been utilized?

2.  Level 1

Solution

Redundant Array of Independent Disks (RAID) Level 1 uses mirroring where data is written to two disks simultaneously, which provides redundancy. The main drawback is its storage efficiency is only 50%.

RAID Level 0 is striping without parity resulting in no fault tolerance. Data is written in blocks across several disks.

RAID Level 5 has striping with parity. Data is written across three or more disks, but additional information is calculated. This allows the volume to continue if one disk is lost. This solution has better storage efficiency than RAID 1.

RAID Level 6 has double parity or Level 5 with an additional parity stripe. This allows the volume to continue when two disks have been lost.
# 4
An organization configures both a warm site and a hot site for disaster preparedness. Doing so poses which difficulties for the organization? **(Select all that apply.)**

3.  Complexity
4.  Budgetary

Solution

Creating a duplicate of anything doubles the complexity of securing that resource properly. Having multiple sites increases the complexity of the infrastructure.

Providing redundancy on a scale that includes multiple locations can be very expensive. Businesses often lease sites from service providers to reduce costs.

Enterprise-level networks often provision resiliency at the site level. An alternate processing or recovery site is a location that can provide the same (or similar) level of service.

Technology diversity refers to environments that are a mix of operating systems, applications, coding languages, virtualization solutions, etc. The diversity level should not change according to the number of sites as they are simply mirrored.
# 5

 A systems engineer decides that security mechanisms should differ for various systems in the organization. In some cases, systems will have multiple mechanisms from multiple sources. Which types of diversity does the engineer practice? **(Select all that apply.)**

1.  Control
2.  Vendor

Solution

Control diversity means that the layers of controls should combine different classes of technical and administrative controls with the range of control functions.

Vendor diversity means that security controls are sourced from multiple sources. A vulnerability in solutions from a single vendor approach is a security weakness.

Change refers to control processes or management. Control involves careful planning, with consideration for how the change will affect dependent components.

Enterprise-level networks often provision resiliency at the site level. An alternate processing or recovery site is a location that can provide the same (or similar) level of service. Resiliency itself does not provide diversity.
# 6
A company is working to restore operations after a blizzard stopped all operations. Evaluate the order of restoration and determine the correct order of restoring devices from first to last.

1.  Routers, firewalls, Domain Name System (DNS), client workstations

Solution

The order of restoration states that switch infrastructure, then routing appliances, followed by firewalls, and then Domain Name System (DNS) should be enabled in that order. The final step is to enable client workstations and devices.

The DNS should not be enabled prior to routers and firewalls. Both routers and firewalls are needed prior to DNS being operable.

Routers should be restored prior to firewalls. Routers should be restored immediately following switch infrastructure as firewalls are not needed until routers are online.

Client workstations should be restored last as firewalls and DNS must be restored prior to bringing the client workstations back online.
# 7
A systems engineer reviews recent backups for a production server. While doing so, the engineer discovers that archive bits on files are clearing and incorrect backup types have been occurring. Which backup type did the engineer intend to use if the bit should not be cleared?

3.  Differential

Solution

With a differential backup, all new and modified files since the last full backup are part of the backup set. With a differential backup type, the archive bit on a file is set to not cleared.

A full backup includes all selected data regardless of when the previous backup occurred. With a full backup type, the archive bit on a file is set to cleared.

Snapshots are a means of getting around the problem of open files when performing a backup. Snapshots use a copy of the data rather than the live data.

With an incremental type backup, new files, as well as files modified since the last backup are part of the backup set. With an incremental backup type, the archive bit on a file is set to cleared.
# 8
Security specialists create a sinkhole to disrupt any adversarial attack attempts on a private network. Which solution do the specialists configure?

1.  Routing traffic to a different network

Solution

A popular disruption strategy is to configure a DNS sinkhole to route suspect traffic to a different network, such as a honeynet, where it can be analyzed.

Port triggering or spoofing can disrupt adversarial attacks by returning fake telemetry data when a host detects port scanning activity.

To create disruption for an adversary, a security specialist can configure a web server with multiple decoy directories or dynamically generated pages to slow down scanning.

Fake telemetry can disrupt an adversary by reporting IP addresses as up and available when they actually are not.
# 9
A systems engineer configures a disk volume with a Redundant Array of Independent Disks (RAID) solution. Which solution does the engineer utilize when allowing for the failure of two disks?

4.  Level 6

Solution

Redundant Array of Independent Disks (RAID) Level 6 has double parity or Level 5 with an additional parity stripe. This allows the volume to continue when two disks have been lost.

Level 1 uses mirroring where data is written to two disks simultaneously, which provides redundancy. The main drawback is its storage efficiency is only 50%.

RAID Level 0 is striping without parity resulting in no fault tolerance. Data is written in blocks across several disks.

RAID Level 5 has striping with parity. Data is written across three or more disks but calculates additional information. This allows the volume to continue if one disk is lost. This solution has better storage efficiency than RAID 1.
# 10

A recent systems crash prompts an IT administrator to perform recovery steps. Which mechanism does the administrator use to achieve nonpersistence?

4.  Revert to known state

Solution

Snapshot/revert to known state is a saved system state that the administrator can reapply to the instance on a system. This is a mechanism that achieves nonpersistence.

Configuration validation is a process that ensures that a recovery solution is working at each layer (hardware, network connectivity, data replication, and application).

Data replication is a process of reinstating data on a system. Nonpersistence would occur by separating any system restore from data replication.

Automation may restore a system as software may build and provision an instance according to any template instructions. This is a mastering instruction.
# 11

An organization stores data in different geographic locations for redundancy. This data replicates so that it is the same in all locations. Engineers discover that some replicas are lagging with updates. What configuration do the engineers discover as the cause?

1.  Asynchronous replication

Solution

Asynchronous replication is not a good choice for a solution that requires data in multiple locations to be consistent. Asynchronous replication writes data to the primary storage first and then copies the data to the replicas at scheduled intervals. The engineers need to look into the schedules.

Synchronous replication writes data to all replicas simultaneously.

On-premises location refers to systems that are physically located at an organization's facility.

Cloud location refers to systems that are physically or virtually located at a cloud service provider rather than at an organization's facility.
# 12

IT staff looks to provide a high level of fault tolerance while implementing a new server. With which systems configuration approach does the staff achieve this goal?

3.  Focusing on critical components
Solution

A system often achieves fault tolerance by provisioning redundancy for critical components and single points of failure. Although not required, a redundant component is available for system recovery.

Elasticity refers to the system's ability to handle any changes in resource demand in real-time. Elasticity often applies to processing power and storage.

A system achieves scalability by adding resources. To scale out is to add more resources in parallel with existing resources.

A system achieves scalability by adding resources. To scale up is to increase the power of existing resources.
# 13
A system has a slight misconfiguration which could be exploited. A manufacturing workflow relies on this system. The admin recommends a trial of the proposed settings under which process?

1.  Change management

Solution

Change management involves careful planning, with consideration for how the change will affect dependent components. For most significant or major changes, organizations should attempt to trial the change first.

The admin performs a change control process prior to the actual change. This process requests and approves changes in a planned and controlled way.

An asset management process tracks all the organization's critical systems, components, devices, and other objects of value in an inventory.

Configuration management ensures that each component of ICT infrastructure is in a trusted state that has not diverged from its documented properties.
# 14
Analyze automation strategies to differentiate between elasticity and scalability. Which scenarios demonstrate scalability? **(Select all that apply.)**

1.  A company is hired to provide data processing for 10 additional clients and has a linear increase in costs for the support.

3.  A company has a 10% increase in clients and a 5% increase in costs.

Solution

Scalability is defined as the costs involved in supplying the service to more users is linear. For example, if the number of users doubles in a scalable system, the costs to maintain the same level of service would also double (or less than double). If costs more than double, the system is less scalable. A company that is hired to provide data processing for ten additional clients and has a linear increase in costs for the support is a scalable system.

A company that has a 10% increase in clients and a 5% increase in costs is highly scalable due to the cost increase being less than the client increase.

Elasticity refers to a system's ability to handle changes in demand in real time. A company that is hired to provide data processing for 10 additional clients and can utilize the same servers to complete the task is displaying elasticity.

A company that has a 10% increase in clients and a 10% decrease in server performance is demonstrating linear elasticity.
# 15
A natural disaster has resulted in a company moving to an alternate processing site. The company has operations moved almost immediately as a result of having a building with all of the equipment and data needed to resume services. The alternative site was actively running prior to the natural disaster. Evaluate the types of recovery sites to determine which processing site the company is utilizing.

4.  Hot site

Solution

The company is utilizing a hot site for recovery. A hot site can failover almost immediately. The site is already within the organization's ownership and is ready to deploy.

A cold site takes longer to set up (up to a week) and does not have the equipment or data needed to set up immediately.

A warm site contains features of both hot and cold sites. An example of a warm site is a building with the computer equipment available, but the company must supply the latest data set to be operational.

Replication is the process of duplicating data between different servers or sites.
