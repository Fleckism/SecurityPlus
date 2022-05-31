---
tags: [Implementation,section]
---
# EXAM OBJECTIVES COVERED

2.1 Explain the importance of security concepts in an enterprise environment

3.1 Given a scenario, implement secure protocols

The [[network]] infrastructure of switches, routers, access points, and secure hosts is implemented for the purpose of running services. The application protocols that enable web, email, and VoIP require secure configuration too.
# HYPERTEXT TRANSFER PROTOCOL AND WEB SERVICES

The foundation of web technology is the HyperText Transfer Protocol ([[Hyper Text Transfer ProtocolTTPs]]]]). Hyper Text Transfer ProtocolTTPs]] enables clients (typically web browsers) to request resources from an Hyper Text Transfer ProtocolTTPs]] server. A client connects to the Hyper Text Transfer ProtocolTTPs]] server using an appropriate [[TCP]] port (the default is port 80) and submits a request for a resource, using a uniform resource locator (URL). The server acknowledges the request and responds with the data (or an error message).

The response and request payload formats are defined in an Hyper Text Transfer ProtocolTTPs]] header. The Hyper Text Transfer ProtocolTTPs]] payload is usually used to serve HTML web pages, which are plaintext files with coded tags (HyperText Markup Language) describing how the page should be formatted. A web browser can interpret the tags and display the text and other resources associated with the page, such as binary picture or sound files linked to the HTML page.

Hyper Text Transfer ProtocolTTPs]] also features a forms mechanism (POST) whereby a user can submit data from the client to the server. Hyper Text Transfer ProtocolTTPs]] is nominally a [[stateless protocol]]; this means that the server preserves no information about the client during a session. However, the basic functionality of Hyper Text Transfer ProtocolTTPs]] servers is often extended by support for scripting and programmable features (web applications). Servers can also **set text file cookies to preserve session information.** These coding features, plus integration with databases, **increase flexibility and interactivity, but also increase the attack surface which exposes more vulnerabilities.**

Many argue that Hyper Text Transfer ProtocolTTPs]] is a stateful protocol. Version 2 of Hyper Text Transfer ProtocolTTPs]] adds more state-preserving features ([blog.zamicol.com/2017/05/is-http2-stateful-protocol-application.html](https://blog.zamicol.com/2017/05/is-http2-stateful-protocol-application.html)).
# TRANSPORT LAYER SECURITY 

As with other early [[TCP]]/IP application protocols, Hyper Text Transfer ProtocolTTPs]] communications are not secured. Secure Sockets Layer ([[SSL]]) was developed by Netscape in the 1990s to address the lack of security in Hyper Text Transfer ProtocolTTPs]]. SSL proved very popular with the industry, and it was quickly adopted as a standard named Transport Layer Security ([[TLS]]). It is typically used with Hyper Text Transfer ProtocolTTPs]] (referred to as Hyper Text Transfer ProtocolTTPs]]S or Hyper Text Transfer ProtocolTTPs]] Secure) but can also be used to secure other application protocols and as a virtual private networking (VPN) solution.

To implement TLS, a server is assigned a digital certificate signed by some trusted certificate authority ([[CA]]). The certificate proves the identity of the server (assuming that the client trusts the CA) and validates the server's public/private key pair. The server uses its key pair and the TLS protocol to agree upon mutually supported ciphers with the client and negotiate an encrypted communications session.

Hyper Text Transfer ProtocolTTPs]]S operates over port 443 by default. Hyper Text Transfer ProtocolTTPs]]S operation is indicated by using https:// for the [[URL]] and by a padlock icon shown in the browser.

It is also possible to install a certificate on the client so that the server can trust the client. This is not often used on the web but is a feature of VPNs and enterprise networks that require mutual authentication.

### SSL/TLS Versions 

While the acronym **SSL is still used**, the **Transport Layer Security versions are the only ones that are safe to use**. A server can provide support for legacy clients, but obviously this is less secure. For example, a TLS 1.2 server could be configured to allow clients to downgrade to TLS 1.1 or 1.0 or even SSL 3.0 if they do not support TLS 1.2.

A downgrade [[attack]] is where a man-in-the-middle [[MITM]]tries to force the use of a weak cipher suite and SSL/TLS version.

TLS version 1.3 was approved in 2018. One of the main features of TLS 1.3 is the removal of the ability to perform downgrade attacks by preventing the use of unsecure features and algorithms from previous versions. There are also changes to the handshake protocol to reduce the number of messages and speed up connections. 

### Cipher Suites

A cipher suite is the algorithms supported by both the client and server to perform the different encryption and hashing operations required by the protocol. Prior to TLS 1.3, a cipher suite would be written in the following form:

ECDHE-RSA-AES128-GCM-SHA256

This means that the server can use Elliptic Curve Diffie-Hellman Ephemeral [[ECDHE]] mode for session key agreement, [[RSA]] signatures, 128-bit AES-GCM (Galois Counter Mode) for symmetric bulk encryption, and 256-bit SHA for HMAC functions. Suites the server prefers are listed earlier in its supported cipher list.

TLS 1.3 uses simplified and shortened suites. A typical TLS 1.3 cipher suite appears as follows:

TLS_AES_256_GCM_SHA384

Only ephemeral key agreement is supported in 1.3 and the signature type is supplied in the certificate, so the cipher suite only lists the bulk encryption key strength and mode of operation (AES_256_GCM), plus the cryptographic hash algorithm (SHA384) used within the new hash key derivation function ([[HKDF]]). HKDF is the mechanism by which the shared secret established by Diffie Hellman key agreement is used to derive symmetric session keys.

Viewing the [[TLS]] handshake in a Wireshark packet capture. Note that the connection is using TLS 1.3 and one of the shortened cipher suites (TLS_AES_128_GCM_SHA256).
# API CONSIDERATIONS

Hyper Text Transfer ProtocolTTPs]] is now used less to serve static web pages, and more to create web applications, often as part of a cloud product. An enterprise might use both public web applications over the Internet and private ones. The primary means of configuring and managing a web application is via its application programming interface (API). For example, an application might allow a user account to be created via a [[URL]]:

https://example.foo/api/users?api_key=123456

The developer uses the POST method to submit data to the URL with the required parameters coded into the request body, often in JavaScript Object Notation (JSON).

POST /api/users Hyper Text Transfer ProtocolTTPs]]/1.1

Content-Type: application/json

{

 "user": {

 "name": "James",

 "email": "jpengelly@comptia.org"

 }

}

Use of these APIs is authorized via a token or secret key. Effective management of these API secrets is a key consideration in modern networks, as they have been widely used to perpetrate various breaches and data thefts. For example, putting the key in the URL carries a severe risk of exposure. APIs can use more secure authentication and authorization methods, such as [[SAML]] and [[OAuth]], but these still come with secrets management requirements. Another API consideration is that usage should be monitored to ensure only authorized endpoints are making transactions.
# SUBSCRIPTION SERVICES

Employees may require access to all kinds of subscription services. Some examples include:

-   Market and financial intelligence and information.
-   Security threat intelligence and information.
-   Reference and training materials in various formats (ebook and video, for instance).
-   Software applications and cloud services paid for by subscription rather than permanent licenses.

Most of this sort of content will be delivered by a secure web site or cloud application. It may be necessary to provision authentication mechanisms for enterprise single sign-on ([[SSO]]) access to the services.

Another use of subscriptions is a web feed, where updated articles or news items are pushed to the client or browser. Web feeds are based on either the Really Simple Syndication (RSS) or Atom formats, both of which use XML to mark up each document supplied by the feed. It is possible that such feeds may be vulnerable to XML injection style attacks, allowing an attacker to show malicious links or even interact with the file system ([https://mikeknoop.com/lxml-xxe-exploit](https://mikeknoop.com/lxml-xxe-exploit)). 

Subscription services may also describe the outsourcing of network and security components and procedures. There may also be subscription use of enterprise cloud applications, which may be mediated by an access broker.
# FILE TRANSFER SERVICES

There are many means of transferring files across networks. A network operating system can host shared folders and files, enabling them to be copied or accessed over the local network or via remote access (over a VPN, for instance). Email and messaging apps can send files as attachments. Hyper Text Transfer ProtocolTTPs]] supports file download (and uploads via various scripting mechanisms). There are also peer-to-peer file sharing services. Despite the [[My linked notes/Dictionary/Availability]] of these newer protocols and services, the file transfer protocol (FTP) remains very popular because it is efficient and has wide cross-platform support.

### File Transfer Protocol 

A File Transfer Protocol ([[FTP]]) server is typically configured with several public directories, hosting files, and user accounts. Most Hyper Text Transfer ProtocolTTPs]] servers also function as FTP servers, and FTP services, accounts, and directories may be installed and enabled by default when you install a web server. FTP is more efficient compared to file attachments or Hyper Text Transfer ProtocolTTPs]] file transfer, but has no security mechanisms. All authentication and data transfer are communicated as plaintext, meaning that credentials can easily be picked out of any intercepted FTP traffic.

You should check that users do not install unauthorized servers on their PCs (a rogue server). For example, a version of IIS that includes Hyper Text Transfer ProtocolTTPs]], FTP, and SMTP servers is shipped with client versions of Windows, though it is not installed by default.

### SSH FTP (SFTP) and FTP Over SSL (FTPS)

SSH FTP ([[SFTP]]) addresses the privacy and integrity issues of FTP by encrypting the authentication and data transfer between client and server. In SFTP, a secure link is created between the client and server using Secure Shell (SSH) over TCP port 22. Ordinary FTP commands and data transfer can then be sent over the secure link without risk of eavesdropping or man-in-the-middle attacks. This solution requires an SSH server that supports SFTP and SFTP client software.

Another means of securing FTP is to use the connection security protocol SSL/TLS. There are two means of doing this:

-   Explicit TLS (FTPES)—use the AUTH TLS command to upgrade an unsecure connection established over port 21 to a secure one. This protects authentication credentials. The data connection for the actual file transfers can also be encrypted (using the PROT command).
-   Implicit TLS (FTPS)—negotiate an SSL/TLS tunnel before the exchange of any FTP commands. This mode uses the secure port 990 for the control connection.

FTPS is tricky to configure when there are firewalls between the client and server. Consequently, FTPES is usually the preferred method.
# EMAIL SERVICES

Email services use two types of protocols:

-   The Simple Mail Transfer Protocol (SMTP) transmits email messages from one system to another.
-   The Post Office Protocol v3 (POP3) receives email messages from an email server to store on a client computer.

### Secure SMTP (SMTPS)

A sender’s SMTP server discovers the IP address of the recipient’s SMTP server using the domain name of the recipient’s email address. The SMTP server for the domain is registered in [[DNS]] using a Mail Exchanger (MX) record.

SMTP communications can be secured using TLS. This works much like Hyper Text Transfer ProtocolTTPs]]S with a certificate on the SMTP server. There are two ways for SMTP to use TLS:

-   STARTTLS—this is a command that upgrades an existing unsecure connection to use TLS. This is also referred to as explicit TLS or opportunistic TLS.
-   SMTPS—this establishes the secure connection before any SMTP commands (HELO, for instance) are exchanged. This is also referred to as implicit TLS.

The STARTTLS method is generally more widely implemented than [[SMTPS]]. Typical SMTP configurations use the following ports and secure services:

-   Port 25—used for message relay (between SMTP servers or Message Transfer Agents [MTA]). If security is required and supported by both servers, the STARTTLS command can be used to set up the secure connection.
-   Port 587—used by mail clients (Message Submission Agents [MSA]) to submit messages for delivery by an SMTP server. Servers configured to support port 587 should use STARTTLS and require authentication before message submission.
-   Port 465—some providers and mail clients use this port for message submission over implicit TLS (SMTPS), though this usage is now deprecated by standards documentation. 

### Secure POP (POP3S)

When a recipient’s email client connects to a server mailbox, POP3 downloads the email messages.

![Screenshot of script used to configure mailbox protocols.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3288-1599771805475.png)

Configuring mailbox access protocols on a server.

A POP3 client application, such as Microsoft Outlook or Mozilla Thunderbird, establishes a TCP connection to the POP3 server over port 110. The user is authenticated (by username and password) and the contents of his or her mailbox are downloaded for processing on the local PC. POP3S is the secured version of the protocol, operating over TCP port 995 by default.

### Secure IMAP (IMAPS)

Compared to POP3, the Internet Message Access Protocol v4 (IMAP4) supports permanent connections to a server and connecting multiple clients to the same mailbox simultaneously. It also allows a client to manage mail folders on the server. Clients connect to [[IMAP]] over TCP port 143. They authenticate themselves then retrieve messages from the designated folders. As with other email protocols, the connection can be secured by establishing an SSL/TLS tunnel. The default port for IMAPS is TCP port 993.
# SECURE/MULTIPURPOSE INTERNET MAIL EXTENSIONS 

Connection security goes a long way toward preventing the compromise of email accounts and the spoofing of email, but end-to-end encryption cannot usually be guaranteed. Consequently, there is still a need for **authentication and confidentiality** to be applied on a per-message basis. One means of doing this is called Secure/Multipurpose Internet Mail Extensions (S/MIME). To use S/MIME, the user is issued a digital certificate containing his or her public key, signed by a CA to establish its validity. The public key is a pair with a private key kept secret by the user. To establish the exchange of secure emails, both users must be using S/MIME and exchange certificates:

1.  Alice sends Bob her digital certificate, containing her public key and validated digital ID (an email address). She signs this message using her private key.
2.  Bob uses the public key in the certificate to decode her signature and the signature of the CA (or chain of CAs) validating her digital certificate and digital ID and decides that he can trust Alice and her email address.
3.  He responds with his digital certificate and public key and Alice, following the same process, decides to trust Bob.
4.  Both Alice and Bob now have one another's certificates in their trusted certificate stores.
5.  When Alice wants to send Bob a confidential message, she makes a hash of the message and signs the hash using her private key. She then encrypts the message, hash, and her public key using Bob's public key and sends a message to Bob with this data as an S/MIME attachment.
6.  Bob receives the message and decrypts the attachment using his private key. He validates the signature and the integrity of the message by decrypting it with Alice's public key and comparing her hash value with one he makes himself.
# VOICE AND VIDEO SERVICES 

Voice over IP (VoIP), web conferencing, and video teleconferencing (VTC) solutions have become standard methods for the provision of business communications. The main challenges that these applications have in common is that they transfer real-time data and must create point-to-point links between hosts on different networks. 

Implementing Internet telephony and video conferencing brings its own raft of security concerns.[[ Each part of the communications media network infrastructure needs to be evaluated for threats and vulnerabilities.]] This includes protocols, servers, handsets, and software. The **protocols** designed to support real-time services cover one or more of the following functions: 

-   **Session control**—used to setup and manage communications sessions. They handle tasks such as user discovery (locating a user on the network), [[My linked notes/Dictionary/Availability]] advertising (whether a user is prepared to receive calls), negotiating session parameters (such as use of audio/video), and session management and termination. 
-   **Data transport**—handles the delivery of the actual video or voice information.
-   **Quality of Service** (QoS)—provides information about the connection to a QoS system, which in turn ensures that voice or video communications are free from problems such as dropped packets, delay, or jitter. 

The Session Initiation Protocol ([[SIP]]) is one of the most widely used session control protocols. SIP endpoints are the end-user devices (also known as user-agents), such as IP-enabled handsets or client and server web conference software. Each device, conference, or telephony user is assigned a unique SIP address known as a SIP Uniform Resource Indicator (URI), such as sip:bob.dobbs@comptia.org

[[SIP]] endpoints can establish communications directly in a peer-to-peer architecture #A_D, but it is more typical to use intermediary servers and directory servers. A SIP network may also use gateways and private branch exchange (PBX) appliances to provide an interface between the VoIP network and external telephone and cellular networks.

While SIP provides session management features, the actual delivery of real-time data uses different protocols. The principal one is Real-time Transport Protocol ([[RTP]]). 

A [[threat actor]] could exploit unencrypted voice and video communications to try to intercept passwords, credit card details, and so on. Without strong mutual authentication, connections are also vulnerable to man-in-the-middle attacks.

![A dialog box labeled “Account Advanced Settings” has a setting “SIP transport: TLS” that is highlighted by a red box added to the image.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3228-1599771805552.png)

Enabling SIP/[[TLS]] security on a 3CX PBX VoIP softphone. (Screenshot used with permission from 3CX.)

Connection security for voice and video works in a similar manner to [[Hyper Text Transfer ProtocolTTPs]]S]]. To initiate the call, the secure version SIPS uses digital certificates to authenticate the endpoints and establish a [[TLS]] tunnel. Where unencrypted SIP typically runs over TCP port 5060, SIPS uses TCP port 5061. The secure connection established by SIPS can also be used to generate a master key to use with the secure versions of the transport protocol ([[SRTP]]). SRTP provides confidentiality for the actual call data.

![Service Node Manager screen for Media Encryption has all items checked: enable media encryption for IP Extensions, IP Trunks, and Inter Media Gateway.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2858-1599771805640.png)

Enforcing RTP protocol encryption on a Mitel PBX system. (Screenshot used with permission from Mitel.)
