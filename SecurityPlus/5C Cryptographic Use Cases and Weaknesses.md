---
tags: [A_D, Implementation,section]
---

## EXAM OBJECTIVES COVERED

1.2 Given a scenario, **analyze**(= Implementation) potential indicators to determine the type of attack

2.8 Summarize the basics of cryptographic concepts

There are many individual [[symmetric]] and [[asymmetric]] [[cipher]] algorithms and hash functions. Characteristics of these ciphers make them better suited to meeting constraints, such as use on battery-powered devices. Some of the ciphers and implementations of ciphers within products can exhibit weaknesses that make them unsuitable for use. It is important that you be able to summarize these use cases and weaknesses so that you can deploy [[security control|controls]] that fit their purpose.

## CRYPTOGRAPHY SUPPORTING [[AUTHENTICATION]] AND [[NON-REPUDIATION]]

A single [[hash]] function, symmetric cipher, or asymmetric cipher is called a **cryptographic primitive**. A complete [[cryptographic]] system or product is likely to use multiple cryptographic primitives, such as within a cipher suite. The properties of different symmetric/asymmetric/hash types and of specific ciphers for each type impose limitations on their use in different contexts and for different purposes.

If you are able to [[encryption|encrypt]] a message in a particular way, it follows that the recipient of the message knows with whom he or she is communicating (that is, the sender is authenticated). This means that encryption can form the basis of identification, authentication, and access control systems.

![Screenshot of browser with web page loaded and a pop-up with headings "Website identification" and "Website permissions", brief content, and links.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2286-1599771797805.png)

Encryption allows subjects to identify and authenticate themselves. The subject could be a person, or a computer such as a web server.

[[Non-repudiation]] **is linked to identification and authentication**. It is the concept that the sender cannot deny sending the message. If the message has been encrypted in a way known only to the sender, it follows that the sender must have composed it.

Authentication and non-repudiation depend on the recipient not being able to encrypt the message, or the recipient would be able to impersonate the sender. **This means that to support authentication and non-repudiation, recipients must be able to use the cryptographic process to decrypt authentication and integrity data, but not to encrypt it.** This use case is supported by [[asymmetric]] encryption ciphers and public/private key pairs.

To use a key pair, the user or server generates the linked keys. The private key is stored securely and protected from use by others by the account password. It is critical that only the user or server be able to use the private key. **The public key is given to clients or correspondents, usually in the form of a digital certificate.**

When the user or server needs to [[Authentication|authenticate]], it encrypts some agreed hashed data using the private key and sends it to the client as a digital signature. The client should be able to decrypt the signature using the public key and derive the same hash value.
## CRYPTOGRAPHY SUPPORTING CONFIDENTIALITY

Cryptography removes the need to store or transfer messages over secure media. It does not matter if a ciphertext is stolen or intercepted because the [[threat actor]] will not be able to understand or change what has been stolen. **This use of cryptography fulfils the goal of** [[confidentiality]]. For this use case, you cannot simply use asymmetric encryption and private/public key pairs, because the algorithm cannot encrypt large amounts of data efficiently. For example, the [[RSA]] asymmetric cipher has a maximum message size of the key size (in bytes) minus 11. A key size of 2048 bits allows a maximum message size of 245 bytes: (2048/8) − 11. The computational overhead of using this type of algorithm to encrypt the contents of a disk or stream of network traffic is far too high.

Therefore, bulk data [[encryption]] uses a [[symmetric]] cipher, such as [[AES]]. A _symmetric [[cipher]]_ can encrypt and decrypt data files and streams of network traffic quickly. The problem is that distributing a symmetric key securely is challenging. The more people who know the key value, the weaker the [[confidentiality]] property is. The risks of a threat actor obtaining the key grow exponentially. Luckily, symmetric keys are only 128 bits or 256 bits long, and so can easily be encrypted using a public key. Consequently, most [[cryptographic]] systems use both symmetric and asymmetric encryption.

[[Encryption]] supporting confidentiality is used for both  

-   **data-at-rest (file encryption)**—the user is allocated an [[asymmetric]] cipher key pair. The private key is written to secure storage—often a trusted platform module ([[TPM]])—and is only available when the user has [[Authentication|authenticated]] to his or her account. The public key is used to encrypt a randomly generated [[AES]] cipher key. When the user tries to encrypt or decrypt files, the AES cipher key is decrypted using the private key to make it available for the encryption or decryption operation.
-   **data-in-transit (transport encryption)**—this uses either digital envelopes or perfect forward secrecy. For HTTPS, a web server is allocated a key pair and stores the private key securely. The public key is distributed to clients via a digital certificate. The client and server use the **key pair** to exchange or agree on one or more AES cipher keys to use as session keys.



## CRYPTOGRAPHY SUPPORTING INTEGRITY AND RESILIENCY

[[Integrity]] is proved by hashing algorithms, which allow two parties to derive the same checksum and show that a message or data has not been tampered with. A basic hash function can also be used with a shared secret to create a message authentication code ([[MAC]]), which prevents a [[MITM|man-in-the-middle]] tampering with the checksum.

As well as providing integrity at the level of individual messages, cryptography can be used to design highly resilient control systems. A **control system** is one with multiple parts, such as sensors, workstations, and servers, and complex operating logic. A system is seen as resilient if, when a compromise of part of the system, does not allow the compromise of the whole system. Cryptography assists this goal by ensuring the [[authentication]] and [[integrity]] of messages delivered over the control system.

Integrity and resiliency are also an issue for computer code. If a [[threat actor]] has administrator privileges, they can change the operation of legitimate code to make it work as malware. A developer can make tampering more difficult using obfuscation. Obfuscation is the art of making a message difficult to understand. Obfuscated source code is rewritten in a way that does not affect the way the computer compiles or executes the code, but makes it difficult for a person reading the code to understand how it works. 

Cryptography is a very effective way of obfuscating a message, but unfortunately, it is too effective in the case of source code because it also means the code cannot be understood (executed) by the computer. At some point, the code must be decrypted to be executed. The key used for decryption usually needs to be bundled with the source code, and this means that you are relying on security by obscurity rather than strong cryptography. **Attempts to protect an embedded key while preserving the functionality of the code—known as _white box cryptography_**—have all been broken. There are no commercial solutions currently available to overcome this problem, but the subject is one of much research interest.

## CRYPTOGRAPHIC PERFORMANCE LIMITATIONS 

Differences between [[cipher|ciphers]] make them more or less useful for resource-constrained environments. The main performance factors are as follows:

-   **Speed**—for symmetric ciphers and hash functions, _speed_ is the amount of data per second that can be processed. Asymmetric ciphers are measured by operations per second. Speed has the most impact when large amounts of data are processed.
-   **Time/latency**—for some use cases, the time required to obtain a result is more important than a data rate. For example, when a secure protocol depends on ciphers in the handshake phase, no data transport can take place until the handshake is complete. This latency, measured in milliseconds, can be critical to performance.
-   **Size**—the security of a cipher is strongly related to the size of the **key**, with longer keys providing better security. **Note that the key size cannot be used to make comparisons between [[algorithm|algorithms]].** For example, a 256-bit [[ECC]] key is stronger than a 2048-bit [[RSA]] key. Larger keys will increase the computational overhead for each operation, reducing speed and increasing latency.
-   **Computational overheads**—in addition to key size selection, different ciphers have unique performance characteristics. Some ciphers require more CPU and memory resources than others, and are less suited to use in a resource-constrained environment.

In selecting a product or individual cipher for a particular use case, a tradeoff must be achieved between the demand for the best security available and the resources available for implementation.

-   **Low power devices**—some technologies or ciphers configured with longer keys require more processing cycles and memory space. This makes them slower and means they consume more power. Consequently, some algorithms and key strengths are unsuitable for handheld devices and embedded systems, especially those that work on battery power. Another example is a contactless smart card, where the card only receives power from the reader and has fairly limited storage capacity, which affects the maximum key size supported.
-   **Low latency uses**—this can impact protocol handshake setup times. A longer handshake will manifest as delay for the user, and could cause timeout issues with some applications. Also, if cryptography is deployed with a real time-sensitive channel, such as voice or video, the processing overhead on both the transmitter and receiver must be low enough not to impact the quality of the signal.


## CRYPTOGRAPHIC SECURITY LIMITATIONS

Resource constraints may require you to make a tradeoff between security and performance, but you cannot trade too far. 

### Entropy and Weak Keys

[[Entropy]] is a measure of disorder. A plaintext will usually exhibit low entropy as it represents a message in a human language or programming language or data structure. The plaintext must be ordered for it to be intelligible to a person, computer processor, or database. One of the requirements of a strong cryptographic algorithm is to produce a disordered [[ciphertext]]. Put another way, the ciphertext must exhibit a high level of entropy. If any elements of order from the plaintext persist, it will make the ciphertext vulnerable to cryptanalysis, and the algorithm can be shown to be weak.

It is important to realize that just because an algorithm, such as [[AES]], is considered strong does not mean that the [[implementation]] of that [[cipher]] in a programming library is also strong. The implementation may have weaknesses. It is vital to monitor the status of this type of programming code and apply updates promptly. If a weakness is revealed, any keys issued under the weak version must be replaced and data re-encrypted.

A weak key is one that produces ciphertext that is lower entropy than it should be. If a key space contains weak keys, the technology using the cipher should prevent use of these keys. [[DES]] and [[RC4]] are examples of algorithms known to have weak keys. The way a cipher is implemented in software may also lead to weak keys being used. An example of this is a bug in the pseudo-random number generator for the OpenSSL server software for Debian Linux, discovered in 2008 ([wiki.debian.org/SSLkeys](https://wiki.debian.org/SSLkeys)). A weak number generator leads to many published keys sharing a common factor. A cryptanalyst can test for the presence of these factors and derive the whole key much more easily. Consequently, the true random number generator ([[TRNG]]) or pseudo [[RNG]] ([[PRNG]]) module in the cryptographic implementation is critical to its strength.

![Screenshot with text including "Please select what kind of key you want" and 4 options; keysize and how long the key should be valid, and user ID.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3571-1599771797891.png)

Pseudo RNG working during key generation using [[GPG]]. This method gains entropy from user mouse and keyboard usage.

You can read more about true versus pseudo random number generation at [random.org](https://www.random.org/).

### Predictability and Reuse

_Predictability_ is a weakness in either the cipher operation or within particular key values that make a ciphertext lower entropy and vulnerable to cryptanalysis. Reuse of the same key within the same session can cause this type of weakness. The RC4 stream cipher and some chained block modes of operation are not as secure as other cipher modes, because they exhibit predictability. Often, it is necessary to use an additional random or pseudo-random value in conjunction with the cipher:

-   Nonce—the principal characteristic of a nonce is that it is never reused ("number used once") within the same scope (that is, with the same key value). It could be a random or pseudo-random value, or it could be a counter value.
-   Initialization vector ([[IV]])—the principal characteristic of an IV is that it is random (or pseudo-random). There may also be a requirement that an IV not be reused (as with a nonce), but this is not the primary characteristic.
-   Salt—this is also a random or pseudo-random number or string. The term _salt_ is used specifically in conjunction with [[hash|hashing]] password values.

## LONGEVITY AND CRYPTOGRAPHIC ATTACKS 

Use of weak cipher suites and implementations can represent a critical [[vulnerability]] for an organization. It means that data that it is storing and processing may not be secure. It may also allow a malicious attacker to masquerade as it by creating spoofed digital certificates, causing huge reputational damage. 

Weaknesses in certain ciphers make some unsafe to use and some that are considered likely to be unsafe in the near-term or medium-term future. In one sense, _longevity_ is a measure of the confidence that people have in a given cipher. Cryptanalysis is undertaken on encryption systems with the purpose of trying to detect weaknesses. However, if weaknesses discovered in a particular cipher or the implementation of a cipher under research conditions lead to the deprecation of that algorithm, that does not necessarily mean that the system is immediately vulnerable in practice. 

RC4 and DES/3DES are already deprecated. RSA is seen as approaching the end of its usefulness, with [[ECC]] and other algorithms offering better security and performance characteristics ([thesslstore.com/blog/is-it-still-safe-to-use-rsa-encryption](https://www.thesslstore.com/blog/is-it-still-safe-to-use-rsa-encryption/)). MD5 and SHA-1 have known weaknesses, but are not necessarily unsecure if compatibility is an overriding concern.

In another sense, _longevity_ is the consideration of how long data must be kept secure. If you assume that a ciphertext will be exposed at some point, how long must that ciphertext resist cryptanalysis? For example, imagine an NSA operative's laptop is stolen. The thief cannot hope to break the encryption with current computing resources, but how long must that encryption mechanism continue to protect the data? If advances in cryptanalysis will put it at risk within 5 years, or 10 years, or 20 years, could a more secure algorithm have been chosen? There is always a tradeoff among security, cost, and interoperability. Malicious mathematical attacks are difficult to launch, and the chances of success against up-to-date, proven technologies and standards are remote. If a deprecated algorithm is in use, there is no need for panic, but there will be a need for a plan to closely monitor the affected systems and to transition to better technologies as quickly as is practical.


## MAN-IN-THE-MIDDLE AND DOWNGRADE ATTACKS

Cryptographic attacks are used to try to intercept confidential data or to spoof cryptographic credentials, such as a digital certificate. Some of these attacks depend on capturing the communications between two parties. They do not break the cryptographic system but exploit vulnerabilities in the way it is used. A _man-in-the-middle ([[MITM]])_ attack is typically focused on public key cryptography.

1.  Mallory eavesdrops the channel between Alice and Bob and waits for Alice to request Bob's public key.
2.  Mallory intercepts the communication, retaining Bob's public key, and sends Mallory's public key to Alice.
3.  Alice uses Mallory's key to encrypt a message and sends it to Bob.
4.  Mallory intercepts the message and decrypts it using Mallory's private key.
5.  Mallory then encrypts a message (possibly changing it) with Bob's public key and sends it to Bob, leaving Alice and Bob oblivious to the fact that their communications have been compromised.

This [[attack]] is prevented by using secure authentication of public keys, such as associating the keys with certificates. This should ensure that Alice rejects Mallory's public key.

**A downgrade attack can be used to facilitate a man-in-the-middle attack by requesting that the server use a lower specification protocol with weaker ciphers and key lengths. For example, rather than use TLS 1.3, as the server might prefer, the client requests the use of SSL. It then becomes easier for Mallory to forge the signature of a certificate authority that Alice trusts and have Alice trust Mallory's public key.**

## KEY STRETCHING AND SALTING

[[Entropy]] is a concern whenever a cryptographic system makes use of user-generated data, such as a password. Users tend to select low entropy passwords, because they are easier to remember. A couple of technologies try to compensate for this. 

### Key Stretching

Key stretching takes a key that's generated from a user password and repeatedly converts it to a longer and more random key. The initial key may be put through thousands of rounds of hashing. This might not be difficult for the attacker to replicate so it doesn't actually make the key stronger, but it slows the attack down, as the attacker has to do all this extra processing for each possible key value. Key stretching can be performed by using a particular software library to hash and save passwords when they are created. The Password-Based Key Derivation Function 2 ([[PBKDF2]]) is very widely used for this purpose, notably as part of Wi-Fi Protected Access ([[WPA]]).

### Salting

Passwords stored as hashes are vulnerable to brute force and dictionary attacks. A password hash cannot be decrypted; [[hash]] functions are one-way. However, an attacker can generate hashes to try to find a match for password hash captured from network traffic or password file. A brute force attack simply runs through every possible combination of letters, numbers, and symbols. A dictionary attack creates hashes of common words and phrases.

Both these attacks can be slowed down by adding a salt value when creating the hash, so you compute:

(salt + password) * SHA = hash

The salt is not kept secret, because any system verifying the hash must know the value of the salt. It simply means that an attacker cannot use pre-computed tables of hashes. The hash values must be recompiled with the specific salt value for each password.

##  COLLISIONS AND THE BIRTHDAY ATTACK

A birthday [[attack]] is a type of brute force attack aimed at exploiting collisions in hash functions. A collision is where a function produces the same hash value for two different plaintexts. This type of attack can be used for the purpose of forging a digital signature. The attack works as follows:

1.  The attacker creates a malicious document and a benign document that produce the same hash value. The attacker submits the benign document for signing by the target.
2.  The attacker then removes the signature from the benign document and adds it to the malicious document, forging the target's signature.

The trick here is being able to create a malicious document that outputs the same hash as the benign document. The birthday paradox means that the computational time required to do this is less than might be expected. The birthday paradox asks how large must a group of people be so that the chance of two of them sharing a birthday is 50%. The answer is 23, but people who are not aware of the paradox often answer around 180 (365/2). The point is that the chances of someone sharing a particular birthday are small, but the chances of any two people sharing any birthday get better and better as you add more people: 1 – (365 * (365 − 1) * (365 – 2) ... * (365 – (_N_ − 1)))/365_N_.

To [[exploit]] the paradox, the attacker creates multiple malicious and benign documents, both featuring minor changes (punctuation, extra spaces, and so on). Depending on the length of the hash and the limits to the non-suspicious changes that can be introduced, if the attacker can generate sufficient variations, then the chance of matching hash outputs can be better than 50%.

This means that to protect against the birthday attack, encryption [[algorithm]] (keyed hash algorithm) must demonstrate collision avoidance (that is, to reduce the chance that different inputs will produce the same output). To exploit the birthday paradox, the attacker generally has to be able to manipulate both documents/messages, referred to as a _chosen prefix attack_ ([sha-mbles.github.io](https://sha-mbles.github.io/)). The birthday paradox method has been used successfully to exploit collisions in the MD5 function to create fake digital certificates that appear to have been signed by a certificate authority in a trusted root chain ([trailofbits.files.wordpress.com/2012/06/flame-md5.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/flame-md5.pdf)).