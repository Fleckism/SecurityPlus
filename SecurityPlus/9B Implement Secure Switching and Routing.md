---
tags: [firstTag, secondTag]
---
# EXAM OBJECTIVES COVERED

1.4 Given a scenario, analyze potential indicators associated with network attacks

3.1 Given a scenario, implement secure protocols (Routing and switching only)

3.3 Given a scenario, implement secure network designs 

Attacks aimed at low-level networking functions can be highly effective. To implement a network design that demonstrates confidentiality, integrity, and availability, you must configure switches and routers with appropriate settings. These devices can be used to enforce network access control mechanisms and ensure fault-tolerant paths within the network.
# MAN-IN-THE-MIDDLE AND LAYER 2 ATTACKS 

Attacks at the physical and data link layers, referred to in the OSI model as layer 1 and layer 2, are often focused on information gathering—network mapping and eavesdropping on network traffic.

### Man-in-the-Middle/On-Path Attacks

Attackers can also take advantage of the lack of security in low-level data link protocols to perform man-in-the-middle (MitM) attacks. A MitM or on-path attack is where the threat actor gains a position between two hosts, and transparently captures, monitors, and relays all communication between the hosts. An on-path attack could also be used to covertly modify the traffic. For example, a MitM host could present a workstation with a spoofed website form, to try to capture the user credential. Another common on-path attack spoofs responses to DNS queries, redirecting users to spoofed websites. On-path attacks can be defeated using mutual authentication, where both hosts exchange secure credentials, but at layer 2 it is not always possible to put these controls in place.

### MAC Cloning 

MAC cloning, or MAC address spoofing, changes the hardware address configured on an adapter interface or asserts the use of an arbitrary MAC address. While a unique MAC address is assigned to each network interface by the vendor at the factory, it is simple to override it in software via OS commands, alterations to the network driver configuration, or using packet crafting software. This can lead to a variety of issues when investigating security incidents or when depending on MAC addresses as part of a security control, as the presented address of the device may not be reliable.
# ARP POISONING AND MAC FLOODING ATTACKS 

A host uses the Address Resolution Protocol (ARP) to discover the host on the local segment that owns an IP address.

### ARP Poisoning Attacks 

An ARP poisoning attack uses a packet crafter, such as Ettercap, to broadcast unsolicited ARP reply packets. Because ARP has no security mechanism, the receiving devices trust this communication and update their MAC:IP address cache table with the spoofed address. 

![Frame 9 is highlighted with Source 10.1.0.101, Destination 10.1.0.2. Frame detail shows destination “Microsof_01:ca:4a” as hardware 00:15:5d:01:ca:4a.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5415-1599771802359.png)

Packet capture opened in Wireshark showing ARP poisoning. (Screenshot used with permission from [wireshark.org](https://www.wireshark.org/).)

This screenshot shows packets captured during a typical ARP poisoning attack:

-   In frames 6-8, the attacking machine (with MAC address ending :4a) directs gratuitous ARP replies at other hosts (:76 and :77), claiming to have the IP addresses .2, .101, and .102.
-   In frame 9, the .101/:77 host tries to send a packet to the .2 host, but it is received by the attacking host (with the destination MAC :4a).
-   In frame 10, the attacking host retransmits frame 9 to the actual .2 host. Wireshark colors the frame black and red to highlight the retransmission.
-   In frames 11 and 12, you can see the reply from .2, received by the attacking host in frame 11 and retransmitted to the legitimate host in frame 12.

The usual target will be the subnet's default gateway (the router that accesses other networks). If the ARP poisoning attack is successful, all traffic destined for remote networks will be sent to the attacker. The attacker can perform a man-in-the-middle attack, either by monitoring the communications and then forwarding them to the router to avoid detection, or modifying the packets before forwarding them. The attacker could also perform a denial of service attack by not forwarding the packets.

### MAC Flooding Attacks 

Where ARP poisoning is directed at hosts, MAC flooding is used to attack a switch. The intention of the attacker is to exhaust the memory used to store the switch's MAC address table. The switch uses the MAC address table to determine which port to use to forward unicast traffic to its correct destination. Overwhelming the table can cause the switch to stop trying to apply MAC-based forwarding and flood unicast traffic out of all ports, working as a hub. This makes sniffing network traffic easier for the threat actor.
# LOOP PREVENTION

An Ethernet switch's layer 2 forwarding function is similar to that of an older network appliance called a bridge. In a network with multiple bridges, implemented these days as switches, there may be more than one path for a frame to take to its intended destination. As a layer 2 protocol, Ethernet has no concept of Time To Live. Therefore, layer 2 broadcast traffic could continue to loop through a network with multiple paths indefinitely. Layer 2 loops are prevented by the Spanning Tree Protocol (STP). Spanning tree is a means for the bridges to organize themselves into a hierarchy and prevent loops from forming.

![Root Bridge has “DP” at each side: one connects to “RP” at Bridge A, the other to “RP” at Bridge B. “DP” at Bridge A connects to “BP” at Bridge B.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3501-1599771802449.png)

STP configuration. (Images © 123RF.com.)

This diagram shows the minimum configuration necessary to prevent loops in a network with three bridges or switches. The root bridge has two designated ports (DP) connected to Bridge A and Bridge B. Bridges A and B both have root ports (RP) connected back to the interfaces on the root bridge. Bridges A and B also have a connection directly to one another. On Bridge A, this interface is active and traffic for Bridge B can be forwarded directly over it. On Bridge B, the interface is blocked (BP) to prevent a loop and traffic for Bridge A must be forwarded via the root bridge. Only Bridge Protocol Data Unit (BPDU) traffic will go across a blocked port.

### Broadcast Storm Prevention 

STP is principally designed to prevent broadcast storms. Switches forward broadcast, multicast, and unknown unicast traffic out of all ports. If a bridged network contains a loop, broadcast traffic will travel through the network, get amplified by the other switches, and arrive back at the original switch, which will re-broadcast each incoming broadcast frame, causing an exponential increase (the storm), which will rapidly overwhelm the switches and crash the network.

A loop can be created accidentally or maliciously by plugging a patch cable from one patch panel port to another or connecting two wall ports. Normally, STP should detect and close the loop, resulting in a few seconds disruption. However, STP may be misconfigured or a threat actor may have managed to disrupt it. A storm control setting on a switch is a backup mechanism to rate-limit broadcast traffic above a certain threshold.

### Bridge Protocol Data Unit (BPDU) Guard

A threat actor might try to attack STP using a rogue switch or software designed to imitate a switch. When a switch does not know the correct port to use for a particular destination MAC address (if the cache has just been flushed, for instance), it floods the unknown unicast frame out to all ports. Topology changes in STP can cause a switch to flush the cache more frequently and to start flooding unicast traffic more frequently, which can have a serious impact on network performance and assists sniffing attacks.

The configuration of switch ports should prevent the use of STP over ports designated for client devices (access ports). An access port is configured with the portfast command to prevent STP changes from delaying client devices trying to connect to the port. Additionally, the BPDU Guard setting should be applied. This causes a portfast-configured port that receives a BPDU to become disabled ([cisco.com/c/en/us/td/docs/switches/lan/catalyst4000/8-2glx/configuration/guide/stp_enha.html](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst4000/8-2glx/configuration/guide/stp_enha.html)). Bridge Protocol Data Units (BPDUs) are used to communicate information about the topology and are not expected on access ports, so BPDU Guard protects against misconfiguration or a possible malicious attack.
# PHYSICAL PORT SECURITY AND MAC FILTERING

Because of the risks from rogue devices and the potential to create loops by incorrect placement of patch cables, access to the physical switch ports and switch hardware should be restricted to authorized staff, using a secure server room and/or lockable hardware cabinets. To prevent the attachment of unauthorized client devices at unsecured wall ports, the switch port that the wall port cabling connects to can be disabled by using the management software, or the patch cable can be physically removed from the port. Completely disabling ports in this way can introduce a lot of administrative overhead and scope for error. Also, it doesn't provide complete protection, as an attacker could unplug a device from an enabled port and connect their own laptop. Consequently, more sophisticated methods of ensuring port security have been developed.

### MAC Filtering and MAC Limiting

Configuring MAC filtering on a switch means defining which MAC addresses are allowed to connect to a particular port. This can be done by creating a list of valid MAC addresses or by specifying a limit to the number of permitted addresses. For example, if port security is enabled with a maximum of two MAC addresses, the switch will record the first two MACs to connect to that port, but then drop any traffic from machines with different MAC addresses that try to connect ([cisco.com/c/en/us/td/docs/ios/lanswitch/command/reference/lsw_book/lsw_m1.html](https://www.cisco.com/c/en/us/td/docs/ios/lanswitch/command/reference/lsw_book/lsw_m1.html)). This provides a guard against MAC flooding attacks.

### DHCP Snooping

Another option is to configure Dynamic Host Configuration Protocol (DHCP) snooping. DHCP is the protocol that allows a server to assign IP address information to a client when it connects to the network. DHCP snooping inspects this traffic arriving on access ports to ensure that a host is not trying to spoof its MAC address. It can also be used to prevent rogue (or spurious) DHCP servers from operating on the network. With DHCP snooping, only DHCP messages from ports configured as trusted are allowed. Additionally dynamic ARP inspection (DAI), which can be configured alongside DHCP snooping, prevents a host attached to an untrusted port from flooding the segment with gratuitous ARP replies. DAI maintains a trusted database of IP:ARP mappings and ensures that ARP packets are validly constructed and use valid IP addresses ([cisco.com/c/en/us/td/docs/switches/lan/catalyst6500/ios/12-2SX/configuration/guide/book/snoodhcp.html](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst6500/ios/12-2SX/configuration/guide/book/snoodhcp.html)).

![Command “ip arp inspection vlan 1,999” gives response “...DHCP_SNOOPING_DENY: 1 Invalid ARPs (Req) on Fal/0/23, vlan 1.” then MAC, IP, and timestamp.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8777-1599771802487.png)

Configuring ARP inspection on a Cisco switch.
# NETWORK ACCESS CONTROL

Endpoint security is a set of security procedures and technologies designed to restrict network access at a device level. Endpoint security contrasts with the focus on perimeter security established by topologies such as DMZ and technologies such as firewalls. Endpoint security does not replace these but adds defense in depth.

The IEEE 802.1X standard defines a port-based network access control (PNAC) mechanism. PNAC means that the switch uses an AAA server to authenticate the attached device before activating the port. Network access control (NAC) products can extend the scope of authentication to allow administrators to devise policies or profiles describing a minimum security configuration that devices must meet to be granted network access. This is called a health policy. Typical policies check things such as malware infection, firmware and OS patch level, personal firewall status, and the presence of up-to-date virus definitions. A solution may also be to scan the registry or perform file signature verification. The health policy is defined on a NAC management server along with reporting and configuration tools.

Posture assessment is the process by which host health checks are performed against a client device to verify compliance with the health policy. Most NAC solutions use client software called an agent to gather information about the device, such as its antivirus and patch status, presence of prohibited applications, or anything else defined by the health policy.

!["5 items are listed under headings Id, Description, Actions, Target Role, and Action. Under Action, each item has 3 buttons: Clone, Delete, Preview.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9725-1599771802533.png)

Defining policy violations in Packet Fence Open Source NAC. (Screenshot used with permission from [packetfence.org](https://packetfence.org/).)

An agent can be persistent, in which case it is installed as a software application on the client, or nonpersistent. A nonpersistent (or dissolvable) agent is loaded into memory during posture assessment but is not installed on the device.

![A Scan Engine tab has the headings “Name” and “Scan Engine”. An “Add Scan” button is selected and shows the options Nessus, Nessus 6, OpenVAS, and WMI](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/6000-1599771802615.png)

Packet Fence supports the use of several scanning techniques, including vulnerability scanners, such as Nessus and OpenVAS, Windows Management Instrumentation (WMI) queries, and log parsers. (Screenshot used with permission from [packetfence.org](https://packetfence.org/).)

Some NAC solutions can perform agentless posture assessment. This is useful when the NAC solution must support a wide range of devices, such as smartphones, tablets, and Internet of Things (IoT) devices, but less detailed information about the client is available with an agentless solution.
# ROUTE SECURITY 

A successful attack against route security enables the attacker to redirect traffic from its intended destination. On the Internet, this may allow the threat actor to herd users to spoofed websites. On an enterprise network, it may facilitate circumventing firewalls and security zones to allow lateral movement and data exfiltration.

Routes between networks and subnets can be configured manually, but most routers automatically discover routes by communicating with each other. Dynamic routers exchange information about routes using routing protocols. It is important that this traffic be separated from channels used for other types of data. Routing protocols do not always have effective integral security mechanisms, so they need to run in an environment where access is very tightly controlled.

Sample routing table showing routes obtained from different sources, such as static configuration, direct connection, and learned from the Border Gateway Protocol (BGP) routing protocol.

Routing is subject to numerous vulnerabilities, including:

-   Spoofed routing information (route injection)—Routing protocols that have no or weak authentication are vulnerable to route table poisoning. This can mean that traffic is misdirected to a monitoring port (sniffing), sent to a blackhole (nonexistent address), or continuously looped around the network, causing DoS. Most dynamic routing protocols support message authentication via a shared secret configured on each device. This can be difficult to administer, however. It is usually also possible to configure how a router identifies the peers from which it will accept route updates. This makes it harder to simply add a rogue router to the system. An attacker would have to compromise an existing router and change its configuration.
-   Source routing—This uses an option in the IP header to pre-determine the route a packet will take through the network (strict) or "waypoints" that it must pass through (loose). This can be used maliciously to spoof IP addresses and bypass router/firewall filters. Routers can be configured to block source routed packets.
-   Software exploits in the underlying operating system—Hardware routers (and switches) have an embedded operating system. For example, Cisco devices typically use the Internetwork Operating System (IOS). Something like IOS suffers from fewer exploitable vulnerabilities than full network operating systems. It has a reduced attack surface compared to a computer OS, such as Windows. 

On the other hand, SOHO broadband routers can be particularly vulnerable to unpatched exploits.
