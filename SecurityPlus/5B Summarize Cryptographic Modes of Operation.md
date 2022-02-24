---
tags: [A_D, secondTag]
---

## EXAM OBJECTIVES COVERED

2.8 Summarize the basics of cryptographic concepts

A **mode of operation** is a means of using a cipher within a product to achieve a security **goal**, such as confidentiality or integrity. Being able to summarize modes of operation will help you to implement and support [[security control]]s such as digital signatures and transport encryption.
 
## DIGITAL SIGNATURES

**Public key cryptography** can authenticate a sender, because they control a private key that encrypts messages in a way that no one else can. Public key cryptography can only be used with very small messages, however. **Hashing** proves integrity by computing a unique checksum from input. **These two cryptographic functions can be combined to authenticate a sender and prove the integrity of a message, with a digital signature.** The following process is used to create a digital signature using [[RSA]] encryption:

1.  Alice (the sender) creates a digest of a message, using a pre-agreed hash algorithm, and encrypts the digest using Alice’s private key. This creates Alice’s digital signature.
2.  Alice attaches the digital signature to the original message and sends both the message and public key to Bob (the receiver).
3.  Bob decrypts the digital signature using Alice's public key, resulting in the digest of the message.
4.  Bob then creates a [[digest]] of the message, using the same pre-agreed hash algorithm that Alice used. Bob compares both digests.

If the two digests (or hash values) are the same, then the data has not been tampered with during transmission, and Alice's identity is guaranteed. If the message changed or a malicious user had intercepted the message and used a different private key, the digests would not match, and the message would not be trusted.

Message authentication and integrity using digital signatures. (Images © 123RF.com.)

It is important to remember that a **digital signature is a hash that is then encrypted using a private key.** Without the encryption, another party could easily intercept the file and the hash, modify the file and compute a new hash, and then send the modified file and hash to the recipient. It is also important to realize that the recipient must have some means of validating that the public key really was issued by Alice. **Also note that digital signatures do not provide any message confidentiality** (?).

The Digital Signature Algorithm ([[DSA]]) is a slightly different format for achieving the same sort of goal. DSA uses elliptic curve cryptography ([[ECC]]) rather than the RSA cipher.

## DIGITAL ENVELOPES AND KEY EXCHANGE

**Symmetric encryption is the only practical means of encrypting and decrypting large amounts of data (bulk encryption),** but it is difficult to distribute the secret key securely. Public key cryptography makes it easy to distribute a key, but can only be used efficiently with small amounts of data. Therefore, both are used within the same product in a type of key exchange system known as a digital envelope or hybrid encryption. A digital envelope allows the sender and recipient to exchange a symmetric encryption key securely by using public key cryptography:

1.  Alice obtains a copy of Bob's public key.
2.  Alice encrypts her message using a secret key cipher, such as [[AES]]. In this context, the secret key is referred to as a _session key._
3.  Alice encrypts the session key with Bob's public key.
4.  Alice attaches the encrypted session key to the ciphertext message in a digital envelope and sends it to Bob. 
5.  Bob uses his private key to decrypt the session key.
6.  Bob uses the session key to decrypt the ciphertext message.

Key exchange using a digital envelope. (Images © 123RF.com.)

Note that in this process, it is the recipient's public key that is used to perform encryption and the recipient's private key that is used for decryption. The validity of the whole digital envelope can be proved using a message authentication code. 

In all these implementations, it is critical that the private key be kept secure and available only to the authorized user.

## DIGITAL CERTIFICATES

When using public/private key pairs, a subject will make his or her public key freely available. This allows recipients of his or her messages to read the digital signature. Similarly, he or she uses the recipient's public key to encrypt a message via a digital envelope. This means that no one other than the intended recipient can read the message.

The question then arises of how anyone can trust the identity of the person or server issuing a public key. One solution is to have a third party, referred to as a _certificate authority ([[CA]]),_ validate the owner of the public key by issuing the subject with a certificate. The certificate is signed by the CA. If the recipient also trusts the CA, they can also trust the public key wrapped in the subject's certificate. The process of issuing and verifying certificates is called _public key infrastructure ([[PKI]])._

## PERFECT FORWARD SECRECY

When using a digital envelope, the parties must exchange or agree upon a bulk encryption secret key, used with the chosen symmetric cipher. In the original implementation of digital envelopes, the server and client exchange secret keys, using the server's RSA key pair to protect the exchange from snooping. In this key exchange model, if data from a session were recorded and then later the server's private key were compromised, it could be used to decrypt the session key and recover the confidential session data.

This risk from [[RSA]] key exchange is mitigated by perfect forward secrecy ([[PFS]]). PFS uses Diffie-Hellman (DH) key agreement to create ephemeral session keys without using the server's private key. Diffie-Hellman allows Alice and Bob to derive the same shared secret just by agreeing some values that are all related by some trapdoor function. In the agreement process, they share some of them, but keep others private. Mallory cannot possibly learn the secret from the values that are exchanged publicly ([en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)). The authenticity of the values sent by the server is proved by using a digital signature.

Using Diffie-Hellman to derive a secret value to use to generate a shared symmetric encryption key securely over a public channel. In computing, _mod_ stands for a modulo operation, which returns the remainder after dividing one number by another.(Images © 123RF.com.)

Using ephemeral session keys means that any future compromise of the server will not translate into an attack on recorded data. Also, even if an attacker can obtain the key for one session, the other sessions will remain confidential. This massively increases the amount of cryptanalysis that an attacker would have to perform to recover an entire "conversation."

[[PFS]] can be implemented using either the Diffie-Hellman Ephemeral mode ([[DHE]] or [[EDH]]) or Elliptic Curve Diffie-Hellman Ephemeral mode ([[ECDHE]]) algorithms. To use PFS, the server and client must negotiate use of a mutually supported cipher suite.

In 2014, a Heartbleed bug was discovered in the way some versions of OpenSSL work that allows remote users to grab 64K chunks of server memory contents ([heartbleed.com](http://heartbleed.com/)). This could include the private key, meaning that any communications with the server could be compromised. The bug had been present for around two years. This illustrates the value of PFS, but ironically many servers would have been updated to the buggy version of OpenSSL to enable support for PFS.

## CIPHER SUITES AND MODES OF OPERATION

In a protocol such as Transport Layer Security ([[TLS]]), the requirements to both authenticate the identity of the server and to encrypt communications between the server and client need to be fulfilled by separate cryptographic products and cipher implementations. The combination of ciphers supported is referred to as a cipher suite. The server and client negotiate mutually compatible cipher suites as part of the TLS handshake.

So far, we have identified two parts of the **cipher suite**:

-   A **signature algorithm**, used to assert the identity of the server's public key and facilitate authentication.
-   A **key exchange/agreement algorithm**, used by the client and server to derive the same bulk encryption symmetric key.

The final part of a cipher suite determines the bulk encryption cipher. When [[AES]] is selected as the symmetric cipher, it has to be used in a mode of operation that supports a stream of network data.

### Cipher Block Chaining (CBC) Mode

The Cipher Block Chaining ([[CBC]]) mode applies an initialization vector ([[IV]]) to the first plaintext block to ensure that the key produces a unique ciphertext from any given plaintext. The output of the first ciphertext block is then combined with the next plaintext block using an XOR operation. This process is repeated through the full "chain" of blocks, which (again) ensures that no plaintext block produces the same ciphertext. CBC needs to use padding to ensure that the data to encrypt is an exact multiple of the block size.

**XOR is a logical operation that outputs 1 only when the inputs are 1 and 0.**

### Counter Mode

Counter mode ([[CTM]]) makes the [[AES]] algorithm work as a stream cipher. Counter mode applies an IV plus an incrementing counter value to the key to generate a keystream. The keystream is then XOR'ed to the data in the plaintext blocks. Each block can be processed individually and consequently in parallel, improving performance. Also, counter modes do not need to use padding. Any unused space in the last block is simply discarded.

## AUTHENTICATED MODES OF OPERATION

Symmetric algorithms do not provide message integrity or authentication. The basic [[CBC]] and counter modes of operation are unauthenticated. While a man-in-the-middle ([[MITM]])cannot decrypt them directly without the secret key, the ciphertexts are vulnerable to arbitrary data being inserted or modified to break the encryption scheme, referred to as a **chosen ciphertext attack**.

### Authenticated Encryption

A message authentication code ([[MAC]]) provides an authentication and integrity mechanism by hashing a combination of the message output and a shared secret key. The recipient can perform the same process using his or her copy of the secret key to verify the data. This type of authenticated encryption scheme is specified in a cipher suite as separate functions, such as "AES CBC with HMAC-SHA." Unfortunately, the implementation of this type of authenticated mode in AES CBC is vulnerable to a type of cryptographic attack called a padding oracle attack ([docs.microsoft.com/en-us/dotnet/standard/security/vulnerabilities-cbc-mode](https://docs.microsoft.com/en-us/dotnet/standard/security/vulnerabilities-cbc-mode)).

### Authenticated Encryption with Additional Data (AEAD)

The weaknesses of [[CBC]] arising from the padding mechanism means that stream ciphers or counter modes are strongly preferred. These use Authenticated Encryption with Additional Data (AEAD) modes of operation. In an [[AEAD]] scheme, the associated data allows the receiver to use the message header to ensure the payload has not been replayed from a different communication stream.

An AEAD mode is identified by a single hyphenated function name, such as AES-GCM or AES-CCM. The ChaCha20-Poly1305 stream cipher has been developed as an alternative to AES.

## 