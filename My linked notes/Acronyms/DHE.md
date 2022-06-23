**Diffie-Hellman Ephemeral mode** (or EDH)

Diffie-Hellman ([[DH]]) key agreement to create ephemeral session keys without using the server's private key.

Using ephemeral session keys means that any future compromise of the server will not translate into an attack on recorded data. Also, even if an attacker can obtain the key for one session, the other sessions will remain confidential. This massively increases the amount of cryptanalysis that an attacker would have to perform to recover an entire "conversation."

- Diffie-Hellman allows the sender and recipient to derive the same value (the session key) from some other pre-agreed values. Some of these are exchanged, and some kept private, but there is no way for a snooper to work out the secret just from the publicly exchanged values. This means session keys can be created without relying on the server's private key, and that it is easy to generate ephemeral keys that are different for each session.

[[underpin]]