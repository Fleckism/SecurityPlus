---
tags: [GRC,section]
---
# EXAM OBJECTIVES COVERED

3.9 Given a scenario, implement public key infrastructure[[PKI]]

4.1 Given a scenario, use the appropriate tool to assess organizational security (OpenSSL only)

As a security professional, you are very likely to have to install and maintain [[public key infrastructure]] (PKI) certificate services for private networks. **You may also need to obtain and manage certificates from public PKI providers.** This topic will help you to install and configure PKI and to troubleshoot and revoke certificates.
# CERTIFICATE AND KEY MANAGEMENT 

**_Key management_ refers to operational considerations for the various stages in a key's life cycle. A key's life cycle may involve the following stages:**

-   **Key generation**—creating a secure key pair of the required strength, using the chosen cipher.
-   **Certificate generation**—to identify the public part of a key pair as belonging to a subject (user or computer), the subject submits it for signing by the CA as a digital certificate with the appropriate key usage. At this point, it is critical to verify the identity of the subject requesting the certificate and only issue it if the subject passes identity checks.
-   **Storage**—the user must take steps to store the private key securely, ensuring that unauthorized access and use is prevented. It is also important to ensure that the private key is not lost or damaged.
-   **Revocation**—if a private key is compromised, the key pair can be revoked to prevent users from trusting the public key.
-   **Expiration and renewal**—a key pair that has not been revoked expires after a certain period. Giving the key or certificate a "shelf-life" increases security. Certificates can be renewed with new key material.

**Key management can be _centralized,_ meaning that one administrator or authority controls the process, or _decentralized,_ in which each user is responsible for his or her keys.**

Certificate and key management can represent a **critical vulnerability if not managed properly**. If an attacker can obtain a private key, it puts both data confidentiality and identification/authentication systems at risk. If an attacker gains the ability to create signed certificates that appear to be valid, it will be easy to harvest huge amounts of information from the network as the user and computer accounts he or she sets up will be automatically trusted. Finally, if a key used for encryption is accidentally destroyed, the data encrypted using that key will be inaccessible, unless there is a backup or key recovery mechanism.
# KEY RECOVERY AND ESCROW 

Keys such as the [[symmetric|private key]] of a root [[CA]] must be subject to the highest possible technical and procedural access controls. If such a key were compromised, it would put the confidentiality and integrity of data processed by hundreds or thousands of systems at risk. Access to such critical encryption keys must be logged and audited and is typically subject to **_M_-of-_N_ control, meaning that of _N_ number of administrators permitted to access the system, _M_ must be present for access to be granted. _M_ must be greater than 1, and _N_ must be greater than _M._ For example, when _M_ = 2 and _N_ = 4, any two of four administrators must be present.** Staff authorized to perform key management must be carefully vetted, and due care should be taken if these employees leave the business.

Another way to use [[M-of-N]] control is to split a key between several storage devices (**such as three USB sticks, any two of which could be used to recreate the full key**).

If the key used to decrypt data is lost or damaged, the encrypted data cannot be recovered unless a backup of the key has been made. A significant problem with key storage is that if you make multiple backups of a key, it is exponentially more difficult to ensure that the key is not compromised. However, if the key is not backed up, the storage system represents a single point of failure. Key recovery defines a secure process for backing up keys and/or recovering data encrypted with a lost key. This process might use _M_-of-_N_ control to prevent unauthorized access to (and use of) the archived keys. [[Escrow]] means that something is held independently. In terms of key management, this refers to archiving a key (or keys) with a third party. This is a useful solution for organizations that don't have the capability to store keys securely themselves, but it invests a great deal of trust in the third party.
# CERTIFICATE EXPIRATION

Certificates are issued with a limited duration, as set by the [[CA]] policy for the certificate type. Root certificates might have long expiration dates (10+ years), whereas web server and user certificates might be issued for 1 year only. Typically, a certificate is renewed before it expires. Where a user is in possession of a valid certificate, less administration is required (in terms of checking identity) than with a request for a new certificate. When you are renewing a certificate, it is possible to use the existing key (referred to specifically as **_certificate renewal_**) or generate a new key (the certificate is **_rekeyed_**). A new key might be generated if the old one was no longer considered long enough or if any compromise of the key was feared.

When a certificate expires, there is the question of what to do with the key pair that it represents. A key can either be archived or destroyed. Destroying the key offers more security, but has the drawback that any data encrypted using the key will be unreadable. Whether a key is archived or destroyed will largely depend on how the key was used. In software terms, a key can be destroyed by overwriting the data (merely deleting the data is not secure). A key stored on hardware can be destroyed by a specified erase procedure or by destroying the device.
# CERTIFICATE REVOCATION LISTS

A certificate may be revoked or suspended:

-   A revoked certificate is no longer valid and cannot be "un-revoked" or reinstated.
-   A suspended certificate can be re-enabled.

A certificate may be revoked or suspended by the owner or by the CA for many reasons. For example, the certificate or its private key may have been compromised, the business could have closed, a user could have left the company, a domain name could have been changed, the certificate could have been misused in some way, and so on. These reasons are codified under choices such as Unspecified, Key Compromise, CA Compromise, Superseded, or Cessation of Operation. A suspended key is given the code Certificate Hold. 

It follows that there must be some mechanism for informing users whether a certificate is valid, revoked, or suspended. CAs must maintain a **certificate revocation list (CRL)** of all revoked and suspended certificates, which can be distributed throughout the hierarchy. 

![sy0-601 windows server crl.png](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/sy0-601%20windows%20server%20crl.png)

CRLs published by Windows Certificate Services—The current CRL contains one revoked certificate. (Screenshot used with permission from Microsoft.)

A CRL has the following attributes:

-   **Publish period**—the date and time on which the CRL is published. Most CAs are set up to publish the CRL automatically.
-   **Distribution point(s)**—the location(s) to which the CRL is published.
-   **Validity period**—the period during which the CRL is considered authoritative. This is usually a bit longer than the publish period (for example, if the publish period was every 24 hours, the validity period might be 25 hours).
-   **Signature**—the CRL is signed by the CA to verify its authenticity.

With the CRL system, there is a risk that the certificate might be revoked but still accepted by clients because an up-to-date CRL has not been published. A further problem is that the browser (or other application) may not be **configured to perform CRL checking**, although this now tends to be the case only with legacy browser software.
# ONLINE CERTIFICATE STATUS PROTOCOL RESPONDERS

Another means of providing up-to-date information is to check the certificate's status on an **Online Certificate Status Protocol (OCSP) server, referred to as an _OCSP responder**._ Rather than return a whole CRL, this just communicates the status of the requested certificate. Details of the OCSP responder service should be published in the certificate.

Most OCSP servers can query the certificate database directly and obtain the real-time status of a certificate. Other OCSP servers actually depend on the CRLs and are limited by the CRL publishing interval.

One of the problems with OCSP is that the job of responding to requests is resource intensive and can place high demands on the issuing CA running the OCSP responder. There is also a privacy issue, as the OCSP responder could be used to monitor and record client browser requests. OCSP [[stapling]] resolves these issues by having the SSL/TLS web server periodically obtain a time-stamped OCSP response from the CA. When a client submits an OCSP request, the web server returns the time-stamped response, rather than making the client contact the OCSP responder itself.
# CERTIFICATE PINNING

When certificates are used by a transport protocol, such as SSL/TLS, there is a possibility that the chain of trust among the client, the server, and whatever intermediate and root CAs have provided certificates can be compromised. If an adversary can substitute a malicious but trusted certificate into the chain (using some sort of proxy or [[MITM|Man-in-the-Middle attack]]), they could be able to snoop on the supposedly secure connection.

**[[Pinning]] refers to several techniques to ensure that when a client inspects the certificate presented by a server or a code-signed application, it is inspecting the proper certificate**. This might be achieved by embedding the certificate data in the application code, or by submitting one or more public keys to an Hyper Text Transfer ProtocolTTPs]] browser via an Hyper Text Transfer ProtocolTTPs]] header, which is referred to as _Hyper Text Transfer ProtocolTTPs]] Public Key Pinning (**HPKP**)._

**[[HPKP]] has serious vulnerabilities and has been deprecated** ([developer.mozilla.org/en-US/docs/Web/Hyper Text Transfer ProtocolTTPs]]/Public_Key_Pinning](https://developer.mozilla.org/en-US/docs/Web/Hyper Text Transfer ProtocolTTPs]]/Public_Key_Pinning)). The replacement mechanism is the Certificate Transparency Framework.
# CERTIFICATE FORMATS

There are various formats for encoding a certificate as a digital file for exchange between different systems. 

### Encoding

Cryptographic data—both certificates and keys—are processed as binary using Distinguished Encoding Rules (**DER**). Binary format files are not commonly used, however.

More typically, the binary data is represented as ASCII text characters using Base64 Privacy-enhanced Electronic Mail ([[PEM]]) encoding. ASCII-format data has descriptive headers, such as the "BEGIN CERTIFICATE" string.

![A Notepad window shows "-----BEGIN CERTIFICATE-----" and then lines of characters with no spaces, including "...AApgTb2LH7xb/gAAAAAC…"](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4926-1599771798794.png)

Base64-encoded .CER file opened in Notepad. (Screenshot used with permission from Microsoft.)

### File Extensions

A three character file extension is a _convention,_ not a standard, and unfortunately file extensions do not always map cleanly to the type of encoding used within a certificate file, or even to the contents of a certificate file. The only certain way to check is to open it in a text editor.

-   **Both .DER and .PEM** can be used as file extensions, although the latter is not recognized by Windows. .PEM is the most widely used extension for ASCII format files in Linux.
-   The **.CRT and .CER** extensions can also be used, but they are not well-standardized. Most of the confusion arises from the way Windows handles certificates. In Linux, .CRT is most likely to represent an ASCII certificate. In Windows, the most common extension is .CER, but this does not tell you whether the file format is binary or ASCII.

### Contents

A certificate file can also contain more than just a single certificate:
(transfer your private key and certificate to another computer use PKCS #12 / .PFX / .P12.)
-   The **PKCS** #12 format allows the export of the private key with the certificate. This would be used either to transfer a private key to a host that could not generate its own keys, or to back up/archive a private key. This type of file format is usually password-protected and always binary. On Windows, these usually have a **.[[PFX]] extension**, while MacOS and iOS use .[[P12]]. In Linux, the certificate and key are usually stored in separate files.
-   The [[P7B]] format implements PKCS #7, which is a means of bundling multiple certificates in the same file. It is typically in ASCII format. This is most often used to deliver a chain of certificates that must be trusted by the processing host. It is associated with the use of S/MIME to encrypt email messages. P7B files do not contain the private key. In Linux, the .PEM extension is very widely used for certificate chains.
# OpenSSL

[[OPENSSL]]

In a Windows environment, certificate infrastructure is installed and managed as Active Directory Certificate Services. There is a certutil tool for command line management, or you can use PowerShell.

For Linux, CA services are typically implemented using the OpenSSL suite ([openssl.org](https://www.openssl.org/)). The following represent a few of the many operations that can be accomplished using openssl commands.

### Root CA

To configure a root CA in OpenSSL, set up a directory structure and adapt an OpenSSL configuration file (openssl.cnf) for any site-local settings. You then need to create an RSA key pair:

openssl genrsa -aes256 -out cakey.pem 4096

The -aes256 argument encrypts the key and requires a password to make use of it. The 4096 argument sets the key length. The output file data is in PEM ASCII format by default. Some sites prefer a naming convention, such as ca.key.

The next step is to use this RSA key pair to generate a self-signed root X.509 digital certificate:

openssl req -config openssl.cnf -key cakey.pem -new -x509 -days 7300 -sha256 -out cacert.pem

This example is simplified. Using a root CA to issue leaf certificates directly is not robust. It is better to create one or more intermediate CAs.

### Certificate Signing Requests

To configure a certificate on a host, create a certificate signing request (**CSR**) with a new key pair. This command is run on the web server:

openssl req -nodes -new -newkey rsa:2048 -out www.csr -keyout www.key

Having run the command, you then complete the prompts to enter the subject information for the certificate, taking care to match the common name (**CN**) to the **FQDN** by which clients access the server. This key is created without a password, which would have to be input at any restart of the web server application. We can rely on general access control security measures to protect the key.

This CSR file must then be transmitted to the CA server. On the CA, run the following command to sign the CSR and output the X.509 certificate:

openssl ca -config openssl.cnf -extensions webserver -infiles www.csr -out www.pem

The passphrase must be entered to confirm use of the cakey.pem private key. The -extensions argument selects an area of the configuration file for a particular certificate type. This sets the key usage attribute, plus any other extended attributes that are needed.

You can view the new certificate to check the details using the following two commands:

openssl x509 -noout -text -in www.pem

openssl verify -verbose -cafile cacert.pem www.pem

Transmit the www.pem file to the web server and update the server configuration to use it and the www.key private key.

### Key and Certificate Management 

You might export a copy of the private key from this server to be held in escrow as a backup. For this usage, you must password-protect the key:

openssl rsa -aes256 -in www.key -out www.key.bak

You might need to convert the certificate format to make it compatible with an application server, such as Java. The following command takes a PEM-encoded certificate and outputs a DER binary-encoded certificate:

openssl x509 -outform der -in www.pem -out www.der

Another use case is to export a key and certificate for use in Windows:

openssl pkcs12 -export -inkey www.key -in www.pem -out www.pfx
# CERTIFICATE ISSUES

The most common problem when dealing with certificate issues is that of a client rejecting a server certificate (or slightly less commonly, an authentication server rejecting a client's certificate). 

-   If the problem is with an existing certificate that has been working previously, check that the certificate has not expired or been revoked or suspended. 
-   If the problem is with a new certificate, check that the key usage settings are appropriate for the application. Some clients, such as VPN and email clients, have very specific requirements for key usage configuration. Also, check that the subject name is correctly configured and that the client is using the correct address. For example, if a client tries to connect to a server by IP address instead of FQDN, a certificate configured with an FQDN will be rejected. 
-   If troubleshooting a new certificate that is correctly configured, check that clients have been configured with the appropriate chain of trust. You need to install root and intermediate CA certificates on the client before a leaf certificate can be trusted. Be aware that some client applications might maintain a different certificate store to that of the OS. 
-   In either case, verify that the time and date settings on the server and client are synchronized. Incorrect date/time settings are a common cause of certificate problems. 

From a security point of view, you must also audit certificate infrastructure to ensure that only valid certificates are being issued and trusted. Review logs of issued certificates periodically. Validate the permissions of users assigned to manage certificate services. Check clients to ensure that only valid root CA certificates are trusted. Make sure clients are checking for revoked or suspended certificates.
