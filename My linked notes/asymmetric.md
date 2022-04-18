---
tags: [A_D, GRC]
#A_D 
#GRC 
#vulnerability 

---
Asymmetric [[encryption]] [[cipher]](aka **public key**)
- public and private key **pair**
- Each key is capable of **reversing** the operation of its pair
- Message must be smaller than key size
- Inefficient with large amounts of data
- **vulnerable** to man-in-the-middle attacks([[MITM]])
- The holder of the private key cannot be impersonated
- Utilized for:
	-  authentication (aka prove identity) and [[non-repudiation]]
	-  key agreement and exchange
	-  When paired with [[hash|hashing]] can prove [[Integrity]] 



Consequently, [[asymmetric]] encryption is mostly used for authentication and non-repudiation and for **key agreement and exchange**. Key agreement/exchange refers to settling on a secret **symmetric** key to use for bulk encryption without anyone else discovering it.

**The basic problem with public key cryptography is that you may not really know with whom you are communicating. The system is vulnerable to man-in-the-middle attacks([[MITM]])**. 

[[Authentication]] and non-repudiation depend on the <mark style="background: #FFB8EBA6;">recipient not being able to encrypt the message, or the recipient would be able to impersonate the sender.</mark> This means that to support authentication and non-repudiation, recipients must be able to use the cryptographic process to decrypt authentication and integrity data, but not to encrypt it. This use case is supported by asymmetric encryption ciphers and public/private key pairs.