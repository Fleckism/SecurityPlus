# 1
Consider the types of zones within a network's topology and locate the zone considered semi-trusted and requires hosts to authenticate to join.

2.  Extranet

An extranet zone is a network of semi-trusted hosts, typically representing business partners, suppliers, or customers. Hosts must authenticate to join the extranet.

A private network (intranet) is a network of trusted hosts owned and controlled by the organization. This type of trusted host network is under administrative control and subject to the security mechanisms set up to defend the network.

Internet, or guest, zones permit anonymous access by untrusted hosts over the Internet. This can also be a mix of anonymous and authenticated access.

Anonymous is not a zone but is a part of the Internet or guest zones.
# 2
Where should an administrator place an internet-facing host on the network?

1.  DMZ

Internet-facing hosts reside in one or more Demilitarized Zones (DMZs), or perimeter networks. Traffic can not pass through a DMZ, but it enables external clients to access data on private systems, such as web servers, without compromising the security of the entire internal network.

Bastion hosts reside in a DMZ and are not fully trusted by the internal network due to the possibility of Internet compromise.

An extranet is a network of semi-trusted hosts, typically representing business partners, suppliers, or customers. Hosts must authenticate to join the extranet.

A private network or intranet is a network of trusted hosts owned and controlled by the organization. It should never be Internet-facing.
# 3
There are several types of security zones on a network. Analyze network activities to determine which of the following does NOT represent a security zone.

2.  Screened host

A screened host is when a smaller network accesses the Internet using a dual-homed proxy/gateway servers.

A Demilitarized Zone (DMZ) is a protected but untrusted area (zone) between the Internet and the private network.

Traffic from wireless networks might be less trusted than from a cabled network. If unauthenticated open access points or authenticated guest Wi-Fi networks exist on the network, admin should keep them isolated.

A guest network is a zone that allows untrusted or semi-trusted hosts on the local network. Examples include publicly accessible computers or visitors bringing their own portable computing devices to the premises.
# 4
Evaluate the typical weaknesses found in network architecture and determine which statement best aligns with a perimeter security weakness.

4.  A company has a flat network architecture.

Overdependence on perimeter security occurs when the network architecture is flat. If an attacker can penetrate the network edge, the attacker will then have freedom of movement throughout the entire network.

A single point of failure occurs with a "pinch point" by relying on a single hardware server or appliance or network channel. Complex dependencies are services that require many different systems to be available.

Ideally, the failure of individual systems or services should not affect the overall performance of other network services.

Availability over confidentiality and integrity occurs when a company takes shortcuts to get a service up and running. Compromising security might represent a quick fix but creates long term risks.
# 5
Evaluate the following choices based on their potential to lead to a network breach. Select the choice that is NOT a network architecture weakness.

4.  Not all hosts on the network can talk to one another.

It is good that not all the hosts can talk to each other. If any host can contact another host, an attacker can penetrate the network edge and gain freedom of movement.

A flat architecture is where all hosts can contact each other, exposing an overdependence on perimeter security.

When services rely on several different systems, the failure of one will affect the overall performance of other network services.

Relying on a single hardware server represents a single point of failure, meaning the whole network crashes if the server goes down.
# 6
Identify the attack that can launch by running software such as Dsniff or Ettercap from a computer attached to the same switch as the target.

1.  ARP poisoning attack

An ARP poisoning attack broadcasts unsolicited ARP reply packets. A sophisticated ARP attack can launch by running software such as Dsniff or Ettercap from a computer attached to the same switch as the target.

MAC spoofing changes the MAC address configured on an adapted interface or asserts the use of an arbitrary MAC address. It is simple to override a MAC address in software via OS commands, alterations to the network driver configuration, or using packet crafting software.

MAC flooding is a variation of an ARP poisoning attack and usually directed against a switch.

One way to launch a MitM attack is to use a Trojan to replace some genuine software on the system. These attacks can also launch against antiquated protocols, such as ARP or DNS.
# 7
Given that layer 2 does not recognize Time to Live, evaluate the potential problems to determine which of the following options prevents this issue.

4.  STP

STP (Spanning Tree Protocol) is a switching protocol that prevents network loops by dynamically disabling links as needed. Since layer 2 protocol has no concept of Time To Live, layer 2 broadcast traffic could continue to loop through a network with multiple paths indefinitely.

ICMP (Internet Control Message Protocol) is an IP-level protocol for reporting errors and status information that supports the function of troubleshooting utilities such as ping.

L2TP (Layer 2 Tunneling Protocol) is the standard VPN (Virtual Private Network) protocol for tunneling point-to-point sessions across a variety of network protocols.

NTP (Network Time Protocol) is a Transmission Control Protocol/Internet Protocol (TCP/IP) application protocol allowing machines to synchronize to the same time clock that runs over UDP port 123.
# 8
Analyze the available detection techniques and determine which are useful in identifying a rogue system through software management. **(Select all that apply.)**

3.  Intrusion detection and NAC are security suites and appliances that combine automated network scanning with defense and remediation suites to prevent rogue devices from accessing the network.
4.  Wireless monitoring can reveal whether there are unauthorized access points.

Intrusion detection and NAC are security suites and appliances that can combine automated network scanning with defense and remediation suites to prevent rogue devices from accessing the network.

Wireless monitoring can reveal the presence of unauthorized or malicious access points and stations.

Visual inspection of ports/switches will reveal any obvious unauthorized devices or appliances; however, a sophisticated attack can prevent observation, such as creating fake asset tags.

Network mapping can identify hosts unless an OS is actively trying to remain unobserved by not operating when scans are running. Identifying a rogue host on a large network from a scan may still be difficult.
# 9
An attacker tricks a host within a subnet into routing through an attacker's machine, rather than the legitimate default gateway, allowing the attacker to eavesdrop on communications and perform a Man-in-the-Middle (MitM) attack. Compare the types of routing vulnerabilities and conclude what the attacker is exploiting in this scenario.

3.  ARP poisoning

ARP poisoning occurs by tricking hosts on the subnet into routing through the attacker's machine rather than the legitimate default gateway. This allows the attacker to eavesdrop on communications and perform replay or MitM attacks.

Route injection occurs when routing protocols have weak or no authentication. This can mean traffic misdirected to a monitoring port, sent to a black hole, or continuously looped.

Denial of service is redirecting traffic to routing loops or black holes, or overloading the router.

Source routing uses an option in the IP header to pre-determine the route a packet will take through the network that it must pass through.
# 10
Which statement regarding attacks on media access control (MAC) addresses accurately pairs the method of protection and what type of attack it guards against? **(Select all that apply.)**


2.  Dynamic Host Configuration Protocol (DHCP) snooping guards against MAC spoofing.

4.  DAI guards against invalid MAC addresses

In MAC filtering, a switch will record the specified number of MACs allowed to connect to a port, but then drop any traffic from other MAC addresses.

DHCP snooping inspects traffic arriving on access ports to ensure that a host is not trying to spoof its MAC address.

MAC filtering on a switch defines which MAC addresses are allowed to connect to a particular port, dropping other traffic to protect against MAC flooding attacks.

DAI allows a network administrator to intercept, log, and discard ARP packets with invalid MAC address to IP address bindings.
# 11
Compare the characteristics of a rogue Access Point (AP) in wireless networks to determine which statements correctly summarize their attributes. **(Select all that apply.)**

1.  An evil twin is a rogue AP, and an attacker can use a Denial of Service (DoS) to disconnect users from the legitimate AP and connect to the evil twin.
2.  Sometimes referred to as an evil twin, a rogue AP masquerading as a legitimate AP, may have a similar name to a legitimate AP.
3.  An attacker can set up a rogue AP with something as simple as a smartphone with tethering capabilities.

A rogue AP masquerading as a legitimate one is an evil twin. When users try to reconnect to an AP after being disconnected, user could connect to the evil twin unknowingly.

An attacker can also form evil twins, giving the AP a similar name (SSID) to that of the legitimate AP. Users may select this AP by mistake, and enter their credentials, which the attacker will capture.

Rogue APs can be setup with something as basic as a smartphone with tethering capabilities. It is vital to periodically survey the site to detect rogue APs.

When enabling authentication security on the AP (without the attacker knowing the details of the authentication method), a DoS will not succeed. It is important to scan for rogue APs, but the ease of a DoS is not the reasoning behind the need for regular scans.
# 12
A network manager suspects that a wireless network is undergoing a deauthentication attack. Applying knowledge of wireless network attacks, which scenario best supports the network manager's suspicion?

4.  A group of users suddenly disconnects from the network. When the users reconnect, they actually connect to an evil twin Access Point (AP), which gives an attacker information about authentication.

A deauthentication attack, coupled with the use of a rogue AP, sends a stream of spoofed deauth frames to cause a client to deauthenticate from the AP. This may allow the attacker to interpose the rogue AP or to sniff information about the authentication process.

Jamming occurs when a wireless network experiences interference from other radio sources. An attacker may jam a network to position an evil twin on the network.

An attacker that creates an AP using a similar name as a legitimate AP is creating an evil twin.

A rogue AP is usually coupled with another attack, such as jamming or deauthentication, to obtain critical information.
# 13
A team is building a wireless network, and the company has requested the team to use a Wired Equivalent Privacy (WEP) encryption scheme. The team has developed a recommendation to utilize a different encryption scheme based on the problems with WEP. Analyze the features of WEP to determine what problems to highlight in the recommendation.


2.  WEP allows for a 256-bit key but is still not secure. The Initialization Vector (IV) is not sufficiently large, thus is not always generated using a sufficiently random algorithm.

WEP version 1 has both 64-bit and 128-bit keys, while WEP version 2 has 128-bit and 256-bit keys but is still not secure. The main problem with WEP is the 24-bit Initialization Vector (IV). The IV changes the keystream each time, but this does not always occur due to problems. One of the problems is that the IV is not sufficiently large, meaning the system will reuse the IV within the same keystream under load.

WEP, depending on the version, allows for the use of 64-, 128-, and 256-bit keys, but none of these options are secure. The IV is not large enough, meaning that the system will reuse it, within the same keystream under load.

WEP does have the option to use 64- and 128-bit keys but also allows for 256-bit keys. Packs use a checksum to verify integrity, but that is easy to compute.

WEP allows for 64-, 128-, and 256-bit keys. The IV is often not generated using a sufficiently random algorithm.
# 14
A company is reviewing the options for installing a new wireless network. They have requested recommendations for utilizing WEP, WPA, or WPA2. Differentiate between Wired Equivalent Privacy (WEP) and Wi-Fi Protected Access (WPA). Determine which of the following statements accurately distinguishes between the options. **(Select all that apply.)**


3.  WPA and WEP use RC4, while WEP uses a 24-bit Initialization Vector (IV). WPA uses a Temporal Key Integrity Protocol (TKIP), and WPA2 uses an Advanced Encryption Standard (AES) for encryption.
4.  WPA2 is the strongest encryption scheme, followed by WPA, then WEP. WPA2 is difficult to crack if protected by a strong password, or if deploying enterprise authentication. WEP is more vulnerable to decryption due to replay attack possibilities.


WPA2 uses an Advanced Encryption Standard (AES) for encryption, while WPA and WEP use RC4. WPA combines the RC4 with a Temporal Key Integrity Protocol (TKIP), while WEP uses a 24-bit Initialization Vector (IV).

WPA2 is the strongest encryption scheme due to the use of AES. WPA is stronger than WEP because of the TKIP. WEP uses the 24-bit IV, which has known [[vulnerability|vulnerabilities]] and is the weakest encryption system of the three.

A strong password, or the use of enterprise authentication, makes WPA difficult to crack. WEP is the most vulnerable due to the possibility of replay attacks.

The encryption options have grown stronger with each development, with WEP deploying first, followed by WPA and WPA2.
# 15
A hotel guest opens their computer and logs into the Wi-Fi without prompting the guest for a username and password. Upon opening an internet browser, a splash page appears that requests the guest's room number and last name for authentication. Which type of authentication is the hotel utilizing?

4.  Open

Mostly used on a public access point, open authentication does not require the client to authenticate, as it sends data over the link unencrypted. When combined with a secondary authentication mechanism, a browser can manage open authentication. The secondary authentication redirects the client to a captive portal or a splash page.

Wi-Fi Protected Setup (WPS) requires all of the wireless devices to be WPS capable and use a PIN. This type of authentication is common for residential consumers.

Extensible Authentication Protocol (EAP) supports different types of authentication within the same overall topology of devices. EAP implementations can include smart cards, one-time passwords, and biometric scanning for authentication.

Group authentication uses a pre-shared key that employs a passphrase to generate the key that encrypts communication. The group uses the same secret key.
# 16
An Internet Service Provider's (ISP) customer network is under a Distributed Denial of Service (DDoS) attack. The ISP decides to use a blackhole as a remedy. How does the ISP justify their decision?

1.  A blackhole drops packets for the affected IP address(es) and is in a separate area of the network that does not reach any other part of the network.

A blackhole drops packets for the affected IP addresses(es). A blackhole is an area of the network that cannot reach any other part of the network which protects the unaffected portion.

A blackhole does make the attack less damaging to the other ISP customers but does not send legitimate traffic to the correct destination. The blackhole does not look at packets and simply drops all packets into the black hole.

A sinkhole routing routes traffic to a particular IP address, to a different network, so the ISP can analyze and identify the source of the attack.

A blackhole is preferred, but it does not evaluate each packet. An ACL option will evaluate each packet but can overwhelm the processing resources, which makes using a blackhole preferred.
# 17
Compare the types of Distributed Denial of Service (DDoS) attacks and select the best example of a synchronize (SYN) flood attack.

3.  Client IP addresses are spoofed to misdirect the server's SYN/ACK packet increasing session queues.

An SYN flood attack works by withholding clients’ ACK packets during TCP's three-way handshakes that can increase the server session queues and prevent other legitimate clients from connecting. The server will continue to send SYN/ACK packets because there is no acknowledgment and will not timeout until sometime later.

A coordinated attack occurs when a group of attackers engage together against a well-known company or government institution.

DDoS attacks can be simple and just focus on consuming network bandwidth resulting in the denial of legitimate hosts.

A smurf attack occurs by the adversary spoofing the client's IP address and then pings the broadcast address of a third-party network with many hosts. This is known as amplifying the network.
# 18
During the planning/scoping phase of the kill chain, an attacker decides that a Distributed Denial of Service (DDoS) attack would be the best way to disrupt the target website and remain anonymous. Evaluate the following explanations to determine the reason the attacker chose a DDoS attack.

2.  DDoS attacks utilize botnets


DDoS uses a botnet to launch the attack. Distributed means the attack launches from multiple, compromised computers and devices, which is a botnet. Since the attack will come from multiple IP addresses, it will mask the identity of the attacker.

A covert channel is a means of secretly communicating with a compromised machine. The purpose of a DDoS is to overload the target so it’s unavailable to legitimate users, not to communicate with it.

A backdoor is a mechanism for gaining access to a computer that bypasses the normal method of authentication. DDoS aims to deny service, not gain access.

DDoS attacks do not use impersonation, which is a social engineering technique where one pretends to be someone else.
# 19
Given knowledge of load balancing and clustering techniques, which configuration provides both fault tolerance and consistent performance for applications like streaming audio and video services?

1.  Active/Passive clustering

In active/passive clustering, if the active node suffers a fault, the connection can failover to the passive node, without performance degradation.

In an active/active cluster, both nodes process connections concurrently, using the maximum hardware capacity. During failover, the failed node’s workload shifts to the remaining node, the workload on the remaining nodes increases, and performance degrades.

Most network appliances process packets on a best effort and first in, first out (FIFO) basis, while the Quality of Service (QoS) framework prioritizes traffic based on its characteristics to better support voice and video applications susceptible to latency and jitter.

Failover ensures that a redundant component, device, or application can quickly and efficiently take over the functionality of an asset that has failed.
# 20
Which statement best describes the difference between session affinity and session persistence?


3.  With session affinity, when a client establishes a session, it remains with the node that first accepted its request, while an application-layer load balancer uses persistence to keep a client connected by setting up a cookie.

Session affinity is a layer 4 approach to handling user sessions. When a client establishes a session, it stays with the node that first accepted the request.

Most network appliances process packets on a best effort and FIFO basis. Layer 4 load balancers only make basic connectivity tests, while layer 7 appliances can test the application's state.

An application-layer load balancer uses persistence to keep a client connected to a session. Persistence typically works by setting a cookie, which can be more reliable than session affinity.

Quality of Service (QoS) prioritizes traffic based on its characteristics, like bandwidth requirements for video and voice applications. A round robin is a simple form of scheduling that picks the next node.