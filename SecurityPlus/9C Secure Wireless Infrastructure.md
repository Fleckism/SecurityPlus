---
tags: [OIR, Implementation,section]
---
# EXAM OBJECTIVES COVERED

1.4 Given a scenario, analyze potential indicators associated with network attacks

3.4 Given a scenario, install and configure wireless security settings 

Most organizations have both a wired and a wireless network for employees to access while on the move within their facilities. Understanding the potential threats and vulnerabilities will allow you to successfully secure the wireless components of an organization's information systems infrastructure.
# WIRELESS NETWORK INSTALLATION CONSIDERATIONS

Wireless network installation considerations refer to the factors that ensure good availability of authorized Wi-Fi access points. A network with patchy coverage is vulnerable to rogue and evil twin attacks.

The 5 GHz band has more space to configure non-overlapping channels. Also note that a [[WAP]] can use bonded channels to improve bandwidth, but this increases risks from interference.

### Wireless Access Point (WAP) Placement

An infrastructure-based wireless network comprises one or more wireless access points, each connected to a wired network. The access points forward traffic to and from the wired switched network. Each WAP is identified by its MAC address, also referred to as its basic service set identifier ([[BSSID]]). Each wireless network is identified by its name, or service set identifier ([[SSID]]).

Wireless networks can operate in either the 2.4 GHz or 5 GHz radio band. Each radio band is divided into a number of channels, and each WAP must be configured to use a specific channel. For performance reasons, the channels chosen should be as widely spaced as possible to reduce different **types of interference**:

-   Co-channel interference ([[CCI]])—when two WAPs in close proximity use the same channel, they compete for bandwidth within that channel, as signals collide and have to be re-transmitted.
-   **Adjacent channel interference** ([[ACI]])—channels have only ~5 MHz spacing, but Wi-Fi requires 20 MHz of channel space. When the channels selected for WAPs are not cleanly spaced, the interference pattern creates significant numbers of errors and loss of bandwidth. For example, if two access points within range of one another are configured in the 2.4 GHz band with **channels 1 and 6**, they will not overlap. If a third access point is added using channel 3, it will use part of the spectrum used by both the other WAPs, and all three networks will suffer from interference.

### Site Surveys and Heat Maps

The coverage and interference factors mean that WAPs must be positioned and configured so that the whole area is covered, but that they overlap as little as possible. A site survey is used to measure signal strength and channel usage throughout the area to cover. A site survey starts with an architectural map of the site, with physical features that can cause background interference marked. These features include solid walls, reflective surfaces, motors, microwave ovens, and so on. The survey is performed with a Wi-Fi-enabled laptop or mobile device with Wi-Fi analyzer software installed. The Wi-Fi analyzer records information about the signal obtained at regularly spaced points as the surveyor moves around the area.

These readings are combined and analyzed to produce a heat map, showing where a signal is strong (red) or weak (green/blue), and which channel is being used and how they overlap. This data is then used to optimize the design, by adjusting transmit power to reduce a WAP's range, changing the channel on a WAP, adding a new WAP, or physically moving a WAP to a new location.
# CONTROLLER AND ACCESS POINT SECURITY 

Where a site survey ensures availability, the confidentiality and integrity properties of the network are ensured by configuring authentication and encryption. These settings could be configured manually on each WAP, but this would be onerous in an enterprise network with tens or hundreds of WAP. If access points are individually managed, this can lead to configuration errors and can make it difficult to gain an overall view of the wireless deployment, including which clients are connected to which access points and which clients or access points are handling the most traffic.

Rather than configure each device individually, enterprise wireless solutions implement wireless controllers for centralized management and monitoring. A controller can be a hardware appliance or a software application run on a server.

![Statistics Information shown includes # of Clients, Current Usage - Top Access Points, Quick Look at most active AP and client, and Recent Activities](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4320-1599771802756.png)

UniFi Wireless Network management console. (Screenshot used with permission from Ubiquiti Networks.)

An access point whose firmware contains enough processing logic to be able to function autonomously and handle clients without the use of a wireless controller is known as a fat WAP, while one that requires a wireless controller in order to function is known as a thin WAP.

Controllers and access points must be made physically secure, as tampering could allow a  #threat actor to insert  a rogue/evil twin WAP to try to intercept logons. These devices must be managed like switches and routers, using secure management interfaces and strong administrative credentials.
# WI-FI PROTECTED ACCESS

As well as the site design, a wireless network must be configured with security settings. Without encryption, anyone within range can intercept and read packets passing over the wireless network. These choices are determined by device support for the various Wi-Fi security standards, by the type of authentication infrastructure, and by the purpose of the [[WLAN]]. The security standard determines the cryptographic protocols that are supported, the means of generating the encryption key, and available methods for authenticating wireless stations when they try to join (or associate with) the network.

The first version of Wi-Fi Protected Access ([[WPA]]) was designed to fix critical vulnerabilities in the earlier wired equivalent privacy ([[WEP]]) standard. Like WEP, version 1 of WPA uses the RC4 stream cipher but adds a mechanism called the Temporal Key Integrity Protocol ([[TKIP]]) to make it stronger.

![Wireless settings page shows 2.4 GHz radio configured with WPA/WPA2-Personal, version WPA2-PSK, and AES encryption. The 5 GHz radio security setting is WPA2/WPA3-Personal, while the version is WPA3-SAE.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2711-1599771802863.png)

Configuring a TP-LINK SOHO access point with wireless encryption and authentication settings. In this example, the 2.4 GHz band allows legacy connections with WPA2-Personal security, while the 5 GHz network is for 802.11ax (Wi-Fi 6) capable devices using WPA3-SAE authentication. (Screenshot used with permission from TP-Link Technologies.)

Neither [[WEP]] nor the original [[WPA]] version are considered secure enough for continued use. WPA2 uses the Advanced Encryption Standard ([[AES]]) cipher with 128-bit keys, deployed within the Counter Mode with Cipher Block Chaining Message Authentication Code Protocol ([[CCMP]]). AES replaces RC4 and CCMP replaces TKIP. CCMP provides authenticated encryption, which is designed to make replay attacks harder.

Weaknesses have also been found in WPA2, however, which has led to its intended replacement by WPA3. The main features of WPA3 are as follows:

-   Simultaneous Authentication of Equals ([[SAE]])—replaces WPA's 4-way handshake authentication and association mechanism with a protocol based on Diffie-Hellman key agreement.
-   Enhanced Open—enables encryption for the open authentication method.
-   Updated cryptographic protocols—replaces AES CCMP with the **AES Galois Counter Mode Protocol** ([[GCMP]]) mode of operation. Enterprise authentication methods must use 192-bit AES, while personal authentication can use either 128-bit or 192-bit.
-   Management protection frames—mandates use of these to protect against key recovery attacks.

Wi-Fi performance also depends on support for the latest 802.11 standards. The most recent generation (802.11ax) is being marketed as Wi-Fi 6. The earlier standards are retroactively named Wi-Fi 5 (802.11ac) and Wi-Fi 4 (802.11n). The performance standards are developed in parallel with the WPA security specifications. Most Wi-Fi 6 devices and some Wi-Fi 5 and Wi-Fi 4 products should support WPA3, either natively or with a firmware/driver update.
# WI-FI AUTHENTICATION METHODS

In order to secure a network, you need to be able to confirm that only valid users are connecting to it. Wi-Fi authentication comes in three types: personal, open, and enterprise. Within the personal category, there are two methods: pre-shared key authentication ([[PSK]]) and simultaneous authentication of equals ([[SAE]]).

### WPA2 Pre-Shared Key Authentication 

In WPA2, pre-shared key (PSK) authentication uses a passphrase to generate the key that is used to encrypt communications. It is also referred to as group authentication because a group of users share the same secret. When the access point is set to WPA2-PSK mode, the administrator configures a passphrase of between 8 and 63 ASCII characters. This is converted to a 256-bit [[HMAC]] (expressed as a 64-character hex value) using the [PBKDF2] key stretching [[algorithm]]. This HMAC is referred to as the pairwise master key ([[PMK]]). The same secret must be configured on the access point and on each node that joins the network. The PMK is used as part of WPA2's 4-way handshake to derive various session keys.

All types of Wi-Fi personal authentication have been shown to be vulnerable to attacks that allow dictionary or brute force attacks against the passphrase. At a minimum, the passphrase must be at least **14 characters** long to try to mitigate risks from cracking.

### WPA3 Personal Authentication

While WPA3 still uses a passphrase to authenticate stations in personal mode, it changes the method by which this secret is used to agree upon session keys. The scheme used is also referred to as Password Authenticated Key Exchange ([[PAKE]]). In WPA3, the Simultaneous Authentication of Equals ([[SAE]]) protocol replaces the 4-way handshake, which has been found to be vulnerable to various attacks. SAE uses the Dragonfly handshake, which is basically Diffie-Hellman over elliptic curves key agreement, combined with a hash value derived from the password and device MAC address to authenticate the nodes. With SAE, there should be no way for an attacker to sniff the handshake to obtain the hash value and try to use an offline brute-force or dictionary attack to recover the password. Dragonfly also implements [[ephemeral session keys]], providing forward secrecy.

The configuration interfaces for access points can use different labels for these methods. You might see WPA2-Personal and WPA3-SAE rather than WPA2-PSK and WPA3-Personal, for example. Additionally, an access point can be configured for WPA3 only or with support for legacy WPA2 (WPA3-Personal Transition mode). Researchers already found flaws in WPA3-Personal, one of which relies on a **downgrade #attack** to use WPA2 ([wi-fi.org/security-update-april-2019](https://www.wi-fi.org/security-update-april-2019)).
# WI-FI PROTECTED SETUP

As setting up an access point securely is relatively complex for residential consumers, vendors have developed a system to automate the process called Wi-Fi Protected Setup ([[WPS]]). To use WPS, both the access point and wireless station (client device) must be WPS-capable. Typically, the devices will have a pushbutton. Activating this on the access point and the adapter simultaneously will associate the devices using a PIN, then associate the adapter with the access point using WPA2. The system generates a random [[SSID]] and [[PSK]]. If the devices do not support the push button method, the PIN (printed on the [[WAP]]) can be entered manually.

Unfortunately, WPS is vulnerable to a brute force attack. While the PIN is eight characters, one digit is a checksum and the rest are verified as two separate PINs of four and three characters. These separate PINs are many orders of magnitude simpler to brute force, typically requiring just hours to crack. On some models, disabling WPS through the admin interface does not actually disable the protocol, or there is no option to disable it. Some APs can lock out an intruder if a brute force attack is detected, but in some cases the attack can just be resumed when the lockout period expires. To counter this, the lockout period can be increased. However, this can leave [[APs]] vulnerable to a denial of service ([[DoS]]) attack. When provisioning a WAP, it is essential to verify what steps the vendor has taken to make their WPS implementation secure and the firmware level required to assure security.

The Easy Connect method, announced alongside WPA3, is intended to replace WPS as a method of securely configuring client devices with the information required to access a Wi-Fi network. Easy Connect is a brand name for the Device Provisioning Protocol ([[DPP]]). Each participating device must be configured with a public/private key pair. Easy Connect uses quick response ([[QR]]) codes or nearfield communication ([[NFC]]) tags to communicate each device's public key. A smartphone is registered as an Easy Connect configurator app, and associated with the WAP using its QR code. Each client device can then be associated by scanning its QR code or NFC tag in the configurator app. As well as fixing the security problems associated with WPS, this is a straightforward means of configuring headless Internet of Things (IoT) devices with Wi-Fi connectivity.

A quick response (QR) code is a barcode standard for encoding arbitrary alphanumeric or binary strings within a square block pattern. The codes can be scanned using any type of digital camera.
# OPEN AUTHENTICATION AND CAPTIVE PORTALS

Selecting open authentication means that the client is not required to authenticate. This mode would be used on a public [[WAP]] (or "hotspot"). In WPA2, this also means that data sent over the link is unencrypted. Open authentication may be combined with a secondary authentication mechanism managed via a browser. When the client associates with the open hotspot and launches the browser, the client is redirected to a captive portal or splash page. This will allow the client to authenticate to the hotspot provider's network (over HTTPS, so the login is secure). The portal may also be designed to enforce terms and conditions and/or take payment to access the Wi-Fi service.

When using open wireless, users must ensure they send confidential web data only over HTTPS connections and only use email, VoIP, IM, and file transfer services with [[SSL/TLS]] enabled. Another option is for the user to join a Virtual Private Network ([[VPN]]). The user would associate with the open hotspot then start the VPN connection. **This creates an encrypted "tunnel" between the user's computer and the VPN server.** This allows the user to browse the web or connect to email services without anyone eavesdropping on the open Wi-Fi network being able to intercept those communications. The VPN could be provided by the user's company or they could use a third-party VPN service provider. Of course, if using a third party, the user needs to be able to trust them implicitly. The VPN must use certificate-based tunneling to set up the "inner" authentication method.

WPA3 can implement a mode called Wi-Fi Enhanced Open, which uses opportunistic wireless encryption ([[OWE]]). OWE uses the **Dragonfly handshake to agree with ephemeral session keys on joining the network.** This means that one station cannot sniff the traffic from another station, because they are using different session keys. There is still no authentication of the access point, however.
#start
# ENTERPRISE/IEEE 802.1X AUTHENTICATION

The main problems with personal modes of authentication are that distribution of the key or passphrase cannot be secured properly, and users may choose unsecure phrases. Personal authentication also fails to provide accounting, as all users share the same key.

As an alternative to personal authentication, the enterprise authentication method implements IEEE 802.1X to use an Extensible Authentication Protocol ([[EAP]]) mechanism. 802.1X defines the use of EAP over Wireless ([[EAPoW]]) to allow an access point to forward authentication data without allowing any other type of network access. It is configured by selecting WPA2-Enterprise or WPA3-Enterprise as the security method on the access point.

With enterprise authentication, when a wireless station requests an association, the WAP enables the channel for EAPoW traffic only. It passes the credentials of the user (supplicant) to an [[AAA]] (RADIUS or TACACS+) server on the wired network for validation. When the supplicant has been authenticated, the AAA server transmits a master key ([[MK]]) to the supplicant. The supplicant and authentication [[server]] then derive the same pairwise master key ([[PMK]]) from the MK. The AAA server transmits the PMK to the access point. The wireless station and access point use the PMK to derive session keys, using either the WPA2 4-way handshake or WPA3 SAE methods.

See [tldp.org/HOWTO/8021X-HOWTO/intro.html](https://www.tldp.org/HOWTO/8021X-HOWTO/intro.html) for more detailed information about the keys used.

![Layer 2 tab under Security shows WPA+WPA2 is set with parameter WPA2 Policy-AES checked, and 802.1X is  enabled for Authentication Key Management.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3006-1599771802927.png)

Using Cisco's Virtual Wireless LAN Controller to set security policies for a WLAN—this policy enforces use of WPA2 and the use of 802.1X (Enterprise) authentication. (Screenshot used with permission from Cisco.)
# EXTENSIBLE AUTHENTICATION PROTOCOL

The Extensible Authentication Protocol ([[EAP]]) defines a framework for negotiating authentication mechanisms rather than the details of the mechanisms themselves. Vendors can write extensions to the protocol to support third-party security devices. EAP implementations can include smart cards, one-time passwords, biometric identifiers, or simpler username and password combinations.

EAP-TLS is one of the strongest types of authentication and is very widely supported. An encrypted Transport Layer Security ([[TLS]]) tunnel is established between the supplicant and authentication server using public key certificates on the authentication server and supplicant. As both supplicant and server are configured with certificates, this provides mutual authentication. The supplicant will typically provide a certificate using a smart card or a certificate could be installed on the client device, possibly in a Trusted Platform Module ([[TPM]]).

![Smart Card or other Certificate Properties dialog box shows Certificate issued to, Friendly name, Issuer, and Expiration date.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7660-1599771803109.png)

Configuring Network Policy Server to authenticate wireless clients using 802.1X EAP-TLS. (Screenshot used with permission from Microsoft.)
# PEAP, EAP-TTLS, AND EAP-FAST

Provisioning certificates to each wireless device is a considerable management challenge. Other types of EAP are designed to provide secure tunneling with server-side certificates only.

### Protected Extensible Authentication Protocol (PEAP)

In Protected Extensible Authentication Protocol ([[PEAP]]), as with EAP-TLS, an encrypted tunnel is established between the supplicant and authentication server, but PEAP only requires a server-side public key certificate. The supplicant does not require a certificate. With the server authenticated to the supplicant, user authentication can then take place through the secure tunnel with protection against sniffing, password-guessing/dictionary, and on-path attacks. The user authentication method (also referred to as the "inner" method) can use either MS-CHAPv2 or EAP-GTC. The Generic Token Card ([[GTC]]) method transfers a token for authentication against a network directory or using a one-time password mechanism.

### EAP with Tunneled TLS (EAP-TTLS)

EAP-Tunneled TLS (EAP-TTLS) is similar to PEAP. It uses a server-side certificate to establish a protected tunnel through which the user's authentication credentials can be transmitted to the authentication server. The main distinction from PEAP is that EAP-TTLS can use any inner authentication protocol (PAP or CHAP, for instance), while PEAP must use EAP-MSCHAP or EAP-GTC. 

### EAP with Flexible Authentication via Secure Tunneling (EAP-FAST)

EAP with Flexible Authentication via Secure Tunneling (EAP-FAST) is similar to PEAP, but instead of using a certificate to set up the tunnel, it uses a Protected Access Credential ([[PAC]]), which is generated for each user from the authentication server's master key. The problem with EAP-FAST is in distributing (provisioning) the PAC securely to each user requiring access. The PAC can either be distributed via an out-of-band method or via a server with a digital certificate (but in the latter case, EAP-FAST does not offer much advantage over using PEAP). Alternatively, the PAC can be delivered via anonymous [[Diffie-Hellman]] key exchange. The problem here is that there is nothing to authenticate the access point to the user. A rogue access point could obtain enough of the user credential to perform an ASLEAP password cracking #attack ([techrepublic.com/article/ultimate-wireless-security-guide-a-primer-on-cisco-eap-fast-authentication](https://www.techrepublic.com/article/ultimate-wireless-security-guide-a-primer-on-cisco-eap-fast-authentication/)).
# RADIUS FEDERATION

Most implementations of EAP use a RADIUS [[server]] to validate the authentication credentials for each user (supplicant). RADIUS federation means that multiple organizations allow access to one another's users by joining their RADIUS servers into a RADIUS hierarchy or mesh. For example, when Bob from widget.foo needs to log on to grommet.foo's network, the RADIUS server at grommet.foo recognizes that Bob is not a local user but has been granted access rights and routes the request to widget.foo's RADIUS server.

One example of RADIUS federation is the eduroam network ([eduroam.org](https://www.eduroam.org/)), which allows students of universities from several different countries to log on to the networks of any of the participating institutions using the credentials stored by their "home" university.
# ROGUE ACCESS POINTS AND EVIL TWINS 

A rogue access point is one that has been installed on the network without authorization, whether with malicious intent or not. It is vital to periodically survey the site to detect rogue [[WAPs]]. A malicious user can set up such an access point with something as basic as a smartphone with tethering capabilities, and a non-malicious user could enable such an access point by accident. If connected to a LAN without security, an unauthorized WAP creates a backdoor through which to attack the network. A rogue WAP could also be used to capture user logon attempts, allow man-in-the-middle attacks, and allow access to private information.

A rogue WAP masquerading as a legitimate one is called an evil twin. An evil twin might just have a similar name ([[SSID]]) to the legitimate one, or the attacker might use some [[DoS]] technique to overcome the legitimate WAP. This attack will not succeed if authentication security is enabled on the WAP, unless the attacker also knows the details of the authentication method. However, the evil twin might be able to harvest authentication information from users entering their credentials by mistake. 

![MetaGeek.png](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/MetaGeek.png)

Surveying Wi-Fi networks using MetaGeek inSSIDer—Note the presence of smart TV appliances with Wi-Fi Direct enabled. (MetaGeek, LLC. © Copyright 2005-2021)

A rogue hardware [[WAP]] can be identified through physical inspections. There are also various Wi-Fi analyzers and monitoring systems that can detect rogue WAPs, including inSSIDer ([metageek.com/products/inssider](https://www.metageek.com/products/inssider/)) and Kismet ([kismetwireless.net](https://www.kismetwireless.net/)).
# DISASSOCIATION AND REPLAY #ATTACKS

In the normal course of operations, an access point and client exchange management frames to control connections. The access point normally broadcasts a beacon frame to advertise service capabilities. Clients can choose to first authenticate and then associate to an access point when they move into range of the beacon. The client or access point can use disassociation and/or deauthentication frames to notify the other party that it has ended a connection. A legitimate client might disassociate but not deauthenticate because it is roaming between wireless access points in a distribution system. A disassociation attack exploits the lack of encryption in management frame traffic to send spoofed frames. One type of disassociation attack injects management frames that spoof the MAC address of a single victim station in a disassociation notification, causing it to be disconnected from the network. Another variant of the attack broadcasts spoofed frames to disconnect all stations. Frames can be spoofed to send either disassociation or deauthentication notifications.

Disassociation/deauthentication attacks may be used to perform a denial of service attack against the wireless infrastructure or to exploit disconnected stations to try to force reconnection to a rogue WAP. Disassociation/deauthentication attacks might also be used in conjunction with a replay attack aimed at recovering the network key. The attacks can be mitigated if the wireless infrastructure supports Management Frame Protection (MFP/802.11w). Both the WAP and clients must be configured to support MFP.

Pre-shared key authentication is vulnerable to various types of replay attack that aim to capture the hash of the passphrase when a wireless station associates with an access point. Once the hash is captured it can be subjected to offline brute-force and dictionary cracking. In WEP, these are referred to as initialization vector (IV) attacks, because they exploit flaws in the mechanism that is supposed to ensure a unique keystream, given the same key. A type of replay attack is used to make the access point generate lots of packets, usually by deauthenticating a station, capturing its encrypted ARP packet, and replaying this rapidly, causing the WAP to cycle through IV values quickly, revealing the hash part.

WPA and WPA2 are not vulnerable to IV attacks, but a serious vulnerability was discovered in 2017 ([krackattacks.com](https://www.krackattacks.com/)). A KRACK attack uses a replay mechanism that targets the 4-way handshake. KRACK is effective regardless of whether the authentication mechanism is personal or enterprise. It is important to ensure both clients and access points are fully patched against such attacks.
# JAMMING ATTACKS

A wireless network can be disrupted by interference from other radio sources. These are often unintentional, but it is also possible for an attacker to purposefully jam an access point. This might be done simply to disrupt services or to position an evil twin on the network with the hope of stealing data. A Wi-Fi jamming attack can be performed by setting up a WAP with a stronger signal. Wi-Fi jamming devices are also widely available, though they are often illegal to use and sometimes to sell. Such devices can be very small, but the attacker still needs to gain fairly close physical proximity to the wireless network.

The only ways to defeat a jamming attack are either to locate the offending radio source and disable it, or to boost the signal from the legitimate equipment. WAPs for home and small business use are not often configurable, but the more advanced wireless access points, such as Cisco's Aironet series, support configurable power level controls. The source of interference can be detected using a spectrum analyzer. Unlike a Wi-Fi analyzer, a spectrum analyzer must use a special radio receiver (Wi-Fi adapters filter out anything that isn't a Wi-Fi signal). They are usually supplied as handheld units with a directional antenna, so that the exact location of the interference can be pinpointed.
