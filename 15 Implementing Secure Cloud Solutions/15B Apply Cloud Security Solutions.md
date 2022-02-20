---
tags: [firstTag, secondTag]
---
# EXAM OBJECTIVES COVERED

1.2 Given a scenario, analyze potential indicators to determine the type of attack (Cloud-based versus on-premises only)

2.2 Summarize virtualization and cloud computing concepts

3.6 Given a scenario, apply cybersecurity solutions to the cloud

Configuring cloud security solutions shares many principles and processes with on-premises security, but plenty of unfamiliar technologies and challenges too. Weak configuration of cloud services can make many attack vectors available, and the public nature of clouds means that they will quickly be discovered and exploited. You must be able to apply policies and technical controls to provision, compute, network, and storage cloud resources with the attributes of confidentiality, integrity, and availability.
# CLOUD SECURITY INTEGRATION AND AUDITING

Cloud-based services must be integrated within regular security policies and procedures and audited for compliance. Where indicators of on-premises attacks are found in local application logs and network traffic, indicators of cloud-based attacks are found in API logs and metrics. The same correlation to suspicious IP address ranges and domains and suspicious code strings must be made, but the source of this data is the cloud service provider (CSP). Accessing this auditing information in real time may be difficult, depending on the cloud service type. There are many cloud-based SIEM solutions that can perform this collection, aggregation, and correlation of security data from both on-premises and cloud-based networks and instances.

As with any contracted service, cloud computing is a means of transferring risk. As such, it is imperative to identify precisely which risks you are transferring, to identify which responsibilities the service provider is undertaking, and to identify which responsibilities remain with you. This should be set out in a service level agreement (SLA) with a responsibility matrix. For example, in an SaaS solution, the provider may be responsible for the confidentiality, integrity, and availability of the software. They would be responsible for configuring a fault tolerant, clustered server service; for firewalling the servers and creating proper authentication, authorization, and accounting procedures; for scanning for intrusions and monitoring network logs, applying OS and software patches; and so on. You might or might not be responsible for some or all of the software management functions, though—ensuring that administrators and users practice good password management, configuring system privileges, making backups of data, and so on.

Where critical tasks are the responsibility of the service provider, you should try to ensure that there is a reporting mechanism to show that these tasks are being completed, that their disaster recovery plans are effective, and so on.

Another proviso is that your company is likely to still be directly liable for serious security breaches; if customer data is stolen, for instance, or if your hosted website is hacked and used to distribute malware. You still have liability for legal and regulatory requirements. You might be able to sue the service provider for damages, but your company would still be the point of investigation. You may also need to consider the legal implications of using a cloud provider if its servers are located in a different country.

You must also consider the risk of insider threat, where the insiders are administrators working for the service provider. Without effective security mechanisms such as separation of duties and quorum authentication (also known as M of N access control), it is highly likely that they would be able to gain privileged access to your data. Consequently, the service provider must be able to demonstrate to your satisfaction that they are prevented from doing so. There is also the risk described earlier that your data is in proximity to other, unknown virtual servers and that some sort of attack could be launched on your data from another virtual server.

The Twitter hack affecting high-profile accounts being hijacked for a bitcoin scam is a good illustration of the risks from insider threat ([https://www.wired.com/story/inside-twitter-hack-election-plan/](https://www.wired.com/story/inside-twitter-hack-election-plan/)).

As with any contracted service, with any *aaS solution, you place a large amount of trust in the service provider. The more important the service is to your business, the more risk you are investing in that trust relationship.
# CLOUD SECURITY CONTROLS

Clouds use the same types of security controls as on-premises networks, including identity and access management (IAM), endpoint protection (for virtual instances), resource policies to govern access to data and services, firewalls to filter traffic between hosts, and logging to provide an audit function.

Most CSP's will provide these security controls as native functionality of the cloud platform. Google's firewall service is an example of this type of cloud-native control ([cloud.google.com/firewalls](https://cloud.google.com/firewalls)). The controls can be deployed and configured using either the CSP's web console, or programmatically via a command line interface (CLI) or application programming interface (API). A third-party solution would typically be installed as a virtual instance within the cloud. For example, you might prefer to run a third-party next-generation firewall. This can be configured as an appliance and deployed to the cloud. The virtual network architecture can be defined so that this appliance instance is able to inspect traffic and apply policies to it, either by routing the traffic through the instance or by using some type of bridging or mirroring. As an example, consider the configuration guide for the Barracuda next-gen firewall ([campus.barracuda.com/product/cloudgenfirewall/doc/79462645/overview](https://campus.barracuda.com/product/cloudgenfirewall/doc/79462645/overview)).

The same considerations can be made for other types of security controls—notably data loss prevention and compliance management. Cloud-native controls might not exist for these use cases, they might not meet the functional requirements that third-party solutions can, and there may be too steep a transition in terms of change management and skills development.

### Application Security and IAM

Application security in the cloud refers both to the software development process and to identity and access management (IAM) features designed to ensure authorized use of applications.

Just as with on-premises solutions, cloud-based IAM enables the creation of user and user security groups, plus role-based management of privileges.

### Secrets Management

A cloud service is highly vulnerable to remote access. A failure of credential management is likely to be exploited by malicious actors. You must enforce strong authentication policies to mitigate risks:

-   Do not use the root user for the CSP account for any day-to-day logon activity.
-   Require strong multifactor authentication (MFA) for interactive logons. Use conditional authentication to deny or warn of risky account activity.
-   Principals—user accounts, security groups, roles, and services—can interact with cloud services via CLIs and APIs. Such programmatic access is enabled by assigning a secret key to the account. Only the secret key (not the ordinary account credential) can be used for programmatic access. When a secret key is generated for an account, it must immediately be transferred to the host and kept securely on that host.
# CLOUD COMPUTE SECURITY

Cloud provides resources abstracted from physical hardware via one or more layers of virtualization. The compute component provides process and system memory (RAM) resource as required for a particular workload. The workload could be a virtual machine instance configured with four CPUs and 16 GB RAM or it could be a container instance spun up to perform a function and return a result within a given timeframe. The virtualization layer ensures that the resources required for this task are made available on-demand. This can be referred to as dynamic resource allocation. It will be the responsibility of the CSP to ensure this capability is met to the standards agreed in the SLA.

Within the compute component, the following critical security considerations can be identified.

### Container Security

A container uses many shared components on the underlying platform, meaning it must be carefully configured to reduce the risk of data exposure. In a container engine such as Docker, each container is isolated from others through separate namespaces and control groups ([docs.docker.com/engine/security/security](https://docs.docker.com/engine/security/security/)). Namespaces prevent one container reading or writing processes in another, while control groups ensure that one container cannot overwhelm others in a DoS-type attack.

### API Inspection and Integration

The API is the means by which consumers interact with the cloud infrastructure, platform, or application. The consumer may use direct API calls, or may use a CSP-supplied web console as a graphical interface for the API. Monitoring API usage gives warning if the system is becoming overloaded (ensuring availability) and allows detection of unauthorized usage or attempted usage.

-   Number of requests—this basic load metric counts number of requests per second or requests per minute. Depending on the service type, you might be able to establish baselines for typical usage and set thresholds for alerting abnormal usage. An unexplained spike in API calls could be an indicator of a DDoS attack, for instance.
-   Latency—this is the time in milliseconds (ms) taken for the service to respond to an API call. This can be measured for specific services or as an aggregate value across all services. High latency usually means that compute resources are insufficient. The cause of this could be genuine load or DDoS, however.
-   Error rates—this measures the number of errors as a percentage of total calls, usually classifying error types under category headings. Errors may represent an overloaded system if the API is unresponsive, or a security issue, if the errors are authorization/access denied types.
-   Unauthorized and suspicious endpoints—connections to the API can be managed in the same sort of way as remote access. The client endpoint initiating the connection can be restricted using an ACL and the endpoint's IP address monitored for geographic location.

### Instance Awareness

As with on-premises virtualization, it is important to manage instances (virtual machines and containers) to avoid sprawl, where undocumented instances are launched and left unmanaged. As well as restricting rights to launch instances, you should configure logging and monitoring to track usage.
# CLOUD STORAGE SECURITY

Where the compute component refers to CPU and system memory resources, the storage component means the provisioning of persistent storage capacity. As with the compute component, the cloud virtualization layer abstracts the underlying hardware to provide the required storage type, such as a virtual hard disk for a VM instance, object-based storage to serve static files in a web application, or block storage for use by a database server. Storage profiles will have different performance characteristics for different applications, such as fast SSD-backed storage for databases versus slower HDD-backed media for archiving. The principal performance metric is the number of input/output operations per second (IOPS) supported.

### Permissions and Resource Policies

As with on-premises systems, cloud storage resources must be configured to allow reads and/or writes only from authorized endpoints. In the cloud, a resource policy acts as the ACL for an object. In a resource policy, permissions statements are typically written as a JavaScript Object Notation (JSON) strings. Misconfiguration of these resource policies is a widely exploited attack vector. For example, the following policy uses the "any" wildcard (*) to assign both actions (read and write) and principals (accounts) to a storage object. This type of policy breaks the principle of least privilege and is highly unsecure:

"Statement": [ {

 "Action": [

 "*"

 ],

 "Effect": "Allow",

 "Principal": "*",

 "Resource": "arn:aws:s3:::515support-courses-data/*"

} ]

### Encryption

Cloud storage encryption equates to the on-premises concept of full disk encryption (FDE). The purpose is to minimize the risk of data loss via an insider or intruder attack on the CSP's storage systems. Each storage unit is encrypted using an AES key. If an attacker were to physically access a data center and copy or remove a disk, the data on the disk would not be readable.

To read or write the data, the AES key must be available to the VM or container using the storage object. With CSP-managed keys, the cloud provider handles this process by using the access control rights configured on the storage resource to determine whether access is approved and, if so, making the key available to the VM or container. The key will be stored in a hardware security module (HSM) within the cloud. The HSM and separation of duties policies protect the keys from insider threat. Alternatively, customers can manage keys themselves, taking on all responsibility for secure distribution and storage.

Encryption can also be applied at other levels. For example, applications can selectively encrypt file system objects or use database-level encryption to encrypt fields and/or records. All networking—whether customer to cloud or between VMs/containers within the cloud—should use encrypted protocols such as HTTPS or IPSec.
# HIGH AVAILABILITY

One of the benefits of the cloud is the potential for providing services that are resilient to failures at different levels, such as component, server, local network, site, data center, and wide area network. The CSP uses a virtualization layer to ensure that compute, storage, and network provision meet the availability criteria set out in its SLA. In terms of storage performance tiers, high availability (HA) refers to storage provisioned with a guarantee of 99.99% uptime or better. As with on-premises architecture, the CSP uses redundancy to make multiple disk controllers and storage devices available to a pool of storage resource. Data may be replicated between pools or groups, with each pool supported by separate hardware resources.

### Replication

Data replication allows businesses to copy data to where it can be utilized most effectively. The cloud may be used as a central storage area, making data available among all business units. Data replication requires low-latency network connections, security, and data integrity. CSPs offer several data storage performance tiers ([cloud.google.com/storage/docs/storage-classes](https://cloud.google.com/storage/docs/storage-classes)). The terms hot and cold storage refer to how quickly data is retrieved. Hot storage retrieves data more quickly than cold, but the quicker the data retrieval, the higher the cost. Different applications have diverse replication requirements. A database generally needs low-latency, synchronous replication, as a transaction often cannot be considered complete until it has been made on all replicas. A mechanism to replicate data files to backup storage might not have such high requirements, depending on the criticality of the data.

### High Availability across Zones

CSPs divide the world into regions. Each region is independent of the others. The regions are divided into availability zones. The availability zones have independent data centers with their own power, cooling, and network connectivity. You can choose to host data, services, and VM instances in a particular region to provide a lower latency service to customers. Provisioning resources in multiple zones and regions can also improve performance and increases redundancy, but requires an adequate level of replication performance.

Consequently, CSPs offer several tiers of replication representing different high availability service levels:

-   Local replication—replicates your data within a single data center in the region where you created your storage account. The replicas are often in separate fault domains and upgrade domains.
-   Regional replication (also called zone-redundant storage)—replicates your data across multiple data centers within one or two regions. This safeguards data and access in the event a single data center is destroyed or goes offline.
-   Geo-redundant storage (GRS)—replicates your data to a secondary region that is distant from the primary region. This safeguards data in the event of a regional outage or a disaster.
# CLOUD NETWORKING SECURITY

Within the cloud, the CSP establishes a virtualization layer that abstracts the underlying physical network. This allows the CSP to operate a public cloud where the networking performed by each customer account is isolated from the others. In terms of customer-configured cloud networking, there are various contexts:

-   Networks by which the cloud consumer operates and manages the cloud systems.
-   Virtual networks established between VMs and containers within the cloud.
-   Virtual networks by which cloud services are published to guests or customers on the Internet.

### Virtual Private Clouds (VPCs)

Each customer can create one or more virtual private clouds (VPCs) attached to their account. By default, a VPC is isolated from other CSP accounts and from other VPCs operating in the same account. This means that customer A cannot view traffic passing over customer B's VPC. The workload for each VPC is isolated from other VPCs. Within the VPC, the cloud consumer can assign an IPv4 CIDR block and configure one or more subnets within that block. Optionally, an IPv6 CIDR block can be assigned also. 

The following notes focus on features of networking in AWS. Other vendors support similar functionality, though sometimes with different terminology. For example, in Microsoft Azure, VPCs are referred to as virtual networks.

### Public and Private Subnets

Each subnet within a VPC can either be private or public. To configure a public subnet, first an Internet gateway (virtual router) must be attached to the VPC configuration. Secondly, the Internet gateway must be configured as the default route for each public subnet. If a default route is not configured, the subnet remains private, even if an Internet gateway is attached to the VPC. Each instance in the subnet must also be configured with a public IP in its cloud profile. The Internet gateway performs 1:1 network address translation (NAT) to route Internet communications to and from the instance. 

The instance network adapter is not configured with this public IP address. The instance's NIC is configured with an IP address for the subnet. The public address is used by the virtualization management layer only. Public IP addresses can be assigned from your own pool or from a CSP-managed service, such as Amazon's Elastic IP ([docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html)).

There are other ways to provision external connectivity for a subnet if it is not appropriate to make it public:

-   NAT gateway—this feature allows an instance to connect out to the Internet or to other AWS services, but does not allow connections initiated from the Internet.
-   VPN—there are various options for establishing connections to and between VPCs using virtual private networks (VPNs) at the software layer or using CSP-managed features.
# VPCS AND TRANSIT GATEWAYS

Routing can be configured between subnets within a VPC. This traffic can be subject to cloud native ACLs allowing or blocking traffic on the basis of host IPs and ports. Alternatively, traffic could be routed through a virtual firewall instance, or other security appliance.

Connectivity can also be configured between VPCs in the same account or with VPCs belonging to different accounts, and between VPCs and on-premises networks. Configuring additional VPCs rather than subnets within a VPC allows for a greater degree of segmentation between instances. A complex network might split segments between different VPCs across different cloud accounts for performance or compliance reasons.

Traditionally, VPCs can be interconnected using peering relationships and connected with on-premises networks using VPN gateways. These one-to-one VPC peering relationships can quickly become difficult to manage, especially if each VPC must interconnect in a mesh-like structure. A transit gateway is a simpler means of managing these interconnections. Essentially, a transit gateway is a virtual router that handles routing between the subnets in each attached VPC and any attached VPN gateways ([aws.amazon.com/transit-gateway](https://aws.amazon.com/transit-gateway/)).

Amazon's white paper sets out options for configuring multi-VPC infrastructure in more detail ([d1.awsstatic.com/whitepapers/building-a-scalable-and-secure-multi-vpc-aws-network-infrastructure.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/building-a-scalable-and-secure-multi-vpc-aws-network-infrastructure.pdf)).
# VPC ENDPOINTS

A VPC endpoint is a means of publishing a service so that it is accessible by instances in other VPCs using only the AWS internal network and private IP addresses ([d1.awsstatic.com/whitepapers/aws-privatelink.pdf](http://d1.awsstatic.com/whitepapers/aws-privatelink.pdf#)). This means that the traffic is never exposed to the Internet. There are two types of VPC endpoint: gateway and interface.

Gateway Endpoints

A gateway endpoint is used to connect instances in a VPC to the AWS S3 (storage) and DynamoDB (database) services. A gateway endpoint is configured as a route to the service in the VPC's route table.

Interface Endpoints

An interface endpoint makes use of AWS's PrivateLink feature to allow private access to custom services:

-   A custom service provider VPC is configured by publishing the service with a DNS host name. Alternatively, the service provider might be an Amazon default service that is enabled as a VPC interface endpoint, such as CloudWatch Events/Logs.
-   A VPC endpoint interface is configured in each service consumer VPC subnet. The VPC endpoint interface is configured with a private IP address within the subnet plus the DNS host name of the service provider.
-   Each instance within the VPC subnet is configured to use the endpoint address to contact the service provider.
# CLOUD FIREWALL SECURITY

As in an on-premises network, a firewall determines whether to accept or deny/discard incoming and outgoing traffic. Firewalls work with multiple accounts, VPCs, subnets within VPCs, and instances within subnets to enforce the segmentation required by the architectural design. Segmentation may be needed for many different reasons, including separating workloads for performance and load balancing, keeping data processing within an isolated segment for compliance with laws and regulations, and compartmentalizing data access and processing for different departments or functional requirements.

Filtering decisions can be made based on packet headers and payload contents at various layers, identified in terms of the OSI model:

-   Network layer (layer 3)—the firewall accepts or denies connections on the basis of IP addresses or address ranges and TCP/UDP port numbers (the latter are actually contained in layer 4 headers, but this functionality is still always described as basic layer 3 packet filtering).
-   Transport layer (layer 4)—the firewall can store connection states and use rules to allow established or related traffic. Because the firewall must maintain a state table of existing connections, this requires more processing power (CPU and memory).
-   Application layer (layer 7)—the firewall can parse application protocol headers and payloads (such as HTTP packets) and make filtering decisions based on their contents. This requires even greater processing capacity (or load balancing), or the firewall will become a bottleneck and increase network latency.

While you can use cloud-based firewalls to implement on-premises network security, here we are primarily concerned with the use of firewalls to filter traffic within and to and from the cloud itself. Such firewalls can be implemented in several ways to suit different purposes:

-   As software running on an instance. This sort of host-based firewall is identical to ones that you would configure for an on-premises host. It could be a stateful packet filtering firewall or a web application firewall (WAF) with a ruleset tuned to preventing malicious attacks. The drawback is that the software consumes instance resources and so is not very efficient. Also, managing the rulesets across many instances can be challenging.
-   As a service at the virtualization layer to filter traffic between VPC subnets and instances. This equates to the concept of an on-premises network firewall.

Native cloud application-aware firewalls incur transaction costs, typically calculated on time deployed and traffic volume. These costs might be a reason to choose a third-party solution instead of the native control.
# SECURITY GROUPS

In AWS, basic packet filtering rules managing traffic that each instance will accept can be managed through security groups ([docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)). A security group provides stateful inbound and outbound filtering at layer 4. The stateful filtering property means that it will allow established and related traffic if a new connection has been accepted.

The default security group allows any outbound traffic and any inbound traffic from instances also bound to the default security group. A custom security group sets the ports and endpoints that are allowed for inbound and outbound traffic. There are no deny rules for security groups; any traffic that does not match an allow rule is dropped. Consequently, a custom group with no rules will drop all network traffic. Multiple instances can be assigned to the same security group, and instances within the same subnet can be assigned to different security groups. You can assign multiple security groups to the same instance. You can also assign security groups to VPC endpoint interfaces.

![AWS console showing step 6 in "Launch an instance" wizard, with "Select an existing security group" selected and details of the security group rules allowing SSH on TCP port 22 from a single IP (blurred out) and HTTPS on TCP port 443 from 0.0.0.0/0.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3907-1599771810652.png)

Adding a custom security group when launching a new instance in AWS EC2. This policy allows SSH access from a single IP address (redacted) and access to HTTPS from any IP address. (Screenshot courtesy of Amazon.com)

Most cloud providers support similar filtering functionality, though they may be implemented differently. For example, in Azure, network security groups can be applied to network interfaces or to subnets ([docs.microsoft.com/en-us/azure/virtual-network/security-overview](https://docs.microsoft.com/en-us/azure/virtual-network/security-overview)).
# CLOUD ACCESS SECURITY BROKERS

A cloud access security broker (CASB) is enterprise management software designed to mediate access to cloud services by users across all types of devices. CASB vendors include Blue Coat, now owned by Symantec ([broadcom.com/products/cyber-security/information-protection/cloud-application-security-cloudsoc](https://www.broadcom.com/products/cyber-security/information-protection/cloud-application-security-cloudsoc)), SkyHigh Networks, now owned by McAfee ([skyhighnetworks.com](https://www.skyhighnetworks.com/)), Forcepoint ([forcepoint.com/product/casb-cloud-access-security-broker](https://www.forcepoint.com/product/casb-cloud-access-security-broker)), Microsoft Cloud App Security ([microsoft.com/en-us/microsoft-365/enterprise-mobility-security/cloud-app-security](https://www.microsoft.com/en-us/microsoft-365/enterprise-mobility-security/cloud-app-security)), and Cisco Cloudlock ([cisco.com/c/en/us/products/security/cloudlock/index.html](https://www.cisco.com/c/en/us/products/security/cloudlock/index.html)).

CASBs provide you with visibility into how clients and other network nodes are using cloud services. Some of the functions of a CASB are:

-   Enable single sign-on authentication and enforce access controls and authorizations from the enterprise network to the cloud provider.
-   Scan for malware and rogue or non-compliant device access.
-   Monitor and audit user and resource activity.
-   Mitigate data exfiltration by preventing access to unauthorized cloud services from managed devices.

In general, CASBs are implemented in one of three ways:

-   Forward proxy—this is a security appliance or host positioned at the client network edge that forwards user traffic to the cloud network if the contents of that traffic comply with policy. This requires configuration of users' devices or installation of an agent. In this mode, the proxy can inspect all traffic in real time, even if that traffic is not bound for sanctioned cloud applications. The problem with this mode is that users may be able to evade the proxy and connect directly. Proxies are also associated with poor performance as without a load balancing solution, they become a bottleneck and potentially a single point of failure.
-   Reverse proxy—this is positioned at the cloud network edge and directs traffic to cloud services if the contents of that traffic comply with policy. This does not require configuration of the users' devices. This approach is only possible if the cloud application has proxy support.
-   Application programming interface (API)—rather than placing a CASB appliance or host inline with cloud consumers and the cloud services, an API-based CASB brokers connections between the cloud service and the cloud consumer. For example, if a user account has been disabled or an authorization has been revoked on the local network, the CASB would communicate this to the cloud service and use its API to disable access there too. This depends on the API supporting the range of functions that the CASB and access and authorization policies demand. CASB solutions are quite likely to use both proxy and API modes for different security management purposes.

### Next-Generation Secure Web Gateway

Enterprise networks often make use of secure web gateways (SWG). An on-premises SWG is a proxy-based firewall, content filter, and intrusion detection/prevention system that mediates user access to Internet sites and services. A next-generation SWG, as marketed by Netskope ([netskope.com/products/next-gen-swg](https://www.netskope.com/products/next-gen-swg)), combines the functionality of an SWG with that of data loss prevention (DLP) and a CASB to provide a wholly cloud-hosted platform for client access to websites and cloud apps. This supports an architecture defined by Gartner as secure access service edge (SASE) ([https://www.paloaltonetworks.com/cyberpedia/what-is-sase](https://www.paloaltonetworks.com/cyberpedia/what-is-sase)).
