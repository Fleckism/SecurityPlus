Symmetric [[cipher]] (**aka private (secret) key**)
- 1 key performs encryption and decryption 
- Provides [[Confidentiality]] 
- keys 128 bits or 256 bits
- Easily encrypted using a public key
- Bulk [[encryption]] (aka large amounts of data)
- **symmetric algorithms** do not provide message i**ntegrity or authentication.**
- Symmetric encryption:  Confidentiality—symmetric ciphers are generally fast and well suited to bulk encrypting large amounts of data.


>Consequently, [[asymmetric]] encryption is mostly used for [[authentication]] and [[non-repudiation]] and for **key agreement and exchange**. Key agreement/exchange refers to settling on a secret **symmetric** key to use for bulk encryption without anyone else discovering it.
==Does this mean that a symmetric key is transferred asymmetrically?==

When paired together public/private key pairs.  Each key can reverse the cryptographic operation performed by it's pair but cannot reverse an operation performed by itself.  The private key must be kept secret by the owner, but the public key is designed to be widely distributed.  The private key cannot determined from the public key, given a sufficient key size.

- If lost
	- It puts both data confidentiality and identification and authentication systems at risk. Depending on the key usage, the key may be used to decrypt data with authorization. The key could also be used to impersonate a user or computer account.
[[CIA]]