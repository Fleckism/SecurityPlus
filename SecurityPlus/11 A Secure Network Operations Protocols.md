---
tags: [Implementation, OIR, ,section]
#Attack
---
# ## 

LESSON INTRODUCTION

When hosts join a network, they need to be [[configured]] with the appropriate settings for that network. The services that provide these settings, such as [[DHCP]] and [[DNS]], must be deployed securely. When hosts access data using server applications, such as web/Hyper Text Transfer ProtocolTTPs]], email, and VoIP, the communications between clients and servers must be managed using secure versions of the application [[protocols]]. You will also need to configure secure protocols that allow users to access networks, host desktops, and appliance configuration interfaces remotely. 

## 

LESSON OBJECTIVES

In this lesson, you will:

-   Implement secure network operations protocols.
-   Implement secure application protocols.
-   Implement secure remote access protocols.
# EXAM OBJECTIVES COVERED

1.4 Given a scenario, analyze #Ops potential indicators associated with network attacks

3.1 Given a scenario, implement secure protocols

Unsecure protocols can be exploited by attackers to compromise data security and systems integrity. In this topic, you will examine some of the protocols and services providing addressing, name resolution, directory services, time synchronization, and monitoring services for network hosts. These network operations protocols might not be as visible as applications such as web and email servers, but they are critical to secure network infrastructure.
# NETWORK ADDRESS ALLOCATION 

Most networks use a mixture of static and dynamic address allocation. **Interface addresses for routers, firewalls, and some types of servers are best assigned and managed manually (aka static?)**. Other server services and client workstations can be assigned dynamic IP configurations and accessed using name resolution.

The Dynamic Host Configuration Protocol ([[DHCP]]) provides an automatic method for network address allocation. The key point about DHCP is that only **one server** should be offering addresses to any one group of hosts. If a **rogue DHCP server** is set up, it can perform [[DoS]] (as client machines will obtain an incorrect [[TCP_IP]] configuration) or be used to snoop network information. **DHCP starvation is a type of DoS attack where a rogue client repeatedly requests new IP addresses using spoofed MAC addresses, with the aim of exhausting the IP address pool.** This makes it more likely that clients seeking an address lease will use the rogue DHCP server.

Enabling the DHCP snooping port security feature on a switch can mitigate rogue DHCP attacks. Windows DHCP servers in an [[AD]] environment automatically log any traffic detected from unauthorized DHCP servers. **More generally, administration of the DHCP server itself must be carefully controlled and the settings checked regularly.** If an attacker compromises the DHCP server, he or she could point network clients to rogue [[DNS]] servers and use that as a means to direct users to [[spoofed]] websites. Another attack is to **redirect traffic through the attacker's machine by changing the default gateway**, enabling the attacker to snoop on all network traffic.

![KALI desktop showing rogue DHCP running in one pane, dnsspoof in another, and pig.py script performing a DHCP pool exhaustion attack in the third.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4085-1599771805256.png)

Attacking network address allocation—a script exhausts the DHCP pool while another runs a rogue [[DHCP]] server. A third tool operates a rogue [[DNS]] to supply spoofed information to clients configured to use the attack machine as a DNS server, via the rogue DHCP configuration.
# DOMAIN NAME RESOLUTION

The Domain Name System ([[DNS]]) resolves fully qualified domain names ([[FQDNs]]) to IP addresses. It uses a distributed database system that contains information on domains and hosts within those domains. The information is distributed among many name servers, each of which holds part of the database. The name servers work over [[port]] 53. Domain name resolution is a security-critical service and the target of many attacks on both local network and the Internet. 

### Domain Hijacking 

Domain hijacking is an [[attack]] where an adversary acquires a domain for a company's trading name or trademark, or perhaps some spelling variation thereof. While there are often trademark and intellectual property laws against doing this, companies need to be careful to renew domain names that they want to continue to use and to protect the credentials used to manage the registration. A domain name must be re-registered every year at minimum.

In a domain hijacking attack an adversary gains control over the registration of a domain name, allowing the host records to be configured to IP addresses of the attacker's choosing. This might be accomplished by supplying false credentials to the domain registrar when applying for a new domain name or re-registering an existing one. An attacker might also be able to exploit the legitimate account used to manage the domain (via a weak password or malware installed on a client computer) or even to compromise the domain registrar's security procedures in some way ([upguard.com/blog/domain-hijacking](https://www.upguard.com/blog/domain-hijacking)).

A company whose domain has been hijacked is likely to find that they are locked out of the registrar's management console, or that the domain has been transferred to another registrar, often operating in a different country. The whois command can be used to lookup domain registration information to try to detect misuse in other cases.

### Uniform Resource Locator (URL) Redirection

A uniform resource locator ([[URL]]) is an address for the pages and files published on websites. A URL comprises a FQDN, file path, and often script parameters. URL redirection refers to the use of [[Hyper Text Transfer ProtocolTTPs]]]] redirects to open a page other than the one the user requested. This is often used for legitimate purposes—to send the user to a login page or to send a mobile device browser to a responsive version of the site, for instance. If the redirect is not properly validated by the web application, an attacker can craft a phishing link that might appear legitimate to a naïve user, such as:

https://trusted.foo/login.php?url="https://tru5ted.foo"

A [[threat actor]] could also compromise a web server and add redirects in .htaccess files. A redirect could also be inserted as JavaScript, either through compromising the server or by uploading a script via a poorly validated form.

### Domain Reputation

If your domain, website, or email servers have been hijacked, they are likely to be used for spam or distributing malware. This will lead to complaints and the likelihood of the domain being listed on a block list. You should set up monitoring using a site such as [talosintelligence.com/reputation_center](https://talosintelligence.com/reputation_center) to detect misuse early.
# DNS POISONING 

[[DNS]] poisoning is an [[attack]] that compromises the process by which clients query name servers to locate the IP address for a [[FQDN]]. There are several ways that a DNS poisoning attack can be perpetrated.

### Man in the Middle
[[MITM]]
If the [[[[threat actor]]]] has access to the same local network as the victim, the attacker can use [[ARP]] poisoning to impersonate a legitimate [[DNS]] server and respond to DNS queries from the victim with spoofed replies. This might be combined with a denial of service attack on the victim's legitimate DNS server. A rogue [[DHCP]] could be used to configure clients with the address of a rogue DNS resolver.

### DNS Client Cache Poisoning

Before DNS was developed in the 1980s, name resolution took place using a text file named HOSTS. Each name:IP address mapping was recorded in this file and system administrators had to download the latest copy and install it on each Internet client or server manually. **Even though all name resolution now functions through DNS, the HOSTS file is still present and most operating systems check the file before using DNS**. Its contents are loaded into a cache of known name:IP mappings and the client only contacts a DNS server if the name is not cached. Therefore, if an attacker is able to place a false name:IP address mapping in the HOSTS file and effectively poison the [[DNS]] cache, he or she will be able to redirect traffic. The HOSTS file requires administrator access to modify. In UNIX and Linux systems it is stored as /etc/hosts, while in Windows it is placed in %SystemRoot%\System32\Drivers\etc\hosts.

### DNS Server Cache Poisoning

DNS server cache poisoning aims to corrupt the records held by the DNS server itself. This can be accomplished by performing [[DoS]] against the server that holds the authorized records for the domain, and then **spoofing replies** to requests from other [[DNS|name]] servers. Another attack involves getting the victim name server to respond to a recursive query from the attacking host. A recursive query compels the DNS server to query the authoritative server for the answer on behalf of the client. The attacker's DNS, masquerading as the authoritative name server, responds with the answer to the query, but also includes a lot of false domain:IP mappings for other domains that the victim DNS accepts as genuine. The nslookup or dig tool can be used to query the name records and cached records held by a server to discover whether any false records have been inserted.
# DNS SECURITY

DNS is a critical service that should be configured to be fault tolerant. **DoS attacks are hard to perform against the servers that perform Internet name resolution**, but if an attacker can target the DNS server on a private network, it is possible to seriously disrupt the operation of that network.

To ensure DNS security on a private network, local DNS servers should only accept recursive queries from local hosts (preferably authenticated local hosts) and **not from the Internet**. You also need to implement access control measures on the server, to prevent a malicious user from altering records manually. Similarly, clients should be restricted to using authorized resolvers to perform name resolution.

Attacks on DNS may also target the server application and/or configuration. Many DNS services run on [[BIND]] (Berkeley Internet Name Domain), distributed by the Internet Software Consortium ([isc.org](https://www.isc.org/)). There are known vulnerabilities in many versions of the BIND server, so it is critical to patch the server to the latest version. The same general advice applies to other DNS server software, such as Microsoft's. Obtain and check security announcements and then test and apply critical and security-related patches and upgrades.

[[DNS footprinting]] means obtaining information about a private network by using its DNS server to perform a zone transfer (all the records in a domain) to a rogue DNS or simply by querying the DNS service, using a tool such as nslookup or dig. To prevent this, you can apply an Access Control List ([[ACL]]) to prevent zone transfers to unauthorized hosts or domains, to prevent an external server from obtaining information about the private network architecture #A_D.

[[DNS]] Security Extensions ([[DNSSEC]]) help to **[[mitigate]] against spoofing and poisoning attacks by providing a validation process for DNS responses**. With DNSSEC enabled, the authoritative server for the zone creates a "package" of resource records (called an [[RRset]]) signed with a private key (the Zone Signing Key). When another server requests a secure record exchange, the authoritative server returns the package along with its public key, which can be used to verify the signature.

The public zone signing key is itself signed with a separate Key Signing Key. Separate keys are used so that if there is some sort of compromise of the zone signing key, the domain can continue to operate securely by revoking the compromised key and issuing a new one.

![Screen shows Forward Lookup Zones for classroom.local as a list with Name, Type, Data, Timestamp. One entry includes win2016dc, RR Signature (RRSIG).](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2201-1599771805348.png)

Windows Server DNS services with DNSSEC enabled. (Screenshot used with permission from Microsoft.)

The Key Signing Key for a particular domain is validated by the parent domain or host ISP. The top-level domain trusts are validated by the Regional Internet Registries and the DNS root servers are self-validated, using a type of [[M-of-N]] control group key signing. This establishes a chain of trust from the root servers down to any particular subdomain.
# SECURE DIRECTORY SERVICES 

A [[network directory]] lists the subjects (principally users, computers, and services) and objects (such as directories and files) available on the network plus the permissions that subjects have over objects. A network directory facilitates authentication and authorization, and it is critical that it be maintained as a highly secure service. Most directory services are based on the Lightweight Directory Access Protocol ([[LDAP]]), running over [[port]] 389. The basic protocol provides no security and all transmissions are in plaintext, making it vulnerable to sniffing and man-in-the-middle attacks([[MITM]]). Authentication (referred to as **binding to the server**) can be implemented in the following ways:

-   **No authentication**—anonymous access is granted to the directory.
-   **Simple bind**—the client must supply its distinguished name ([[DN]]) and password, but these are passed as **plaintext**.
-   **Simple Authentication and Security Layer** ([[SASL]])—the client and server negotiate the use of a supported authentication mechanism, such as Kerberos. The STARTTLS command can be used to require encryption (sealing) and message integrity (signing). This is the preferred mechanism for Microsoft's Active Directory ([[AD]]) implementation of LDAP.
-   LDAP Secure ([[LDAPS]])—the server is installed with a digital certificate, which it uses to set up a secure tunnel for the user credential exchange. LDAPS uses [[port]] 636.

If secure access is required, anonymous and simple authentication access methods should be disabled on the server.

Generally two levels of access will need to be granted on the directory: **read-only access (query)** and **read/write access (update)**. This is implemented using an access control policy, but the precise mechanism is vendor-specific and not specified by the LDAP standards documentation.

Unless hosting a public service, the [[LDAP]] directory server should also only be accessible from the private network. This means that the **LDAP port should be blocked by a firewall** from access over the public interface. If there is integration with other services over the Internet, ideally only authorized IPs should be permitted.
# TIME SYNCHRONIZATION

Many applications on networks are time dependent and time critical. These include authentication and security mechanisms, scheduling applications, and backup software. The Network Time Protocol ([[NTP]]) provides a transport over which to synchronize these time dependent applications. NTP works over [[UDP]] on [[port]] 123.

Top-level NTP servers (stratum 1) obtain the Coordinated Universal Time ([[UTC]]) from a highly accurate clock source, such as an atomic clock. Lower tier servers then obtain the UTC from multiple stratum 1 servers and sample the results to obtain an authoritative time. Most organizations will use a stratum 2 server to obtain the time for use on the LAN. Servers at lower tiers may then perform the same sort of sampling operation, adjust for the delay involved in propagating the signal, and provide the time to clients. Clients themselves usually obtain the time using a modified form of the protocol (Simple NTP).

NTP has historically lacked any sort of security mechanism, but there are moves to create a security extension for the protocol called Network Time Security ([blog.cloudflare.com/secure-time](https://blog.cloudflare.com/secure-time/)).
# SIMPLE NETWORK MANAGEMENT PROTOCOL SECURITY

The Simple Network Management Protocol ([[SNMP]]) is a widely used framework for management and monitoring. SNMP consists of an SNMP monitor and agents.

-   The agent is a process (software or firmware) running on a [[switch, router, server]], or other SNMP-compatible network device.
-   This agent maintains a database called a management information base ([[MIB]]) that holds statistics relating to the activity of the device (for example, the number of frames per second handled by a switch). The agent is also capable of initiating a trap operation where it informs the management system of a notable event (port failure, for instance). The threshold for triggering traps can be set for each value. Device queries take place over port 161 ([[UDP]]); traps are communicated over port 162 (also UDP).
-   The SNMP monitor (a software program) provides a location from which network activity can be overseen. It monitors all agents by polling them at regular intervals for information from their MIBs and displays the information for review. It also displays any trap operations as alerts for the network administrator to assess and act upon as necessary.

If SNMP is not used, you should remember to change the default configuration password and disable it on any SNMP-capable devices that you add to the network. If you are running SNMP v1 or v2c, keep to the following guidelines:

-   SNMP community names are sent in plaintext and so should not be transmitted over the network if there is any risk that they could be intercepted.
-   Use difficult-to-guess community names; never leave the community name blank or set to the default.
-   Use Access Control Lists to restrict management operations to known hosts (that is, restrict to one or two host IP addresses).
-   SNMP v3 supports encryption and strong user-based authentication. Instead of community names, the agent is configured with a list of usernames and access permissions. When authentication is required, the SNMP message is signed with a hash of the user's passphrase. The agent can verify the signature and authenticate the user using its own record of the passphrase.
