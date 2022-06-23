# 04B
![Pasted image 20220518141305.png](app://local/C:/Users/Jamie/Documents/SercurityPlus/My%20linked%20notes/assets/Pasted%20image%2020220518141305.png?1652897585051)

## Scenario 1
**Victim's Defenses**:  Network administration and access based on [[least privilege]]: use of  multi - [[factor authentication]]
**Victim's [[vulnerability|vulnerabilities]]:** MS office [[misconfigurations]]; Adobe products lacking latest security patches
**Malicious Actor's Goal**:  Intellectual property theft.  Victim worked from home.

**Malware Type:** Trojans
**Attack Vector:** Malicious.pdf [[file]]
**Delivery Method:** Phishing or hoax email
**Payload:** keylogger

## Scenario 2
**Victim's Defenses**:  VPNs updated with latest patches; extensive network security monitoring capabilities
**Victim's [[vulnerability|vulnerabilities]]:** MS products lacking latest security patches:  MS Office docs with embedded content ([[OLE]]) allowed
**Malicious Actor's Goal**: Loss of availability and financial gain by encrypting data

**Malware Type:** Trojan
**Attack Vector:** Malicious MS Office doc
**Delivery Method:** Spear-fishing email
**Payload:** Cryptoransomware [[Ransomware]]

**Forensics**
When reconstructing the attacks, one must first analyze the victim's networks and systems to find attack vectors, delivery methods, and probably payloads.  The [[attack vector]] is how the attacker gained access to the victims' machine. the [[delivery method]] is the route the attack used to place malicious code on the victim's machine.  The [[payload]] is the actual malware involved , tailored to the attacker's objectives.
**Social Engineering**
Threat actors took advantage of the COVID-19 pandemic.  They knew that companies where rushing to institute (setup) WFH initiatives resulting in possible misconfigurations in any systems involved.  Phishing and hoax e-mails campaigns where also more effective because of this new work environment.

#
# 5B How to validate messages for identity and integrity.


![[Pasted image 20220518141053.png]]

- Alice 
	- Creates SHA-1 [[hash]] of original message (Aka) Checksum or message digest
	- Then [[encryption|encrypts]] it with her [[private key]] to create a 
	- [[Digital Signature]] which she attaches to the original message to deliver to
- Bob
	- Decrypts the original message container the
	- Digital Signature using
	- Alice's [[public key]] resulting in the SHA-1 hash of the original message
	- Bob then compares the checksum(digest) if these match [[integrity]] is confirmed, if they do not then the message has been compromised. 

# 6A Implement Certificates and Certificate Authorities

![[PB6 .png]]
Users have issues with certificates
- Someone can't visit a website using an IP Address
	- Likely Issue:  The cert is configured with a [[FQDN]]
	- Likely Solution:  Connect using the FQDN.
- Root Certificate and Secure Certificate G2 are valid
	- Likely Issue:  Client missing chain of trust
	- Install secure CA-G2 Cert (aka intermediate cert)
	- Install root CA-G2 Cert







# 7B Implement Knowledge-Based Authentication
![[PB7.png]]

## Scenario 
Dealing with [[threat intelligence]] you have to reconstruct the methods of attack so that you can attempt to attribute the [[TTPs]] to a group of threat actors.  
- The following victims fell to password attacks

Attacker 1 
- Targeted a privileged user (system administrator) in an organization that relies heavily on current  and legacy MS server technologies. Forensic evidence indicates privilege escalation in which the attacker interacted with windows 10 desktop and windows server 2016 domain controllers used by the sysadmin.  The attacker engaged in enumeration of the Security Account Manager ([[SAM]])  registry hive file and eventually extracted it.

Attacker 2
- Exploited weaknesses in the credentials used by the a privileged database administrator (DBA) with access to the organizations cloud and on-premises Oracle database assets.  The attack had advanced knowledge of Amazon Linux and appeared to mimic customary activity of the DBA.  The penetration testing division of the firm re-created the attack sequence, based on forensic evidence and discovered that the DBAs password could be cracked in a matter of hours, leveraging password/hash reference database files built-in to several penetration testing applications.

Attacker 3
- Targeted a retail business executive with general access under MS Azure AD and several other Azure-based applications.  The penetration testing division of the firm re-created the attack sequence based on forensic evidence and discovered that the executive referenced personal or general details in her credentials. As customary practice, the testers used the pwned passwords file available online from haveibeenpwned.com and successfully cracked the password.



# 9C Implement Secure Wireless Infrastructure
![[Pasted image 20220523191206.png]]
Scenario
- Setup WLAN comprised of enterprise controller and two enterprise Wireless access points ([[WAPs]])
	- 1st AP will be indoors
	- 2nd AP will face a private courtyard in the company building
	- Objective of WLAN is to enforce social distancing
- Security is a high priority classified work on premises 
- Backward compatibility is not allowed.
- Security is enforced over convenience
- WLAN will be segmented and isolated from core corporate network is exclusive to employees
- No guest or guest network

Tasks
- Select an authentication method that enforces the company's existing [[PKI]] infrastructure (**smartcards and other certificates** already used for U.S. government work).
- Enforce usage of **next-generation Wi-Fi** for the strongest possible security.
- Select a channel structure and throughput level that assures the **highest speed and availability possible**.
- Select a strong security mode and encryption algorithms that enforce the highest possible confidentiality and integrity.
- Enforce (enable) protected management frames to adhere to WPA3 standards with SSID hidden (these two factors are non-negotiable).

Review
- Usage of 802.1X EAP-TLS, RADIUS would offer a corporation the ability to apply its existing PKI infrastructure.
- Projects supporting the U.S. Government will have access to digital certificates and smartcards
- EAP-TLS incorporates these and additional authentication methods common in the Department of Defense projects.
- Including PKI to 802.1.X authentication would meet the company's objectives for high authentication security. 802.1X Enterprise is the general term for 802.1X authentication and not a specific implementztion, such as 802.1X EAP-TLS with RADIUS.  PAKE, PASK, SAE and Wi-Fi Enhanced Open are features of WPA2 and WPA3 Personal.
- Wi-Fi 6 or -ax mode, already incorporated in home and enterprise wireless networking products, correlates with improved security fatures offered by WPA3. Moreover, the array of radio bands available for 6GHz (and 5GHz) is much greater than 2.4GHz.  The scenario also specifically stated that backward compatibility to previous Wi-Fi generations is not allowed, in the interest of security, making Wi-Fi 6 the best choice.  The WPA 3 standard mandates the use of Management Protection Frames (MPF) to protect against key recovery attacks. MPF and Simultaneous Authentication of Equals (SAE)- also part of WPA3, help alleviate the problem of attacks leveled against the previous WPA2 4-way handshake process.  The now widely reported KRACK attack method from 2017 specifically targets the WPA2 handshake with replacy techniques proven to be successful.  KRACK reinforced the need for MPF and SAE now available in WPA3
- WPA3 Enterprise adheres to the most up to date encryption, hashing, and digitial signature algorithms available. According to the Wi-Fi Alliance, enterprise security in WPA3 has increased dramatically, including changes such as the minimum required usage of 192-bit AES Galois Counter Mode Protocol (GCMP), among other high bit, high security algorithms.  WPA2 Enterprise contains weaker security features and algorithms, such as 128-bit AES CCMP.  WPA3 Personal is not acceptable for enterprise level security.
- Througput settings would be optimal at a channel width of 80MHz as the scenario required high availability and high speeds.  The 5GHz(and 6GHz) band offers a larger array of radio bands, less congestion, less interference, and faster network performance as compared to the 2.4GHz bands, making 5-6GHz channels the best answer choice.  The wider channel (80MHz compared to 20MHz), the higher the throughput.  As an example, 160MHz channel widths are possible with 5GHz and 6GHz even though 160MHz was not an answer option.