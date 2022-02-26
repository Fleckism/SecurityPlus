---
tags: [A_D, GRC]
---
Asymmetric
- public and private key **pair**(aka **public key**)
- Each key is capable of **reversing** the operation of its pair
- Message much be smaller than key size
- Inefficient with large amounts of data
- The holder of the private key cannot be impersonated
> ==Utilized:== 
> - authentication (aka prove identity) and [[non-repudiation]]
> - key agreement and exchange
> - When paired with [[hash|hashing]] can prove [[Integrity]] 


==Key agreement/exchange refers to settling on a secret symmetric key to use for bulk encryption without anyone else discovering it.==

Authentication and non-repudiation depend on the recipient not being able to encrypt the message, or the recipient would be able to impersonate the sender. This means that to support authentication and non-repudiation, recipients must be able to use the cryptographic process to decrypt authentication and integrity data, but not to encrypt it. This use case is supported by asymmetric encryption ciphers and public/private key pairs.