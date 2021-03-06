
## EXAM OBJECTIVES COVERED
#concepts #study
2.1 Explain the importance of security concepts in an enterprise environment ([[hash|hashing]] only) 

2.8 Summarize the basics of cryptographic concepts

A [[cipher]] is the particular operations performed to encode or decode data. Modern cryptographic systems make use of [[symmetric]] and [[asymmetric]] cipher types to encode and decode data. As well as these cipher types, one-way hash functions have an important role to play in many security controls. Being able to compare and contrast the characteristics of these types of [[cryptographic]] ciphers and functions is essential for you to deploy security controls for different use cases.

## CRYPTOGRAPHIC CONCEPTS 

Cryptography (literally meaning "secret writing") has been around for thousands of years. It is the art of making information secure by encoding it. This stands in opposition to the concept of security through obscurity. **Security through obscurity means keeping something a secret by hiding it.** This is generally acknowledged to be impossible (or at least, high risk) on any sort of computer network. With cryptography, it does not matter if third parties know of the existence of the secret, because they can never know what it is without obtaining an appropriate credential.

The following terminology is used to discuss cryptography: 

-   [[Plaintext]] (or _cleartext_)—an unencrypted message. 
-   [[Ciphertext]]—an encrypted message. 
-   [[Cipher]]—the process (or algorithm) used to encrypt and decrypt a message. 
-   [[Cryptanalysis]]—the art of cracking cryptographic systems. 

In discussing cryptography and attacks against encryption systems, it is customary to use a cast of characters to describe different actors involved in the process of an attack. The main characters are: 

-   Alice—the sender of a genuine message.
-   Bob—the intended recipient of the message.
-   Mallory—a malicious attacker attempting to subvert the message in some way.

There are three main types of cryptographic algorithm with different roles to play in the **assurance** of the [[security properties]] [[confidentiality]], [[integrity]], [[Availability]], and [[non-repudiation]]. These types are hashing algorithms and two types of encryption ciphers: symmetric and asymmetric.

## HASHING ALGORITHMS 

[[Hash |Hashing]] is the simplest type of [[cryptographic]] operation. A cryptographic hashing algorithm produces a fixed length string from an input plaintext that can be of any length. The output can be referred to as a checksum, message digest, or hash. The function is designed so that it is impossible to recover the plaintext data from the [[digest]] (one-way) and so that different inputs are unlikely to produce the same output (a [[collision]]).

A hashing algorithm is used to prove integrity. For example, Bob and Alice can compare the values used for a password in the following way:

1.  Bob already has a digest calculated from Alice's plaintext password. Bob cannot recover the plaintext password value from the hash.
2.  When Alice needs to authenticate to Bob, she types her password, converts it to a hash, and sends the digest to Bob.
3.  Bob compares Alice's [[digest]] to the hash value he has on file. If they match, he can be sure that Alice typed the same password.

As well as comparing password values, a hash of a file can be used to verify the integrity of that file after transfer. 

1.  Alice runs a hash function on the setup.exe file for her product. She publishes the digest to her website with a download link for the file.
2.  Bob downloads the setup.exe file and makes a copy of the digest.
3.  Bob runs the same hash function on the downloaded setup.exe file and compares it to the reference value published by Alice. If it matches the value published on the website, the integrity of the file can be assumed.
4.  Consider that Mallory might be able to substitute the download file for a malicious file. Mallory cannot change the reference hash, however.
5.  This time, Bob computes a hash but it does not match, leading him to suspect that the file has been tampered with.

Confirming a file download using cryptographic hashes. (Images © 123RF.com.)

There are two popular implementations [[hash]] algorithms:

-   Secure Hash Algorithm (SHA)—considered the strongest algorithm. There are variants that produce different-sized outputs, with longer digests considered more secure. The most popular variant is SHA-256, which produces a 256-bit digest.
-   Message Digest Algorithm #5 (MD5)—produces a 128-bit digest. MD5 is not considered to be quite as safe for use as SHA-256, but it might be required for compatibility between security products.

![Text screenshot shows an alphanumeric key ("baa30028bd0cac06…") generated by File Checksum Integrity Verifier version 2.05 from a specified JPG file.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9762-1599771797191.png)

Computing an SHA value from a file. (Screenshot used with permission from Microsoft.)

## ENCRYPTION CIPHERS AND KEYS

While a hash function can be used to prove the integrity of data, it cannot be used to store or transmit data. The plaintext cannot be recovered from the [[digest]]. An encryption algorithm is a type of cryptographic process that encodes data so that it can be recovered, or decrypted. The use of a key with the encryption cipher ensures that decryption can only be performed by authorized persons.

### Substitution and Transposition [[cipher]]

To understand how encryption works, it is helpful to consider simple substitution and transposition ciphers. A substitution cipher involves replacing units (a letter or blocks of letters) in the plaintext with different ciphertext. Simple substitution ciphers rotate or scramble letters of the alphabet. For example, ROT13 (an example of a Caesar cipher) rotates each letter 13 places (so A becomes N for instance). The ciphertext "Uryyb Jbeyq" means "Hello World".

In contrast to substitution ciphers, the units in a transposition cipher stay the same in plaintext and ciphertext, but their order is changed, according to some mechanism. Consider how the ciphertext "HLOOLELWRD" has been produced:

H L O O L

E L W R D

The letters are simply written as columns and then the rows are concatenated to make the ciphertext. It's called a **rail fence cipher**. All modern encryption uses these basic techniques of substitution and transposition, but in much more complex ways.

### Keys and Secret Ciphers

Encryption ciphers use a key to increase the security of the process. For example, if you consider the Caesar cipher ROT13, you should realize that the key is 13. You could use 17 to achieve a different ciphertext from the same method. The key is important because it means that even if the cipher method is known, a message still cannot be decrypted without knowledge of the specific key. This is particularly important in modern cryptography. Attempting to hide details of the cipher (a secret algorithm) amounts to "security by obscurity." Modern ciphers are made stronger by being open to review (cryptanalysis) by third-party researchers.

## SYMMETRIC ENCRYPTION 

A **symmetric cipher is one in which encryption and decryption are both performed by the same secret key**. The secret key is so-called because it must be kept secret. If the key is lost or stolen, the security is breached. **Symmetric encryption is used for confidentiality**. For example, Alice and Bob can share a confidential file in the following way:

1.  Alice and Bob meet to agree which cipher to use and a secret key value. They both record the value of the secret key, making sure that no one else can discover it.
2.  Alice encrypts a file using the cipher and key.
3.  She sends only the ciphertext to Bob over the network.
4.  Bob receives the ciphertext and is able to decrypt it by applying the same cipher with his copy of the secret key.

Symmetric encryption operation and weaknesses. (Images © 123RF.com.)

Symmetric encryption is also referred to as single key or private key or shared secret. Note that "private key" is also used to refer to part of the public key cryptography process, so take care not to confuse the two uses.

Symmetric encryption is very fast. It is used for bulk encryption of large amounts of data. The main problem is secure distribution and storage of the key, or the exact means by which Alice and Bob "meet" to agree the key. If Mallory intercepts the key and obtains the ciphertext, the security is broken.

Note that **symmetric encryption cannot be used for authentication or integrity**, because Alice and Bob are able to create exactly the same secrets, because they both know the same key.

## STREAM AND BLOCK CIPHERS

There are two types of symmetric encryption: stream ciphers and block ciphers.

### Stream Ciphers 

In a stream cipher, each byte or bit of data in the plaintext is encrypted one at a time. This is suitable for encrypting communications where the total length of the message is not known. The plaintext is combined with a separate randomly generated message, calculated from the key and an initialization vector ([[IV]]). The IV ensures the key produces a unique ciphertext from the same plaintext. The keystream must be unique, so an IV must not be reused with the same key. The recipient must be able to generate the same keystream as the sender and the streams must be synchronized. Stream ciphers might use markers to allow for synchronization and retransmission. Some types of stream ciphers are made self-synchronizing.

### Block Ciphers 

In a [[block cipher]], the plaintext is divided into equal-size blocks (usually 128-bit). If there is not enough data in the plaintext, it is padded to the correct size using some string defined in the algorithm. For example, a 1200-bit plaintext would be padded with an extra 80 bits to fit into 10 x 128-bit blocks. Each block is then subjected to complex transposition and substitution operations, based on the value of the key used.

The Advanced Encryption Standard ([[AES]]) is the default symmetric encryption cipher for most products. Basic AES has a key size of 128 bits, but the most widely used variant is AES256, with a 256-bit key. 

### Key Length

The range of key values available to use with a particular cipher is called the keyspace. The keyspace is roughly equivalent to two to the power of the size of the key. Using a longer key (256 bits rather than 128 bits, for instance) makes the encryption scheme stronger. You should realize that key lengths are not equivalent when comparing different algorithms, however. Recommendations on minimum key length for any given algorithm are made by identifying whether the algorithm is vulnerable to cryptanalysis techniques and by the length of time it would take to "brute force" the key, given current processing resources.

## ASYMMETRIC ENCRYPTION

In a [[symmetric]] encryption [[cipher]], the same secret key is used to perform both encryption and decryption operations. With an [[asymmetric]] cipher, operations are performed by two different but related public and private keys in a key pair. 

Each key is capable of reversing the operation of its pair. For example, if the **public key is used to encrypt a message**, only the paired private key can decrypt the ciphertext produced. The public key cannot be used to decrypt the ciphertext, even though it was used to encrypt it. 

The keys are linked in such a way as to make it impossible to derive one from the other. This means that the key holder can distribute the public key to anyone he or she wants to receive secure messages from. No one else can use the public key to decrypt the messages; only the linked private key can do that.(**private key decrypts the messages**)

1.  Bob generates a key pair and keeps the private key secret.
2.  Bob publishes the public key. Alice wants to send Bob a confidential message, so she takes a copy of Bob's public key.
3.  Alice uses Bob's public key to encrypt the message.
4.  Alice sends the ciphertext to Bob.
5.  Bob receives the message and is able to decrypt it using his private key.
6.  If Mallory has been snooping, she can intercept both the message and the public key.
7.  However, Mallory cannot use the public key to decrypt the message, so the system remains secure.

Asymmetric encryption. (Images © 123RF.com.)

**Asymmetric encryption can be used to prove identity.** The holder of a private key cannot be impersonated by anyone else. The drawback of asymmetric encryption is that it involves substantial computing overhead compared to symmetric encryption. The message cannot be larger than the key size. Where a large amount of data is being encrypted on disk or transported over a network, asymmetric encryption is inefficient.

Consequently, [[asymmetric]] encryption is mostly used for authentication and non-repudiation and for **key agreement and exchange**. Key agreement/exchange refers to settling on a secret **symmetric** key to use for bulk encryption without anyone else discovering it.

## PUBLIC KEY CRYPTOGRAPHY ALGORITHMS

[[Asymmetric]] encryption is often referred to as public key cryptography. Many public key cryptography products are based on the RSA algorithm. Ron Rivest, Adi Shamir, and Leonard Adleman published the RSA cipher in 1977 ([rsa.com](https://www.rsa.com/)). The [[RSA]] algorithm provides the mathematical properties for deriving key pairs and performing the encryption and decryption operations. This type of algorithm is called a **trapdoor function**, because it is easy to perform using the public key, but difficult to reverse without knowing the private key.

Elliptic curve cryptography ([[ECC]]) is another type of trapdoor function that can be used in **public key**([[asymmetric]]) cryptography [[cipher|ciphers]]. The principal advantage of ECC over RSA's algorithm is that there are no known "shortcuts" to cracking the cipher or the math that underpins it, regardless of key length. Consequently, ECC used with a key size of 256 bits is very approximately comparable to RSA with a key size of 2048 bits. 

RSA key pair security depends on the difficulty of finding the prime factors of very large integers (modular exponentiation). ECC depends on the discrete logarithm problem. Cloudflare have produced an excellent overview of the differences ([blog.cloudflare.com/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography](https://blog.cloudflare.com/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/)).


