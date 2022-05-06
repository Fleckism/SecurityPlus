**Internet Key Exchange**

IKE negotiations take place over two phases:

1.  Phase I establishes the identity of the two hosts and p**erforms key agreement using the Diffie-Hellman algorithm to create a secure channel**. Two methods of authenticating hosts are commonly used:
    -   **Digital certificates**—the hosts use certificates issued by a mutually trusted certificate authority to identify one another.
    -   **Pre-shared key (group authentication)**—the same passphrase is configured on both hosts.
2.  Phase II uses the secure channel created in Phase I to establish which ciphers and key sizes will be used with AH and/or ESP in the IPSec session.