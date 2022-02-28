---
tags: [A_D, GRC]
---
the **process or action of verifying** the identity of a user or process.
- [[security control]]
- When authentication is needed.([[asymmetric]] encryption is used)
	- **User or server** encrypts an agreed hashed data using **private key**
	- **Client** receives the key decrypts the signature with the **public key** and derive the same has value
	- aka digital signature


# Full 
When the user or server needs to Authentication, it encrypts some agreed hashed data using the private key and sends it to the client as a digital signature. The client should be able to decrypt the signature using the public key and derive the same hash value.