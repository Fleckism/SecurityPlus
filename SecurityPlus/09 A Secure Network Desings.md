---
tags: [A_D, Implementation,section]
---
# ## 

LESSON INTRODUCTION

Managing user authentication and authorization is only one part of building secure information technology services. The network infrastructure must also be designed to run services with the properties of confidentiality, integrity, and [[Availability]]. While design might not be a direct responsibility for you at this stage in your career, you should understand the factors that underpin design decisions, and be able to **implement a design by deploying routers, switches, access points, and load balancers in secure configurations.**

## 

LESSON OBJECTIVES

In this lesson, you will:

-   Implement secure network designs #A_D.
-   Implement secure routing and switching.
-   Implement secure wireless infrastructure.
-   Implement load balancers.
# EXAM OBJECTIVES COVERED

3.3 Given a scenario, implement secure network designs #A_D

While you may not be responsible for network design in your current role, it is important that you understand the [[vulnerability|vulnerabilities]] that can arise from weaknesses in network architecture #A_D, and some of the general principles for ensuring a well-designed network. This will help you to contribute to projects to improve resiliency and to make recommendations for improvements.


# SECURE NETWORK designs #A_D

A secure network design provisions the assets and services underpinning business workflows with the properties of confidentiality, integrity, and [[Availability]]. Weaknesses in the network architecture #A_D make it more susceptible to undetected intrusions or to catastrophic service failures. Typical weaknesses include:

-   **Single points of failure**—a "pinch point" relying on a single hardware server or appliance or network channel.
-   **Complex dependencies**—services that require many different systems to be available. Ideally, the failure of individual systems or services should not affect the overall performance of other network services.
-   **[[Availability]] over confidentiality and integrity**—often it is tempting to take "shortcuts" to get a service up and running. Compromising security might represent a quick fix but creates long term risks.
-   **Lack of documentation and change control**—network segments, appliances, and services might be added without proper change control procedures, leading to a lack of visibility into how the network is constituted. It is vital that network managers understand business workflows and the network services that underpin them.
-   **Overdependence on perimeter security**—if the network architecture #A_D is **"flat"** (that is, if any host can contact any other host), penetrating the network edge gives the attacker freedom of movement.

Cisco's SAFE architecture #A_D ([cisco.com/c/en/us/solutions/enterprise/design-zone-security/landing_safe.html#~overview](https://www.cisco.com/c/en/us/solutions/enterprise/design-zone-security/landing_safe.html#~overview)) is a good starting point for understanding the complex topic of network architecture #A_D design. The SAFE guidance refers to places in the network (PIN). These represent types of network locations, including campus networks, branch offices, data centers, and the cloud. There are two special locations in these networks—Internet Edge and WAN—that facilitate connections between locations and with untrusted networks.

**Each PIN can be protected with security controls and capabilities, classified into a series of secure domains, such as threat defense, segmentation, security intelligence, and management.** 
# BUSINESS WORKFLOWS AND NETWORK architecture #A_D

Network architecture #A_D is designed to support business workflows. You can illustrate the sorts of decisions that need to be made by **analyzing a simple workflow**, such as email:

-   **Access**—the client device must access the network, obtaining a physical channel and logical address. The user must be authenticated and authorized to use the email application. The corollary is that unauthorized users and devices must be denied access.
-   **Email mailbox server**—ensure that the mailbox is only accessed by authorized clients and that it is fully available and fault tolerant. Ensure that the email service runs with a minimum number of dependencies and that the service is designed to be resilient to faults.
-   **Mail transfer server**—this must connect with untrusted Internet hosts, so communications between the untrusted network and trusted LAN must be carefully controlled. Any data or software leaving or entering the network must be subject to policy-based controls.

You can see that this type of business flow will involve systems in different places in the network. Placing the client, the mailbox, and the mail transfer server all within the same logical network "segment" will introduce many [[vulnerability|vulnerabilities]]. Understanding and controlling how data flows between these locations is a key part of secure and effective network design.
# NETWORK APPLIANCES

A number of network appliances are involved in provisioning a network architecture #A_D:

-   [[Switches]]—forward frames between nodes in a cabled network. Switches work at layer 2 and 3 of the OSI model_._ At layer 2 they make forwarding decisions based on the hardware or [[MAC address |Media Access Control (MAC)]] address of attached nodes. Switches can establish network segments that either map directly to the underlying cabling or logical segments, created in the switch configuration as  virtual LANs ([[VLANs]]).

When designing and troubleshooting a network, it is helpful to compartmentalize functions to discrete layers. The Open Systems Interconnection ([[OSI]]) model is a widely quoted example of how to define layers of network functions.

-   [[WAP |Wireless access points]]—provide a bridge between a cabled network and wireless clients, or stations. Access points work at layer 2 of the OSI model.
-   [[Routers]]—forward packets around an internetwork, making forwarding decisions based on IP addresses. Routers work at layer 3 of the OSI model. Routers can apply logical IP subnet addresses to segments within a network.
-   [[firewall]]—apply an access control list ([[ACL]]) to filter traffic passing in or out of a network segment. Firewalls can work at layer 3 of the OSI model or higher.
-   [[Load balancers]]—distribute traffic between network segments or servers to optimize performance. Load balancers can work at layer 4 of the OSI model or higher.
-   Domain Name System ([[DNS]]) servers—host name records and perform name resolution to allow applications and users to address hosts and services using fully qualified domain names ([[FQDN |FQDNs]]) rather than IP addresses. DNS works at layer 7 of the OSI model. Name resolution is a critical service in network design. Abuse of name resolution is a common [[attack vector]].

Appliances, protocols, and addressing functions within the OSI network layer reference model. (Images © 123RF.com.)
# ROUTING AND SWITCHING PROTOCOLS

The basic function of a network is to forward traffic from one node to another. A number of routing and switching protocols are used to implement forwarding. The forwarding function takes place at two different layers:

-   Layer 2 forwarding occurs between nodes on the same local network segment that are all in the same broadcast domain. At layer 2, a broadcast domain is either all the nodes connected to the same physical unmanaged switch, or all the nodes within a virtual LAN (VLAN) configured on one or more managed switches. At layer 2, each node is identified by the network interface's hardware or [[MAC address |Media Access Control  address]]. A MAC address is a 48-bit value written in hexadecimal notation, such as 00-15-5D-F4-83-48.
-   Layer 3 forwarding, or routing, occurs between both logically and physically defined networks. A single network divided into multiple logical broadcast domains is said to be subnetted. Multiple networks joined by routers form an internetwork. At layer 3, nodes are identified by an Internet Protocol (IP) address.

### Address Resolution Protocol (ARP)

The Address Resolution Protocol ([[ARP]]) maps a network interface's hardware (MAC) address to an IP address. Normally a device that needs to send a packet to an IP address but does not know the receiving device's MAC address broadcasts an ARP Request packet, and the device with the matching IP responds with an ARP Reply.

![A Host with IP 10.0.0.22 sends a message “Who has 10.0.0.11? Tell 10.0.0.22” that 10.0.0.33 ignores but 10.0.0.11 replies directly to 10.0.0.22.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1904-1599771801862.png)

ARP in action—An ARP broadcast is used when there is no MAC:IP mapping in the cache and is received by all hosts on the same network, but only the host with the requested IP should reply. (Images © 123RF.com.)

### Internet Protocol (IP)

[[IP]] provides the addressing mechanism for logical networks and subnets. A 32-bit IPv4 address is written in dotted decimal notation, with either a network suffix or subnet mask to divide the address into network ID and host ID portions. For example, in the IP address 172.16.1.101/16, the /16 suffix indicates that the first half of the address (172.16.0.0) is the network ID, while the remainder uniquely identifies a host on that network. This /16 suffix can also be written as a subnet mask in the form 255.255.0.0.

Networks also use 128-bit IPv6 addressing. IPv6 addresses are written using hex notation in the general format: 2001:db8::abc:0:def0:1234. In IPv6, the last 64-bits are fixed as the host's interface ID. The first 64-bits contain network information in a set hierarchy. For example, an ISP's routers can use the first 48-bits to determine where the network is hosted on the global Internet. Within that network, the site administrator can use the 16 bits remaining (out of 64) to divide the local network into subnets.

### Routing Protocols

Information about how to reach individual networks within an internetwork is processed by routers, which store the data in a **routing table**. A route to a network can be configured statically, but most networks use routing protocols to transmit new and updated routes between routers. Some common routing protocols include Border Gateway Protocol (BGP), Open Shortest Path First (OSPF), Enhanced Interior Gateway Routing Protocol (EIGRP), and Routing Information Protocol (RIP).
[[NETWORK SEGMENTATION]] 

A network segment is one where all the hosts attached to the segment can use local (layer 2) forwarding to communicate freely with one another. The hosts are said to be within the same broadcast domain. Segregation means that the hosts in one segment are restricted in the way they communicate with hosts in other segments. They might only be able to communicate over certain network ports, for instance.

 "Freely" means that no network appliances or policies are preventing communications. Each host may be configured with access rules or host firewalls or other security tools to prevent access, but the "view from the network" is that hosts in the same segment are all free to attempt to communicate.

Assuming an Ethernet network, network segments can be established physically by connecting all the hosts in one segment to one switch and all the hosts in another segment to another switch. The two switches can be connected by a router and the router can enforce network policies or access control lists ([[ACL]]) to restrict communications between the two segments.

Because enterprise networks typically feature hundreds of switching appliances and network ports (not to mention wireless access and remote access), segmentation is more likely to be enforced using virtual LANs ([[VLANs]]). Any given switch port can be assigned to any VLAN in the same topology, regardless of the physical location of the switch. The segmentation enforced by VLANs at layer 2 can be mapped to logical divisions enforced by IP subnets at layer 3.
# NETWORK TOPOLOGY AND ZONES 

Given the ability to create segregated segments with the network, you can begin to define a topology of different network zones. **A topology is a description of how a computer network is physically or logically organized.** The logical and physical network topology should be analyzed to identify points of vulnerability and to ensure that the goals of confidentiality, integrity, and [[Availability]] are met by the design.

The main building block of a security [[Topology discovery|Topology]] is the zone. A zone is an area of the network where the security configuration is the same for all hosts within it. Zones should be segregated from one another by physical and/or logical segmentation, using VLANs and subnets. Traffic between zones should be strictly controlled using a security device, typically a firewall.
 
Dividing a campus network or data center into zones implies that each zone has a different security configuration. The main zones are as follows:

-   Intranet (private network)—this is a network of trusted hosts owned and controlled by the organization. Within the intranet, there may be sub-zones for different host groups, such as servers, employee workstations, VoIP handsets, and management workstations.

Hosts are trusted in the sense that they are under your administrative control and subject to the security mechanisms (antivirus software, user rights, software updating, and so on) that you have set up to defend the network.

-   [[Extranet]]—this is a network of semi-trusted hosts, typically representing business partners, suppliers, or customers. Hosts must authenticate to join the extranet.
-   Internet/guest—this is a zone permitting anonymous access (or perhaps a mix of anonymous and authenticated access) by untrusted hosts over the Internet.

A large network may need more zones to represent different host groups, such as separating wireless stations from desktop workstations, and putting servers in their own groups. Cisco's enterprise security architecture #A_D uses core and distribution layers to interconnect access blocks, with each access block representing a different zone and business function.

![A center box labeled “Core/Distribution” is connected to 9 different VLAN boxes, as well as to 3 more boxes that are also connected to an ISP router.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2693-1599771801963.png)

Enterprise security architecture #A_D. (Images © 123RF.com.)
# DEMILITARIZED ZONES

The most important distinction between different security zones is whether a host is Internet-facing. An Internet-facing host accepts inbound connections from and makes connections to hosts on the Internet. Internet-facing hosts are placed in one or more demilitarized zones (DMZs). A [[DMZ]] is also referred to as a perimeter or edge network. The basic principle of a DMZ is that traffic cannot pass directly through it. A DMZ enables external clients to access data on private systems, such as web servers, without compromising the security of the internal network as a whole. If communication is required between hosts on either side of a DMZ, a host within the DMZ acts as a proxy. For example, if an intranet host requests a connection with a web server on the Internet, a proxy in the DMZ takes the request and checks it. If the request is valid, it retransmits it to the destination. External hosts have no idea about what (if anything) is behind the DMZ.

Both extranet and Internet services are likely to be Internet-facing. The hosts that provide the extranet or public access services should be placed in one or more demilitarized zones. These would typically include web servers, mail and other communications servers, proxy servers, and remote access servers. The hosts in a DMZ are not fully trusted by the internal network because of the possibility that they could be compromised from the Internet. They are referred to as bastion hosts and run minimal services to reduce the attack surface as much as possible. A bastion host would not be configured with any data that could be a security risk to the internal network, such as user account credentials.

It is quite likely that more than one DMZ will be required as the services that run in them may have different security requirements :

-   A DMZ hosting proxies or secure web gateways to allow employees access to web browsing and other Internet services.
-   A DMZ hosting communication servers, such as email, VoIP, and conferencing.
-   A DMZ for servers providing remote access to the local network via a Virtual Private Network (VPN).
-   A DMZ hosting traffic for authorized cloud applications.
-   A multi-tier DMZ to isolate front-end, middleware, and back-end servers.
# DEMILITARIZED ZONE TOPOLOGIES

To configure a DMZ, two different security configurations must be enabled: one on the external interface and one on the internal interface. **A DMZ and intranet are on different subnets, so communications between them need to be routed.**

### Screened Subnet

A screened [[subnet]] uses two firewalls placed on either side of the DMZ. The edge firewall restricts traffic on the external/public interface and allows permitted traffic to the hosts in the [[DMZ]]. The edge firewall can be referred to as the screening firewall or router. The internal firewall filters communications between hosts in the DMZ and hosts on the LAN. This firewall is often described as the choke firewall. A choke point is a purposefully narrow gateway that facilitates better access control and easier monitoring.

![A VLAN100 (Dept LAN) box is connected to a Core/Distribution box that is connected to an Extranet box that is connected to an ISP router icon.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9450-1599771802030.png)

A screened subnet DMZ topology. (Images © 123RF.com.)

### Triple-Homed Firewall

A DMZ can also be established using one router/firewall appliance with **three network interfaces,** referred to as triple-homed. One interface is the public one, another is the DMZ, and the third connects to the LAN. Routing and filtering rules determine what forwarding is allowed between these interfaces. This can achieve the same sort of configuration as a screened subnet.

![A VLAN100 (Dept LAN) box is connected to a Core/Distribution box that is connected to an Extranet box that is connected to an ISP router icon.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4718-1599771802119.png)

A triple-homed firewall DMZ topology. (Images © 123RF.com.)
# SCREENED HOSTS

Smaller networks may not have the budget or technical expertise to implement a DMZ. In this case, Internet access can still be implemented using a dual-homed proxy/gateway server acting as a screened host.

![A VLAN100 (Dept LAN) box is connected to a Core/Distribution box that is connected to an Extranet box that is connected to an ISP router icon](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8346-1599771802220.png)

A screened host. (Images © 123RF.com.)

Sometimes the term DMZ (or "DMZ host") is used by SOHO router vendors to mean a host on the local network that accepts connections from the Internet. This might be simpler to configure and solve some access problems, but it makes the whole network very vulnerable to intrusion and [[DoS]]. An enterprise DMZ is established by a separate network interface and subnet so that traffic between hosts in the DMZ and the LAN must be routed (and subject to firewall rules). Most SOHO routers do not have the necessary ports or routing functionality to create a true DMZ.
# IMPLICATIONS OF IPV6

IPv6 has impacts for on-premises networks, for the way your company accesses cloud services, and for the way clients access web servers and other public servers that you publish.

IPv6 may be enabled by default on clients and servers, and even on network appliances (routers and firewalls), so there must be a management and security plan for it. If IPv6 is enabled but unmanaged, there is the potential for malicious use as a **backdoor or covert channel**. IPv6 also exposes novel [[attack vector]]s, such as spoofing and DoS attacks on neighbor discovery ([https://www.cisco.com/c/en/us/products/ios-nx-os-software/ipv6-first-hop-security-fhs/index.html?dtid=osscdc000283](https://www.cisco.com/c/en/us/products/ios-nx-os-software/ipv6-first-hop-security-fhs/index.html?dtid=osscdc000283)).

Hosts should be allocated IPv6 addresses that map to the same zones as the IPv4 topology. Firewalls should be configured with [[ACLs]] that either achieve the same security configuration as for IPv4 or block IPv6, if that is a better option. One issue here is that IPv6 is not intended to perform any type of address translation. Rather than obscure internal/external traffic flows with private to public address mapping, IPv6 routing and filtering policies should be configured to mirror the equivalent IPv4 architecture #A_D.

The Internet Society has published a white paper on security implications of IPv6 ([internetsociety.org/wp-content/uploads/2019/03/deploy360-ipv6-security-v1.0.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/deploy360-ipv6-security-v1.0.pdf)). Infoblox's white paper on migrating services to IPv6 provides more useful context ([infoblox.com/wp-content/uploads/2016/04/infoblox-whitepaper-seven-deadly-traps-of-ipv6-deployment_0.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/infoblox-whitepaper-seven-deadly-traps-of-ipv6-deployment_0.pdf)).
# OTHER SECURE NETWORK DESIGN CONSIDERATIONS

Network design must also be considered for data centers and the cloud. A data center is a facility dedicated to hosting servers, rather than a mix of server and client workstation machines.

### East-West Traffic

**Traffic that goes to and from a data center is referred to as north-south.** This traffic represents clients outside the data center making requests and receiving responses. In data centers that support cloud and other Internet services, **most traffic is actually between servers within the data center. This is referred to as east-west traffic.**

Consider a client uploading a photograph as part of a social media post. The image file might be checked by an analysis server for policy violations (indecent or copyright images, for instance), a search/indexing service would be updated with the image metadata, the image would be replicated to servers that provision content delivery networks ([[CDNs]]), the image would be copied to backup servers, and so on. A single request to the cloud tends to cascade to multiple requests and transfers within the cloud.

The preponderance of east-west traffic complicates security design. If each of these cascading transactions were to pass through a firewall or other security appliance, it would create a severe bottleneck. These requirements are driving the creation of virtualized security appliances that can monitor traffic as it passes between servers ([blogs.cisco.com/security/trends-in-data-center-security-part-1-traffic-trends](https://blogs.cisco.com/security/trends-in-data-center-security-part-1-traffic-trends)).

### Zero Trust

Zero trust is based on the idea that perimeter security is unlikely to be completely robust. On a modern network, there are just too many opportunities for traffic to escape monitoring by perimeter devices and DMZs. **Zero trust uses systems such as continuous authentication and conditional access to mitigate privilege escalation and account compromise by [[threat actor]]s**.

Another zero trust technique is to apply microsegmentation. Microsegmentation is a security process that is capable of applying policies to a single node, as though it was in a zone of its own. Like east-west traffic, this requires a new generation of virtualized security appliances to implement ([vmware.com/solutions/micro-segmentation.html](https://www.vmware.com/solutions/micro-segmentation.html)).
