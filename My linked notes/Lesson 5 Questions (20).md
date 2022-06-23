# 1
Which of the following is NOT a use of cryptography?

3.  Security through obscurity


Solution

Security through obscurity involves keeping something a secret by hiding it. With cryptography, messages do not need to be hidden since they are not understandable unless decrypted.

Non-repudiation is when the sender cannot deny sending the message. If the message has been encrypted in a way known only to the sender, logic follows the sender must have composed it.

Obfuscation is the art of making a message difficult to understand. Cryptography is a very effective way of obfuscating a message by encrypting it.

Resiliency occurs when the compromise of a small part of the system is prevented from allowing compromise of the whole system. Cryptography ensures the authentication and integrity of messages delivered over the control system.
# 2
Evaluate the differences between stream and block ciphers and select the true statement.

3.  A block cipher is padded to the correct size if there is not enough data in the plaintext.


Solution

In a block cipher, if there is not enough data in the plaintext, it's padded to the correct size. Padding is not an issue with streaming, where each byte or bit of data in the plaintext is encrypted one at a time, but it is problematic in dealing with block size.

A block cipher is not suitable to communications, but a stream cipher is, since each byte or bit of data in the plaintext is encrypted one at a time.

Based on the value of the key used, a stream cipher is not subjected to complex transposition and substitution operations.

In a stream cipher, the plaintext is not divided into equal-size blocks.
# 3
Which statement best describes key differences between symmetric and asymmetric cryptographic ciphers?

1.  Symmetric encryption is used for confidentiality, and uses the same key for encryption and decryption.

Solution

Symmetric encryption is used for confidentiality. Symmetric encryption is very fast and useful for bulk encryption of large amounts of data. Symmetric encryption cannot be used for authentication or integrity because both parties know the same key.

Asymmetric encryption uses two different but related public and private keys to perform operations. Asymmetric encryption can be used to prove identity, authentication, non-repudiation, and key agreement and exchange.

Symmetric encryption is very fast and useful for bulk encryption of large amounts of data. Symmetric encryption cannot be used for authentication or integrity, because both parties know the same key.

Asymmetric encryption involves substantial computing overhead compared to symmetric encryption. Asymmetric encryption is inefficient for encrypting or transporting large amounts of data.
# 4
A security technician needs to transfer a large file to another user in a data center. Which statement best illustrates what type of encryption the technician should use to perform the task?


2.  The technician should use asymmetric encryption to verify the data center user’s identity and agree on a symmetric encryption algorithm for the data transfer.


Solution

Asymmetric encryption is used for authentication, non-repudiation, and key agreement and exchange. Symmetric encryption is more efficient for bulk encryption of large amounts of data for transfer.

Symmetric encryption is very fast and used for bulk encryption of large amounts of data. Symmetric encryption cannot be used for authentication or integrity, because both parties know the same key.

Asymmetric encryption can be used to prove identity. Asymmetric encryption involves substantial computing overhead compared to symmetric encryption, so it is inefficient for large data transfers.

Key agreement/exchange refers to settling on a secret symmetric key to use for bulk encryption without anyone else discovering it.
# 5
Which of the following statements best describes the trade-off when considering which type of encryption cipher to use?


2.  Asymmetric encryption requires substantially more overhead computing power than symmetric encryption. Asymmetric encryption is inefficient when transferring or encrypting large amounts of data.


Solution

Asymmetric encryption involves substantially more computing overhead than symmetric encryption. Asymmetric encryption is inefficient when encrypting a large amount of data on a disk or transporting it over a network.

Secure Hash Algorithm (SHA) is considered the strongest hashing algorithm. The most popular variant, SHA-256, produces a 256-bit digest. Other variants produce different-sized outputs; longer digests are considered more secure.

Symmetric encryption is fast and used for bulk encryption of large amounts of data.

The Message Digest Algorithm #5 (MD5) hashing algorithm produces a 128-bit digest. MD5 is not considered to be quite as safe for use as SHA-256, but it might be required for compatibility between security products.

# 6
Compare and contrast the modes of operation for block ciphers. Which of the following statements is true?


2.  CTM mode allows block ciphers to behave like stream ciphers.

Solution

Counter Mode (CTM) combines each block with a counter value. This allows each block to be processed individually and in parallel, improving performance.

Electronic Code Book (ECB) mode applies the same key to each plaintext block, which means identical plaintext blocks can output identical ciphertexts. This is not how a stream cipher behaves.

Counter Mode (CTM) allows block ciphers to behave like stream ciphers, which are faster than block ciphers.

Cipher Block Chaining (CBC) mode applies an Initialization Vector (IV) to the first plaintext block to ensure that the key produces a unique ciphertext from any given plaintext and repeating as a “chain.” This is not how a stream cipher behaves.
# 7
An employee works on a small team that shares critical information about the company's network. When sending emails that have this information, what would be used to provide the identity of the sender and prove that the information has not been tampered with?

2.  Digital signature


Solution

A digital signature proves the identity of the sender of a message and to show that a message has not been tampered with since the sender posted it. This provides authentication, integrity, and non-repudiation.

A private key will encrypt the message. Encrypting the message will scramble the data to protect it during transmission.

The public key is what the recipient will use to decrypt the message. The decryption will allow the recipient to read the data upon receipt.

An RSA Algorithm is what many of the public key cryptography products are based on.
# 8
Which of the following utilizes both symmetric and asymmetric encryption?

1.  Digital envelope

Solution

A digital envelope is a type of key exchange system that utilizes symmetric encryption for speed and asymmetric encryption for convenience and security.

A digital certificate is an electronic document that associates credentials with a public key. This only involves asymmetric encryption.

Digital evidence or Electronically Stored Information (ESI) is evidence that cannot be seen with the naked eye; rather, it must be interpreted using a machine or process. There is no encryption involved.

A digital signature is a message digest encrypted with a user's private key. It uses only asymmetric encryption to prove the identity of the sender of a message and to show a message has not been tampered with.
# 9
When using a digital envelope to exchange key information, the use of what key agreement mitigates the risk inherent in the Rivest–Shamir–Adleman (RSA) algorithm, and by what means?

1.  Perfect forward secrecy (PFS) uses Diffie-Hellman (DH) key agreement to create ephemeral session keys without using the server's private key.



Solution

Perfect forward secrecy (PFS) mitigates the risk from RSA key exchange, using Diffie-Hellman (DH) key agreement to create ephemeral session keys without using the server's private key.

Modes of operation refer to AES use in a cipher suite. Cipher Block Chaining (CBC) mode applies an initialization vector (IV) to a chain of plaintext data and uses padding to fill out blocks of data.

Counter mode makes the AES algorithm work as a stream cipher. Each block of data can be processed individually and in parallel, improving performance.

A certificate authority (CA), validates the owner of a public key, issuing a signed certificate. The process of issuing and verifying certificates is called public key infrastructure (PKI).
# 10
Which two cryptographic functions can be combined to authenticate a sender and prove the integrity of a message?

4.  Public key cryptography and hashing

Solution

Public key cryptography (public and private keys) can be used to authenticate a sender. Combine this with a hash output of the message and a secret (or private) key to create a message authentication code (MAC) to validate the integrity of the message.

A key exchange system known as a digital envelope or hybrid encryption combines the bulk encryption capabilities of symmetric encryption with the authentication capability of public key cryptography.

Asymmetric encryption is also called public key cryptography. A digital envelope allows the sender and recipient to exchange a symmetric encryption key securely by using public key cryptography.

Hashing proves integrity by computing a unique checksum from input. Digital envelope is another term for the hybrid encryption that combines public key encryption and symmetric encryption.
# 11
A system administrator downloads and installs software from a vendor website. Soon after installing the software, the administrator’s computer is taken over remotely. After closer investigation, the software package was modified, probably while it was downloading. What action could have prevented this incident from occurring?

1.  Validate the software using a checksum

Solution

The administrator should have validated the software with a checksum, which uses a cryptographic algorithm to generate a unique hash value based on the file contents. If the file is changed, the checksum of the modified file will not match the original.

A private certificate does not validate software.

A key signing key is associated with Domain Name System Security Extensions (DNSSEC), which validates DNS responses to help mitigate spoofing and poisoning attacks. It does not apply to software.

Kerberos is an authentication service based on a time-sensitive ticket-granting system. It is used to validate users, not software.
# 12
A security team is in the process of selecting a cryptographic suite for their company. Analyze cryptographic implementations and determine which of the following performance factors is most critical to this selection process if users primarily access systems on mobile devices.

3.  Computational overhead

Solution

Some technologies or ciphers configured with longer keys require more processing cycles and memory space, which makes them slower and consume more power. This makes them unsuitable for handheld devices and embedded systems that work on battery power.

Speed is most impactful when processing large amounts of data.

For some use cases, the time required to obtain a result is more important than a data rate. Latency issues may negatively affect performance when an operation or application times out before the authentication handshake.

Cost issues may arise in any decision-making process, but for mobile device cryptography, computing overhead is a primary limiting factor.
# 13
Which statement best illustrates the importance of a strong true random number generator (TRNG) or pseudo-random number generator (PRNG) in a cryptographic implementation?

1.  A weak number generator leads to many published keys sharing a common factor.

Solution

A cryptanalyst can test for the presence of common factors and derive the whole key much more easily. The TRNG or PRNG module in the cryptographic implementation is critical to its strength.

Predictability is a weakness in either the cipher operation or within particular key values that make a ciphertext more vulnerable to cryptanalysis. Reuse of the same key within the same session can cause this weakness.

The principal characteristic of a nonce is that it is never reused ("number used once") within the same key value. A nonce can be a random, pseudo-random, or counter value.

Salt is a random or pseudo-random number or string. The term salt is used specifically in conjunction with hashing password values.
# 14
A client contacts a server for a data transfer. Instead of requesting TLS1.3 authentication, the client claims legacy systems require the use of SSL. What type of attack might a data transfer using this protocol facilitate?

4.  Man-in-the-middle

Solution

A downgrade attack can be used to facilitate a man-in-the-middle attack by requesting that the server use a lower specification protocol with weaker ciphers and key lengths, making it easier for a malicious actor to forge the trusted certificate authority’s signature.

Credential harvesting is a campaign specifically designed to steal account credentials.

Key stretching takes a key that is generated from a user password and repeatedly converts it to a longer and more random key, adding extra layers of processing to a potential attacker’s task.

Phishing is a combination of social engineering and spoofing. It persuades or tricks the target into interacting with a malicious resource disguised as a trusted one, traditionally using email as the vector.
# 15
Which statement describes the mechanism by which encryption algorithms help protect against birthday attacks?

3.  Encryption algorithms add salt when computing password hashes.

Solution

A salt is an additional value stored with the hashed data field. The purpose of salt is to frustrate attempts to crack the hashes of passwords in this case. This will protect against birthday attacks.

Key stretching takes a key that is generated from a user password, and repeatedly converts it to a longer and more random key. The initial key is put through thousands of rounds of hashing to slow down attackers.

Securely authenticating public keys, such as associating the keys with certificates, helps protect against man-in-the-middle attacks.

Blockchain is a concept in which an expanding list of transactional records is secured using cryptography. Each record is referred to as a block and is run through a hash function.
# 16
An attacker uses a cryptographic technology to create a covert message channel in transmission control protocol (TCP) packet data fields. What cryptographic technique does this attack strategy employ?

3.  Steganography

Solution

Steganography obscures the presence of a message and can be used to encode messages within TCP packet data fields to create a covert message channel for data exfiltration.

Homomorphic encryption is used to share privacy-sensitive data sets. It allows a recipient to perform statistical calculations on data fields while keeping the data set as a whole encrypted.

Blockchain uses cryptography to secure an expanding list of transactional records. Each record, or block, goes through a hash function. Each block’s hash value links to the hash value of the previous block.

Key stretching takes a key that is generated from a user password and repeatedly converts it to a longer and more random key, through thousands of rounds of hashing.
# 17
Examine each statement and determine which most accurately describes a major limitation of quantum computing technology.

1.  Presently, quantum computers do not have the capacity to run useful applications.

Solution

Presently, the most powerful quantum computers have about 50 qubits. A quantum computer will need about a million qubits to run useful applications.

Quantum computing could put the strength of current cryptographic ciphers at risk, but it also has the promise of underpinning more secure cryptosystems in the future.

Cryptographic agility refers to an organization's ability to update the specific algorithms used in security products without affecting the business workflows that those products support. Quantum computing could pose a threat to cryptographic agility.

Steganography obscures the presence of a message and can be used for data exfiltration. The quantum computing properties of entanglement, superposition, and collapse suit the design of a tamper-evident communication system that would allow secure key agreement.
# 18
Which statement most accurately describes the mechanisms by which blockchain ensures information integrity and availability?

2.  Blockchain ensures availability through decentralization, and integrity through cryptographic hashing and timestamping.

Solution

The blockchain ledger is decentralized and distributed across a peer-to-peer (P2P) network to mitigate the risks of a single point of failure or compromise. Each block in a blockchain validates the hash of the previous block, all the way through to the beginning of the chain, ensuring that each historical transaction has not been tampered with.

Blockchain is open. It may ensure the integrity and transparency of financial transactions, among other potential applications.

Each block typically includes a timestamp of transactions, as well as the data involved in the transactions themselves, helping ensure data integrity.

One of the most important characteristics of a blockchain is decentralization. Being distributed across a peer-to-peer (P2P) network, blockchain users can trust each other equally.
# 19
A hospital must balance the need to keep patient privacy information secure and the desire to analyze the contents of patient records for a scientific study. What cryptographic technology can best support the hospital’s needs?

4.  Homomorphic encryption

Solution

Homomorphic encryption is used to share privacy-sensitive data sets. It allows a recipient to perform statistical calculations on data fields, while keeping the data set as a whole encrypted, thus preserving patient privacy.

Blockchain uses cryptography to secure an expanding list of transactional records. Each record, or block, goes through a hash function. Each block’s hash value links to the hash value of the previous block.

Quantum computing could serve as a secure foundation for secure cryptosystems and tamper-evident communication systems that would allow secure key agreement.

Perfect forward security (PFS) mitigates the risks from RSA key exchanges through the use of ephemeral session keys to maintain confidentiality.
# 20
During a penetration test, an adversary operator sends an encrypted message embedded in an attached image. Analyze the scenario to determine what security principles the operator is relying on to hide the message. **(Select all that apply.)**

1.  Security by obscurity
4.  Confidentiality

Solution

When used to conceal information, steganography amounts to "security by obscurity," which is usually deprecated.

A message can be encrypted by some mechanism before embedding it in a covertext, providing confidentiality.

Steganography technology can also provide integrity or non-repudiation; for example, it can show that something was printed on a particular device at a particular time, which could demonstrate that it was genuine or a fake.

A phishing or hoax email can be made more convincing by using prepending. In an offensive sense, prepending means adding text that appears legitimate and to have been generated by the mail system such as "MAILSAFE:PASSED."
