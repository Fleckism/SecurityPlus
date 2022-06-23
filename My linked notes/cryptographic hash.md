A cryptographic hash produces a fixed-length string from arbitrary-length plaintext data using an algorithm such as [[SHA]]. If the function is secure, it should not be possible to match the hash back to a plaintext. **Hashing is mostly used to prove integrity**. If two sources have access to the same plaintext, they should derive the same hash value. Hashing is used for two main purposes within a database:

- Proves [[Integrity]] 
-  As an indexing method to speed up searches and provide deidentified references to records.
-   As a storage method for data such as passwords where the original plaintext does not need to be retained.
