---
tags: [section]
---
# EXAM OBJECTIVES COVERED

1.4 Given a scenario, analyze #Ops ( #Ops) potential #Indicators indicators associated with network attacks

3.3 Given a scenario, #Implementation  secure network designs #A_D #A_D 

A denial of service ([[DoS]]) attack can be extremely destructive and very difficult to mitigate. As a network security professional, it is vital for you to be able to compare and contrast DoS and distributed DoS ([[DDoS]]) methods and to be able to recommend and configure load balancing technologies that can make networks more resilient to these attacks.
# DISTRIBUTED DENIAL OF SERVICE ATTACKS 

Most denial of service (DoS) attacks against websites and gateways are distributed DoS (DDoS). This means that the attack is **launched from multiple hosts simultaneously**. Typically, a #[[threat actor]] will compromise machines to use as handlers in a command and control network. The handlers are used to compromise hundreds or thousands or millions of hosts with DoS tools (bots) forming a botnet. 

Some types of DDoS attacks simply aim to consume network bandwidth, denying it to legitimate hosts, by using overwhelming numbers of bots. Others cause resource exhaustion on the hosts' processing requests, consuming CPU cycles and memory. This delays processing of legitimate traffic and could potentially crash the host system completely. For example, a [[SYN]] flood [[attack]] works by withholding the client's ACK packet during TCP's three-way handshake. Typically the client's IP address is spoofed, meaning that an invalid or random IP is entered so the server's SYN/ACK packet is misdirected. A server, router, or firewall can maintain a queue of pending connections, recorded in its state table. When it does not receive an ACK packet from the client, it resends the SYN/ACK packet a set number of times before timing out the connection. The problem is that a server may only be able to manage a limited number of pending connections, which the DoS attack quickly fills up. This means that the server is unable to respond to genuine traffic.
# AMPLIFICATION, APPLICATION, AND OT ATTACKS 

In a distributed reflection [[DoS]] (DRDoS) or amplification SYN flood attack, the [[threat actor]] spoofs the victim's IP address and attempts to open connections with multiple servers. Those servers direct their SYN/ACK responses to the victim server. This rapidly consumes the victim's available bandwidth.

### Application Attacks

Where a network attack uses low-level techniques, such as SYN or SYN/ACK flooding, an application attack targets vulnerabilities in the headers and payloads of specific application protocols. For example, one type of amplification attack targets DNS services with bogus queries. One of the advantages of this technique is that while the request is small, the response to a DNS query can be made to include a lot of information, so this is a very effective way of overwhelming the bandwidth of the victim network with much more limited resources on the attacker's botnet.

The Network Time Protocol ([[NTP]]) can be abused in a similar way. NTP helps servers on a network and on the Internet to keep the correct time. It is vital for many protocols and security mechanisms that servers and clients be synchronized. One NTP query (monlist) can be used to generate a response containing a list of the last 600 machines that the NTP server has contacted. As with the [[DNS amplification attack]], this allows a short request to direct a long response at the victim network.

### Operational Technology (OT) Attacks

An operational technology ([[OT]]) network is established between embedded systems devices and their controllers. The term "operational" is used because these systems monitor and control physical electromechanical components, such as valves, motors, electrical switches, gauges, and sensors. [[DDoS]] attacks against the controllers in such networks can use the same techniques as against computer networks. Also, because of the limited processing ability of some controller types, older DDoS techniques, such as Smurf ([cloudflare.com/learning/ddos/smurf-ddos-attack](https://www.cloudflare.com/learning/ddos/smurf-ddos-attack/)) or Ping of Death ([imperva.com/learn/application-security/ping-of-death](https://www.imperva.com/learn/application-security/ping-of-death/)), can continue to be effective against embedded systems. The limited resources of these devices mean that DDoS can rapidly overwhelm available memory or CPU time.

As well as being the target of an attack, embedded systems might be used as bots. Any type of Internet-enabled device is vulnerable to compromise. This includes web-enabled cameras, [[SOHO]] routers, and smart TVs and other appliances. This is referred to as an Internet of Things (IoT) botnet.
# DISTRIBUTED DENIAL OF SERVICE ATTACK MITIGATION

[[DDoS]] attacks can be diagnosed by traffic spikes that have no legitimate explanation, but can usually only be counteracted by providing high [[Availability]] services, such as load balancing and cluster services. In some cases, a stateful firewall can detect a DDoS attack and automatically block the source. However, for many of the techniques used in DDoS attacks, the source addresses will be randomly spoofed or launched by bots, making it difficult to detect the source of the attack.

![Summary screen lists Top Signatures, Top Source IPs, and Top Destination IPs. Count of Top Source IPs shown is 84, 6, 1, 1, 1, 1, 1." id="d1e28021__image_kjw_nqd_khb](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2220-1599771803292.png)

Dropping traffic from block-listed IP ranges using Security Onion IDS. (Screenshot used with permission from Security Onion.)

When a network is faced with a DDoS or similar flooding attack, an [[ISP]] can use either an access control list ([[ACL]]) or a blackhole to drop packets for the affected IP address(es). A blackhole is an area of the network that cannot reach any other part of the network. The blackhole option is preferred, as evaluating each packet in a multi-gigabit stream against ACLs overwhelms the processing resources available. A standard method of doing this with border gateway protocol ([[BGP]]) routing is called a remotely triggered blackhole ([[RTBH]]) ([cisco.com/c/dam/en_us/about/security/intelligence/blackhole.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/blackhole.pdf)). The blackhole also makes the attack less damaging to the ISP's other customers. With both approaches, legitimate traffic is discarded along with the DDoS packets.

Another option is to use [[sinkhole routing]] so that the traffic flooding a particular IP address is routed to a different network where it can be analyzed. Potentially some legitimate traffic could be allowed through, but the real advantage is to identify the source of the attack and devise rules to filter it. The target can then use low [[TTL]] [[DNS]] records to change the IP address advertised for the service and try to allow legitimate traffic past the flood.

There are cloud DDoS mitigation services that can act as sinkhole network providers and try to "scrub" flooded traffic.
# LOAD BALANCING

A load balancer distributes client requests across available server nodes in a farm or pool. This is used to provision services that can scale from light to heavy loads, and to provide mitigation against DDoS attacks. A load balancer also provides fault tolerance. If there are multiple servers available in a farm, all addressed by a single name/IP address via a load balancer, then if a single server fails, client requests can be routed to another server in the farm. You can use a load balancer in any situation where you have multiple servers providing the same function. Examples include web servers, front-end email servers, and web conferencing, A/V conferencing, or streaming media servers.

There are two main types of [[load balancers]]:

-   Layer 4 load balancer—basic load balancers make forwarding decisions on IP address and TCP/UDP port values, working at the transport layer of the OSI model.
-   Layer 7 load balancer (content switch)—as web applications have become more complex, modern load balancers need to be able to make forwarding decisions based on application-level data, such as a request for a particular URL or data types like video or audio streaming. This requires more complex logic, but the processing power of modern appliances is sufficient to deal with this. 

Topology of basic load balancing architecture #A_D. (Images © 123RF.com.)

### Scheduling

The scheduling algorithm is the code and metrics that determine which node is selected for processing each incoming request. The simplest type of scheduling is called round robin; this just means picking the next node. Other methods include picking the node with the fewest connections or the best response time. Each method can also be weighted, using administrator set preferences or dynamic load information or both.

The load balancer must also use some type of heartbeat or health check probe to verify whether each node is available and under load or not. Layer 4 load balancers can only make basic connectivity tests while layer 7 appliances can test the application's state, as opposed to only verifying host [[Availability]].

### Source IP Affinity and Session Persistence 

When a client device has established a session with a particular node in the server farm, it may be necessary to continue to use that connection for the duration of the session. Source IP or session affinity is a layer 4 approach to handling user sessions. It means that when a client establishes a session, it becomes stuck to the node that first accepted the request.

An application-layer load balancer can use persistence to keep a client connected to a session. Persistence typically works by setting a cookie, either on the node or injected by the load balancer. This can be more reliable than source IP affinity, but requires the browser to accept the cookie.
# CLUSTERING 

Where load balancing distributes traffic between independent processing nodes, clustering allows multiple redundant processing nodes that share data with one another to accept connections. This provides redundancy. If one of the nodes in the cluster stops working, connections can failover to a working node. To clients, the cluster appears to be a single server.

### Virtual IP 

For example, you might want to provision two load balancer appliances so that if one fails, the other can still handle client connections. Unlike load balancing with a single appliance, the public IP used to access the service is shared between the two instances in the cluster. This is referred to as a virtual IP or shared or floating address. The instances are configured with a private connection, on which each is identified by its "real" IP address. This connection runs some type of redundancy protocol, such as Common Address Redundancy Protocol ([[CARP]]), that enables the active node to "own" the virtual IP and respond to connections. The redundancy protocol also implements a heartbeat mechanism to allow failover to the passive node if the active one should suffer a fault.

Topology of clustered load balancing architecture #A_D. (Images © 123RF.com.)

### Active/Passive (A/P) and Active/Active (A/A) Clustering

In the previous example, if one node is active, the other is passive. This is referred to as active/passive clustering. The major advantage of active/passive configurations is that performance is not adversely affected during failover. However, the hardware and operating system costs are higher because of the unused capacity.

An active/active cluster means that both nodes are processing connections concurrently. This allows the administrator to use the maximum capacity from the available hardware while all nodes are functional. In the event of a failover the workload of the failed node is immediately and transparently shifted onto the remaining node. At this time, the workload on the remaining nodes is higher and performance is degraded.

In a standard active/passive configuration, each active node must be matched by a passive node. There are N+1 and N+M configurations that provision fewer passive nodes than active nodes, to reduce costs.

### Application Clustering

Clustering is also very commonly used to provision fault tolerant application services. If an application server suffers a fault in the middle of a session, the session state data will be lost. Application clustering allows servers in the cluster to communicate session information to one another. For example, if a user logs in on one instance, the next session can start on another instance, and the new server can access the cookies or other information used to establish the login.
# QUALITY OF SERVICE (QOS)

Most network appliances process packets on a best effort and first in, first out ([[FIFO]]) basis. Quality of Service ([[QoS]]) is a framework for prioritizing traffic based on its characteristics. It is primarily used to support voice and video applications that require a minimum level of bandwidth and are sensitive to latency and jitter. [[Latency]] is the time it takes for a transmission to reach the recipient, measured in milliseconds (ms). Jitter is defined as being a variation in the delay, or an inconsistent rate of packet delivery. FIFO-based delivery makes it more likely that other applications sharing the same network will cause loss of bandwidth and increase latency and jitter for a real-time service.
 
#Implementation QoS is a complex project, as there are many different ways to do it, and many different protocols and appliances involved. In overview, a QoS implementation could work as follows:

1.  The organization performs application discovery to identify bandwidth, latency, and jitter thresholds of the protocols in use and determine their relative priority. The applications are then mapped to standard class of service ([[CoS]]) codes at layer 2 and layer 3. These codes are configured across the range of hosts and intermediate systems that handle QoS traffic.
2.  A QoS-compatible endpoint device or application uses the DiffServ field in the IP header (layer 3) and adds an 802.1p field to the Ethernet header (layer 2) to indicate that the packet should be treated as priority (traffic marking). It transmits the frame to the switch.
3.  If the switch supports QoS, it uses the 802.1p header to prioritize the frame. Note that it can only do this by holding a queue of outgoing traffic and delaying non-priority frames. If the queue is full, a traffic policing policy must state whether non-priority frames should be dropped, or whether the queue should be cleared at the expense of reducing QoS.
4.  A similar process occurs at routers and load balancers on the network edge, though they can inspect the DiffServ IP packet header, rather than having to rely on the more limited 802.1p header. Note that prioritization always takes place on the outbound interface, with low priority traffic being held in a queue.

There are many variations on this process. Modern layer 3 switches can inspect Differentiated Services Code Point ([[DSCP]]) values, rather than relying on 802.1p tagging, for instance. QoS may need to take place over wireless networks, which use a different tagging mechanism. There is also a wholly different approach to QoS called IntServ. This uses the Resource Reservation Protocol ([[RSVP]]) to negotiate a link with the performance characteristics required by the application or policy.

[[QoS]] marking introduces the potential for DoS attacks. If a [[threat actor]] can craft packets that are treated as high priority and send them at a high rate, the network can be overwhelmed. Part of QoS involves identifying trust boundaries to establish a legitimate authority for marking traffic. You should also ensure that there is always sufficient bandwidth for security-critical monitoring data and network management/configuration traffic.

For more information, consider these case studies and design overviews from Microsoft ([docs.microsoft.com/en-us/skypeforbusiness/optimizing-your-network/expressroute-and-qos-in-skype-for-business-online](https://docs.microsoft.com/en-us/skypeforbusiness/optimizing-your-network/expressroute-and-qos-in-skype-for-business-online)) and Cisco ([https://www.ciscolive.com/c/dam/r/ciscolive/apjc/docs/2018/pdf/BRKCRS-2501.pdf](https://www.ciscolive.com/c/dam/r/ciscolive/apjc/docs/2018/pdf/BRKCRS-2501.pdf#)).
