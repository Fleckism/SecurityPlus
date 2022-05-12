**certificate authority**
- A server that guarantees subject identities by issuing signed digital certificate wrappers for their public keys
The functions of a CA are as follows:
The certificate contains the 
- subject's **public key** and is signed by the 
- CA's **private key**
-   Provide a range of certificate services useful to the community of users serviced by the CA.
-   Ensure the validity of certificates and the identity of those applying for them (registration).
-   Establish trust in the CA by users and government and regulatory authorities and enterprises, such as financial institutions.
-   Manage the servers (repositories) that store and administer the certificates.
-   Perform key and certificate lifecycle management, notably revoking invalid certificates.
**Add things from [[6A Certificates and  Certificate Authorities]] and [[6B PKI Management]]**
**Add acronyms from above into file with no links**
#zFleck 

![[Pasted image 20220511073900.png]]

- In most cases, the subject generates a key pair then adds the public key along with subject information and certificate type in a certificate signing request (CSR) and submits it to the CA. If the CA accepts the request, it generates a certificate with the appropriate key usage and validity, signs it, and transmits it to the subject.

![[Pasted image 20220511073917.png]]

![[Pasted image 20220511074355.png]]

![[Pasted image 20220511074407.png]]


root CA (root certificate authority)
- In PKI, a CA that issues certificates to intermediate CAs in a hierarchical structure.

A server that guarantees subject identities by issuing signed digital certifcate wrappers for their public keys