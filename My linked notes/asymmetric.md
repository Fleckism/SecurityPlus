**A**symmetric [[encryption]] [[cipher]](aka **public key**)
- 1 public and  1 private key **pair**
- Each key is capable of **reversing** the operation of its pair
- Message must be smaller than key size
- Inefficient with large amounts of data
- **vulnerable** to man-in-the-middle attacks([[MITM]])
- The holder of the private key cannot be impersonated
- Utilized for:
	-  authentication (aka prove identity) and [[non-repudiation]]
	-  key agreement and exchange
	-  When paired with [[hash|hashing]] can prove [[Integrity]] 

>Consequently, [[asymmetric]] encryption is mostly used for [[authentication]] and [[non-repudiation]] and for **key agreement and exchange**. Key agreement/exchange refers to settling on a secret **symmetric** key to use for bulk encryption without anyone else discovering it.

Contrast to [[symmetric]]

When paired together public/private key pairs.  Each key can reverse the cryptographic operation performed by it's pair but cannot reverse an operation performed by itself.  The private key must be kept secret by the owner, but the public key is designed to be widely distributed.  The private key cannot determined from the public key, given a sufficient key size.
## Long
**The basic problem with public key cryptography is that you may not really know with whom you are communicating. The system is vulnerable to man-in-the-middle attacks([[MITM]])**. 

[[Authentication]] and non-repudiation depend on the recipient not being able to encrypt the message, or the recipient would be able to impersonate the sender. This means that to support authentication and non-repudiation, recipients must be able to use the cryptographic process to decrypt authentication and integrity data, but not to encrypt it. This use case is supported by asymmetric encryption ciphers and public(asymmetric) / private(symmetric) key pairs.

# ugh
Public key cryptography (public and private keys) can be used to authenticate a sender. Combine this with a hash output of the message and a secret (or private) key to create a message authentication code (MAC) to validate the integrity of the message.

A key exchange system known as a digital envelope or hybrid encryption combines the bulk encryption capabilities of symmetric encryption with the authentication capability of public key cryptography.

Asymmetric encryption is also called public key cryptography. A digital envelope allows the sender and recipient to exchange a symmetric encryption key securely by using public key cryptography.

Hashing proves integrity by computing a unique checksum from input. Digital envelope is another term for the hybrid encryption that combines public key encryption and symmetric encryption.

#A_D 
#GRC 
#vulnerability 
