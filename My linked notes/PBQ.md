# 04B
![Pasted image 20220518141305.png](app://local/C:/Users/Jamie/Documents/SercurityPlus/My%20linked%20notes/assets/Pasted%20image%2020220518141305.png?1652897585051)

## Scenario 1
**Victim's Defenses**:  Network administration and access based on [[least privilege]]: use of  multi - [[factor authentication]]
**Victim's Vulnerabilities:** MS office [[misconfigurations]]; Adobe products lacking latest security patches
**Malicious Actor's Goal**:  Intellectual property theft.  Victim worked from home.

**Malware Type:** Trojans
**Attack Vector:** Malicious.pdf [[file]]
**Delivery Method:** Phishing or hoax email
**Payload:** keylogger

## Scenario 2
**Victim's Defenses**:  VPNs updated with latest patches; extensive network security monitoring capabilities
**Victim's Vulnerabilities:** MS products lacking latest security patches:  MS Office docs with embedded content ([[OLE]]) allowed
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
- Someone can't visit a website using an IP Address
	- Likely Issue:  The cert is configured with a [[FQDN]]
	- Likely Solution:  Connect using the FQDN.