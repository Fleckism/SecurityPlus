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