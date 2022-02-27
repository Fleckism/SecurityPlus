---
tags: [A_D, GRC]
---
-  operations performed to [[encoding|encode]] or **decode data**
- The use of a **key with the [[encryption]] cipher** ensures that decryption can only be performed by authorized persons.
- Utilized:
	- Used as a mode of operation to achieve a security goal([[security control|control]])
- **Cipher suite** 
	- A **signature algorithm**, used to assert the identity of the server's public key and facilitate authentication.
	- A **key exchange/agreement algorithm**, used by the client and server to derive the same bulk encryption symmetric key.
	- The final part of a cipher suite determines the bulk encryption cipher.

A **substitution cipher** involves replacing units (a letter or blocks of letters) in the plaintext with different ciphertext. Simple substitution ciphers rotate or scramble letters of the alphabet. For example, ROT13 (an example of a Caesar cipher) rotates each letter 13 places (so A becomes N for instance). The ciphertext "Uryyb Jbeyq" means "Hello World".

**transposition cipher** stay the same in plaintext and ciphertext, but their order is changed, according to some mechanism. Consider how the ciphertext "HLOOLELWRD" has been produced:

H L O O L

E L W R D

The letters are simply written as columns and then the rows are concatenated to make the ciphertext. It's called a rail fence cipher. All modern encryption uses these basic techniques of substitution and transposition, but in much more complex ways.

### Stream Ciphers 
+ each byte or bit of data in the plaintext is encrypted one at a time. 
+ total length of the message is not known. The plaintext is combined with a separate randomly generated message, calculated from the key and an 
+ initialization vector ([[IV]]). The IV ensures the key produces a unique ciphertext from the same plaintext. 
+ The keystream must be unique, so an IV must not be reused with the same key. The recipient must be able to generate the same keystream as the sender and the streams must be synchronized. Stream ciphers might use markers to allow for synchronization and retransmission. Some types of stream ciphers are made self-synchronizing.

In a **symmetric encryption cipher, the same secret key is used to perform both encryption and decryption operations**. 

With an ==asymmetric cipher, operations are performed by two different but related public and private keys in a key pair.== 

**Asymmetric encryption can be used to prove identity.** aka Public key
Consequently, asymmetric encryption is mostly used for authentication and non-repudiation and for key agreement and exchange.

[[RSA]]

The letters are simply written as columns and then the rows are concatenated to make the ciphertext. It's called a **rail fence cipher**. All modern encryption uses these basic techniques of substitution and transposition, but in much more complex ways.

# Full description
