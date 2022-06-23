# 1
A system administrator is configuring a new Dynamic Host Configuration Protocol (DHCP) server. Analyze the types of attacks DHCP servers are prone to and determine which steps the system administrator should take to protect the server. **(Select all that apply.)**

1.  Use scanning and intrusion detection to pick up suspicious activity.
2.  
3.  Enable logging and review the logs for suspicious events.
4.  Disable unused ports and perform regular physical inspections to look for unauthorized devices.

Solution

The system administrator should use scanning and intrusion detection to pick up suspicious activity.

The system administrator should set logging to be enabled and then review the logs regularly for suspicious events.

The system administrator should disable unused ports and perform regular physical inspections to ensure that unauthorized devices are not connected via unused jacks.

The system administrator should enable DHCP snooping on switch access ports to prevent the use of unauthorized DHCP servers. DHCP snooping acts as a firewall between the server and untrusted hosts and should be enabled versus disabled.

# 2
A system administrator needs secure remote access into a Linux server. Evaluate the types of remote administration to recommend which protocol should be used in this situation.


2.  Secure Shell (SSH)


Solution

Secure Shell (SSH) is the principal means of obtaining secure remote access to a UNIX or Linux server. The main uses of SSH are for remote administration and secure file transfer (SFTP).

Telnet is a terminal emulation software used to support a remote connection to another computer. It does not support file transfer directly, and is not secure.

Remote Desktop Protocol (RDP) is Microsoft's protocol for operating remote connections to a Windows machine.

SSH uses Kerberos to allow authentication to the SSH server. Kerberos uses the Ticket Granting Ticket (TGT) method.
# 3
A security engineer encrypted traffic between a client and a server. Which security protocol does the engineer configure if an ephemeral key agreement is used?


3.  TLS 1.3

Solution

Only ephemeral key agreement is supported in TLS 1.3. The signature type is supplied in the certificate, so the cipher suite only lists the bulk encryption key strength and mode of operation (AES_256_GCM), plus the cryptographic hash algorithm (SHA384).

Prior to TLS 1.3, Elliptic Curve Diffie-Hellman Ephemeral mode for session key agreement, RSA signatures, 128-bit AES-GCM (Galois Counter Mode) for symmetric bulk encryption, and 256-bit SHA for HMAC functions can be used.

AES 256 refers to a mode of operation used by TLS to encrypt data that is communicated between systems.

SHA 384 refers to a cryptographic hashing algorithm that is used for encryption by protocols such as TLS.

# 4
An attacker modifies the HOSTS file on a workstation to redirect traffic. Consider the types of attacks and deduce which type of attack has likely occurred.


3.  DNS client cache poisoning

Solution

The HOSTS file is checked before using Domain Name System (DNS). Its contents are loaded into a cache of known names and the client only contacts a DNS server if the name is not cached. If an attacker can place a false name, then the attacker will be able to direct traffic.

A DNS server cache poisoning attack is a redirection attack that aims to corrupt the records held by the DNS server itself.

DNS spoofing is an attack that compromises the name resolution process.

Typosquatting means that the threat actor registers a domain name that is very similar to a real one, such as connptia.org, hoping that users will not notice the difference.
# 5
Analyze the methods for authentication to a Secure Shell (SSH) and determine which statement best summarizes the host-based authentication method.

4.  The client sends a request for authentication and the server generates a challenge with the public key.

Solution

In host-based authentication, the server is configured with a list of authorized client public keys. The client requests authentication using one of these keys and the server generates a challenge with the public key.

The public key authentication method uses the user's private key that is configured with a passphrase that the user must input to access the key.

The username and password method require the client to submit credentials that the SSH server verifies against a local user database.

The Kerberos method requires the client to submit the Kerberos credentials (TGT) that are obtained when the user logged onto the workstation.
# 6
A system administrator is setting up a new Simple Mail Transfer Protocol (SMTP) configuration. Make recommendations for how the administrator should configure the ports. **(Select all that apply.)**

3.  Port 25 should be used for message relay.
4.  Port 465 should be used for message submission over implicit TLS.

Solution

Port 25 is used for message relay between Simple Mail Transfer Protocol (SMTP) servers or Message Transfer Agents (MTA). If security is required and supported by both servers, the STARTTLS command can be used to set up the secure connection.

Port 465 is used by providers and mail clients for message submission over implicit Transport Layer Security (TLS).

Port 587, versus 110, is used by mail clients (Message Submission Agents) to submit messages for delivery by an SMTP server.

Port 143 is used by Internet Message Access Protocol (IMAP) to connect clients. IMAP supports permanent connections to a server and connecting multiple clients to the same mailbox simultaneously.
# 7
If an administrator in an exchange server needs to send digitally signed and encrypted messages, what messaging implementation will best suit the administrator’s needs?

1.  Secure/Multipurpose Internet Mail Extensions (S/MIME)

Solution

One means of applying authentication and confidentiality on a per-message basis is an email encryption standard called Secure/Multipurpose Internet Mail Extensions (S/MIME). S/MIME adds digital signatures and public key cryptography to mail communications. To use S/MIME, a sender and receiver exchange digital certificates signed by a certification authority (CA).

POP3 is a mailbox protocol designed to store the messages delivered by SMTP on a server. When the client connects to the mailbox, POP3 downloads the messages to the recipient's email client.

IMAP4 is an application protocol that allows a client to access and manage email messages stored in a mailbox on a remote server.

SMTP is the basic protocol used to send mail between hosts on the Internet.
# 8
A system administrator needs to implement a secure remote administration protocol and would like more information on Telnet. Evaluate and select the features of Telnet that the administrator should consider to accomplish this task. **(Select all that apply.)**

1.  Telnet does not support direct file transfer.
2.  Telnet uses TCP port 23.


Solution

Telnet is a terminal emulation software used to support a remote connection to another computer. It does not support file transfer directly, but when connected to the computer, it acts as if the keyboard is attached to the remote computer so the same commands can be used as a local user.

Telnet uses TCP port 23 by default.

Telnet is not secure. Telnet daemon software has exploitable vulnerabilities.

Telnet communications, including passwords, are sent in cleartext. One option is to ensure Telnet is only used over a secure channel, such as an IPSec tunnel.
# 9
An organization routinely communicates directly to a partner company via a domain name. The domain name now leads to a fraudulent site for all users. Systems administrators find incorrect host records in DNS. What do the administrators believe to be the root cause?

3.  An attacker masquerades as an authoritative name server.


Solution

DNS server cache poisoning aims to corrupt the records held by the DNS server itself. A DNS server queries an authoritative server for domain information. An attacker can masquerade as an authoritative name server and respond with fraudulent information.

An ARP cache contains entries that map IP addresses to MAC addresses. An ARP cache is not related to name resolution.

Before developers created DNS, early name resolution took place using a text file named HOSTS. In this case, all users are experiencing an issue, not just some.

Domain Reputation can be impacted if an attacker hijacks public servers. In this case, systems admin found invalid host records, which ruled out hijacking.
# 10
An authoritative server for a zone creates an RRset signed with a Zone Signing Key. Another server requests a secure record exchange and the authoritative server returns the package along with the public key. Evaluate the scenario to determine what the authoritative server is demonstrating in this situation.


2.  DNS Security Extension


Solution

A DNS Security Extension (DNSSEC) transaction is being simulated. This consists of the authoritative server for the zone creating a package of resource records (RRset) signed with a private key (Zone Signing Key). When another server requests a secure record exchange, the authoritative server returns the package along with its public key, which can verify the signature.

DNS is a system for resolving host names and domain labels to IP addresses.

DNS footprinting means obtaining information about a private network by using its DNS server to perform a zone transfer (all of the records in a domain) to a rogue DNS.

DHCP provides for an automatic method for network address allocation.
# 11
A system administrator uses a Graphical User Interface (GUI) remote administration tool over TCP port 3389 to manage a server operating Windows 2016. Evaluate the types of remote administration tools to conclude which protocol the administrator is using.

4.  Remote Desktop

Solution

Remote Desktop Protocol (RDP) is Microsoft's protocol for operating remote connections to a Windows machine. RDP uses TCP port 3389.

Secure Shell (SSH) is the principal means of obtaining secure remote access to a UNIX or Linux server.

Telnet is terminal emulation software to support a remote connection to another computer and uses TCP port 23 by default. Telnet is not secure but can be used over a secure channel, such as an IPSec tunnel.

The Dynamic Host Configuration Protocol (DHCP) provides an automatic method for network address allocation
# 12
A technician is configuring Internet Protocol Security (IPSec) for communications over a Virtual Private Network (VPN). Evaluate the features of available modes and recommend the best option for implementation.

1.  Tunnel mode because the whole IP packet is encrypted, and a new IP header is added.

Solution

The technician should use tunnel mode because the whole IP packet, including header and payload, is encrypted and a new IP header added. This mode is used for communications across an unsecure network (creating a VPN).

In transport mode, the IP header for each packet is not encrypted, just the data (payload). This mode is used for secure communications on a private network (an end-to-end implementation).

In tunnel mode, the header and the payload are encrypted.

In transport mode, the payload is encrypted but this does not provide sufficient security for a VPN.
# 13
A system administrator is deploying a new web server. Which hardening procedures should the administrator consider? **(Select all that apply.)**

1.  The administrator should use SFTP to transfer files to and from the server remotely.

3.  The administrator should assign a digital certificate and enable the use of TLS 1.3.


Solution

Secure file transfer protocol (SFTP) safely transfers files remotely via SSH.

Transport layer security (TLS) enables secure communication between the client and the web server. This is implemented by assigning a certificate to the web server. TLS 1.3 prevents downgrade attacks.

Most web servers must allow for secure access to guest web access. Guest web access should only be allowed to view content in the website and not from any other web server directory.

Web servers should deploy using configuration templates where possible.
# 14


Question

When a company attempts to re-register their domain name, they find that an attacker has supplied false credentials to the domain registrar and redirected their host records to a different IP address. What type of attack has occurred?

1.  Domain hijacking

Solution

In domain hijacking (or brandjacking), the attacker steals a domain name by altering its registration information and then transferring the domain name to another entity.

Before DNS, a text file named HOSTS recorded name:IP address mapping, which most operating systems still check before using DNS. If an attacker can place a false name:IP address mapping in the HOSTS file, poisoning the DNS cache, the attacker can redirect traffic.

The Dynamic Host Configuration Protocol (DHCP) facilitates automatic network address allocation. If an attacker establishes a rogue DHCP, it can perform DoS or snoop on network information.

DNS server cache poisoning corrupts records within the DNS server itself.
# 15


Question

Transport layer security (TLS) version 1.3 improves upon a vulnerability in TLS1.2. Which statement correctly describes a remedy for this vulnerability?


2.  TLS version 1.3 removes the ability to downgrade to weaker encryption ciphers and earlier versions of transport layer security.


Solution

TLS 1.3 removes the ability to perform downgrade attacks by preventing the use of unsecure features and algorithms from previous versions.

Configuring a TLS 1.2 server allows clients to downgrade to TLS 1.1 or 1.0 or SSL 3.0 if they do not support TLS 1.2. A man-in-the-middle can use a downgrade attack to try to force the use of a weak cipher suite and secure sockets layer (SSL)/TLS version.

Secure shell file transfer protocol (SFTP) addresses the privacy and integrity issues of FTP by encrypting the authentication and data transfer between client and server.

The Open Authorization (OAuth) protocol is a standard for federated identity management to consider for secure application programming interfaces (APIs), not a TLS1.3 feature.
