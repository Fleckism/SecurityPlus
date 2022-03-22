---
tags: [Implement, A_D]
---
# EXAM OBJECTIVES COVERED

3.1 Given a scenario, implement secure protocols

3.3 Given a scenario, implement secure network designs

4.1 Given a scenario, use the appropriate tool to assess organizational security (SSH only)

With today's mobile workforce, most networks have to support connections by remote employees, contractors, and customers to their network resources. These remote connections often make use of untrusted public networks, such as the Internet. Consequently, understanding how to implement secure remote access protocols will be a major part of your job as an information security professional.

There are also many cases where a user needs to remotely access an individual host. This is most commonly implemented to allow administrators to perform remote management of workstations, servers, and network appliances, but it can also be used to provide ordinary users access to a desktop as well.
# REMOTE ACCESS ARCHITECTURE 

Remote access means that the user's device does not make a direct cabled or wireless connection to the network. The connection occurs over or through an **intermediate network**. Historically, remote access might have used analog modems connecting over the telephone system or possibly a private link (a leased line). These days, most remote access is implemented as a virtual private network ([[VPN]]), running over the **Internet**. **Administering remote access involves essentially the same tasks as administering the local network**. Only authorized users should be allowed access to local network resources and communication channels. Additional complexity comes about because it can be more difficult to ensure the security of remote workstations and servers and there is greater opportunity for remote logins to be exploited. 

With a remote access VPN, clients connect to a VPN gateway on **the edge of the private network**. This is the "telecommuter" model, allowing home-workers and employees working in the field to connect to the corporate network. The VPN protocol establishes a secure tunnel so that the contents are kept private, even when the packets pass over ISPs' routers.

Remote access VPN. (Images © 123RF.com.)

A VPN can also be deployed in a site-to-site model to connect two or more private networks. **Where remote access VPN connections are typically initiated by the client**, a site-to-site VPN is configured to operate automatically. The gateways exchange security information using whichever protocol the VPN is based on. This establishes a trust relationship between the gateways and sets up a secure connection through which to **tunnel** data. Hosts at each site do not need to be configured with any information about the VPN. The routing infrastructure at each site determines whether to deliver traffic locally or send it over the VPN tunnel.

Site-to-site VPN. (Images © 123RF.com.)
# TRANSPORT LAYER SECURITY VPN

Several VPN protocols have been used over the years. Legacy protocols such as the Point-to-Point Tunneling Protocol [[(PPTP) have been deprecated]] because they do not offer adequate security. Transport Layer Security ([[TLS]]) and IPSec are now the preferred options for configuring VPN access.

![Screenshot of User Authentication Settings and Cryptographic Settings.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9158-1599771805930.png)

Configuring an OpenVPN server in the pfSense security appliance. (Screenshot used with permission from Rubicon Communications, LLC.)

A TLS VPN (still more commonly referred to as an [[SSL VPN]]) requires a remote access server listening on port 443 (or any arbitrary port number). The client makes a connection to the server using TLS so that the server is authenticated to the client (and optionally the client's certificate must be authenticated by the server). This creates an encrypted tunnel for the user to submit authentication credentials, which would normally be processed by a [[RADIUS server]]. Once the user is authenticated and the connection fully established, the VPN gateway tunnels all communications for the local network over the secure socket.

![Screenshot of VPN / OpenVPN / Servers / Edit window. General Information and Cryptographic Settings are shown.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3280-1599771805987.png)

Configuring a client certificate for mutual authentication in the pfSense security appliance. (Screenshot used with permission from Rubicon Communications, LLC.)

The port can be either TCP or UDP. UDP might be chosen for marginally superior performance, especially when tunneling latency-sensitive traffic such as voice or video. TCP might be easier to use with a default firewall policy. TLS over UDP is also referred to as Datagram TLS (DTLS).

OpenVPN is an open source example of a TLS VPN ([openvpn.net](https://openvpn.net/)). OpenVPN can work in [[TAP]] (bridged) mode to tunnel layer 2 frames or in [[TUN]] (routed) mode to forward IP packets. Another option is Microsoft's Secure Socket Tunneling Protocol ([[SSTP]]), which works by tunneling Point-to-Point Protocol (PPP) layer 2 frames over a TLS session ([docs.microsoft.com/en-us/openspecs/windows_protocols/ms-sstp/70adc1df-c4fe-4b02-8872-f1d8b9ad806a](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-sstp/70adc1df-c4fe-4b02-8872-f1d8b9ad806a)). The Point-to-Point Protocol (PPP) is a widely used remote dial-in protocol. It provides encapsulation for IP traffic plus IP address assignment and authentication via the widely supported Challenge Handshake Authentication Protocol (CHAP).
# NTERNET PROTOCOL SECURITY

Transport Layer Security is applied at the application level, either by using a separate secure port or by using commands in the application protocol to negotiate a secure connection. Internet Protocol Security ([[IPSec]]) operates at the **network layer (layer 3)** of the [[OSI]] model, so it can be implemented without having to configure specific application support. IPSec can provide both **confidentiality (by encrypting data packets)** and[[ [[integrity]]/anti-replay]] (by signing each packet). The main drawback is that it adds overhead to data communications. IPSec can be used to secure communications on local networks and as a remote access protocol.

When IPv6 was being drafted, IPSec was considered a mandatory component as it was felt that all traffic over the new protocol should be secure. In recent years, [[RFC]]s have been revised so that now, IPSec is recommended for IPv6 but no longer mandatory ([tools.ietf.org/html/rfc6434#page-17](https://tools.ietf.org/html/rfc6434#page-17)).

Each host that uses IPSec must be assigned a policy. An IPSec policy sets the authentication mechanism and also the protocols and mode for the connection. Hosts must be able to match at least one matching security method for a connection to be established. There are two core protocols in [[IPSec]], which can be applied singly or together, depending on the policy.

### Authentication Header (AH)

The Authentication Header ([[AH]]) protocol performs a cryptographic hash on the whole packet, including the IP header, plus a shared secret key (known only to the communicating hosts), and adds this [[HMAC]] in its header as an **Integrity** Check Value ([[ICV]]). The recipient performs the same function on the packet and key and should derive the same value to confirm that the packet has not been modified. The payload is **not encrypted** so this protocol does not provide confidentiality. Also, the inclusion of IP header fields in the ICV means that the check will fail across [[NAT]] [[gateways]], where the IP address is rewritten. Consequently, AH is not often used.

![There are 4 blocks in a row: IP Header, AH (which contains a small block named ICV), TCP/UDP, and Payload.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/81-1599771806095.png)

IPSec datagram using AH—The integrity of the payload and IP header is ensured by the Integrity Check Value (ICV), but the payload is not encrypted.

### Encapsulation Security Payload (ESP)

Encapsulation Security Payload ([[ESP]]) provides **confidentiality and/or authentication and integrity**. It can be used to encrypt the packet rather than simply calculating an [[HMAC]]. ESP attaches three fields to the packet: a header, a trailer (providing padding for the cryptographic function), and an Integrity Check Value. Unlike AH, ESP excludes the IP header when calculating the ICV.

![There are 4 blocks in a row: IP Header, ESP (which contains 2 blocks named TCP/UDP and Payload), Trailer, and ICV.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2880-1599771806141.png)

IPSec datagram using ESP—The [[TCP]] header and payload from the original packet are encapsulated within ESP and encrypted to provide confidentiality.

With ESP, algorithms for both **confidentiality** ([[symmetric]] cipher) and **authentication/integrity** ([[hash]] function) are usually applied together. It is possible to use one or the other, however.
# IPSEC TRANSPORT AND TUNNEL MODES

[[IPSec]] can be used in two modes:

-   **Transport mode**—this mode is used to secure communications between hosts on a private network (an end-to-end implementation). When ESP is applied in transport mode, the IP header for each packet is not encrypted, just the payload data. If AH is used in transport mode, it can provide integrity for the IP header.

![There are 4 blocks in a row: IP Header, AH (which contains a  block named ICV), ESP (which contains 2 blocks named TCP/UDP and Payload), and Trailer.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4255-1599771806237.png)

IPSec datagram using AH and ESP in transport mode.

-   **Tunnel mode**—this mode is used for communications between VPN gateways across an unsecure network (creating a VPN). This is also referred to as a router implementation. With ESP, the whole IP packet (header and payload) is encrypted and encapsulated as a datagram with a new IP header. [[AH]] has no real use case in tunnel mode, as confidentiality will usually be required.

![There are 4 blocks in a row: New IP Header, ESP (which contains a block with the original encapsulated packet), Trailer, and ICV.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9959-1599771806294.png)

IPSec datagram using ESP in tunnel mode.

![VPN > Mobile Clients configuration page showing Tunnel IPv4 selected for Mode and ESP selected under Phase 2 Proposal Protocol.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/6158-1599771806356.png)

Configuring an IPSec tunnel with ESP encryption in the pfSense security appliance. (Screenshot used with permission from Rubicon Communications, LLC.)

**The principles underlying IPSec are the same for IPv4 and IPv6**, but the header formats are different. IPSec makes use of extension headers in IPv6 while in IPv4, [[ESP]] and [[AH]] are allocated new IP protocol numbers (50 and 51), and either modify the original IP header or encapsulate the original packet, depending on whether transport or tunnel mode is used.

### Rate
# INTERNET KEY EXCHANGE 

IPSec's encryption and hashing functions depend on a shared secret. The secret must be communicated to both hosts and the hosts must confirm one another's identity (mutual authentication). Otherwise, the connection is vulnerable to man-in-the-middle and spoofing attacks [[MITM]] . The Internet Key Exchange ([[IKE]]) protocol handles authentication and key exchange, referred to as Security Associations ([[SA]]).

![Screenshot of 5 settings for Phase 1 Proposal (Authentication) and 4 settings for Phase 1 Proposal (Algorithms).](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8165-1599771806473.png)

Configuring [[IKE]] in the pfSense security appliance. (Screenshot used with permission from Rubicon Communications, LLC.)

IKE negotiations take place over two phases:

1.  Phase I establishes the identity of the two hosts and p**erforms key agreement using the Diffie-Hellman algorithm to create a secure channel**. Two methods of authenticating hosts are commonly used:
    -   **Digital certificates**—the hosts use certificates issued by a mutually trusted certificate authority to identify one another.
    -   **Pre-shared key (group authentication)**—the same passphrase is configured on both hosts.
2.  Phase II uses the secure channel created in Phase I to establish which ciphers and key sizes will be used with AH and/or ESP in the IPSec session.
# LAYER 2 TUNNELING PROTOCOL AND IKE V2

This first version of IKE is optimized to ensure the mutual authentication of two peer hosts, such as in a site-to-site VPN. On its own, it does not provide a simple means for a client user account to authenticate to a remote network directory. Consequently, for remote access VPNs, a combination of IPSec with the Layer 2 Tunneling Protocol ([[L2TP]]) VPN protocol is often used.

### Layer 2 Tunneling Protocol/IPSec VPN

A L2TP/IPSec VPN would typically operate as follows:

1.  The client and VPN gateway set up a secure IPSec channel over the Internet, using either a pre-shared key or certificates for IKE.
2.  The VPN gateway uses L2TP to set up a tunnel to exchange local network data encapsulated as Point-to-Point Protocol ([[PPP]]) frames. This double encapsulation of traffic is the main drawback, as it adds overhead.
3.  The user authenticates over the PPP session using [[EAP]] or CHAP.

### IKE v2

The drawbacks of the original version of IKE were addressed by an updated protocol. IKE v2 has some additional features that have made the protocol popular for use as a standalone remote access VPN solution. The main changes are:

-   Support for [[EAP]] authentication methods, allowing, for example, user authentication against a RADIUS server.
-   Simplified connection set up—IKE v2 specifies a single 4-message setup mode, reducing bandwidth without compromising security.
-   Reliability—IKE v2 allows NAT traversal and MOBIKE multihoming. Multihoming means that a client such as a smartphone with multiple interfaces (such as Wi-Fi and cellular) can keep the IPSec connection alive when switching between them.

Compared to L2TP/IPSec, using IKE v2 is more efficient. This solution is becoming much better supported, with native support in Windows 10, for instance.
# VPN CLIENT CONFIGURATION

To configure a VPN client, you may need to install the client software if the VPN type is not natively supported by the OS. For example, OpenVPN requires client installation. You then configure the client with the address of the VPN gateway, the VPN protocol type (if it cannot autodetect it), the username, and the account credentials. You may also need to deploy a client certificate that is trusted by the VPN concentrator to the machine and make that available to the VPN client. In addition, you might need to configure settings for how the VPN connection operates. 

### Always-On VPN

Traditional remote access VPN solutions require the user to initiate the connection and enter their authentication credentials. An always-on VPN means that the computer establishes the **VPN whenever an Internet connection over a trusted network is detected,** using the user's cached credentials to authenticate. Microsoft has an Always-On VPN solution for Windows Server and Windows 10 clients ([docs.microsoft.com/en-us/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy-deployment](https://docs.microsoft.com/en-us/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy-deployment)) and an OpenVPN client can be configured to autoconnect ([openvpn.net/vpn-server-resources/setting-your-client-to-automatically-connect-to-your-vpn-when-your-computer-starts](https://openvpn.net/vpn-server-resources/setting-your-client-to-automatically-connect-to-your-vpn-when-your-computer-starts/)). 

### Split Tunnel versus Full Tunnel

When a **client connected to a remote access VPN tries to access other sites on the Internet**, there are two ways to manage the connection:

-   **Split tunnel**—the client accesses the Internet directly using its "native" IP configuration and DNS servers.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2828-1599771806536.png)

Split tunnel VPN traffic flow. (Images © 123RF.com.)

-   **Full tunnel**—Internet access is mediated by the corporate network, which will alter the client's IP address and DNS servers and may use a proxy.

**Full tunnel offers better security**, but the network address translations and [[DNS]] operations required may cause problems with some websites, especially cloud services. It also means more data is channeled over the link.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2266-1599771806598.png)

Full tunnel VPN traffic flow. (Images © 123RF.com.)
# REMOTE DESKTOP 

A remote access VPN joins the user's PC or smartphone to the local network, via the secure tunnel. Another model for remote networking involves connecting to a host within the local network over a remote administration protocol. A protocol such as Secure Shell ([[SSH]]) traditionally provides terminal access, and there are many tools that can connect to a graphical desktop. A GUI remote administration tool sends screen and audio data from the remote host to the client and transfers mouse and keyboard input from the client to the remote host.

Microsoft's Remote Desktop Protocol ([[RDP]]) can be used to access a physical machine on a one-to-one basis. Alternatively, the site can operate a remote desktop gateway that facilitates access to virtual desktops or individual apps running on the network servers ([docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/welcome-to-rds](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/welcome-to-rds)). There are several popular alternatives to Remote Desktop. Most support remote access to platforms other than Windows (macOS and iOS, Linux, Chrome OS, and Android for instance). Examples include TeamViewer ([teamviewer.com/en](https://www.teamviewer.com/en/)) and Virtual Network Computing (VNC), which is implemented by several different providers (notably [realvnc.com/en](https://www.realvnc.com/en/)).

Traditionally, these remote desktop products require a client app. The canvas element introduced in HTML5 allows a browser to draw and update a desktop with relatively little lag. It can also handle audio. This is referred to as an HTML5 VPN or as a clientless remote desktop gateway ([guacamole.apache.org](https://guacamole.apache.org/)). This solution also uses a protocol called WebSockets, which enables bidirectional messages to be sent between the server and client without requiring the overhead of separate HTTP requests.
# OUT-OF-BAND MANAGEMENT AND JUMP SERVERS 

Remote access management refers to the specific use case of using a secure channel to administer a network appliance or server. The secure admin workstations ([[SAWs]]) used to perform management functions must be tightly locked down, ideally installed with no software other than that required to access the administrative channel—minimal web browser, remote desktop client, or SSH virtual terminal, for instance. **SAWs should be denied Internet access or be restricted to a handful of approved vendor sites (for patches, drivers, and support).** The devices must also be subject to stringent access control and auditing so that any misuse is detected at the earliest opportunity.

### Out-of-Band Management

Remote management methods can be described as either in-band or out-of-band ([[OOB]]). An in-band management link is one that shares traffic with other communications on the "production" network. A serial console or modem port on a router is a physically out-of-band management method. When using a browser-based management interface or a virtual terminal over Ethernet and IP, the link can be made out-of-band by connecting the port used for management access to physically separate network infrastructure. This can be costly to implement, but out-of-band management is more secure and means that access to the device is preserved when there are problems affecting the production network. With an in-band connection, better security can be implemented by using a VLAN to isolate management traffic. This makes it harder for potential eavesdroppers to view or modify traffic passing over the management interface. This sort of virtual OOB does still mean that access could be compromised by a system-wide network failure, however.

### Jump Servers

**One of the challenges of managing hosts that are exposed to the Internet, such as servers and appliances in a DMZ, is to provide administrative access to them. Accessing these individual hosts directly from a secure zone may open their administrative interfaces to exploitation and be used as a pivot point back into the internal network.** Consequently, the administrative servers in the secure zone that are permitted to access hosts in the DMZ must be tightly controlled. Configuring and auditing this type of control when there are many different servers operating in both zones is complex.

One solution to this complexity is to add a single administration server, or jump server, to the secure zone. The jump [[server]] only runs the necessary administrative port and protocol (typically SSH or RDP). Administrators connect to the jump server then use the jump server to connect to the admin interface on the application server. The application server's admin interface has a single entry in its ACL (the jump server) and denies connection attempts from any other hosts. 

Securing management traffic using a jump server. (Images © 123RF.com.)
# SECURE SHELL

Secure Shell ([[SSH]]) is the principal means of obtaining secure remote access to a command line terminal. The main uses of SSH are for remote administration and secure file transfer (SFTP). There are numerous commercial and open source SSH products available for all the major network operating system (NOS) platforms. The most widely used is OpenSSH ([openssh.com](https://www.openssh.com/)).

SSH servers are identified by a public/private key pair (the host key). A mapping of host names to public keys can be kept manually by each SSH client or there are various enterprise software products designed for SSH host key management.

![Warning box lists the unknown server’s rsa2 key fingerprint and has buttons: Yes, No, Cancel, Copy Key, Help.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/6686-1599771806798.png)

Confirming the SSH server's host key using the PuTTY SSH client (Screenshot used with permission from PuTTY.)

The host key must be changed if any compromise of the host is suspected. If an attacker has obtained the private key of a server or appliance, they can masquerade as that server or appliance and perform a man-in-the-middle attack, usually with a view to obtaining other network credentials. 

The server's host key is used to set up a secure channel to use for the client to submit authentication credentials. 

### SSH Client Authentication

SSH allows various methods for the client to authenticate to the SSH server. Each of these methods can be enabled or disabled as required on the server, using the /etc/ssh/sshd_config file:

-   **Username/password**—the client submits credentials that are verified by the SSH server either against a local user database or using a RADIUS/TACACS+ server.
-   **Public key authentication**—each remote user's public key is added to a list of keys authorized for each local account on the SSH server. 
-   **Kerberos**—the client submits a Ticket Granting Ticket (TGT) to the Ticket Granting Service (TGS) along with the Service Principal Name (SPN) of the SSH server that the client wants to access. The Key Distribution Center (KDC) verifies the TGT of the client to authorize access. The TGS then sends a valid session key to the client that can be forwarded to the SSH server to prove identity and gain access.

Managing valid client public keys is a critical security task. Many recent attacks o n web servers have exploited poor key management. If a user's private key is compromised, delete the public key from the appliance then regenerate the key pair on the user's (remediated) client device and copy the public key to the SSH server. Always delete public keys if the user's access permissions have been revoked.

### SSH Commands

SSH commands are used to connect to hosts and set up authentication methods. To connect to an SSH server at 10.1.0.10 using an account named "bobby" and password authentication, run:

ssh bobby@10.1.0.10

The following commands create a new key pair and copy it to an account on the remote server:

ssh-keygen -t rsa

ssh-copy-id bobby@10.1.0.10

At an SSH prompt, you can now use the standard Linux shell commands. Use exit to close the connection.

You can also use the scp command to copy a file from the remote server to the local host:

scp bobby@10.1.0.10:/logs/audit.log audit.log

Reverse the arguments to copy a file from the local host to the remote server. To copy the contents of a directory and any subdirectories (recursively), use the -r option.
