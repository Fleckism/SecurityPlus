---
tags: [A_D, secondTag]
---
- public and private key pair
- Each key is capable of **reversing** the operation of its pair.
> ==Utilized== authentication (aka prove identity) and [[non-repudiation]]


Authentication and non-repudiation depend on the recipient not being able to encrypt the message, or the recipient would be able to impersonate the sender. This means that to support authentication and non-repudiation, recipients must be able to use the cryptographic process to decrypt authentication and integrity data, but not to encrypt it. This use case is supported by asymmetric encryption ciphers and public/private key pairs.