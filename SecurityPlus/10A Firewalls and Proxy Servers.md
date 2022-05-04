---
tags: [A_D, Implementation,section]
---
# ## 

LESSON INTRODUCTION

In addition to the secure switching and routing appliances and protocols used to implement network connectivity, the network infrastructure design must also include security appliances to ensure confidentiality, integrity, and [[My linked notes/Dictionary/Availability]] of services and data. You should be able to distinguish the features of security and monitoring devices and software and deploy these devices to appropriate locations in the network.

## 

LESSON OBJECTIVES

In this lesson, you will:

-   Implement firewalls and proxy servers.
-   Implement network security monitoring.
-   Summarize the use of SIEM.
# EXAM OBJECTIVES COVERED

3.3 Given a scenario, implement secure network designs #A_D

The firewall is one of the longest serving types of network security control, developed to segregate some of the first Internet networks in the 1980s. Since those early days, firewall types and functionality have both broadened and deepened. **As a network security professional, a very large part of your workday will be taken up with implementing, configuring, and troubleshooting [[firewall]] and [[proxies]].**
# PACKET FILTERING FIREWALLS 

Packet filtering describes the earliest type of network firewall. All firewalls can still perform this basic function. 

### Access Control Lists (ACLs)

A packet filtering firewall is configured by specifying a **group of rules**, called an access control list ([[ACL]]). Each rule defines a specific type of data packet and the **appropriate action** to take when a packet matches the rule. An action can be either to deny (block or drop the packet, and optionally log an event) or to accept (let the packet pass through the firewall). A packet filtering firewall can **inspect the headers of IP packets**. This means that rules can be based on the information found in those headers:

-   [[IP filtering]]—accepting or denying traffic on the basis of its source and/or destination IP address.
-   [[Protocol ID/type]] (TCP, UDP, ICMP, routing protocols, and so on).
-   [[Port filtering/security]]—accepting or denying a packet on the basis of source and destination port numbers (TCP or UDP application type).

There may be additional functionality in some products, such as the ability to block some types of [[ICMP]] (ping) traffic but not others, or the ability to filter by hardware [[MAC address]]. Another distinction that can be made is whether the firewall can control only inbound traffic or both inbound and outbound traffic. This is also often referred to as **ingress and egress traffic or filtering.** Controlling outbound traffic is useful because it can block applications that have not been authorized to run on the network and defeat malware, such as [[backdoors]]. Ingress and egress traffic is filtered using separate ACLs. 

### Stateless Operation

A basic packet filtering firewall is [[stateless]]. This means that it does not preserve information about network sessions. Each packet is analyzed independently, with no record of previously processed packets. This type of filtering requires the least processing effort, but it can be vulnerable to attacks that are spread over a sequence of packets. A stateless firewall can also introduce problems in traffic flow, especially when some sort of load balancing is being used or when clients or servers need to use dynamically assigned ports. 
# STATEFUL INSPECTION FIREWALLS

A stateful inspection firewall addresses these problems by **tracking information** about the session established between **two hosts, or blocking malicious attempts to start a bogus session**. The vast majority of firewalls now incorporate some level of stateful inspection capability. Session data is stored in a state table. When a packet arrives, the firewall checks it to confirm whether it belongs to an existing connection. If it does not, it applies the ordinary packet filtering rules to determine whether to allow it. Once the connection has been allowed, the firewall usually allows traffic to pass unmonitored, in order to conserve processing effort.

![A list of states is shown with Interface, Protocol, Source (Original) -&gt; Destination (Original), State, Packets, and Bytes; a State filter is above.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4775-1599771803592.png)

State table in the pfSense firewall [[appliance]]. (Screenshot used with permission from Rubicon Communications, LLC.)

Stateful inspection can occur at two layers: transport and application.

### Transport Layer ([[OSI]] Layer 4)

At the [[transport layer]], the firewall examines the TCP three-way handshake to distinguish new from established connections. A legitimate [[TCP]] connection should follow a SYN > SYN/ACK > ACK sequence to establish a session, which is then tracked using sequence numbers. Deviations from this, such as SYN without ACK or sequence number anomalies, can be dropped as malicious flooding or session hijacking attempts. The firewall can be configured to respond to such attacks by blocking source IP addresses and throttling sessions. It can also track [[UDP]] connections, though this is harder as UDP is a connectionless protocol. It is also likely to be able to detect IP header and [[ICMP]] anomalies.

![Advanced options include Source OS, Diffserv Code Point, Allow IP options, Disable reply-to, Tag, Tagged, and Max. states, src nodes, and connections.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2664-1599771803697.png)

pfSense firewall rule configuration—Advanced settings allow maximums for states and connections to be applied. (Screenshot used with permission from [pfsense.org](https://www.pfsense.org/).)

### Application Layer ([[OSI]] Layer 7)

An application-**aware** firewall can inspect the contents of packets at the application layer. One key feature is to **verify the application protocol matches the port**; to verify that malware isn't sending raw TCP data over port 80 just because port 80 is open, for instance. As another example, a web application firewall could analyze #Ops the Hyper Text Transfer ProtocolTTPs]] headers and the HTML code present in Hyper Text Transfer ProtocolTTPs]] packets to try to identify code that matches a pattern in its threat database. **Application-aware firewalls have many different names, including application layer gateway, stateful multilayer inspection, or deep packet inspection**. Application aware devices have to be configured with separate filters for each type of [[traffic]] (Hyper Text Transfer ProtocolTTPs]] and Hyper Text Transfer ProtocolTTPs]]S, SMTP/POP/IMAP, FTP, and so on). Application aware firewalls are very powerful, but they are not invulnerable. Their very complexity means that it is possible to craft DoS attacks against exploitable vulnerabilities in the firewall firmware. Also, the **firewall cannot examine encrypted data packets, unless configured with an SSL/TLS inspector.**
# IPTABLES

iptables is a command line [[|tools|utility]] provided by many Linux distributions that allows administrators to edit the rules enforced by the Linux kernel firewall ([linux.die.net/man/8/iptables](https://linux.die.net/man/8/iptables)). iptables works with chains, which apply to the different types of traffic, such as the INPUT chain for traffic destined for the local host. Each chain has a default policy set to DROP or ALLOW traffic that does not match a rule. Each rule, processed in order, determines whether traffic matching the criteria is allowed or dropped.

The command iptables --list INPUT --line-numbers -n will show the contents of the INPUT chain with line numbers and no name resolution. The rules in the following example drop any traffic from the specific host at 10.1.0.192 and allow ICMP echo requests (pings), DNS, and Hyper Text Transfer ProtocolTTPs]]/Hyper Text Transfer ProtocolTTPs]]S traffic either from the local subnet (10.1.0.0/24) or from any network (0.0.0.0/0):

Chain INPUT (policy DROP)

# target prot opt source   destination 

1 DROP  all -- 10.1.0.192  0.0.0.0/0 

2 ACCEPT icmp -- 10.10.0.0/24 0.0.0.0/0 icmptype 8

3 ACCEPT udp -- 0.0.0.0/0  0.0.0.0/0  udp dpt:53

4 ACCEPT tcp -- 0.0.0.0/0  0.0.0.0/0  tcp dpt:53

5 ACCEPT tcp -- 10.1.0.0/24 0.0.0.0/0  tcp dpt:80

6 ACCEPT tcp -- 10.1.0.0/24 0.0.0.0/0  tcp dpt:443

7 ACCEPT all -- 0.0.0.0/0  0.0.0.0/0  ctstate RELATED,ESTABLISHED

The destination 0.0.0.0/0 means "anywhere." When set on the INPUT chain, the effect is to match any IP address that the local host is currently using. The [[ctstate]] rule is a stateful rule that allows any traffic that is part of an established or related session. As established connections should already have been allowed, this reduces processing requirements to minimize impact on traffic flow.

The following command will insert a new rule as line 2 to allow traffic to the SSH server TCP port (22) from the local subnet:

iptables -I INPUT 2 -p tcp -s 10.1.0.0/24 --dport 22 -j ACCEPT

Different switches can be used to append (-A), delete (-D), or replace (-R) rules.

Access control list entries shown using the command iptables --list INPUT --line-numbers -n with iptables command.
# FIREWALL IMPLEMENTATION 

You should consider how the firewall is implemented—as hardware or software, for instance—to cover a given placement or use on the network. Some types of firewalls are better suited for placement at the network edge or zonal borders; others are designed to protect individual hosts.

### Firewall Appliances

An appliance firewall is a stand-alone hardware firewall deployed to monitor traffic passing into and out of a network zone. A firewall appliance can be deployed in two ways:

-   **Routed** ([[OSI|layer 3]])—the firewall performs forwarding between subnets. Each interface on the firewall connects to a different subnet and represents a different security zone.
-   **Bridged** ([[OSI|layer 2]])—the firewall inspects traffic passing between two nodes, such as a router and a switch. This is also referred to as transparent mode. The firewall does not have an IP interface (except for configuration management). It bridges the Ethernet interfaces between the two nodes. Despite performing forwarding at layer 2, the firewall can still inspect and filter traffic on the basis of the full range of packet headers. The typical use case for a transparent firewall is to deploy it without having to reconfigure subnets and reassign IP addresses on other devices.

![Tab has Device Information, VPN Sessions, System Resources Status, Interface Status, Failover Status, Traffic Status, and Latest ASDM Syslog Messages.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3699-1599771803856.png)

Cisco ASA (Adaptive Security Appliance) ASDM (Adaptive Security Device Manager) interface. (Screenshot used with permission from Cisco.)

A router firewall or firewall router appliance implements filtering functionality as part of the router firmware. **The difference is that a router appliance is primarily designed for routing, with firewall as a secondary feature.** SOHO Internet router/modems come with a firewall built-in, for example. 

### Application-Based Firewalls

[[firewall]] can also run as software on any type of computing host. There are several types of application-based firewalls:

-   **Host-based** firewall (or personal firewall)—implemented as a software application running on a single host designed to protect that host only. As well as enforcing packet filtering ACLs, a personal firewall can be used to allow or deny software processes from accessing the network.
-   **Application** firewall—software designed to run on a server to protect a particular application only (a web server firewall, for instance, or a firewall designed to protect an SQL Server database). This is a type of host-based firewall and would typically be deployed in addition to a network firewall.
-   **Network operating system** ([[NOS]]) firewall—a software-based firewall running under a network server OS, such as Windows or Linux. The server would function as a gateway or proxy for a network segment.
# PROXIES AND GATEWAYS 

A [[firewall]] that performs application layer filtering is likely to be implemented as a proxy. Where a network firewall only accepts or blocks traffic, **a proxy server works on a store-and-forward model.** The proxy deconstructs each packet, performs analysis, then rebuilds the packet and forwards it on, providing it conforms to the rules. 

The amount of rebuilding depends on the [[proxy]]. Some proxies may only manipulate the [[IP]] and [[TCP]] headers. Application-aware proxies might add or remove Hyper Text Transfer ProtocolTTPs]] headers. **A deep packet inspection proxy might be able to remove content from an Hyper Text Transfer ProtocolTTPs]] payload.**

### Forward Proxy Servers

A forward [[proxy]] provides for protocol-specific outbound traffic. For example, you might deploy a web proxy that enables client computers on the LAN to connect to websites and secure websites on the Internet. **This is a forward proxy that services TCP ports 80 and 443 for outbound traffic.** 

![Tab shows “Blacklist Update” and a text box, then buttons Download, Cancel, Restore Default. “Enter FTP or Hyper Text Transfer ProtocolTTPs]] path to the blacklist archive here.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8453-1599771803938.png)

Configuring content filter settings for the Squid proxy server (squid-cache.org) running on pfSense. The filter can apply [[ACL|ACLs]] and time-based restrictions, and use block lists to prohibit access to URLs. (Screenshot used with permission from Rubicon Communications, LLC.)

The main benefit of a proxy is that client computers connect to a specified point on the perimeter network for web access. The proxy can be positioned within a [[DMZ]]. This provides for a degree of traffic management and security. In addition, most web [[proxy]] servers provide caching engines, whereby frequently requested web pages are retained on the proxy, negating the need to re-fetch those pages for subsequent requests.

**A proxy server must understand the application it is servicing.** For example, a web proxy must be able to parse and modify Hyper Text Transfer ProtocolTTPs]] and Hyper Text Transfer ProtocolTTPs]]S commands (and potentially HTML and scripts too). Some proxy servers are application-specific; others are multipurpose. A multipurpose proxy is one configured with filters for multiple protocol types, such as [[Hyper Text Transfer ProtocolTTPs]]]], [[FTP]], and [[SMTP]].

Proxy servers can generally be classed as non-transparent or transparent.

-   A non-transparent proxy means that the client must be configured with the proxy server address and port number to use it. The port on which the proxy server accepts client connections is often configured as **port 8080**.
-   A transparent (or forced or intercepting) proxy intercepts client traffic without the client having to be reconfigured. A transparent proxy must be implemented on a switch or router or other inline network appliance.

![Settings include Transparent Hyper Text Transfer ProtocolTTPs]] Proxy, Interface(s), and Bypass Proxies for: Private Address Destination, These Source IPs, These Destination IPs.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5112-1599771804006.png)

Configuring transparent proxy settings for the Squid proxy server (squid-cache.org) running on pfSense. (Screenshot used with permission from Rubicon Communications, LLC.)

Both types of proxy can be configured to require users to be authenticated before allowing access. The proxy is likely to be able to use [[SSO]] to do this without having to prompt the user for a password. 

A proxy autoconfiguration ([[PAC]]) script allows a client to configure proxy settings without user intervention. The Web Proxy Autodiscovery ([[WPAD]]) protocol allows browsers to locate a PAC file. This can be an [[attack vector]], as a malicious proxy on the local network can be used to obtain the user's hash as the browser tries to authenticate ([nopsec.com/responder-beyond-wpad](https://www.nopsec.com/responder-beyond-wpad/)).

### Reverse Proxy Servers

A reverse proxy server provides for protocol-specific inbound traffic. For security purposes, you might not want external hosts to be able to connect directly to application servers, such as web, email, and VoIP servers. Instead, you can deploy a reverse proxy on the network edge and configure it to listen for client requests from a public network (the Internet). The proxy applies filtering rules and if accepted, it creates the appropriate request for an application server within a [[DMZ]]. In addition, **some reverse proxy servers can handle application-specific [[Load balancers|load balancing]]**, traffic encryption, and caching, reducing the overhead on the application servers.
# ACCESS CONTROL LISTS

[[Firewall]] access control lists ([[ACL |ACLs]]) are configured on the principle of least access. This is the same as the principle of least privilege; only allow the minimum amount of traffic required for the operation of valid network services and no more. The rules in a firewall's ACL are processed top-to-bottom. If traffic matches one of the rules, then it is allowed to pass; consequently, the most specific rules are placed at the top. The final default rule is typically to block any traffic that has not matched a rule (implicit deny). If the firewall does not have a default implicit deny rule, an explicit deny all rule can be added manually to the end of the ACL.

![Rule list is shown with States, Protocol, Source, Port, Destination, Port, Gateway, Queue, Schedule, Description, and Actions. Rule order can change.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3817-1599771804108.png)

Sample firewall ruleset configured on pfSense. This ruleset blocks all traffic from bogon networks and a specific private address range but allows any Hyper Text Transfer ProtocolTTPs]], Hyper Text Transfer ProtocolTTPs]]S, or SMTP traffic from any other source. (Screenshot used with permission from Rubicon Communications, LLC.)

Each rule can specify whether to block or allow traffic based on several parameters, often referred to as tuples. If you think of each rule being like a row in a database, the tuples are the columns. For example, in the previous screenshot, the [[tuples]] include Protocol, Source (address), (Source) Port, Destination (address), (Destination) Port, and so on.

Even the simplest packet filtering firewall can be complex to configure securely. It is essential to create a written policy describing what a filter ruleset should do and to test the configuration as far as possible to ensure that the ACLs you have set up work as intended. Also test and document changes made to [[ACL|ACLs]]. Some other basic principles include:

-   Block incoming requests from internal or private IP addresses (that have obviously been spoofed).
-   **Block incoming requests from protocols that should only be functioning at a local network level, such as ICMP, DHCP, or routing protocol traffic.**
-   Use penetration testing to confirm the configuration is secure. Log access attempts and monitor the logs for suspicious activity.
-   Take the usual steps to secure the hardware on which the firewall is running and use of the management interface.

Access control list entries shown using the command iptables --list INPUT --line-numbers -n.
# NETWORK ADDRESS TRANSLATION

Network address translation ([[NAT]]) was devised as a way of freeing up scarce IP addresses for hosts needing Internet access. A private network will typically use a private addressing scheme to allocate IP addresses to hosts. These addresses can be drawn from one of the pools of addresses defined in RFC 1918 ([tools.ietf.org/html/rfc1918](https://tools.ietf.org/html/rfc1918)) as non-routable over the Internet:

-   10.0.0.0 to 10.255.255.255 (Class A private address range).
-   172.16.0.0 to 172.31.255.255 (Class B private address range).
-   192.168.0.0 to 192.168.255.255 (Class C private address range).

A NAT gateway is a service that translates between the private addressing scheme used by hosts on the LAN and the public addressing scheme used by router, firewall, or proxy server on the [[network edge]]. NAT provides security in the sense that it can manage ingress and egress traffic at well-defined points on the network edge, but it is important to realize that it does not perform a filtering function.

There are several types of NAT:

-   **Static and dynamic source NAT**—perform 1:1 mappings between private ("inside local") network address and public ("inside global") addresses. These mappings can be static or dynamically assigned.
-   **Overloaded NAT/Network Address Port Translation** ([[NAPT]])/Port Address Translation ([[PAT]])—provides a means for multiple private IP addresses to be mapped onto a single public address. For example, say two hosts (192.168.0.101 and 192.168.0.102) initiate a web connection at the same time. The NAPT service creates two new port mappings for these requests (192.168.0.101:61101 and 192.168.0.102:61102). It then substitutes the private IPs for the public IP and forwards the requests to the public Internet. It performs a reverse mapping on any traffic returned using those ports, inserting the original IP address and port number, and forwards the packets to the internal hosts.

![nat-overloading.png](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/nat-overloading.png)

NAT overloading. (Image © 123RF.com.)

-   **Destination NAT/port forwarding**—uses the router's public address to publish a web service, but forwards incoming requests to a different IP. Port forwarding means that the router takes requests from the Internet for a particular application (say, Hyper Text Transfer ProtocolTTPs]]/port 80) and sends them to a designated host and port in the DMZ or LAN.

![Edit Redirect Entry has Interface (WAN), Protocol (TCP), Destination port range (Any), Redirect target IP (10.1.0.10), and Redirect target port (Hyper Text Transfer ProtocolTTPs]])](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8572-1599771804610.png)

Configuring port forwarding on a pfSense firewall appliance—This rule forwards any Hyper Text Transfer ProtocolTTPs]] traffic received on the appliance's WAN interface to the 10.1.0.10 host on the LAN. (Screenshot used with permission from [pfsense.org](https://www.pfsense.org/).)

The larger IPv6 address space makes most use cases for NAT redundant. A host can use a link-local address to contact neighboring nodes, but any routed traffic should use a globally unique address. In IPv6 it is routing policies and firewall filtering that manage which hosts and networks are reachable. That said, there are mechanisms for translating prefixes at the network edge ([[NPTv6]]) and for translation between IPv6 addresses ([[NAT66]]) or IPv6 and IPv4 addresses ([[NAT64]] and [[NAT46]]).
# VIRTUAL FIREWALLS

Virtual firewalls are usually deployed within data centers and cloud services. A virtual firewall can be implemented in three different ways:

-   [[Hypervisor]]-based—this means that filtering functionality is built into the hypervisor or cloud provisioning tool. You can use the cloud's web app or application programming interface ([[API]]) to write access control lists ([[ACL]]s) for traffic arriving or leaving a virtual host or virtual network.
-   [[Virtual appliance]]—this refers to deploying a vendor firewall appliance instance using virtualization, in the same way you might deploy a Windows or Linux guest OS.
-   [[Multiple context]]—this refers to multiple virtual firewall instances running on a hardware firewall appliance. Each context has a separate interface and can perform a distinct filtering role.

While they can be deployed like "regular" firewalls for zone-based routing and filtering, **virtual firewalls**' most significant role is to support the east-west security and zero-trust microsegmentation design paradigms. They are able to inspect traffic as it passes from host-to-host or between virtual networks, rather than requiring that traffic be routed up to a firewall appliance and back.
# OPEN-SOURCE VERSUS PROPRIETARY FIREWALLS

The ability to inspect source code will be a requirement for high-security environments that cannot rely on implicit trust when selecting vendors. The code underpinning appliance-based, software, and virtual firewalls can be developed as open-source or proprietary or somewhere in between:

-   Wholly proprietary—implemented as a proprietary OS, such as Cisco ASA, Juniper JunOS, PaloAlto PAN-OS, or Barracuda's Windows-based appliance.
-   Mostly proprietary—developed from a Linux kernel, but with proprietary features added. Examples include Check Point IPSO, FortiGate FortiOS, and Sonicwall. Any code developed from a GPL source should be available, but in general terms these products cannot be used independently of a commercial contract with the vendor.
-   Wholly open-source—these can be used independently of the vendor, but the vendors typically have commercial appliances and support contracts too. Examples include pfSense and Smoothwall.

In determining whether to follow a self-installed versus supported deployment, as well as the core appliance code, you need to consider access to support, update [[My linked notes/Dictionary/Availability]], and access to subscription-based features, such as signatures and threat feeds.
