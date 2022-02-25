
---
tags: [firstTag,secondTag]
---
# EXAM OBJECTIVES COVERED
2.8 Summarize the basics of cryptographic concepts

# QUANTUM AND POST-QUANTUM

_Quantum_ refers to computers that use properties of quantum mechanics to significantly out-perform classical computers at certain tasks.

### Computing

A quantum computer performs processing on units called _qubits_ (quantum bits). A qubit can be set to 0 or 1 or an indeterminate state called a _superposition,_ where there is a probability of it being either 1 or 0. The likelihood can be balanced 50/50 or can be weighted either way. The power of quantum computing comes from the fact that qubits can be entangled. When the value of a qubit is read, it collapses to either 1 or 0, and all other entangled qubits collapse at the same time. The strength of this architecture is that a single operation can utilize huge numbers of state variables represented as qubits, while a classical computer's CPU must go through a read, execute, write cycle for each bit of memory. This makes quantum very well-suited to solving certain tasks, two of which are the factoring problem that underpins RSA encryption and the discrete logarithm problem that underpins ECC.

### Communications

While quantum computing could put the strength of current cryptographic ciphers at risk, it also has the promise of underpinning more secure cryptosystems. The properties of entanglement, superposition, and collapse suit the design of a tamper-evident communication system that would allow secure key agreement.

### Post-Quantum

Post-quantum refers to the expected state of computing when quantum computers that can perform useful tasks are a reality. Currently, the physical properties of qubits and entanglement make quantum computers very hard to scale up. At the time of writing, the most powerful quantum computers have about 50 qubits. A quantum computer will need about a million qubits to run useful applications.

No one can predict with certainty if or when such a computer will be implemented. In the meantime, NIST is running a project to develop cryptographic ciphers that are resistant to cracking even by quantum computers ([csrc.nist.gov/Projects/Post-Quantum-Cryptography](https://csrc.nist.gov/Projects/Post-Quantum-Cryptography)).

More generally, _cryptographic agility_ refers to an organization's ability to update the specific algorithms used across a range of security products without affecting the business workflows that those products support ([cryptosense.com/blog/achieving-crypto-agility](https://cryptosense.com/blog/achieving-crypto-agility/)).

### Lightweight Cryptography

Another problem affecting current cryptographic ciphers is use on low-power devices. NIST is hoping that a compact cipher suite will be developed that is both quantum resistant and that can run on battery-powered devices with minimal CPU and memory resources ([csrc.nist.gov/projects/lightweight-cryptography](https://csrc.nist.gov/projects/lightweight-cryptography)).

# HOMOMORPHIC ENCRYPTION

Homomorphic encryption is principally used to share privacy-sensitive data sets. When a company collects private data, it is responsible for keeping the data secure and respecting the privacy rights of individual data subjects. Companies often want to use third parties to perform analysis, however. Sharing unencrypted data in this scenario is a significant risk. Homomorphic encryption is a solution for this use case because it allows the receiving company to perform statistical calculations on fields within the data while keeping the data set as a whole encrypted. For example, if you want to perform analytics on customer interactions, an analysis tool will be able to sum logons without any account identifiers like email addresses ever being decrypted.

# BLOCKCHAIN 

Blockchain is a concept in which an expanding list of transactional records is secured using cryptography. Each record is referred to as a _block_ and is run through a hash function. The hash value of the previous block in the chain is added to the hash calculation of the next block in the chain. This ensures that each successive block is cryptographically linked. Each block validates the hash of the previous block, all the way through to the beginning of the chain, ensuring that each historical transaction has not been tampered with. In addition, each block typically includes a timestamp of one or more transactions, as well as the data involved in the transactions themselves. 

The blockchain is recorded in a public ledger. This ledger does not exist as an individual file on a single computer; rather, one of the most important characteristics of a blockchain is that it is decentralized. The ledger is distributed across a peer-to-peer (P2P) network in order to mitigate the risks associated with having a single point of failure or compromise. Blockchain users can therefore trust each other equally. Likewise, another defining quality of a blockchain is its openness—everyone has the same ability to view every transaction on a blockchain. 

Blockchain technology has a variety of potential applications. It can ensure the integrity and transparency of financial transactions, online voting systems, identity management systems, notarization, data storage, and more. However, blockchain is still an emerging technology, and outside of cryptocurrencies, has not yet been adopted on a wide-ranging scale.

# STEGANOGRAPHY 

Steganography (literally meaning "hidden writing") is a technique for obscuring the presence of a message. Typically, information is embedded where you would not expect to find it; a message hidden in a picture, for instance. The container document or file is called the _covertext._ A _steganography tool_ is software that either facilitates this or conversely that can be used to detect the presence of a hidden message within a covertext. 

When used to conceal information, steganography amounts to "security by obscurity," which is usually deprecated. However, a message can be encrypted by some mechanism before embedding it, providing confidentiality. The technology can also provide integrity or non-repudiation; for example, it could show that something was printed on a particular device at a particular time, which could demonstrate that it was genuine or a fake, depending on context.

One example of steganography is to encode messages within TCP packet data fields to create a covert message channel. Another approach is to change the least significant bit of pixels in an image file. This can code a useful amount of information without distorting the original image noticeably. Similar techniques can be used with other media types as cover files, such as audio and video files. 

These methods might be used for command and control or to exfiltrate data covertly, bypassing protection mechanisms such as data loss prevention (DLP) ([blog.trendmicro.com/trendlabs-security-intelligence/steganography-and-malware-concealing-code-and-cc-traffic/](https://blog.trendmicro.com/trendlabs-security-intelligence/steganography-and-malware-concealing-code-and-cc-traffic/)). Future developments may see use of steganography in streaming media or voiceover IP (VoIP).

# STEGANOGRAPHY 

Steganography (literally meaning "hidden writing") is a technique for obscuring the presence of a message. Typically, information is embedded where you would not expect to find it; a message hidden in a picture, for instance. The container document or file is called the _covertext._ A _steganography tool_ is software that either facilitates this or conversely that can be used to detect the presence of a hidden message within a covertext. 

When used to conceal information, steganography amounts to "security by obscurity," which is usually deprecated. However, a message can be encrypted by some mechanism before embedding it, providing confidentiality. The technology can also provide integrity or non-repudiation; for example, it could show that something was printed on a particular device at a particular time, which could demonstrate that it was genuine or a fake, depending on context.

One example of steganography is to encode messages within TCP packet data fields to create a covert message channel. Another approach is to change the least significant bit of pixels in an image file. This can code a useful amount of information without distorting the original image noticeably. Similar techniques can be used with other media types as cover files, such as audio and video files. 

These methods might be used for command and control or to exfiltrate data covertly, bypassing protection mechanisms such as data loss prevention (DLP) ([blog.trendmicro.com/trendlabs-security-intelligence/steganography-and-malware-concealing-code-and-cc-traffic/](https://blog.trendmicro.com/trendlabs-security-intelligence/steganography-and-malware-concealing-code-and-cc-traffic/)). Future developments may see use of steganography in streaming media or voiceover IP (VoIP).
# 
