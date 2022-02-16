is the particular operations performed to encode or decode data.

To understand how encryption works, it is helpful to consider simple substitution and transposition ciphers. A **substitution cipher** involves replacing units (a letter or blocks of letters) in the plaintext with different ciphertext. Simple substitution ciphers rotate or scramble letters of the alphabet. For example, ROT13 (an example of a Caesar cipher) rotates each letter 13 places (so A becomes N for instance). The ciphertext "Uryyb Jbeyq" means "Hello World".

**transposition cipher** stay the same in plaintext and ciphertext, but their order is changed, according to some mechanism. Consider how the ciphertext "HLOOLELWRD" has been produced:

H L O O L

E L W R D

The letters are simply written as columns and then the rows are concatenated to make the ciphertext. It's called a rail fence cipher. All modern encryption uses these basic techniques of substitution and transposition, but in much more complex ways.

### Stream Ciphers 

In a stream cipher, each byte or bit of data in the plaintext is encrypted one at a time. This is suitable for encrypting communications where the total length of the message is not known. The plaintext is combined with a separate randomly generated message, calculated from the key and an initialization vector ([[IV]]). The IV ensures the key produces a unique ciphertext from the same plaintext. The keystream must be unique, so an IV must not be reused with the same key. The recipient must be able to generate the same keystream as the sender and the streams must be synchronized. Stream ciphers might use markers to allow for synchronization and retransmission. Some types of stream ciphers are made self-synchronizing.