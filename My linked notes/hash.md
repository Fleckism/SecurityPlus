---
tags: [Implementation, secondTag]
---
A cryptographic hashing algorithm produces a fixed length string from an input plaintext that can be of any length.

The output can be referred to as a 
- checksum, 
- message [[digest]], or 
- [[hash]]

There are two popular implementations [[hash]] algorithms:

-   Secure Hash Algorithm (SHA)—considered the strongest algorithm. There are variants that produce different-sized outputs, with longer digests considered more secure. The most popular variant is SHA-256, which produces a 256-bit digest.
-   Message Digest Algorithm #5 (MD5)—produces a 128-bit digest. MD5 is not considered to be quite as safe for use as SHA-256, but it might be required for compatibility between security products.

Passwords stored as hashes are vulnerable to brute force and dictionary attacks. A password hash cannot be decrypted; [[hash]] functions are one-way