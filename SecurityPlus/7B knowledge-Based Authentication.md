---
tags: [OIR, attack, A_D]
---
# EXAM OBJECTIVES COVERED

1.2 Given a scenario, analyze potential indicators to determine the type of attack

3.8 Given a scenario, implement authentication and authorization solutions 

4.1 Given a scenario, use the appropriate tool to assess organizational security (password crackers only)

**_Knowledge-based authentication_ refers primarily to issuing users with password-based account access mechanisms**. Configuring password-based authentication protocols and supporting users with authentication issues is an important part of the information security role. In this topic, you will learn how some common authentication protocols work and about the ways that they can be put at risk by password cracking techniques.
# LOCAL, NETWORK, AND REMOTE AUTHENTICATION

One of the most important features of an operating system is the **_authentication provider,_ which is the software architecture and code that underpins the mechanism by which the user is authenticated before starting a shell**. This is usually described as a login (Linux) or a logon or sign-in (Microsoft). Knowledge-based authentication, using a password or personal identification number (PIN), is the default authentication provider for most operating systems.

Knowledge-based authentication relies on cryptographic [[hash|hashes]]. A plaintext password is not usually transmitted or stored in a credential database because of the risk of compromise. Instead, the password is stored as a cryptographic hash. When a user enters a password to log in, an authenticator converts what is typed into a hash and transmits that to an authority. The authority compares the submitted hash to the one in the database and authenticates the subject only if they match.

### Windows Authentication

Windows authentication involves a complex architecture of components ([docs.microsoft.com/en-us/windows-server/security/windows-authentication/credentials-processes-in-windows-authentication](https://docs.microsoft.com/en-us/windows-server/security/windows-authentication/credentials-processes-in-windows-authentication)), but the following three scenarios are typical:

-   Windows local sign-in—the Local Security Authority ([[LSA]]) compares the submitted credential to a hash stored in the Security Accounts Manager ([[SAM]]) database, which is part of the registry. This is also referred to as _interactive logon._
-   Windows network sign-in—the LSA can pass the credentials for authentication to a network service. The preferred system for network authentication is based on Kerberos, but legacy network applications might use NT LAN Manager ([[NTLM]]) authentication.
-   Remote sign-in—if the user's device is not connected to the local network, authentication can take place over some type of virtual private network ([[VPN]]) or web portal.

### Linux Authentication

In Linux, local user account names are stored in /etc/passwd. When a user logs in to a local interactive shell, the password is checked against a hash stored in /etc/shadow. Interactive login over a network is typically accomplished using Secure Shell ([[SSH]]). With SSH, the user can be authenticated using cryptographic keys instead of a password.

A pluggable authentication module ([[PAM]]) is a package for enabling different authentication providers, such as smart-card login ([tecmint.com/configure-pam-in-centos-ubuntu-linux](https://www.tecmint.com/configure-pam-in-centos-ubuntu-linux/)). The PAM framework can also be used to implement authentication to network servers.

### Single Sign-On (SSO)

A single sign-on ([[SSO]]) system allows the user to authenticate once to a local device and be authenticated to compatible application servers without having to enter credentials again. In Windows, SSO is provided by the Kerberos framework.
# KERBEROS AUTHENTICATION

Kerberos is a single sign-on network authentication and authorization protocol used on many networks, notably as implemented by Microsoft's Active Directory ([[AD]]) service. Kerberos was named after the three-headed guard dog of Hades (Cerberus) because it consists of three parts. Clients request services from application servers, which both rely on an intermediary—a Key Distribution Center ([[KDC]])—to vouch for their identity. There are two services that make up a KDC: the Authentication Service and the Ticket Granting Service. The KDC runs on [[port]] 88 using [[TCP]] or [[UDP]].

![Diagram of the Kerberos Authentication Service.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8226-1599771799055.png)

Kerberos Authentication Service. (Images © 123RF.com.)

The [[Authentication]] Service is responsible for authenticating user logon requests. More generally, users and services can be authenticated; these are collectively referred to as **_principals**._ For example, when you sit at a Windows domain workstation and log on to a realm (or domain), the first step of logon is to authenticate with a KDC server, implemented as a domain controller.

1.  The client sends the authentication service ([[AS]]) a request for a Ticket Granting Ticket ([[TGT]]). This is composed by encrypting the date and time on the local computer with the user's password hash as the key. 

The password hash itself is not transmitted over the network. Also, although we refer to passwords for simplicity, the system can use other authentication providers, such as smart-card logon.

The Ticket Granting Ticket (TGT; or user ticket) is time-stamped (under Windows, they have a default maximum age of 10 hours). This means that workstations and servers on the network must be synchronized (to within five minutes) or a ticket will be rejected. This helps prevent replay attacks.

2.  The AS checks that the user account is present, that it can decode the request by matching the user's password hash with the one in the Active Directory database, and that the request has not expired. If the request is valid, the AS responds with the following data:

-   Ticket Granting Ticket (TGT)—this contains information about the client (name and IP address) plus a timestamp and validity period. This is encrypted using the KDC's secret key.
-   TGS session key for use in communications between the client and the Ticket Granting Service ([[TGS]]). This is encrypted using a hash of the user's password.

The **TGT is an example of a logical token**. All the TGT does is identify who you are and confirm that you have been authenticated—it does not provide you with access to any domain resources.
# KERBEROS AUTHORIZATION 

Presuming the user entered the correct password, the client can decrypt the Ticket Granting Service (TGS) session key but not the TGT. This establishes that the client and KDC know the same shared secret and that the client cannot interfere with the TGT.

1.  To access resources within the domain, the client requests a Service Ticket (a token that grants access to a target application server). This process of granting service tickets is handled by the TGS.
2.  The client sends the TGS a copy of its TGT and the name of the application server it wishes to access plus an authenticator, consisting of a time-stamped client ID encrypted using the TGS session key.  
      
    The TGS should be able to decrypt both messages using the KDC's secret key for the first and the TGS session key for the second. This confirms that the request is genuine. It also checks that the ticket has not expired and has not been used before (replay attack).
3.  The TGS service responds with:

-   Service session key—for use between the client and the application server. This is encrypted with the TGS session key.
-   Service ticket—containing information about the user, such as a timestamp, system IP address, Security Identifier (SID) and the SIDs of groups to which he or she belongs, and the service session key. This is encrypted using the application server's secret key.

![(1) PC requests a service ticket from KDC and (2) presents it to an application server. (3) Mutual authentication may occur before (4) data transfer.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3016-1599771799155.png)

Kerberos Ticket Granting Service. (Images © 123RF.com.)

4.  The client forwards the service ticket, which it cannot decrypt, to the application server and adds another time-stamped authenticator, which is encrypted using the service session key.

5.  The application server decrypts the service ticket to obtain the service session key using its secret key, confirming that the client has sent an untampered message. It then decrypts the authenticator using the service session key.
6.  Optionally, the application server responds to the client with the timestamp used in the authenticator, which is encrypted by using the service session key. The client decrypts the timestamp and verifies that it matches the value already sent, and concludes that the application server is trustworthy.  
      
    This means that the server is authenticated to the client (referred to as _mutual authentication_). This prevents a man-in-the-middle [[MITH]] attack, where a malicious user could intercept communications between the client and server.
7.  The server now responds to client requests (assuming they conform to the server's access control list).

The data transfer itself is not encrypted (at least as part of Kerberos; some sort of transport encryption can be deployed).

One of the noted drawbacks of Kerberos is that the KDC represents a single point-of-failure for the network. In practice, backup KDC servers can be implemented (for example, Active Directory supports multiple domain controllers, each of which are running the KDC service).
# PAP, CHAP, AND MS-CHAP AUTHENTICATION

Kerberos is designed to work over a trusted local network. Several authentication protocols have been developed to work with remote access protocols, where the connection is made over a serial link or virtual private network ([[VPN]]).

### Password Authentication Protocol (PAP)

The Password Authentication Protocol ([[PAP]]) is an unsophisticated authentication method developed as part of the Point-to-Point Protocol ([[PPP]]), used to transfer TCP/IP data over serial or dial-up connections. It is also used as the basic authentication mechanism in HTTP. It relies on clear text password exchange and is therefore obsolete for most purposes, except through an encrypted tunnel.

### Challenge Handshake Authentication Protocol (CHAP)

The Challenge Handshake Authentication Protocol ([[CHAP]]) was also developed as part of PPP as a means of authenticating users over a remote link. CHAP relies on an encrypted challenge in a system called a _three-way handshake._

1.  **Challenge**—the server challenges the client, sending a randomly generated challenge message.
2.  **Response**—the client responds with a hash calculated from the server challenge message and client password (or other shared secret).
3.  **Verification**—the server performs its own hash using the password hash stored for the client. If it matches the response, then access is granted; otherwise, the connection is dropped.

The handshake is repeated with a different challenge message periodically during the connection (although transparent to the user). This guards against _replay attacks,_ in which a previous session could be captured and reused to gain access.

MS-CHAPv2 is Microsoft's implementation of CHAP. Because of the way it uses vulnerable NTLM hashes, MS-CHAP should not be deployed without the protection of a secure connection tunnel so that the credentials being passed are encrypted. 

![Screenshot of Configure Authentication Methods window.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1932-1599771799293.png)

Defining allowed authentication mechanisms on a Windows VPN. (Screenshot used with permission from Microsoft.)
# PASSWORD ATTACKS

When a user chooses a password, **the password is converted to a hash using a cryptographic function,** such as MD5 or SHA. This means that, in theory, no one except the user (not even the system administrator) knows the password, because the plaintext should not be recoverable from the hash. 

### Plaintext/Unencrypted Attacks

A _plaintext/unencrypted attack_ exploits password storage or a network authentication protocol that does not use encryption. Examples include PAP, basic HTTP/FTP authentication, and Telnet. These protocols must not be used. Passwords must never be saved to an unmanaged file. **One common source of credential breaches is passwords embedded in application code that has subsequently been uploaded to a public repository.**

### Online Attacks

An _online password attack_ is where the threat actor interacts with the authentication service directly—a web login form or VPN gateway, for instance. The attacker submits passwords using either a database of known passwords (and variations) or a list of passwords that have been cracked offline.

Also, be aware that there are databases of username and password/password hash combinations for multiple accounts stored across the Internet. These details derive from successful hacks of various companies' systems. These databases can be searched using a site such as [haveibeenpwned.com](https://haveibeenpwned.com/).

An **online password attack can show up in audit logs as repeatedly failed logons and then a successful logon, or as successful logon attempts at unusual times or locations.** Apart from ensuring the use of strong passwords by users, online password attacks can be mitigated by restricting the number or rate of logon attempts, and by shunning logon attempts from known bad IP addresses.

**Note that restricting logons can be turned into a vulnerability as it exposes the account to denial of service attacks. The attacker keeps trying to authenticate, locking out valid users.**

### Password Spraying

Password spraying is a horizontal brute-force online attack. This means that the attacker chooses one or more common passwords (for example, password or 123456) and tries them in conjunction with multiple usernames.

### Offline Attacks 

An _offline attack_ means that the attacker has managed to obtain a database of password hashes, such as %SystemRoot%\System32\config\SAM, %SystemRoot%\NTDS\NTDS.DIT (the Active Directory credential store), or /etc/shadow. Once the password database has been obtained, the password cracker does not interact with the authentication system. **The only indicator of this type of attack (other than misuse of the account in the event of a successful attack) is a file system audit log that records the malicious account accessing one of these files. Threat actors can also read credentials from host memory, in which case the only reliable indicator might be the presence of attack tools on a host.**

If the attacker cannot obtain a database of passwords, a packet sniffer might be used to obtain the client response to a server challenge in a protocol such as [[NTLM]] or [[CHAP]]/MS-CHAP. Although these protocols avoid sending the hash of the password directly, the response is derived from it in some way. Password crackers can exploit weaknesses in a protocol to calculate the hash and match it to a dictionary word or brute force it.
# BRUTE-FORCE AND DICTIONARY ATTACKS

Some password attacks exploit the weak credentials chosen by users. Others can exploit vulnerabilities in the storage mechanism. For example, the Windows SAM database can be configured to store hashes for compatibility with older versions (LM and NTLMv1 hashes). These legacy hashes are cryptographically weak and highly vulnerable to password cracking ([ldapwiki.com/wiki/LM%20hash](https://ldapwiki.com/wiki/LM%20hash)).

### Brute-Force Attack

A brute-force attack attempts every possible combination in the output space in order to match a captured hash and guess at the plaintext that generated it. The output space is determined by the number of bits used by the algorithm (128-bit MD5 or 256-bit SHA256, for instance). The larger the output space and the more characters that were used in the plaintext password, the more difficult it is to compute and test each possible hash to find a match. Brute-force attacks are heavily constrained by time and computing resources, and are therefore most effective at cracking short passwords. **However, brute-force attacks distributed across multiple hardware components, like a cluster of high-end graphics cards, can be successful at cracking longer passwords.**

### Dictionary and Rainbow Table Attacks

A dictionary attack can be used where there is a good chance of guessing the likely value of the plaintext, such as a non-complex password. The software generates hash values from a dictionary of plaintexts to try to match one to a captured hash. **Rainbow table attacks refine the dictionary approach. The attacker uses a precomputed lookup table of all possible passwords** and their matching hashes. Not all possible hash values are stored, as this would require too much memory. **Values are computed in chains, and only the first and last values need to be stored**. The hash value of a stored password can then be looked up in the table and the corresponding plaintext discovered.

**Using a salt to add a random value** to the stored plaintext helps to slow down rainbow table attacks, because the tables cannot be created in advance and must be recreated for each combination of password and salt value. Rainbow tables are also impractical when trying to discover long passwords (more than about 14 characters). **UNIX and Linux password storage mechanisms use salt, but Windows does not**. Consequently, in a Windows environment, it is even more important to enforce strong password policies.

### Hybrid Attack

A hybrid password attack uses a combination of attack methods when trying to crack a password. **A typical hybrid password attack uses a combination of dictionary and brute force attacks**. It is principally targeted against naïve passwords with inadequate complexity, such as james1. The password cracking algorithm tests dictionary words and names in combination with a mask that limits the number of variations to test for, such as adding numeric prefixes and/or suffixes. Other types of algorithms can be applied, based on what hackers know about how users behave when forced to select complex passwords that they don't really want to make hard to remember. Other examples might include substituting "s" with "5" or "o" with "0."
# PASSWORD CRACKERS

Although there are some Windows tools, including the infamous Cain and L0phtcrack ([l0phtcrack.com](https://www.l0phtcrack.com/)) tools, most password crackers run primarily on Linux. Additionally, John the Ripper is an open source tool used for fast password cracking. Its primary focus is UNIX-based operating systems, but also Windows LanMan (LM) hashes. For example, a tool such as Hashcat ([hashcat.net/hashcat](https://hashcat.net/hashcat/)) is run using the following general syntax:

hashcat -m _HashType_ -a _AttackMode_ -o _OutputFile InputHashFile_

The input file should contain hashes of the same type, using the specified format ([hashcat.net/wiki/doku.php?id=example_hashes](https://hashcat.net/wiki/doku.php?id=example_hashes)). Hashcat can be used with a single word list (dictionary mode -a 0) or multiple word lists (combinator mode -a 1). Mode -a 3 performs a brute-force attack, but this can be combined with a mask for each character position. This reduces the key space that must be searched and speeds up the attack. For example, you might learn or intuit that a company uses only letter characters in passwords. By omitting numeric and symbol characters, you can speed up the attack on each hash.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2057-1599771799321.png)

Running a masked brute-force attack—this example is running on a VM, so the recovery rate is very low. (Screenshot hashcat [hashcat.net/hashcat](https://hashcat.net/hashcat/).)
# AUTHENTICATION MANAGEMENT

Users often adopt **poor credential management practices that are very hard to control, such as using the same password for corporate networks and consumer websites.** This makes enterprise network security vulnerable to data breaches from these websites. An authentication management solution for passwords mitigates this risk by using a device or service as a proxy for credential storage. The manager generates a unique, strong password for each web-based account. The user authorizes the manager to authenticate with each site using a master password.

Password managers can be implemented with a hardware token or as a software app:

-   Password key—USB tokens for connecting to PCs and smartphones. Some can use nearfield communications (NFC) or Bluetooth as well as physical connectivity ([theverge.com/2019/2/22/18235173/the-best-hardware-security-keys-yubico-titan-key-u2f](https://www.theverge.com/2019/2/22/18235173/the-best-hardware-security-keys-yubico-titan-key-u2f)).
-   Password vault—software-based password manager, typically using a cloud service to allow access from any device ([pcmag.com/picks/the-best-password-managers](https://www.pcmag.com/picks/the-best-password-managers)). A USB key is also likely to use a vault for backup. Most operating systems and browsers implement native password vaults. Examples include Windows Credential Manager and Apple's iCloud Keychain ([imore.com/icloud-keychain](https://www.imore.com/icloud-keychain)).

Authentication management products can be certified under the Federal Information Processing Standard (FIPS 140-2). This provides assurance that the cryptographic implementation meets a certain level of robustness.
