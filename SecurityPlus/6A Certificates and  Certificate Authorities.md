---
tags: [GRC,,section]
---
# LESSON INTRODUCTION

Digital certificates and public key infrastructure ([[PKI]]) are critical services used to manage identification, authentication, and data confidentiality across most private and public networks. It is important that you understand the types of certificate that can be issued and are able to apply effective management principles when configuring and supporting these systems.

Lesson Objectives

In this lesson, you will:

-   Implement certificates and certificate authorities.
-   Implement PKI management.
# EXAM OBJECTIVES COVERED

3.9 Given a scenario, implement public key infrastructure

**A _digital certificate_ is a public assertion of identity, validated by a certificate authority ([[CA]]).** As well as asserting identity, certificates can be issued for different purposes, such as protecting web server communications or signing messages. Issuing certificates is likely to be an important part of your day-to-day role as a security administrator.
# PUBLIC AND PRIVATE KEY USAGE 

Public key ([[asymmetric]]) cryptography solves the problem of distributing encryption keys when you want to communicate securely with others or authenticate a message that you send to others.

-   When you want others to send you confidential messages, you give them your public key to use to encrypt the message. The message can then only be decrypted by your private key, which you keep known only to yourself.
-   When you want to authenticate yourself to others, you create a signature and sign it by encrypting the signature with your private key. You give others your public key to use to decrypt the signature. As only you know the private key, everyone can be assured that only you could have created the signature.

**The basic problem with public key cryptography is that you may not really know with whom you are communicating. The system is vulnerable to man-in-the-middle attacks([[MITM]])**. This problem is particularly evident with e-commerce. How can you be sure that a shopping site or banking service is really maintained by whom it claims? The fact that the site is distributing public keys to secure communications is no guarantee of actual identity. How do you know that you are corresponding directly with the site using its certificate? How can you be sure there isn't a man-in-the-middle intercepting and modifying what you think the legitimate server is sending you?

**Public key infrastructure ([[PKI]]) aims to prove that the owners of public keys are who they say they are. Under PKI, anyone issuing public keys should obtain a digital certificate.** The validity of the certificate is guaranteed by a certificate authority ([[CA]]). The validity of the CA can be established using various models.
# CERTIFICATE AUTHORITIES

The certificate authority (CA) is the entity responsible for issuing and guaranteeing certificates. Private CAs can be set up within an organization for internal communications. Most network operating systems, including Windows Server, have certificate services. For public or business-to-business communications, however, the CA must be trusted by each party. Third-party CA services include IdenTrust, Digicert, Sectigo/Comodo, GoDaddy, and GlobalSign. The functions of a CA are as follows:

-   Provide a range of certificate services useful to the community of users serviced by the CA.
-   Ensure the validity of certificates and the identity of those applying for them (registration).
-   Establish trust in the CA by users and government and regulatory authorities and enterprises, such as financial institutions.
-   Manage the servers (repositories) that store and administer the certificates.
-   **Perform key and certificate lifecycle management, notably revoking invalid certificates.**

![The Issued Certificates folder is highlighted and a list of items is shown in a table including Certificate Template and Certificate Expiration date.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2781-1599771797970.png)

Microsoft Windows Server CA. (Screenshot used with permission from Microsoft.)
# PKI TRUST MODELS

The _trust model_ is a critical [[PKI]] concept, and shows how users and different CAs are able to trust one another.

### Single CA

In this simple model, a single CA issues certificates to users; users trust certificates issued by that CA and no other. The problem with this approach is that the single CA server is very exposed. If it is compromised, the whole PKI collapses.

### Hierarchical (Intermediate CA)

In the [[hierarchical model]], a single CA (called the _root_) issues certificates to several intermediate CAs. The intermediate CAs issue certificates to subjects (leaf or end entities). This model has the advantage that different intermediate CAs can be set up with different certificate policies, enabling users to perceive clearly what a particular certificate is designed for. Each leaf certificate can be traced back to the root CA along the certification path. This is also referred to as certificate chaining, or a _chain of trust._ The root's certificate is self-signed. In the hierarchical model, the root is still a single point of failure. If the root is damaged or compromised, the whole structure collapses. To mitigate against this, however, the root server can be taken offline, as most of the regular CA activities are handled by the intermediate CA servers.

![Screenshot with the "Issuer" certificate field highlighted, showing the field value "CN = GlobalSign, O = GlobalSign, OU = GlobalSign Root CA - R3".](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5857-1599771798031.png)

A certification path. The leaf certificate ([www.globalsign.com](https://www.globalsign.com/)) was issued by an intermediate Extended Validation CA, and that CA's certificate was issued by the root CA. (Screenshot used with permission from Microsoft.)

Another problem is that there is limited opportunity for cross-certification; that is, to trust the CA of another organization. Two organizations could agree to share a root CA, but this would lead to operational difficulties that could only increase as more organizations join. In practice, most clients are configured to trust multiple root CAs.

### Online versus Offline CAs

An online CA is one that is available to accept and process certificate signing requests, publish certificate revocation lists, and perform other certificate management tasks. Because of the high risk posed by compromising the root CA, a secure configuration involves making the root an offline CA. This means that it is disconnected from any network and usually kept in a powered-down state. The root CA will need to be brought online to add or update intermediate CAs.
# REGISTRATION AUTHORITIES AND CSRS

**Registration is the process by which end users create an account with the CA and become authorized to request certificates.** The exact processes by which users are authorized and their identity proven are determined by the CA implementation. For example, in a Windows Active Directory network, users and devices can often auto-enroll with the CA just by authenticating to Active Directory. Commercial CAs might perform a range of tests to ensure that a subject is who he or she claims to be. It is in the CA's interest to ensure that it only issues certificates to legitimate users, or its reputation will suffer.

On a private network (such as a Windows domain), the right to issue certificates of different types must be carefully controlled. The Windows CA supports access permissions for each certificate type so that you can choose which accounts are able to issue them.

When a subject wants to obtain a certificate, it completes a **[[certificate signing request]] (CSR)** and submits it to the CA. The CSR is a Base64 ASCII file containing the information that the subject wants to use in the certificate, including its public key.

The CA reviews the certificate and checks that the information is valid. For a web server, this may simply mean verifying that the subject name and fully qualified domain name ([[FQDN]]) are identical, and verifying that the CSR was initiated by the person administratively responsible for the domain, as identified in the domain's WHOIS records. If the request is accepted, the CA signs the certificate and sends it to the subject.

The registration function may be delegated by the CA to one or more registration authorities (RAs). These entities complete identity checking and submit CSRs on behalf of end users, but they do not actually sign or issue certificates.
# DIGITAL CERTIFICATES

**A digital certificate is essentially a wrapper for a subject's public key.** As well as the public key, it contains information about the subject and the certificate's issuer or guarantor. The certificate is digitally signed to prove that it was issued to the subject by a particular CA. The subject could be a human user (for certificates allowing the signing of messages, for instance) or a computer server (for a web server hosting confidential transactions, for instance).

![The field "Public Key" is highlighted in a list of items with value "RSA (2048 Bits)". A pane below is filled with pairs of alphanumeric characters.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9294-1599771798160.png)

Digital certificate details. (Screenshot used with permission from Microsoft.)

Digital certificates are based on the X.509 standard approved by the International Telecommunications Union and standardized by the Internet Engineering Taskforce ([https://datatracker.ietf.org/doc/html/rfc5208](https://datatracker.ietf.org/doc/html/rfc5208)). The Public Key Infrastructure X.509 (PKIX) working group manages the development of these standards. RSA also created a set of standards, referred to as Public Key Cryptography Standards (PKCS), to promote the use of public key infrastructure.
# CERTIFICATE ATTRIBUTES

The X.509 standard defines the fields or attributes that must be present in the certificate. Some of the main fields are listed in the following **table**.

Field

Usage

Serial number

A number uniquely identifying the certificate within the domain of its CA. 

Signature algorithm

The algorithm used by the [[CA]] to sign the certificate.

Issuer

The name of the CA. 

Valid from/to

Date and time during which the certificate is valid.

Subject

The name of the certificate holder, expressed as a distinguished name (DN). Within this, the [[common name ]](CN) part should usually match either the fully qualified domain name ([[FQDN]]) of the server or a user email address.

Public key

Public key and algorithm used by the certificate holder.

Extensions

V3 certificates can be defined with extended attributes, such as friendly subject or issuer names, contact email addresses, and intended key usage. 

Subject alternative name (SAN)

This extension field is the preferred mechanism to specify additional host names for a single certificate.
# SUBJECT NAME ATTRIBUTES

When certificates were first introduced, the common name (CN) attribute was used to identify the [[FQDN]] by which the server is accessed, such as www.comptia.org. This usage grew by custom rather than design, however. The CN attribute can contain different kinds of information, making it difficult for a browser to interpret it correctly. Consequently, the CN attribute is deprecated as a method of validating subject identity ([tools.ietf.org/html/rfc2818#section-3.1](https://tools.ietf.org/html/rfc2818#section-3.1)).

The [[subject alternative name]] (SAN)** extension field is structured to represent different types of identifiers, including domain names. If a certificate is configured with a SAN, the browser should validate that, and ignore the CN value. It is still safer to put the FQDN in the CN as well, because not all browsers and implementations stay up to date with the standards.

The SAN field also allows a certificate to represent different subdomains, such as www.comptia.org and members.comptia.org.

![Dialog box has 3 panes: Certificate Hierarchy, Certificate Fields with "Certificate Subject Alt Name" highlighted, and Field Value listing DNS names.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7329-1599771798230.png)

Microsoft's website certificate configured with alternative subject names for different subdomains. (Screenshot used with permission from Microsoft.)

Listing the specific subdomains is more secure, but if a new subdomain is added, a new certificate must be issued. A wildcard domain, such as *.comptia.org, means that the certificate issued to the parent domain will be accepted as valid for all subdomains (to a single level).

![Detail of certificate properties dialog box with the Subject alternative name field selected in the first pane and the values DNS Name=*.comptia.org and DNS Name=comptia.org shown in the second pane](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2679-1599771798295.png)

CompTIA's website certificate configured with a wildcard domain, allowing access via either https://comptia.org or https://www.comptia.org. (Screenshot used with permission from Microsoft.)
# TYPES OF CERTIFICATE 

Certificate policies define the different uses of certificate types issued by the [[CA]]. These can be configured as standard certificate templates.

A certificate type is set by configuring the Key Usage attribute. The Extended Key Usage (EKU) field—referred to by Microsoft as _Enhanced Key Usage_—is a complementary means of defining usage. Typical values used include Server Authentication, Client Authentication, Code Signing, or Email Protection. The EKU field is more flexible than the Key Usage field, but problems can occur when nonstandard or vendor-specific definitions are used.

An extension can be tagged as **_critical,_** meaning that the application processing the certificate must be able to interpret the extension correctly; otherwise, the certificate should be rejected. In the case of a Key Usage extension marked as critical, an application should reject the certificate if it cannot resolve the Key Usage value. For example, this prevents a certificate issued for encrypting traffic sent to a web server from being used for signing an email message.

![The Certificate Templates folder is highlighted, and a list of items under the column headings "Name" and "Intended Purpose" is shown.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1167-1599771798391.png)

Certificate templates for Windows Server CA. (Screenshot used with permission from Microsoft.)
# WEB SERVER CERTIFICATE TYPES

==A server certificate guarantees the identity of e-commerce sites or any sort of website to which users submit data that should be kept confidential.== One of the problems with public key cryptography and trust models is that anyone can set up a [[PKI]] solution. It is also simple to register convincing-sounding domain names, such as my-bank-server.foo, where the "real" domain is mybank.foo. If users choose to trust a certificate in the naïve belief that simply having a certificate makes a site trustworthy, they could expose themselves to fraud. There have also been cases of disreputable sites obtaining certificates from third-party [[CA]]s that are automatically trusted by browsers that apparently validate their identities as financial institutions.

Differently graded certificates might be used to provide levels of security; for example, an online bank requires higher security than a site that collects marketing data.

-   Domain Validation (DV)—proving the ownership of a particular domain. This may be proved by responding to an email to the authorized domain contact or by publishing a text record to the domain. This process can be highly vulnerable to compromise. 

![Browser pop-up window showing Security tab displays over a web page with a small locked padlock icon before the page URL.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8767-1599771798466.png)

Domain validation certificate. Only the padlock is shown and the browser reports that the owner is not verified. (Screenshot used with permission from Microsoft.)

-   Extended Validation (EV)—subjecting to a process that requires more rigorous checks on the subject's legal identity and control over the domain or software being signed. EV standards are maintained by the CA/Browser forum ([cabforum.org](https://cabforum.org/)). An EV certificate cannot be issued for a wildcard domain.

![Browser pop-up window showing Security tab displays over a web page with a small locked padlock icon and "GMO GlobalSign, Inc. US)" before the URL.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4498-1599771798580.png)

Extended validation certificate from GlobalSign with the verified owner shown in green next to the padlock. (Screenshot used with permission from GlobalSign, Inc.)

Selected fields in a digital certificate viewed from the Firefox browser.
# OTHER CERTIFICATE TYPES

Web servers are not the only systems that need to validate identity. There are many other certificate types, designed for different purposes.

### Machine/Computer Certificates

It might be necessary to issue certificates to machines (servers, PCs, smartphones, and tablets), regardless of function. For example, in an Active Directory domain, machine certificates could be issued to Domain Controllers, member servers, or even client workstations. Machines without valid domain-issued certificates could be prevented from accessing network resources. Machine certificates might be issued to network appliances, such as routers, switches, and firewalls. The SAN and often the CN attribute should be set to the FQDN of the machine (host name and local domain part).

### Email/User Certificates

An _email certificate_ can be used to sign and encrypt email messages, typically using Secure Multipart Internet Message Extensions (S/MIME) or Pretty Good Privacy (PGP). The user's email address must be entered as the SAN and CN. On a directory-based local network, such as Windows Active Directory, there may be a need for a wider range of user certificate types. For example, in AD there are user certificate templates for standard users, administrators, smart card logon/users, recovery agent users, and Exchange mail users (with separate templates for signature and encryption). Each certificate template has different key usage definitions.

![Screenshot of Certificate Enrollment window.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/6394-1599771798657.png)

Requesting a certificate. The [[CA]] has made several user-type certificate templates available with different key usage specifications (encrypting files, signing emails, encrypting emails, and so on). (Screenshot used with permission from Microsoft.)

### Code Signing Certificates

A code signing certificate is issued to a software publisher, following some sort of identity check and validation process by the CA. The publisher then signs the executables or [[DLLs]] that make up the program to guarantee the validity of a software application or browser plug-in. Some types of scripting environments, such as PowerShell, can also require valid digital signatures. The CN is set to an organization name, such as "CompTIA Development Services, LLC," rather than an FQDN.

### Root Certificate

The root certificate is the one that identifies the CA itself. The root certificate is self-signed. A root certificate would normally use a key size of at least 2048 bits. Many providers are switching to 4096 bits. The CN for a root certificate is set to the organization/CA name, such as "CompTIA Root CA," rather than an FQDN.

### Self-signed Certificates

Any machine, web server, or program code can be deployed with a [[self-signed certificate]]. Self-signed certificates will be marked as untrusted by the operating system or browser, but an administrative user can choose to override this.
