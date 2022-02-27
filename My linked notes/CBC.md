---
tags: [A_D, secondTag]
---
**Cipher Block Chaining**
- (CBC) [[mode]] applies an initialization vector ([[IV]]) to the first plaintext block to ensure that the key produces a unique ciphertext from any given plaintext. The output of the first ciphertext block is then combined with the next plaintext block using an XOR operation. This process is repeated through the full "chain" of blocks, which (again) ensures that no plaintext block produces the same ciphertext. CBC needs to use padding to ensure that the data to encrypt is an exact multiple of the block size.

**XOR is a logical operation that outputs 1 only when the inputs are 1 and 0.**