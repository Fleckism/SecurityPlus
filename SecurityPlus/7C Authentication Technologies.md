---
tags: [firstTag, secondTag]
---
# EXAM OBJECTIVES COVERED

2.4 Summarize authentication and authorization design concepts

3.3 Given a scenario, implement secure network designs (HSM only)

3.8 Given a scenario, implement authentication and authorization solutions 

Authentication technologies can be used as something you have or ownership/possession factor. Many organizations are deploying multifactor authentication systems based on smart cards and USB key fobs. You are likely to have to support the installation and configuration of these technologies during your career.
# SMART-CARD AUTHENTICATION 

Smart-card authentication means programming cryptographic information onto a card equipped with a secure processing chip. The chip stores the user's digital certificate, the private key associated with the certificate, and a personal identification number (PIN) used to activate the card. 

For Kerberos authentication, smart-card logon works as follows: 

1.  The user presents the smart card to a reader and is prompted to enter a PIN.
2.  Inputting the correct PIN authorizes the smart card's cryptoprocessor to use its private key to create a Ticket Granting Ticket (TGT) request, which is transmitted to the authentication server (AS). 
3.  The AS is able to decrypt the request because it has a matching public key and trusts the user's certificate, either because it was issued by a local certification authority or by a third-party CA that is a trusted root CA.
4.  The AS responds with the TGT and Ticket Granting Service (TGS) session key.

"Smart card" can refer to a wide range of different technologies. Secure Kerberos-based authentication requires a card with a cryptoprocessor ([smartcardbasics.com/smart-card-types.html](http://www.smartcardbasics.com/smart-card-types.html)).
# KEY MANAGEMENT DEVICES

When using public key infrastructure (PKI) for smart-card authentication, the security of the private key issued to each user is critical. One problem is that only the user should ever be in ownership of the private key. If the network administrator is able to view these keys, they can impersonate any subject. Various technologies can be used to avoid the need for an administrator to generate a private key and transmit it to the user:

-   Smart card—some cards are powerful enough to generate key material using the cryptoprocessor embedded in the card.
-   USB key—a cryptoprocessor can also be implemented in the USB form factor.
-   Trusted Platform Module (TPM)—a secure cryptoprocessor enclave implemented on a PC, laptop, smartphone, or network appliance. The TPM is usually a module within the CPU. Modification of TPM data is only permitted by highly trusted processes. A TPM can be used to present a virtual smart card ([docs.microsoft.com/en-us/windows/security/identity-protection/virtual-smart-cards/virtual-smart-card-overview](https://docs.microsoft.com/en-us/windows/security/identity-protection/virtual-smart-cards/virtual-smart-card-overview)).

Smart cards, USB keys, and virtual smart cards are provisioned as individual devices. Often keys need to be provisioned to non-user devices too, such as servers and network appliances. A hardware security module (HSM) is a network appliance designed to perform centralized PKI management for a network of devices. This means that it can act as an archive or escrow for keys in case of loss or damage. Compared to using a general-purpose server for certificate services, HSMs are optimized for the role and so have a smaller attack surface. HSMs are designed to be tamper-evident to mitigate risk of insider threat, and can also provide enterprise-strength cryptographically secure pseudorandom number generators (CSPRNGs). HSMs can be implemented in several form factors, including rack-mounted appliances, plug-in PCIe adapter cards, and USB-connected external peripherals.

The FIPS 140-2 scheme provides accreditation for cryptographically strong products. ([entrust.com/digital-security/hsm/solutions/compliance/certifications/fips-140-2](https://www.entrust.com/digital-security/hsm/solutions/compliance/certifications/fips-140-2))

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9286-1599771799417.jpg)

Smart card, smart card reader, and hardware security module. (Images © 123RF.com.)
# EXTENSIBLE AUTHENTICATION PROTOCOL/IEEE 802.1X

The smart-card authentication process described earlier is used for Kerberos authentication where the computer is attached to the local network and the user is logging on to Windows. Authentication may also be required in other contexts:

-   When the user is accessing a wireless network and needs to authenticate with the network database.
-   When a device is connecting to a network via a switch and network policies require the user to be authenticated before the device is allowed to communicate.
-   When the user is connecting to the network over a public network via a virtual private network (VPN).

In these scenarios, the Extensible Authentication Protocol (EAP) provides a framework for deploying multiple types of authentication protocols and technologies. EAP allows lots of different authentication methods, but many of them use a digital certificate on the server and/or client machines. This allows the machines to establish a trust relationship and create a secure tunnel to transmit the user credential or to perform smart-card authentication without a user password.

Where EAP provides the authentication mechanisms, the IEEE 802.1X Port-based Network Access Control (NAC) protocol provides the means of using an EAP method when a device connects to an Ethernet switch port, wireless access point (with enterprise authentication configured), or VPN gateway. 802.1X uses authentication, authorization, and accounting (AAA) architecture:

-   Supplicant—the device requesting access, such as a user's PC or laptop.
-   Network access server (NAS)—edge network appliances, such as switches, access points, and VPN gateways. These are also referred to as _RADIUS clients_ or authenticators.
-   AAA server—the authentication server, positioned within the local network.

With AAA, the NAS devices do not have to store any authentication credentials. They forward this data between the AAA server and the supplicant. There are two main types of AAA server: RADIUS and TACACS+.
# REMOTE AUTHENTICATION DIAL-IN USER SERVICE

The Remote Authentication Dial-in User Service (RADIUS) standard is published as an Internet standard. There are several RADIUS server and client products.

The Network Access Server (NAS)/Network Access Point (NAP) device (RADIUS client) is configured with the IP address of the RADIUS server and with a shared secret. This allows the client to authenticate to the server. Remember that the client is the access device (switch, access point, or VPN gateway), not the user's PC or laptop. A generic RADIUS authentication workflow proceed as follows:

1.  The user's device (the supplicant) makes a connection to the NAS appliance, such as an access point, switch, or remote access server. 

RADIUS authentication with EAP overview. (Images © 123RF.com.)

2.  The NAS prompts the user for their authentication credentials. RADIUS supports PAP, CHAP, and EAP. Most implementations now use EAP, as PAP and CHAP are not secure. If EAP credentials are required, the NAS enables the supplicant to transmit EAP over LAN (EAPoL) data, but does not allow any other type of network traffic.
3.  The supplicant submits the credentials as EAPoL data. The RADIUS client uses this information to create an Access-Request RADIUS packet, encrypted using the shared secret. It sends the Access-Request to the AAA server using UDP on port 1812 (by default).
4.  The AAA server decrypts the Access-Request using the shared secret. If the Access-Request cannot be decrypted (because the shared secret is not correctly configured, for instance), the server does not respond.
5.  With EAP, there will be an exchange of Access-Challenge and Access-Request packets as the authentication method is set up and the credentials verified. The NAS acts as a pass-thru, taking RADIUS messages from the server, and encapsulating them as EAPoL to transmit to the supplicant.
6.  At the end of this exchange, if the supplicant is authenticated, the AAA server responds with an Access-Accept packet; otherwise, an Access-Reject packet is returned.

Optionally, the NAS can use RADIUS for accounting (logging). Accounting uses port 1813. The accounting server can be different from the authentication server.
# TERMINAL ACCESS CONTROLLER ACCESS-CONTROL SYSTEM

RADIUS is used primarily for network access control. AAA services are also used for the purpose of centralizing logins for the administrative accounts for network appliances. This allows network administrators to be allocated specific privileges on each switch, router, access point, and firewall. Whereas RADIUS can be used for this network appliance administration role, the Cisco-developed Terminal Access Controller Access-Control System Plus (TACACS+) is specifically designed for this purpose ([https://www.cisco.com/c/en/us/support/docs/security-vpn/remote-authentication-dial-user-service-radius/13838-10.html](https://www.cisco.com/c/en/us/support/docs/security-vpn/remote-authentication-dial-user-service-radius/13838-10.html)):

-   TACACS+ uses TCP communications (over port 49), and this reliable, connection-oriented delivery makes it easier to detect when a server is down.
-   All the data in TACACS+ packets is encrypted (except for the header identifying the packet as TACACS+ data), rather than just the authentication data. This ensures confidentiality and integrity when transferring critical network infrastructure data.
-   Authentication, authorization, and accounting functions are discrete. Many device management tasks require reauthentication (similar to having to re-enter a password for sudo or UAC) and per-command authorizations and privileges for users, groups, and roles. TACACS+ supports this workflow better than RADIUS.
# TOKEN KEYS AND STATIC CODES

Smart-card authentication works well when you have close control over user accounts and the devices used on the network. Other types of ownership-based authentication technologies use various hardware and software tokens. These avoid some of the management issues of using the digital certificates required by smart-card authentication.

A one-time password (OTP) is one that is generated automatically, rather than being chosen by a user, and used only once. Consequently, it is not vulnerable to password guessing or sniffing attacks. An OTP is generated using some sort of hash function on a secret value plus a synchronization value (seed), such as a timestamp or counter.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2484-1599771799628.png)

Key fob token generator. (Image © 123RF.com.)

The SecurID token from RSA represents one popular implementation of an OTP token key. The device generates a passcode based on the current time and a secret key coded into the device. The code is entered along with a PIN or password known only to the user. Network access devices must be configured with an agent to intercept the credentials and direct them to an Authentication Manager server for validation. This server can integrate with directory products, such as AD.

There are also simpler token keys and smart cards that simply transmit a static token programmed into the device. For example, many building entry systems work on the basis of static codes. These mechanisms are highly vulnerable to cloning and replay attacks.

There are many other ways of implementing hardware token keys. For example, a Fast Identity Online (FIDO) Universal Second Factor (U2F) USB token registers a public key with the authentication service. The authentication mechanism then requires the private key locked to the token, which is authorized using PIN or fingerprint activation ([fidoalliance.org/showcase/fido-u2f-security-key](https://fidoalliance.org/showcase/fido-u2f-security-key/)). This can also be used with the Windows Hello authentication provider ([microsoft.com/security/blog/2019/06/10/advancing-windows-10-passwordless-platform](https://www.microsoft.com/security/blog/2019/06/10/advancing-windows-10-passwordless-platform/)).
# OPEN AUTHENTICATION

The Initiative for Open Authentication (OATH) is an industry body established with the aim of developing an open, strong authentication framework. _Open_ means a system that any enterprise can link into to perform authentication of users and devices across different networks. _Strong_ means that the system is based not just on passwords, but also on 2- or 3-factor authentication or on 2-step verification. OATH has developed two algorithms for implementing one time passwords (OTPs).

### HMAC-Based One-Time Password Algorithm (HOTP)

HMAC-based One-time Password Algorithm (HOTP) is an algorithm for token-based authentication ([https://www.ietf.org/rfc/rfc4226.html](https://www.ietf.org/rfc/rfc4226.html)). The authentication server and client token are configured with the same shared secret. This should be an 8-byte value generated by a cryptographically strong random number generator. The token could be a fob-type device or implemented as a smartphone authentication/authenticator app. The shared secret can be transmitted to the smartphone app as a QR code image acquirable by the phone's camera so that the user doesn't have to type anything. Obviously, it is important that no other device is able to acquire the shared secret. The shared secret is combined with a counter to create a one-time password when the user wants to authenticate. The device and server both compute the hash and derive an HOTP value that is 6-8 digits long. This is the value that the user must enter to authenticate with the server. The counter is incremented by one.

The server is configured with a counter window to cope with the circumstance that the device and server counters move out of sync. This could happen if the user generates an OTP but does not use it, for instance.

### Time-Based One-Time Password Algorithm (TOTP)

The Time-based One-time Password Algorithm (TOTP) is a refinement of the HOTP ([https://datatracker.ietf.org/doc/html/rfc6238](https://nam02.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdatatracker.ietf.org%2Fdoc%2Fhtml%2Frfc6238&data=04%7C01%7Cdandries%40comptia.org%7C79b46abac0f04b29ecae08d9bef00625%7C8c39a7ffe0774d1c9a1c7431fe5eb465%7C0%7C0%7C637750760424782889%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000&sdata=iBZcXWlOthfRUWPX5dGZdB8zh1PoUKo3picunapbngM%3D&reserved=0)). One issue with HOTP is that tokens can be allowed to persist unexpired, raising the risk that an attacker might be able to obtain one and decrypt data in the future. In TOTP, the HMAC is built from the shared secret plus a value derived from the device's and server's local timestamps. TOTP automatically expires each token after a short window (60 seconds, for instance). For this to work, the client device and server must be closely time-synchronized. One well-known implementation of HOTP and TOTP is Google Authenticator.

![Box reads "The code was sent in the SMS text message to your phone number" with a box to enter the code and links to resend or use another 2FA method.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9217-1599771799663.png)

Two-step verification mechanism protecting web application access. The site sends a Time-based One Time Password with a duration of five minutes to the registered cell phone by SMS.
# 2-STEP VERIFICATION

_2-step verification_ or _out-of-band mechanisms_ generate a software token on a server and send it to a resource assumed to be safely controlled by the user. The token can be transmitted to the device in a number of ways:

-   Short Message Service (SMS)—the code is sent as a text to the registered phone number.
-   Phone call—the code is delivered as an automated voice call to the registered phone number.
-   Push notification—the code is sent to a registered authenticator app on the PC or smartphone.
-   Email—the code is sent to a registered email account.

These mechanisms are sometimes also described as _2-factor authentication (2FA)._ However, anyone intercepting the code within the time frame could enter it as something you know without ever possessing or looking at the device itself ([auth0.com/blog/why-sms-multi-factor-still-matters](https://auth0.com/blog/why-sms-multi-factor-still-matters/)).
# 
# 
# 
# 
# 
# 
# 
# 
# 
# 
# 
# 
# 
# 
# 