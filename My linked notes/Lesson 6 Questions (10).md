# 1
 A web administrator visits a website after installing its certificate to test the SSL binding. The administrator's client computer did not trust the website's certificate. The administrator views the website's certificate from the browser to determine which certificate authority (CA) generated the certificate. Which certificate field would assist with the troubleshooting process? 

3.  Issuer

Solution

The Issuer field provides the name of the certificate authority (CA) that generated and issued the certificate for the web server.

The subject alternative name (SAN) displays the extension field to identify the domain name system (DNS) name or names by which a host is identified.

The Signature algorithm field displays the algorithm used by the certificate authority to sign the certificate.

The Subject field displays the name of the certificate holder, expressed as a distinguished name (DN). The common name (CN) in this part would match the fully qualified domain name (FQDN) of the server or a user email address.

# 2
An employee has requested a digital certificate for a user to access the Virtual Private Network (VPN). It is discovered that the certificate is also being used for digitally signing emails. Evaluate the possible extension attributes to determine which should be modified so that the certificate only works for VPN access.

2.  Extended key usage

Solution

Set the Extended Key Usage (EKU) field of a certificate to define its usage. Applications such as virtual private network (VPN) or email clients may require specific requirements for key usage configuration.

The validity field displays the date and time during which the certificate is valid. Certificates are issued with a limited duration, as set by the certificate authority (CA) policy for the certificate type.

The serial number is a number uniquely identifying the certificate within the domain of its CA. This prevents a CA from generating duplicate certificates. 

The public key field displays the public key and algorithm used by the certificate holder. This key can be shared with other clients and users on the public network.
# 3
A website with many subdomains has been issued a web server certificate for domain validation. This certificate verifies the parent domain and all subdomains (to a single level). This certificate is also known as which of the following?

3.  Root certificate

Solution

A wildcard certificate with a field entry of a wildcard domain such as *.comptia.org, means that the certificate issued to the parent domain will be accepted as valid for all subdomains (to a single level).

A subject alternative name (SAN) certificate list different identifiers including domain names which are specific for each certificate. This becomes a wildcard certificate when a wildcard domain is listed.

The root certificate is the one that identifies the certificate authority (CA) itself. The root certificate is self-signed. A root certificate would normally use a key size of at least 2048 bits.

A code signing certificate is issued to a software publisher by the CA. The publisher signs the executables or DLLs to guarantee the validity of a software application or browser plug-in.
# 4
Digital certificates are based on the X.509 standard that defines the fields (or information) about a subject (or entity using the certificate) and the certificate’s issuer. Which of the following fields would not be included in a standard public certificate?

3.  Endorsement key

Solution

An endorsement key is not required for a digital certificate. It is part of a Trusted Platform Module (TPM) and used to create subkeys for key storage, signature, and encryption operations.

The Extensions field defines which extended attributes a certificate supports. V3 certificates can be defined with extended attributes, such as friendly subject or issuer names, contact email addresses, and intended key usage.

The Public key field denotes the public key and algorithm used by the certificate holder. This key is distributed to the public to initiate a secure connection with a website or remote server.

The Subject field names the certificate holder, expressed as a distinguished name (DN). Within this, the common name (CN) usually matches either the fully qualified domain name (FQDN) of a server or a user email address.
# 5
What is the purpose of a web server certificate?

4.  Guarantee the identity of a website.

Solution

A web server certificate guarantees the identity of the server that provides web services like a website or e-commerce sites. The web server’s public certificate allows users to submit data securely to the web server.

Signing and encrypting email messages is done with an email certificate, typically using Secure/Multipurpose Internet Mail Extensions (SMIME) or Pretty Good Privacy (PGP).

A code signing certificate is issued to a software publisher following an identity check and validation process to guarantee the validity of a software application or browser plug-in.

A root certificate identifies the certificate authority (CA) and is self-signed. The operating system or browser mark self-signed certificates as untrusted, but an administrative user can choose to override this.


# 6

Question

If not managed properly, certificate and key management can represent a critical vulnerability. Assess the following statements about key management and select the true statements. **(Select all that apply.)**

2.  It is exponentially more difficult to ensure the key is not compromised with multiple backups of a private key.
3.  If a private key, or secret key, is not backed up, the storage system represents a single point of failure.


Solution

A problem with key storage is the difficulty associated with multiple backups of a private key. It is exponentially more difficult to ensure the key is not compromised in this situation.

If a key is not backed up, it represents a single point of failure. Key recovery is a process for backing up keys and/or recovering data encrypted with a lost key.

If a key is compromised and is used for signing only, it can be destroyed, and a new key issued. A key used for encryption cannot be destroyed so easily. The encrypted data has to be recovered first.

If the private key used to both encrypt and sign a document is compromised, both uses of the key are of great security risk and may provide external threats more access to private data.
# 7
An employee handles key management and has learned that a user has used the same key pair for encrypting documents and digitally signing emails. Prioritize all actions that should be taken and determine the first action that the employee should take.

2.  Recover the encrypted data.

Solution

The first step is to recover any data encrypted with the key so the data can be decrypted. Once the data is recovered, the key can be revoked and an administrator can issue a new key pair.

After the data has been recovered, the keys should be revoked. They are compromised and should not be used for any future tasks.

After the compromised keys are revoked, the user can be issued new keys. The user requires two sets of keys, one for encrypting messages and the other for digitally signing documents.

Certificate generation is used to identify the public part of a key pair as belonging to a subject and will occur after the user’s new keys have been generated.
# 8
An employee handling key management discovers that a private key has been compromised. Evaluate the stages of a key's life cycle and determine which stage the employee initiates upon learning of the compromise.

4.  Revocation

Solution

Upon learning of a compromise, the current key should be revoked, and a new key can then be generated.

Certificate generation identifies the public part of a key pair as belonging to a subject, and the subject submits it for signing by the CA as a digital certificate with the appropriate key usage.

Key generation occurs during the initial distribution of the key, or after having revoked one.

Expiration and renewal are used for a key pair that has not been revoked or expired after a certain period. A given shelf-life increases security.
# 9
A company has a critical encryption key that has an _M_-of-_N_ control configuration for protection. Examine the examples and select the one that correctly illustrates the proper configuration for this type of protection of critical encryption keys.

2.  _M_=3 and _N_=5


Solution

A correct configuration for an M-of-N control is _M_=3 and _N_=5. _M_ stands for the number of authorized administrators that must be present to access the critical encryption keys and _N_ is the total number of authorized administrators. In this scenario, 3 of the 5 administrators must be present for access.

_M_ is always greater than 1 for this type of configuration making _M_=1 and _N_=5 not a valid choice. If only 1 administrator must be present, this configuration would be unnecessary.

_M_=6 and _N_=5 is not possible as this configuration is asking for more administrators to be present than is authorized.

The final option of _M_=0 is not viable because _M_ must always equal more than 1.
# 10
A Certificate Revocation List (CRL) has a publish period set to 24 hours. Based on the normal procedures for a CRL, what is the most applicable validity period for this certificate?

1.  26 hours

Solution

One or two hours over the publish period is considered normal thus making 26 hours within the window.

The validity period is the period during which the CRL is considered authoritative. This is usually a bit longer than the publish period, giving a short window to update and keep the CRL authoritative.

The validity period would not be less than the publish period as it would make the CRL nonauthoritative prior to the next publishing.

If the validity period was set to 72 hours this would be much too long after the publish period. The CRL would be published two additional times prior to the validity period ending.