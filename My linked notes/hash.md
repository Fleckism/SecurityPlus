---
A cryptographic hashing [[algorithm]] produces a fixed length string from an input plaintext that can be of any length.
---
==Hashing produces a fixed length string from plaintext input==
- Provides [[Authentication]] and [[Integrity]]
- Output referred to
	- Checksum
	- message [[digest]] 
	- hash = digest
- aka digitally signing
	- A hashing function is used to create a message digest. The digest is then signed using the sender's private key. The resulting signature can be decrypted by the recipient using the sender's public key and cannot be modified by any other agency. The recipient can calculate his or her own digest of the message and compare it to the signed hash to validate that the message has not been altered.
- ==Salt== is a random (pseudo) number or string added to a password before hashing. (Pepper is a fixed value)
	- Slows down (Vulnerable to) brute force and dictionary [[Attack]]s

==Hash the same data and compare checksums!==

There are two popular #Implementation  [[hash]] [[algorithm]]:

-   Secure Hash Algorithm ([[SHA]])—considered the strongest algorithm. 
-   Message Digest Algorithm #5 ([[MD5]])—produces a 128-bit digest. Might be required for compatibility between security products.
- A password hash cannot be decrypted; hash functions are one-way

==Hashing is used for two main purposes within a database:==
-   As an indexing method to speed up searches and provide deidentified references to records.
-   As a storage method for data such as passwords where the original plaintext does not need to be retained.

```
A salt is an additional value stored with the hashed data field. The purpose of salt is to frustrate attempts to crack the hashes. It means that the attacker cannot use pre-computed tables of hashes using dictionaries of plaintexts. These tables have to be recompiled to include the salt value.
```

The administrator should have validated the software with a checksum, which uses a cryptographic algorithm to generate a unique hash value based on the file contents. If the file is changed, the checksum of the modified file will not match the original.

A private certificate does not validate software.

A key signing key is associated with Domain Name System Security Extensions (DNSSEC), which validates DNS responses to help mitigate spoofing and poisoning attacks. It does not apply to software.

Kerberos is an authentication service based on a time-sensitive ticket-granting system. It is used to validate users, not software.

new hash key derivation function (HKDF)