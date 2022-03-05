---
tags: [GRC, implementation]
---
# ## 

LESSON INTRODUCTION

As well as ensuring that only valid users and devices connect to managed networks and devices, you must ensure that these subjects are authorized with only necessary permissions and privileges to access and change resources. These tasks are complicated by the need to manage identities across on-premises networks and cloud services. Also, account security depends on effective organizational policies for personnel and security training. You will often be involved in shaping and updating these policies in line with best practice, as well as delivering security awareness education and training programs.

## 

LESSON OBJECTIVES

In this lesson, you will:

-   Implement identity and account types.
-   Implement account policies.
-   Implement authorization solutions.
-   Explain the importance of personnel policies.
# EXAM OBJECTIVES COVERED

3.7 Given a scenario, implement identity and account management controls

5.3 Explain the importance of policies to organizational security

**Least privilege** is the principle at the heart of most organizational security policies. Identity and privilege management helps an organization to account for the actions of both regular and administrative users. These systems are complicated by the presence of default, shared, guest, and device account types that are difficult to associate with a single identity.
# IDENTITY MANAGEMENT CONTROLS

On a private network, a digital identity can be represented by an account. The network administrator ensures the integrity of the server hosting the accounts, while each user is responsible for protecting the credentials so that only they can authenticate to the account and use it. On public networks and as an extra layer of protection on private networks, the account may also be identified by some cryptographic material.

### Certificates and Smart Cards

Public key infrastructure ([[PKI]]) allows the management of digital identities, where a certificate authority ([[CA]]) issues certificates to **validated subjects (users and servers)**. The subject identity can be trusted by any third party that also trusts the CA.

**The certificate contains the subject's public key and is signed by the CA's private key**. These public keys allow third parties to verify the certificate and the signature. The **subject's public key** is part of a pair with a linked private key. The private key must be kept secret. It can be stored on the computer, either in the file system or in a trusted platform module ([[TPM]]) chip. Alternatively, a **user's certificate and private key** can be stored on a smart card or USB key and used to authenticate to different PCs and mobile devices.

### Tokens

It is inconvenient for users to authenticate to each application they need to use. In a single sign-on system, the user authenticates to an identity provider ([[IdP]]) and receives a cryptographic token. The user can present that token to compatible applications as proof they are authenticated, and receive authorizations from the application. With a token, there is always a risk that a malicious actor will be able to capture and **replay** it. The application protocol that makes use of tokens must be designed to resist this type of attack.

### Identity Providers

The identity provider is the service that provisions the user account and processes authentication requests. On a private network, these identity directories and application authorization services can be operated locally. The same site operates both identity provision and application provision. Most networks now make use of third-party cloud services, however. In this scenario, various protocols and frameworks are available to implement federated identity management across web-based services. This means that a user can create a digital identity with one provider, but other sites can use that identity to authorize use of an application.
# BACKGROUND CHECK AND ONBOARDING POLICIES 

Identity and access management ([[IAM]]) involves both IT/security procedures and technologies and Human Resources (HR) policies. Personnel management policies are applied in three phases:

-   Recruitment (hiring)—locating and selecting people to work in particular job roles. Security issues here include screening candidates and performing background checks.
-   Operation (working)—it is often the HR department that manages the communication of policy and training to employees (though there may be a separate training and personal development department within larger organizations). As such, it is critical that HR managers devise training programs that communicate the importance of security to employees.
-   Termination or separation (firing or retiring)—whether an employee leaves voluntarily or involuntarily, termination is a difficult process, with numerous security implications. 

### Background Check

A background check determines that a person is who they say they are and are not concealing criminal activity, bankruptcy, or connections that would make them unsuitable or risky. Employees working in high confidentiality environments or with access to high value transactions will obviously need to be subjected to a greater degree of scrutiny. For some jobs, especially federal jobs requiring a security clearance, background checks are mandatory. Some background checks are performed internally, whereas others are done by an external third party. 

### Onboarding

Onboarding at the HR level is the process of welcoming a new employee to the organization. The same sort of principle applies to taking on new suppliers or contractors. Some of the same checks and processes are used in creating customer and guest accounts. As part of onboarding, the IT and HR function will combine to create an account for the user to access the computer system, assign the appropriate privileges, and ensure the account credentials are known only to the valid user. These functions must be integrated, to avoid creating accidental configuration vulnerabilities, such as IT creating an account for an employee who is never actually hired. Some of the other tasks and processes involved in onboarding include:

-   **Secure transmission of credentials**—creating and sending an initial password or issuing a smart card securely. The process needs protection against rogue administrative staff. Newly created accounts with simple or default passwords are an easily exploitable backdoor.
-   **Asset allocation**—provision computers or mobile devices for the user or agree to the use of bring-your-own-device handsets.
-   **Training/policies**—schedule appropriate security awareness and role-relevant training and certification. 

### Nondisclosure Agreement (NDA)

The terms of an nondisclosure agreement (NDA) might be incorporated within the employee contract or could be a separate document. When an employee or contractor signs an NDA, they are asserting that they will not share confidential information with a third party.
# PERSONNEL POLICIES FOR PRIVILEGE MANAGEMENT

HR and IT must collaborate to ensure effective privilege management. These policies aim to ensure that the risk of insider threat is minimized. 

### Separation of Duties 

Separation of duties is a means of establishing checks and balances against the possibility that critical systems or procedures can be compromised by insider threats. Duties and responsibilities should be divided among individuals to prevent ethical conflicts or abuse of powers. 

An employee is supposed to work for the interests of their organization exclusively. A situation where someone can act in his or her own interest, personally, or in the interests of a third party is said to be a conflict of interest.

Separation of duties means that employees must be constrained by security policies:

-   Standard operating procedures (SOPs) mean that an employee has no excuse for not following protocol in terms of performing these types of critical operations.
-   Shared authority means that no one user is able to take action or enable changes on his or her own authority. At least two people must authorize the change. One example is separating responsibility for purchasing (ordering) from that of authorizing payment. Another is that a request to create an account should be subject to approval and oversight.

Separation of duties does not completely eliminate risk because there is still the chance of collusion between two or more people. This, however, is a much less likely occurrence than a single rogue employee.

### Least Privilege

Least privilege means that a user is granted sufficient rights to perform his or her job and no more. This mitigates risk if the account should be compromised and fall under the control of a threat actor. **Authorization creep** refers to a situation where a user acquires more and more rights, either directly or by being added to security groups and roles. Least privilege should be ensured by closely analyzing business workflows to assess what privileges are required and by performing regular account audits. 

### Job Rotation

Job rotation (or rotation of duties) means that no one person is permitted to remain in the same job for an extended period. For example, managers may be moved to different departments periodically, or employees may perform more than one job role, switching between them throughout the year. Rotating individuals into and out of roles, such as the firewall administrator or access control specialist, helps an organization ensure that it is not tied too firmly to any one individual because vital institutional knowledge is spread among trusted employees. **Job rotation also helps prevent abuse of power, reduces boredom, and enhances individuals' professional skills.** 

### Mandatory Vacation

Mandatory vacation means that employees are forced to take their vacation time, during which someone else fulfills their duties. The typical mandatory vacation policy requires that employees take at least one vacation a year in a full-week increment so that they are away from work for at least five days in a row. **During that time, the corporate audit and security employees have time to investigate and discover any discrepancies in employee activity.**
# OFFBOARDING POLICIES

An exit interview (or offboarding) is the process of ensuring that an employee leaves a company gracefully. Offboarding is also used when a project using contractors or third parties ends. In terms of security, there are several processes that must be completed:

-   Account management—disable the user account and privileges. Ensure that any information assets created or managed by the employee but owned by the company are accessible (in terms of encryption keys or password-protected files).
-   Company assets—retrieve mobile devices, keys, smart cards, USB media, and so on. The employee will need to confirm (and in some cases prove) that they have not retained copies of any information assets.
-   Personal assets—wipe employee-owned devices of corporate data and applications. The employee may also be allowed to retain some information assets (such as personal emails or contact information), depending on the policies in force.

The departure of some types of employees should trigger additional processes to re-secure network systems. Examples include employees with detailed knowledge of security systems and procedures, and access to shared or generic account credentials. These credentials must be changed immediately.
# SECURITY ACCOUNT TYPES AND CREDENTIAL MANAGEMENT

Operating systems, network appliances, and network directory products use some standard account types as the basis of a privilege management system. These include standard user, administrative user, security group accounts, and service accounts.

Standard users have limited privileges, typically with access to run programs and to create and modify files belonging only to their profile. 

### Credential Management Policies for Personnel

**Improper credential management continues to be one of the most fruitful vectors for network attacks.** If an organization must continue to rely on password-based credentials, its usage needs to be governed by strong policies and training.

A password policy instructs users on best practice in choosing and maintaining passwords. More generally, a credential management policy should instruct users on how to keep their authentication method secure, whether this be a password, smart card, or biometric ID. Password protection policies mitigate against the risk of attackers being able to compromise an account and use it to launch other attacks on the network. The credential management policy also needs to alert users to diverse types of social engineering attacks. Users need to be able to spot phishing and pharming attempts, so that they do not enter credentials into an unsecure form or spoofed site. 

### Guest Accounts

A guest account is a special type of shared account with no password. It allows anonymous and unauthenticated access to a resource. The Windows OS creates guest user and group accounts when installed, but the guest user account is disabled by default. Guest accounts are also created when installing web services, as most web servers allow unauthenticated access.
# SECURITY GROUP-BASED PRIVILEGES 

As well as an account to use resources on the local computer, users also typically need accounts to use resources on the network. In fact, most accounts are created on a network directory and then given permission to log in on certain computer or workstation objects.

One approach to network privilege management is to assign privileges directly to user accounts. This model is only practical if the number of users is small. With large number of users, it is difficult to audit and to apply privilege policies consistently.

The concept of a security group account simplifies and centralizes the administrative process of assigning rights. Rather than assigning rights directly, the system owner assigns them to security group accounts. User accounts gain rights by being made a member of a security group. A user can be a member of multiple groups and can therefore receive rights and permissions from several sources.

Using security groups to assign privileges. (Images © 123RF.com.)
# ADMINISTRATOR/ROOT ACCOUNTS

Administrative or privileged accounts are able to install and remove apps and device drivers, change system-level settings, and access any object in the file system. Ideally, only accounts that have been created and assigned specific permissions should have this kind of elevated privilege. In practice, it is very hard to eliminate the presence of default administrator accounts. A default account is one that is created by the operating system or application when it is installed. The default account has every permission available. In Windows, this account is called Administrator; in Linux, it is called root. This type of account is also referred to as a superuser.

### Generic Administrator Account Management

Superuser accounts directly contradict the principles of least privilege and separation of duties. Consequently, superuser accounts should be prohibited from logging on in normal circumstances. The default superuser account should be restricted to disaster recovery operations only. In Windows, the account is usually disabled by default and can be further restricted using group policy ([docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-h--securing-local-administrator-accounts-and-groups](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-h--securing-local-administrator-accounts-and-groups)). The first user account created during setup has superuser permissions, however.

On Windows networks, you also need to distinguish between local administrators and domain administrators. The scope of a local administrator's privileges is restricted to the machine hosting the account. Domain administrators can have privileges over any machine joined to the domain.

Ubuntu Linux follows a similar approach; the root account is configured with no password and locked, preventing login. An alternate superuser account is created during setup. In other Linux distributions, a password is usually set at install time. This password must be kept as secure as is possible.

### Administrator Credential Policies 

The default superuser should be replaced with one or more named accounts with sufficient elevated privileges for a given job role. This can be referred to as generic account prohibition. It means that administrative activity can be audited and the system as a whole conforms to the property of non-repudiation. 

It is a good idea to restrict the number of administrative accounts as much as possible. The more accounts there are, the more likely it is that one of them will be compromised. On the other hand, you do not want administrators to share accounts, as that compromises accountability.

Users with administrative privileges must take the greatest care with credential management. Privilege-access accounts must use strong passwords and ideally multifactor authentication (MFA). 

### Default Security Groups

Most operating systems also create default security groups, with a default set of permissions. In Windows, privileges are assigned to local group accounts (the Users and Administrators groups) rather than directly to user accounts. Custom security groups with different permissions can be created to enforce the principle of least privilege. In Linux, privileged accounts are typically configured by adding either a user or a group account to the /etc/sudoers file ([linux.com/training-tutorials/start-fine-tuning-sudo-linux](https://www.linux.com/training-tutorials/start-fine-tuning-sudo-linux/)).
# SERVICE ACCOUNTS

Service accounts are used by scheduled processes and application server software, such as databases. Windows has several default service account types. These do not accept user interactive logons but can be used to run processes and background services:

-   System—has the most privileges of any Windows account. The local system account creates the host processes that start Windows before the user logs on. Any process created using the system account will have full privileges over the local computer.
-   Local Service—has the same privileges as the standard user account. It can only access network resources as an anonymous user.
-   Network Service—has the same privileges as the standard user account but can present the computer's account credentials when accessing network resources.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3635-1599771800122.png)

Configuring the credentials for a service running on Windows Server. This service is using the local system account. This account has full local administrator privileges. (Screenshot used with permission from Microsoft.)

Linux also uses the concept of service accounts to run non-interactive daemon processes, such as web servers and databases. These accounts are usually created by the server application package manager. Users can be prevented from logging into these accounts (often by setting the password to an unknown value and denying shell access).

If a named account is manually configured to run a service, the password for the service account will effectively be shared by multiple administrators. Many operating systems support automatic provisioning of credentials for service accounts, reducing the risk of insider threat ([techcommunity.microsoft.com/t5/ask-the-directory-services-team/managed-service-accounts-understanding-implementing-best/ba-p/397009](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/managed-service-accounts-understanding-implementing-best/ba-p/397009)).

Be aware of the risk of using a personal account when a service account is appropriate. If you use a personal account and the user changes the password or the account is disabled for some reason, then the service will fail to run, which can cause serious problems with business applications.
# SHARED/GENERIC/DEVICE ACCOUNTS AND CREDENTIALS

A shared account is one where passwords (or other authentication credentials) are known to more than one person. Typically, simple SOHO networking devices do not allow for the creation of multiple accounts and a single "Admin" account is used to manage the device. These accounts might be configured with a default password. Other examples include the default (or generic) OS accounts, such as Administrator and Guest in Windows or root in Linux, or accounts added to default security groups. Shared accounts may also be set up for temporary staff.

A shared account breaks the principle of non-repudiation and makes an accurate audit trail difficult to establish. It makes it more likely that the password for the account will be compromised. The other major risk involves password changes to an account. Since frequent password changing is a common policy, organizations will need to ensure that everyone who has access to an account knows when the password will change, and what that new password will be. This necessitates distributing passwords to a large group of people, which itself poses a significant challenge to security. Shared accounts should only be used where these risks are understood and accepted.

### Credential Policies for Devices

Network appliances designed for enterprise use are unlikely to be restricted to a single default account, and will use TACACS+ to support individual accounts and role-based permissions. If a device can only be operated with a shared password, ensure separation of duties to ensure the device remains in an authorized configuration.

### Privilege Access Management

Even with the most carefully designed role-based permissions, it is almost impossible to eliminate use of shared/device/root passwords completely. Enterprise privilege access management products provide a solution for storing these high-risk credentials somewhere other than a spreadsheet and for auditing elevated privileges generally ([gartner.com/reviews/market/privileged-access-management](https://www.gartner.com/reviews/market/privileged-access-management)).
# SECURE SHELL KEYS AND THIRD-PARTY CREDENTIALS

Secure Shell (SSH) is a widely used remote access protocol. It is very likely to be used to manage devices and services. SSH uses two types of key pairs:

-   A host key pair identifies an SSH server. The server reveals the public part when a client connects to it. The client must use some means of determining the validity of this public key. If accepted, the key pair is used to encrypt the network connection and start a session.
-   A user key pair is a means for a client to login to an SSH server. The server stores a copy of the client's public key. The client uses the linked private key to generate an authentication request and sends the request (not the private key) to the server. The server can only validate this request if the correct public key is held for that client.

SSH keys have often not been managed very well, leading to numerous security breaches, most infamously the Sony hack ([ssh.com/malware](https://www.ssh.com/malware/)). There are vendor solutions for SSH key management or you can configure servers and clients to use public key infrastructure (PKI) and certificate authorities (CAs) to validate identities.

A third-party credential is one used by your company to manage a vendor service or cloud app. As well as administrative logons, devices and services may be configured with a password or cryptographic keys to access hosts via SSH or via an application programming interface (API). Improper management of these secrets, such as including them in code or scripts as plaintext, has been the cause of many breaches ([nakedsecurity.sophos.com/2019/03/25/thousands-of-coders-are-leaving-their-crown-jewels-exposed-on-github](https://nakedsecurity.sophos.com/2019/03/25/thousands-of-coders-are-leaving-their-crown-jewels-exposed-on-github/)).

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2885-1599771800213.png)

Security credentials for an account on Amazon Web Services (AWS). The user can authenticate with a password credential, or use an access key within a script. The access key is stored only on the user's client device and cannot be retrieved via the console. It can be disabled or deleted, however. (Screenshot courtesy of Amazon.com)
