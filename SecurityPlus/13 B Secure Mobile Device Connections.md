
# EXAM OBJECTIVES COVERED

1.4 Given a scenario, analyze  potential indicators associated with network attacks
#attack #threat #vulnerability 
3.5 Given a scenario, implement secure mobile solutions
#Implementation 
As well as authentication and authorization for features and apps, management suites can also assist with networking options for mobile. You must be able to disable communication types that are not secure for local networks, and advise users about the security of communications when they use their devices remotely.
# CELLULAR AND GPS CONNECTION METHODS 

Mobile devices use a variety of connection methods to establish communications in local and personal area networks and for Internet data access via service providers.

![8 configuration settings for Cellular and connectivity are available (to set as Block or Not configured) but all 8 are labeled “(Samsung KNOX only)”.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7778-1599771808559.png)

Locking down Android connectivity methods with Intune—note that most settings can be applied only to Samsung KNOX-capable devices. (Screenshot used with permission from Microsoft.)

### Cellular Data Connections

Smartphones and some tablets use the cell phone network for calls and data access. A cellular data connection is less likely to be subject to monitoring and filtering. It may be appropriate to disable it when a device has access to an enterprise network or data, to prevent its use for data **exfiltration**.

There have been attacks and successful exploits against the major infrastructure and protocols underpinning the telecoms network, notably the SS7 hack ([theregister.com/2017/05/03/hackers_fire_up_ss7_flaw](https://www.theregister.com/2017/05/03/hackers_fire_up_ss7_flaw)). There is little that either companies or individuals can do about these weaknesses. The attacks require a high degree of sophistication and are relatively uncommon.

### Global Positioning System (GPS)

A global positioning system (GPS) sensor triangulates the device position using signals from orbital GPS satellites. As this triangulation process can be slow, most smartphones use **Assisted GPS** (A-GPS) to obtain coordinates from the **nearest cell tower and adjust for the device's position relative to the tower.** A-GPS uses cellular data. GPS satellites are operated by the US Government. Some GPS sensors can use signals from other satellites, operated by the EU (Galileo), Russia (GLONASS), or China (BeiDou).

**GPS signals can be jammed or even spoofed** using specialist radio equipment. This might be used to defeat geofencing mechanisms, for instance ([kaspersky.com/blog/gps-spoofing-protection/26837](https://www.kaspersky.com/blog/gps-spoofing-protection/26837/)).
# WI-FI AND TETHERING CONNECTION METHODS 

Mobile devices usually default to using a Wi-Fi connection for data, if present. If the user establishes a connection to a corporate network using strong WPA3 security, there is a fairly low risk of eavesdropping or man-in-the-middle attacks ([[MITM]]). The risks from Wi-Fi come from users connecting to open access points or possibly a rogue access point imitating a corporate network. These allow the access point owner to launch any number of attacks, even potentially compromising sessions with secure servers (using a [[DNS spoofing attack]], for instance).

### Personal Area Networks (PANs)

Personal area networks (PANs) enable connectivity between a mobile device and peripherals. **Ad hoc (or peer-to-peer)** networks between mobile devices or between mobile devices and other computing devices can also be established. In terms of corporate security, these peer-to-peer functions should generally be disabled. It might be possible for an attacker to exploit a misconfigured device and obtain a bridged connection to the corporate network.

### Ad Hoc Wi-Fi and Wi-Fi Direct

Wireless stations can establish peer-to-peer connections with one another, rather than using an access point. This can also be called an **ad hoc network**, meaning that the network is not made permanently available. There is no established, standards-based support for ad hoc networking, however. [[MITRE]] have a project to enable Android smartphones to configure themselves in an ad hoc network ([mitre.org/research/technology-transfer/open-source-software/smartphone-ad-hoc-networking-span](https://www.mitre.org/research/technology-transfer/open-source-software/smartphone-ad-hoc-networking-span)).

Wi-Fi Direct allows one-to-one connections between stations, though in this case one of the devices actually functions as a soft access point. Wi-Fi Direct depends on Wi-Fi Protected Setup ([[WPS]]), which has many [[vulnerability|vulnerabilities]]. Android supports operating as a Wi-Fi Direct AP, but iOS uses a proprietary multipeer connectivity framework. You can connect an iOS device to another device running a Wi-Fi direct soft [[AP]], however.

There are also wireless mesh products from vendors such as Netgear and Google that allow all types of wireless devices to participate in a peer-to-peer network. These products might not be interoperable, though more are now supporting the EasyMesh standard ([wi-fi.org/discover-wi-fi/wi-fi-easymesh](https://www.wi-fi.org/discover-wi-fi/wi-fi-easymesh)).

### Tethering and Hotspots

A smartphone can share its Internet connection with another device, such as a PC. Where this connection is shared over Wi-Fi with multiple other devices, the smartphone can be described as a hotspot. Where the connection is shared by connecting the smartphone to a PC over a USB cable or with a single PC via Bluetooth, it can be referred to as tethering. However, the term "Wi-Fi tethering" is also quite widely used to mean a hotspot. This type of functionality would typically be disabled when the device is connected to an enterprise network, as it might be used to circumvent security mechanisms, such as data loss prevention or a web content filtering policies.
# BLUETOOTH CONNECTION METHODS 

Bluetooth is one of the most popular technologies for implementing Personal Area Networks (PANs). While native Bluetooth has fairly low data rates, it can be used to pair with another device and then use a Wi-Fi link for data transfer. This sort of connectivity is implemented by iOS's AirDrop feature.

Bluetooth devices have a few known security issues:

-   **Device discovery**—a device can be put into discoverable mode meaning that it will connect to any other Bluetooth devices nearby. Unfortunately, even a device in non-discoverable mode is quite easy to detect.
-   **Authentication and authorization**—devices authenticate ("pair") using a simple passkey configured on both devices. This should always be changed to some secure phrase and never left as the default. Also, check the device's pairing list regularly to confirm that the devices listed are valid.
-   **[[Malware]]**—there are proof-of-concept Bluetooth worms and application exploits, most notably the BlueBorne exploit ([armis.com/blueborne](https://www.armis.com/blueborne/)), which can compromise any active and unpatched system regardless of whether discovery is enabled and without requiring any user intervention. There are also [[vulnerability|vulnerabilities]] in the authentication schemes of many devices. Keep devices updated with the latest firmware.

![Pair Device dialog box asks: “Pair device? Does the PIN on “COMPTIA-MOBILE” match the PIN below? 998584” with buttons for Yes and Cancel.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5907-1599771808640.png)

Pairing a computer with a smartphone. (Screenshot used with permission from Microsoft.)

It is also the case that using a control center toggle may not actually turn off the Bluetooth radio on a mobile device. If there is any doubt about patch status or exposure to [[vulnerability|vulnerabilities]], Bluetooth should be fully disabled through device settings.

Unless some sort of authentication is configured, a discoverable device is vulnerable to bluejacking, a sort of spam where someone sends you an unsolicited text (or picture/video) message or vCard (contact details). This can also be a vector for malware, as demonstrated by the Obad Android Trojan malware ([securelist.com/the-most-sophisticated-android-trojan/35929](https://securelist.com/the-most-sophisticated-android-trojan/35929/)).

Bluesnarfing refers to using an exploit in Bluetooth to steal information from someone else's phone. The exploit (now patched) allows attackers to circumvent the **authentication** mechanism. Even without an exploit, a short (4 digit) PIN code is vulnerable to brute force password guessing.

Other significant risks come from the device that is being connected. A peripheral device with malicious firmware can be used to launch highly effective attacks. This type of risk has a low likelihood, as the resources required to craft such malicious peripherals are demanding.
# INFRARED AND RFID CONNECTION METHODS

Infrared signaling has been used for [[PAN]] in the past (IrDA), but the use of infrared in modern smartphones and wearable technology focuses on two other uses:

-   **IR blaster**—this allows the device to interact with an IR receiver and operate a device such as a TV or HVAC monitor as though it were the remote control handset.
-   **IR sensor**—these are used as proximity sensors (to detect when a smartphone is being held to the ear, for instance) and to measure health information (such as heart rate and blood oxygen levels). 

**Radio Frequency ID** (RFID) is a means of encoding information into passive tags, which can be easily attached to devices, structures, clothing, or almost anything else. **A passive tag can have a range from a few centimeters to a few meters.** When a reader is within range of the tag, it produces an electromagnetic wave that powers up the tag and allows the reader to collect information from it or to change the values encoded in the tag. There are also **battery-powered active tags that can be read at much greater distances (hundreds of meters)**.

One type of RFID attack is skimming, which is where an attacker uses a fraudulent RFID reader to read the signals from a contactless bank card. Any reader can access any data stored on any RFID tag, so sensitive information must be protected using cryptography. It is also possible (in theory) to design RFID tags to inject malicious code to try to exploit a vulnerability in a reader.
# NEAR FIELD COMMUNICATIONS AND MOBILE PAYMENT SERVICES 

[[NFC]] is based on a particular type of radio frequency ID (RFID). NFC sensors and functionality are now commonly incorporated into smartphones. An NFC chip can also be used to read passive RFID tags at close range. It can also be used to configure other types of connections (pairing Bluetooth devices for instance) and for exchanging information, such as contact cards. An NFC transaction is sometimes known as a **bump**, named after an early mobile sharing app, later redeveloped as Android Beam, to use NFC. The typical use case is in "smart" posters, where the user can tap the tag in the poster to open a linked web page via the information coded in the tag. Attacks could be developed using [[vulnerability|vulnerabilities]] in handling the tag ([securityboulevard.com/2019/10/nfc-false-tag-vulnerability-cve-2019-9295](https://securityboulevard.com/2019/10/nfc-false-tag-vulnerability-cve-2019-9295/)). It is also possible that there may be some way to exploit NFC by crafting tags to direct the device browser to a malicious web page where the attacker could try to exploit any [[vulnerability|vulnerabilities]] in the browser.

**NFC does not provide encryption**, so eavesdropping and man-in-the-middle [[MITM]] attacks are possible if the attacker can find some way of intercepting the communication and the software services are not encrypting the data.

The widest application of NFC is to make payments via contactless point-of-sale (PoS) machines. To configure a payment service, the user enters their credit card information into a mobile wallet app on the device. The wallet app does not transmit the original credit card information, but a one-time token that is interpreted by the card merchant and linked backed to the relevant customer account. There are three major mobile wallet apps: **Apple Pay, Google Pay (formerly Android Pay), and Samsung Pay**.

Despite having a close physical proximity requirement, NFC is vulnerable to several types of attacks. Certain antenna configurations may be able to pick up the RF signals emitted by NFC from several feet away, giving an attacker the ability to eavesdrop from a more comfortable distance. An attacker with a reader may also be able to skim information from an NFC device in a crowded area, such as a busy train. An attacker may also be able to corrupt data as it is being transferred through a method similar to a DoS attack—by flooding the area with an excess of RF signals to interrupt the transfer. 

Skimming a credit or bank card will give the attacker the long card number and expiry date. Completing fraudulent transactions directly via NFC is much more difficult as the attacker would have to use a valid merchant account and fraudulent transactions related to that account would be detected very quickly.
# USB CONNECTION METHODS

Android devices can be connected to a computer via the USB port. Apple devices require a lightning-to-USB converter cable. Once attached the computer can access the device's hard drive, sync or backup apps, and upgrade the firmware.

Some Android USB ports support USB On The Go (OTG) and there are adapters for iOS devices. USB OTG allows a port to function either as a host or as a device. For example, a port on a smartphone might operate as a device when connected to a PC, but as a host when connected to a keyboard or external hard drive. The extra pin communicates which mode the port is in.

There are various ways in which USB OTG could be abused. Media connected to the smartphone could host malware. The malware might not be able to affect the smartphone itself but could be spread between host computers or networks via the device. It is also possible that a charging plug could act as a **Trojan and try to install apps (referred to as juice-jacking)**, though modern versions of both iOS and Android now require authorization before the device will accept the connection.
# SMS/MMS/RCS AND PUSH NOTIFICATIONS

The Short Message Service (SMS) and Multimedia Message Service (MMS) are operated by the cellular network providers. They allow transmission of text messages and binary files. **[[vulnerability|vulnerabilities]] in SMS and the SS7 signaling protocol** that underpins it have cast doubt on the security of 2-step verification mechanisms ([kaspersky.com/blog/ss7-hacked/25529](https://www.kaspersky.com/blog/ss7-hacked/25529/)).

**Rich Communication Services** (RCS) is designed as a platform-independent advanced messaging app, with a similar feature set to proprietary apps like WhatsApp and iMessage. These features include support for video calling, larger binary attachments, group messaging/calling, and read receipts. RCS is supported by carriers via Universal Profile for Advanced Messaging ([gsma.com/futurenetworks/digest/universal-profile-version-2-0-advanced-rcs-messaging](https://www.gsma.com/futurenetworks/digest/universal-profile-version-2-0-advanced-rcs-messaging/)). The main drawbacks of RCS are that carrier support is patchy (messages fallback to SMS if RCS is not supported) and there is no end-to-end encryption, at the time of writing ([theverge.com/2020/5/27/21271186/google-rcs-t-mobile-encryption-ccmi-universal-profile](https://www.theverge.com/2020/5/27/21271186/google-rcs-t-mobile-encryption-ccmi-universal-profile)).

[[vulnerability|vulnerabilities]] in processing attachments and rich formatting have resulted in DoS attacks against certain handsets in the past, so it is important to keep devices patched against known threats.

**Push notifications** are store services (such as Apple Push Notification Service and Google Cloud to Device Messaging) that an app or website can use to display an alert on a mobile device. Users can choose to disable notifications for an app, but otherwise the app developer can target notifications to some or all users with that app installed. Developers need to take care to properly secure the account and services used to send push notifications. There have been examples in the past of these accounts being hacked and used to **send fake communications**.
# FIRMWARE OVER-THE-AIR UPDATES

A baseband update modifies the firmware of the radio modem used for cellular, Wi-Fi, Bluetooth, NFC, and GPS connectivity. The radio firmware in a mobile device contains an operating system that is separate from the end-user operating system (for example, Android or iOS). The modem uses its own baseband processor and memory, which boots a real-time operating system ([[RTOS]]). An RTOS is often used for time-sensitive embedded controllers, of the sort required for the modulation and frequency shifts that underpin radio-based connectivity.

The procedures for establishing radio connections are complex and require strict compliance with regulatory certification schemes, so incorporating these functions in the main OS would make it far harder to bring OS updates to market. Unfortunately, baseband operating systems have been associated with several [[vulnerability|vulnerabilities]] over the years, so it is imperative to ensure that updates are applied promptly. These updates are usually pushed to the handset by the device vendor, often as part of OS upgrades. The updates can be delivered wirelessly, either through a Wi-Fi network or the data connection, referred to as over-the-air (OTA). A handset that has been jailbroken or rooted might be able to be configured to prevent baseband updates or apply a particular version manually, but in the general course of things, there is little reason to do so.

There are various ways of exploiting [[vulnerability|vulnerabilities]] in the way these updates work. A well-resourced attacker can create an "evil base station" using a Stingray/International Mobile Subscriber Identity ([[IMSI]]) catcher. This will allow the attacker to identify the location of cell devices operating in the area. In some circumstances it might be possible to launch a man-in-the-middle  [[MITM]] attack and abuse the firmware update process to compromise the phone.
# MICROWAVE RADIO CONNECTION METHODS

Cellular networks are microwave radio networks provisioned for multiple subscribers. Microwave radio is also used as a backhaul link from a cell tower to the service provider's network. These links are important to 5G, where many relays are required and provisioning fiber optic cabled backhaul can be difficult. Private microwave links are also used between sites. A microwave link can be provisioned in two modes:

-   **Point-to-point** (P2P) microwave uses high-gain antennas to link two sites. "High-gain" means that the antenna is highly directional. Each antenna is pointed directly at the other. In terms of security, this makes it difficult to eavesdrop on the signal, as an intercepting antenna would have to be positioned within the direct path. The satellite modems or routers are also normally paired to one another and can use over-the-air encryption to further mitigate against snooping attacks.
-   **Point-to-multipoint** (P2M) microwave uses smaller sectoral antennas, each covering a separate quadrant. Where P2P is between two sites, P2M links multiple sites or subscriber nodes to a single hub. This can be more cost-efficient in high density urban areas and requires less radio spectrum. Each subscriber node is distinguished by multiplexing. Because of the higher risk of signal interception compared to P2P, it is crucial that links be protected by over-the-air encryption.

Multipoint can be used in other contexts. For example, Bluetooth supports a multipoint mode. This can be used to connect a headset to multiple sources (a PC and a smartphone, for instance) simultaneously.
