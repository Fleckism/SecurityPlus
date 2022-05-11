
# EXAM OBJECTIVES COVERED

2.4 Summarize authentication and authorization design concepts

3.8 Given a scenario, implement authentication and authorization solutions

4.1 Given a scenario, use the appropriate **tool to assess organizational security ([[chmod]] only)**

Implementing an effective authorization solution system requires understanding of the different models that such systems can be based on. While an on-premises network can use a local directory to manage accounts and rights, as organizations move services to the cloud, these authorizations have to be #Implementation  using **federated identity management solutions**.
# DISCRETIONARY AND ROLE-BASED ACCESS CONTROL

An important consideration in designing a security system is to determine how users receive rights or permissions. The different models are referred to as **access control schemes**. #A_D 

### Discretionary Access Control (DAC)

Discretionary access control ([[DAC]]) is based on the primacy of the resource owner. The owner is originally the creator of a file or service, though ownership can be assigned to another user. The owner is granted full control over the resource, meaning that he or she can modify its access control list ([[ACL]]) to grant rights to others.

DAC is the most flexible model and is currently implemented widely in terms of computer and network security. In terms of file system security, it is the model used by default for most UNIX/Linux distributions and by Microsoft Windows. As the most flexible model, it is also the weakest because it makes centralized administration of security policies the most difficult to enforce. It is also the easiest to compromise, as it is vulnerable to [[insider threats]] and abuse of compromised accounts.

### Role-Based Access Control (RBAC)

Role-based access control ([[RBAC]]) adds an extra degree of centralized control to the DAC model. Under RBAC, a set of organizational roles are defined, and subjects allocated to those roles. Under this system, the right to modify roles is reserved to a system owner. Therefore, the system is non-discretionary, as each subject account has no right to modify the [[ACL]] of a resource, even though they may be able to change the resource in other ways. **Users are said to gain rights implicitly (through being assigned to a role) rather than explicitly (being assigned the right directly)**.

RBAC can be partially implemented through the use of security group accounts, but they are not identical schemes. Membership of security groups is largely discretionary (assigned by administrators, rather than determined by the system). Also, ideally, a subject should only inherit the permissions of a role to complete a particular task rather than retain them permanently.
# FILE SYSTEM PERMISSIONS 

An access control model can be applied to any type of data or software resource but is most closely associated with network, file system, and database security. With file system security, each object in the file system has an ACL associated with it. The [[ACL]] contains a list of accounts (principals) allowed to access the resource and the permissions they have over it. Each record in the ACL is called an access control entry ([[ACE]]). The order of ACEs in the ACL is important in determining effective permissions for a given account. ACLs can be enforced by a file system that supports permissions, such as NTFS, ext3/ext4, or ZFS.

![Screenshot showing Permission Entry for LABFILES folder.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7383-1599771801338.png)

Configuring an access control entry for a folder. (Screenshot used with permission from Microsoft.)

**For example, in Linux, there are three basic permissions:**

-   Read (r)—the ability to access and view the contents of a file or list the contents of a directory.
-   Write (w)—the ability to save changes to a file, or create, rename, and delete files in a directory (also requires execute).
-   Execute (x)—the ability to run a script, program, or other software file, or the ability to access a directory, execute a file from that directory, or perform a task on that directory, such as file search.

These permissions can be applied in the context of the owner user (u), a group account (g), and all other users/world (o). A permission string lists the permissions granted in each of these contexts:

d rwx r-x r-x home

The string above shows that for the directory (d), the owner has read, write, and execute permissions, while the group context and other users have read and execute permissions.

The [[chmod]] command is used to modify permissions. It can be used in symbolic mode or absolute mode. In symbolic mode, the command works as follows:

chmod g+w, o-x home

The effect of this command is to append write permission to the group context and remove execute permission from the other context. By contrast, the command can also be used to replace existing permissions. For example, the following command applies the configuration shown in the first permission string:

chmod u=rwx,g=rx,o=rx home

In absolute mode, permissions are assigned using octal notation, where r=4, w=2, and x=1. For example, the following command has the same effect:

chmod 755 home
# MANDATORY AND ATTRIBUTE-BASED ACCESS CONTROL

The [[DAC]] and [[RBAC]] models expose privileged accounts to the threat of compromise. More restrictive access control models can be used to mitigate this threat.

### Mandatory Access Control (MAC)

Mandatory access control ([[MAC]]) is based on the idea of security clearance levels. Rather than defining ACLs on resources, each object and each subject is granted a clearance level, referred to as a label. If the model used is a hierarchical one (that is, high clearance users are trusted to access low clearance objects), subjects are only permitted to access objects at their own clearance level or below.

The labelling of objects and subjects takes place using pre-established rules. The critical point is that these rules cannot be changed by any subject account, and are therefore non-discretionary. Also, a subject is not permitted to change an object's label or to change his or her own label.

### Attribute-Based Access Control (ABAC)

Attribute-based access control ([[ABAC]]) is the most fine-grained type of access control model. As the name suggests, an ABAC system is capable of making access decisions based on a combination of subject and object attributes plus any context-sensitive or system-wide attributes. As well as group/role memberships, these attributes could include information about the OS currently being used, the IP address, or the presence of up-to-date patches and anti-malware. An attribute-based system could monitor the number of events or alerts associated with a user account or with a resource, or track access requests to ensure they are consistent in terms of timing of requests or geographic location. It could be programmed to implement policies, such as [[M-of-N]] control and separation of duties.
# RULE-BASED ACCESS CONTROL

Rule-based access control is a term that can refer to any sort of access control model where access control policies are determined by **system-enforced rules rather than system users.** As such, RBAC, ABAC, and MAC are all examples of rule-based (or non-discretionary) access control. As well as the formal models, rule-based access control principles are increasingly being implemented to protect computer and network systems founded on discretionary access from the sort of misconfiguration that can occur through DAC.

### Conditional Access

Conditional access is an example of rule-based access control. A conditional access system monitors account or device behavior throughout a session. If certain conditions are met, the account may be suspended or the user may be required to reauthenticate, perhaps using a 2-step verification method. The User Account Control ([[UAC]]) and sudo restrictions on privileged accounts are examples of conditional access. The user is prompted for confirmation or authentication when requests that require elevated privileges are made. Role-based rights management and ABAC systems can apply a number of criteria to conditional access, including location-based policies ([docs.microsoft.com/en-us/azure/active-directory/conditional-access/overview](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/overview)).

### Privileged Access Management

A privileged account is one that can make significant configuration changes to a host, such as installing software or disabling a firewall or other security system. Privileged accounts also have rights to log on network appliances and application servers.

Privileged access management ([[PAM]]) refers to policies, procedures, and technical controls to prevent the malicious abuse of privileged accounts and to mitigate risks from weak configuration control over privileges. These controls identify and document privileged accounts, giving visibility into their use, and manage the credentials used to access them ([beyondtrust.com/resources/glossary/privileged-access-management-pam](https://www.beyondtrust.com/resources/glossary/privileged-access-management-pam)).
# DIRECTORY SERVICES

Directory services are the principal means of providing privilege management and authorization on an enterprise network, storing information about users, computers, security groups/roles, and services. A directory is like a database, where an object is like a record, and things that you know about the object (attributes) are like fields. In order for products from different vendors to be interoperable, most directories are based on the same standard. The Lightweight Directory Access Protocol ([[LDAP]]) is a protocol widely used to query and update X.500 format directories. 

A distinguished name ([[DN]]) is a unique identifier for any given resource within an X.500-like directory. **A distinguished name is made up of attribute=value pairs, separated by commas**. The most specific attribute is listed first, and successive attributes become progressively broader. This most specific attribute is also referred to as the relative distinguished name, as it uniquely identifies the object within the context of successive (parent) attribute values.

![Items listed in "CN=Users" are shown. One item is Name: "CN=Bobby"
Class: "user"
Distinguished Name: "CN=Bobby,CN=Users,DC=classroom,DC=local"](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3499-1599771801395.png)

Browsing objects in an Active Directory LDAP schema. (Screenshot used with permission from Microsoft.)

The types of attributes, what information they contain, and the way object types are defined through attributes (some of which may be required, and some optional) is described by the #zFleck [[directory schema]]. Some of the attributes commonly used include common name (CN), organizational unit (OU), organization (O), country (C), and domain component (DC). For example, the distinguished name of a web server operated by Widget in the UK might be:

CN=WIDGETWEB, OU=Marketing, O=Widget, C=UK, DC=widget, DC=foo
# FEDERATION AND ATTESTATION

An on-premises network can use technologies such as LDAP and Kerberos, very often implemented as a Windows Active Directory network, because the administration of accounts and devices can be centralized. Expanding this type of network to share resources with business partners or use services in public clouds means implementing some type of federation technology.

### Federation

**Federation is the notion that a network needs to be accessible to more than just a well-defined group of employees**. In business, a company might need to make parts of its network open to partners, suppliers, and customers. The company can manage its employee accounts easily enough. Managing accounts for each supplier or customer internally may be more difficult. Federation means that the company trusts accounts created and managed by a different network. As another example, in the consumer world, a user might want to use both Google Apps and Twitter. If Google and Twitter establish a federated network for the purpose of authentication and authorization, then the user can log on to Twitter using his or her Google credentials or vice versa.

### Identity Providers and Attestation

In these models, the networks perform federated identity management. A user from one network is able to provide attestation that proves their identity. In very general terms, the process is similar to that of Kerberos authorization, and works as follows:

1.  The user (principal) attempts to access a service provider (SP), or the relying party (RP). The service provider redirects the principal to the identity provider (IdP) to authenticate.
2.  The principal authenticates with the identity provider and obtains an attestation of identity, in the form of some sort of token or document signed by the IdP.
3.  The principal presents the attestation to the service provider. The SP can validate that the IdP has signed the attestation because of its trust relationship with the IdP.
4.  The service provider can now connect the authenticated principal to its own accounts database. It may be able to query attributes of the user account profile held by the IdP, if the principal has authorized this type of access.

Federated identity management overview. (Images © 123RF.com.)

### Cloud versus On-Premises Requirements 

Where a company needs to make use of cloud services or share resources with business partner networks, authentication and authorization design comes with more constraints and additional requirements. Web applications might not support Kerberos, while third-party networks might not support direct federation with [[Active Directory/LDAP]]. The design for these cloud networks is likely to require the use of standards for performing federation and attestation between web applications.
# SECURITY ASSERTION MARKUP LANGUAGE 

A federated network or cloud needs specific protocols and technologies to implement user identity assertions and transmit attestations between the principal, the relying party, and the identity provider. Security Assertion Markup Language ([[SAML]]) is one such solution. SAML attestations (or authorizations) are written in eXtensible Markup Language (XML). Communications are established using Hyper Text Transfer ProtocolTTPs]]/Hyper Text Transfer ProtocolTTPs]]S and the Simple Object Access Protocol ([[SOAP]]). These secure tokens are signed using the XML signature specification. The use of a digital signature allows the relying party to trust the identity provider.

As an example of a SAML implementation, Amazon Web Services (AWS) can function as a SAML service provider. This allows companies using AWS to develop cloud applications to manage their customers' user identities and provide them with permissions on AWS without having to create accounts for them on AWS directly.

<samlp:Response xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol"

xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion" ID="200" Version="2.0"

IssueInstant="2020-01-01T20:00:10Z " Destination="https://sp.foo/saml/acs" InResponseTo="100".

 <saml:Issuer>https://idp.foo/sso</saml:Issuer>

 <ds:Signature>...</ds:Signature>

 <samlp:Status>...(success)...</samlp:Status.

<saml:Assertion xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

xmlns:xs="http://www.w3.org/2001/XMLSchema" ID="2000" Version="2.0"

IssueInstant="2020-01-01T20:00:09Z">

<saml:Issuer>https://idp.foo/sso</saml:Issuer>

<ds:Signature>...</ds:Signature>

 <saml:Subject>...

 <saml:Conditions>...

 <saml:AudienceRestriction>...

 <saml:AuthnStatement>...

 <saml:AttributeStatement>

 <saml:Attribute>...

 <saml:Attribute>...

 </saml:AttributeStatement>

 </saml:Assertion>

</samlp:Response>
# OAUTH AND OPENID CONNECT

Many public clouds use application programming interfaces ([[APIs]]) based on Representational State Transfer ([[REST]]) rather than [[SOAP]]. These are often called RESTful APIs. Where SOAP is a tightly specified protocol, REST is a looser architectural framework. This allows the service provider more choice over implementation elements. Compared to SOAP and SAML, there is better support for mobile apps. 

### OAuth

Authentication and authorization for a RESTful API is often implemented using the Open Authorization ([[OAuth]]) protocol. OAuth is designed to facilitate sharing of information (resources) within a user profile between sites. The user creates a password-protected account at an identity provider ([[IdP]]). The user can use that account to log on to an OAuth consumer site without giving the password to the consumer site. A user (resource owner) can grant a client an authorization to access some part of their account. A client in this context is an app or consumer site.

The user account is hosted by one or more resource servers. A resource server is also called an API server because it hosts the functions that allow clients (consumer sites and mobile apps) to access user attributes. Authorization requests are processed by an authorization server. A single authorization server can manage multiple resource servers; equally the resource and authorization server could be the same server instance.

The client app or service must be registered with the authorization server. As part of this process, the client registers a redirect URL, which is the endpoint that will process authorization tokens. Registration also provides the client with an ID and a secret. The ID can be publicly exposed, but the secret must be kept confidential between the client and the authorization server. When the client application requests authorization, the user approves the authorization server to grant the request using an appropriate method. OAuth supports several grant types—or flows—for use in different contexts, such as server to server or mobile app to server. Depending on the flow type, the client will end up with an access token validated by the authorization server. The client presents the access token to the resource server, which then accepts the request for the resource if the token is valid.

OAuth uses the JavaScript object notation ([[JSON]]) web token ([[JWT]]) format for claims data. JWTs can easily be passed as Base64-encoded strings in URLs and Hyper Text Transfer ProtocolTTPs]] headers and can be digitally signed for authentication and integrity.

### OpenID Connect (OIDC)

OAuth is explicitly designed to authorize claims and not to authenticate users. The implementation details for fields and attributes within tokens are not defined. There is no mechanism to validate that a user who initiated an authorization request is still logged on and present. The access token once granted has no authenticating information. Open ID Connect ([[OIDC]]) is an authentication protocol that can be implemented as special types of OAuth flows with precisely defined token fields.

Note that OpenID can also refer to an earlier protocol developed between 2005 and 2007. This implemented a similar framework and underpinned early "sign on with" functionality, but is now regarded as obsolete. OpenID uses XML-format messaging and supports only web applications and not mobile apps.
