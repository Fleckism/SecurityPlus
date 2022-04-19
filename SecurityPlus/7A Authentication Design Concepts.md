---
tags: [section]
---
# LESSON INTRODUCTION

Each network user and host device must be identified with an account so that you can control their access to your organization's applications, data, and services. The processes that support this requirement are referred to as identity and access management ([[IAM]]). Within IAM, authentication technologies ensure that only valid subjects (users or devices) can operate an account. Authentication requires the account holder to submit credentials that should only be known or held by them in order to access the account. There are many authentication technologies and it is imperative that you be able to compare and contrast and to implement these security controls.

Lesson Objectives

In this lesson, you will:

-   Summarize authentication ( #A_D ) design #concepts.
-   Implement knowledge-based authentication.
-   Implement authentication technologies.
-   Summarize biometrics authentication concepts.
# EXAM OBJECTIVES COVERED

2.4 Summarize authentication and authorization design concepts

Strong authentication is the first line of defense in the battle to secure network resources. But authentication is not a single process; there are many different methods and mechanisms, some of which can be combined to form more effective products. As a network security professional, familiarizing yourself with identification and authentication technologies can help you select, implement, and support the ones that are appropriate for your environment.
# IDENTITY AND ACCESS MANAGEMENT 

An **access control system** is the set of technical controls that govern how subjects may interact with objects. Subjects in this sense are users, devices, or software processes, or anything else that can request and be granted access to a resource. Objects are the resources; these could be networks, servers, databases, files, and so on. An identity and access management (IAM) system is usually described in terms of four main processes: 

-   **Identification**—creating an account or ID that uniquely represents the user, device, or process on the network. 
-   **Authentication**—proving that a subject is who or what it claims to be when it attempts to access the resource. 
-   **Authorization**—determining what rights subjects should have on each resource, and enforcing those rights. 
-   **Accounting**—tracking authorized usage of a resource or use of rights by a subject and alerting when unauthorized use is detected or attempted. 

Differences among identification, authentication, authorization, and accounting. (Images © 123RF.com.)

[[IAM]] enables you to define the attributes that make up an entity's identity, such as its purpose, function, security clearance, and more. These attributes subsequently enable access management systems to make informed decisions about whether to grant or deny an entity access, and if granted, decide what the entity has authorization to do. For example, an individual employee may have his or her own identity in the IAM system. The employee's role in the company factors into his or her identity, such as what department the employee is in and whether the employee is a manager. For example, if you are setting up an e-commerce site and want to enroll users, you need to select the appropriate controls to perform each function: 

-   **Identification**—ensure that customers are legitimate. For example, you might need to ensure that billing and delivery addresses match and that they are not trying to use fraudulent payment methods. 
-   **Authentication**—ensure that customers have unique accounts and that only they can manage their orders and billing information. 
-   **Authorization**—rules to ensure customers can place orders only when they have valid payment mechanisms in place. You might operate loyalty schemes or promotions that authorize certain customers to view unique offers or content. 
-   **Accounting**—the system must record the actions a customer takes (to ensure that they cannot deny placing an order, for instance). 

The servers and protocols that implement these functions are referred to as authentication, authorization, and accounting ([[AAA]]). The use of [[IAM]] to describe enterprise processes and workflows is becoming more prevalent as the importance of the identification phase is better acknowledged.
# AUTHENTICATION FACTORS 

Assuming that an account has been created securely (the identity of the account holder has been verified), **authentication verifies that only the account holder is able to use the account**, and that the system may only be used by account holders. Authentication is performed when the account holder supplies the appropriate **credentials** (or authenticators) to the system. These are compared to the credentials stored on the system. If they match, the account is authenticated. 

There are many different technologies for defining credentials and can be categorized as _factors._ 

### Something You Know Authentication

The typical knowledge factor is the _logon,_ composed of a username and a password. The username is typically not a secret (although it should not be published openly), but the password must be known only to the account holder. A passphrase is a longer password composed of several words. This has the advantages of being more secure and easier to remember. A personal identification number (PIN) is also something you know, although long PIN codes are hard to remember, and short codes are too vulnerable for most authentication systems. Swipe patterns are often used for authentication to touch-based devices.

![CompTIA logo shows above username "James at CompTIA" and input box with gray text "Password" and cursor.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7852-1599771798946.png)

Windows sign-in screen. (Screenshot used with permission from Microsoft.)

A knowledge factor is also used for account reset mechanisms. For example, to reset the password on an account, the user might have to respond to a challenge question, such as, "What is your favorite movie?"

### Something You Have Authentication

An **_ownership** factor_ means that the account holder possesses something that no one else does, such as a **smart card, fob, or wristband** programmed with a unique identity certificate or account number. Alternatively, they might have a USB fob that generates a unique code. These ownership factors can be described as hard tokens.

A device such as a smartphone can also be used to receive a uniquely generated access code as a soft token. Unlike a password, these tokens are valid for only one use, typically within a brief time window.

### Something You Are/Do Authentication

A _biometric factor_ uses either physiological identifiers, such as a fingerprint, or behavioral identifiers, such as the way someone moves (gait). The identifiers are scanned and recorded as a template. When the user authenticates, another scan is taken and compared to the template.
# AUTHENTICATION DESIGN 

_[[Authentication]] design_ refers to selecting a technology that meets requirements for confidentiality, integrity, and availability:

-   _Confidentiality,_ in terms of authentication, is critical, because if account credentials are leaked, [[threat actor]]s can impersonate the account holder and act on the system with whatever rights they have.
-   _Integrity_ means that the authentication mechanism is reliable and not easy for [[threat actor]]s to bypass or trick with counterfeit credentials.
-   _Availability_ means that the time taken to authenticate does not impede workflows and is easy enough for users to operate.

Authentication is used in different contexts and factors are not always well-suited to a context. For example, you might authenticate to a PC by inputting a password to get access to the device. This might also authenticate you to a network. But authentication is also used for physical security. If you consider numerous employees arriving for work, asking them to type a password to gain access to the building would take too long and cause huge disruption (**lack of availability**). It is also highly likely that passwords would be observed (**lack of confidentiality**). Finally, it is likely that users would simply start holding the door open for each other (**lack of integrity**). Authentication design tries to anticipate these issues and implements a technology that fits the use case.

(See [[security control]])
# MULTIFACTOR AUTHENTICATION 

An authentication technology is considered strong if it combines the use of more than one type of knowledge, ownership, and biometric factor, and is called multifactor authentication ([[MFA]]). Single-factor authentication can quite easily be compromised: a password could be written down or shared, a smart card could be lost or stolen, and a biometric system could be subject to high error rates or spoofing.

_Two-Factor Authentication ([[2FA]])_ combines either an ownership-based smart card or biometric identifier with something you know, such as a password or PIN. Three-factor authentication combines all three technologies, or incorporates an additional attribute, such as location; for example, a smart card with integrated fingerprint reader. This means that to authenticate, the user must possess the card, the user's fingerprint must match the template stored on the card, and the user must input a PIN or password.

Multifactor authentication requires a combination of different technologies. For example, requiring a PIN along with date of birth may be stronger than entering a PIN alone, but it is not multifactor.
# AUTHENTICATION ATTRIBUTES

Compared to the **three main authentication factors**, an authentication attribute is either a non-unique property or a factor that cannot be used independently. 

### Somewhere You Are Authentication

Location-based authentication measures some statistic about where you are. This could be a geographic location, measured using a device's location service, or it could be by IP address. A device's IP address could be used to refer to a logical network segment, or it could be linked to a geographic location using a geolocation service. Within a premises network, the physical port location, virtual LAN (VLAN), or Wi-Fi network can also be made the basis of location-based authentication.

Location-based authentication is not used as a primary authentication factor, but it may be used as a continuous authentication mechanism or as an access control feature. For example, if a user enters the correct credentials at a VPN gateway but his or her IP address shows him/her to be in a different country than expected, access controls might be applied to restrict the privileges granted or refuse access completely. Another example is where a user appears to login from different geographic locations that travel time would make physically impossible.

### Something You Can Do Authentication

Behavioral characteristics, such as the way you walk or the way you hold your smartphone, can uniquely identify you to a considerable degree of accuracy. Although this factor is impractical to use for primary authentication, it can be used for contextual and continual authentication to ensure that a device continues to be operated by the owner.

### Something You Exhibit Authentication

_Something you exhibit_ also refers to behavioral-based authentication and authorization, with specific emphasis on personality traits. For example, the way you use smartphone apps or web search engines might conform to a pattern of behavior that can be captured by machine learning analysis as a statistical template. If someone else uses the device, their behavior will be different, and this anomalous pattern could be used to lock the device and require reauthentication.

### Someone You Know Authentication

A someone you know authentication scheme uses a web of trust model, where new users are vouched for by existing users. As the user participates in the network, their identity becomes better established. One example is the decentralized web of trust model, used by Pretty Good Privacy (PGP) as an alternative to PKI ([weboftrust.info/index.html](https://www.weboftrust.info/index.html)).
