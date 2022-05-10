**Diffie-Hellman Ephemeral mode** (or EDH)

Diffie-Hellman (DH) key agreement to create ephemeral session keys without using the server's private key.

Using ephemeral session keys means that any future compromise of the server will not translate into an attack on recorded data. Also, even if an attacker can obtain the key for one session, the other sessions will remain confidential. This massively increases the amount of cryptanalysis that an attacker would have to perform to recover an entire "conversation."

[[underpin]]