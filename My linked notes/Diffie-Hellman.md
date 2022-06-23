A cryptographic key exchange method developed by Whitfield Diffie and Martin Hellman in 1976. Also known as the "Diffie-Hellman-Merkle" method and "exponential key agreement." Diffie-Hellman enables parties at both ends to derive a shared, secret key from a common starting point without the key ever being transmitted from one side to the other.

Although Diffie-Hellman is an asymmetric algorithm, it does not use public and private keys like the popular RSA method. Its logarithms and modular arithmetic are complicated mathematics; however, the example below is simplified to explain the concept. The numbers used are minuscule by comparison to those used in a real exchange. See [elliptic curve cryptography](https://www.pcmag.com/encyclopedia/term/elliptic-curve-cryptography), [RSA](https://www.pcmag.com/encyclopedia/term/rsa) and [key management](https://www.pcmag.com/encyclopedia/term/key-management).

![_DIFFHEL.GIF](https://i.pcmag.com/imagery/encyclopedia-terms/diffie-hellman-_diffhel.fit_lim.size_640x.gif)

**Very Clever Math**

Both sides use a public common number, and each side uses a different random number as a power to raise the common number. The results are then sent to each other. The receiving party raises the received number to the same random power they used before, and the results wind up the same on both sides.