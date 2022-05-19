# 1
Denial of Service (DoS) is a network-based attack that consumes the network's bandwidth that could impact a directory service, but is more of a network concern than when managing a directory service.

Confidentiality of the information on the network (read access) is a concern. A user may be able to view a file, but not read it.

The integrity of the information on the network (write access) is also a concern. Only users who have write access are able to modify a file.

Non-repudiation means a subject cannot deny doing something, such as creating, modifying, or sending a resource. It is a consideration for managing privileges and authorization.
# 2
This company is using a Single Sign-On (SSO) policy. This means that a user only has to authenticate to a system once, to gain access to all the resources to which the system has granted rights to the user. An example is when a user authenticates with Windows, and also authenticates with the Windows domain's SQL Server, and Exchange Server services.

Least privilege means that the system grants rights necessary for users to perform their job and no more.

Implicit deny is the foundation of a system's access control. This means that unless there is a rule specifying that a system grants access to a user, the system will deny any access request.

The system generates an access key for a user when the user supplies authentication data. The system compares it with the server's security database, and both must match. The server security service generates the access key.
# 3
Group memberships of an authenticated user are on the access key and also contain the user's username. The system provides the access key upon authentication, and the user has access to all of the allowed resources based on the group membership.

A security database holds authentication data for users and compares this information with the supplied authentication data from the user. If the supplied data and the data within the security database match, then the system has authenticated the user, and the security database generates an access key.

An Access Control List (ACL) controls access to resources. The ACL contains entries for all usernames and groups that have permission to use the resource.

A directory is like a database, such as an object is like a record, and the attributes known about the object are like fields.
# 4
A password complexity requirement is a baseline account policy commonly enforced in a domain network. It requires the use of upper- and lower-case letters, numbers, and special characters for passwords to make password guessing difficult.

A lockout duration period is a common account policy enforced to prevent further attempts to use an account when entering a password fails three times, for example. An administrator can force an unlock when a support ticket is submitted.

A password history policy is commonly enforced in a domain network. It prevents reusing the same password up to 24 previously used passwords in a Windows domain.

Using a shared account, especially for administrative work, goes against security best practices. Use individual accounts for accountability.
# 5
The System account, not the Local Service account, creates the host processes that start Windows before the user logs on.

The Network Service account and the Local Service account have the same privileges as the standard user account. Standard users have limited privileges, typically with access to run programs, create, and modify files only belonging to their profile.

Any process created using the System account will have full privileges over the local computer. The System account has the most privileges of any Windows account.

The Local Service account can only access network resources as an anonymous user, unlike a Network Service account. Network Service accounts can present the computer's account credentials when accessing network resources.

# 6
The administrator is permission auditing, involving the regular review of privileges such as group membership, access control lists for each resource plus identifying, and disabling unnecessary accounts.

Recertification is a security control where admin audits user access privileges to ensure they are accurate and adhere to relevant standards and regulations. A resource or user change triggers recertification.

Logging is an automated process of capturing data to provide information on the use of the website, alerts of any unusual or suspicious behavior, and audit changes made to pages and settings.

Usage auditing means configuring the security log to record key indicators, then reviewing the logs for suspicious activity. This process does not involve reviewing user privileges.
# 7
Usage auditing refers to configuring the security log to record key indicators and then reviewing the logs for suspicious activity. Behavior recorded by event logs that differs from expected behavior may indicate everything from a minor security infraction to a major incident.

The systems administrator puts in place permission auditing to review privileges regularly. This includes monitoring group membership and access control lists for each resource plus identifying and disabling unnecessary accounts.

An information security audit measures how the organization's security policy is employed and determines how secure the network or site is that is being audited.

A compliance audit reviews a company's policies and procedures and determines if it is in compliance with regulatory guidelines.
# 8
If admin detects or suspects an account misuse, they can manually disable the account, preventing the account from being used for login. A remote logoff command can end a session in progress.

Smart cards or USB keys can store a user's certificate and private key, which can authenticate to different PCs and mobile devices. A stolen laptop and key represent a vulnerability.

An account enters a locked state because of a policy violation, such as entering an incorrect password. Lockouts usually occur for a limited duration.

A time of day policy establishes authorized logon hours for an account. Time- and location-based policies prevent users from logging in outside of authorized hours and locales.
# 9
An exit interview (or offboarding) is the process of ensuring that an employee leaves a company gracefully, and that company assets remain secure.

When an employee leaves, proper account management involves disabling the user’s account and privileges.

When IT disables an employee’s account, any information assets created or managed by the employee, but owned by the company, must still be accessible in terms of encryption keys or password-protected files.

Employee contracts might incorporate the terms of a nondisclosure agreement (NDA), or it could be a separate document. This is generally part of the onboarding process.
# 10
Traditional password complexity rules (that is, no use of username within password and combination of at least eight upper/lower case alpha-numeric and non-alpha-numeric characters) often result in users writing down passwords. NIST recommends only blocking common passwords, such as dictionary words, repetitive strings (like 12345678), and contextual information.

NIST recommends allowing users to choose a password (or other memorized secret) of between 8 and 64 ASCII or Unicode characters, including spaces.

IT should not centrally store plaintext passwords. IT administrators do not need to know users’ plaintext passwords.

Users should avoid using dictionary words, strings found in breach databases, and strings that repeat contextual information, such as username or company name.
# 11
Federation means the company trusts the accounts created and managed by a different network. The networks establish trust relationships, so the identity of a user (principal) from network A (identity provider), can be trusted as authentic by network B (service provider).

SSO (Single-Sign On) means a user authenticates to a system once, to access the resources the system has granted rights to use. This is not an example of a trust relationship.

Permission is a security setting, not a trust relationship. It controls access to objects, including file system items and network resources.

Access control is the process of determining and assigning privileges to resources, objects, and data. It does not involve a trust relationship.
# 12
Discretionary Access Control (DAC) is not rule-based. DAC stresses the importance of the owner, who has full control over resources and can modify the Access Control List to grant rights to others.

Role-Based Access Control (RBAC) considers a user’s organizational role, such as the rule the systems use to assign rights, rather than being directly assigned the rights.

Mandatory Access Control (MAC) uses a security clearance level as the rule to determine a user’s rights

Attribute-Based Access Control (ABAC) uses a combination of subject and object attributes, along with any context-sensitive or system-wide attributes, as the rule administrators apply when assigning rights. These could include group/role memberships, information about the current OS, the IP address, or the presence of up-to-date patches, and anti-malware.
# 13
Security Assertion Markup Language (SAML) is an identity federation format used to exchange authentication information between the principal, the service provider, and the identity provider.

Authentication and authorization for a RESTful API is often implemented using the Open Authorization (OAuth) protocol.

OpenID is an identity federation method enabling users authentication on cooperating websites by a third-party authentication service.

Lightweight Directory Access Protocol (LDAP) is not an identity federation. It is a network protocol used to access network directory databases storing information about authorized users and their privileges, as well as other organizational information.
# 14
A distinguished name is a unique identifier for any given resource within an X.500-like directory and made up of attribute=value pairs, separated by commas. The most specific attribute lists first, and then successive attributes become progressively broader.

Also referred to as the relative distinguished name, the most specific attribute (in this case, system1) uniquely identifies the object within the context of successive attribute values.

The directory schema describes the types of attributes, what information they contain, and the way attributes define object types. Some of the attributes commonly used include Common Name (CN), Organizational Unit (OU), Organization (O), Country (C), and Domain Component (DC).

In this scenario, CN=system1 is the Common Name, CN=User is the broader common name, OU=Univ is the Organizational Unit, and DC=local is the Domain Component. This goes in order of a specific system to the broadest Domain Component.
# 15
Organizational Units (OUs) represent administrative boundaries. They allow the enterprise administrator to delegate administrative responsibility for users and resources in different locations or departments. An OU grouped by location will be sufficient if different IT departments are responsible for services in different geographic locations. An OU grouped by department is more applicable if different IT departments are responsible for supporting different business functions.

Within each root-level parent OU, use separate child OUs for different types of objects such as servers, client systems, users and groups. Be consistent.

Do not create too many root-level containers or nest containers too deeply. They should not be more than five levels.

Separate administrative user and group accounts from standard ones.
# 16
The data owner is responsible for data guardianship and training, for this role will focus on compliance issues and data classification systems.

The system owner is responsible for designing and planning computers, networks, and database systems. The role requires expert knowledge of Information Technology (IT) security and network design.

The system administrator is responsible for the day-to-day system admin role and requires a technical understanding of access controls and privilege management systems.

Privileged users are employees with access to privileged data and require extra training on data management and Personally Identifiable Information (PII) plus any relevant regulatory or compliance frameworks.
# 17
Unless the phishing email is part of a penetration test, other members of the IT team likely know a member of their team is sending a simulated phishing email.

A bug bounty is a program operated by a software vendor or website operator where individuals receive rewards for reporting vulnerabilities. While contractors may perform pen tests on a contractual basis, a bug bounty program is a way of crowd sourcing vulnerability detection.

A phishing campaign training event means sending simulated phishing messages to users. This allows IT to target those users who respond to the messages for follow-up training.

Untrained users represent a serious vulnerability because they are susceptible to social engineering and malware attacks, such as phishing attempts.
# 18
An AUP governs employees' use of company equipment and Internet services. AUPs protect an organization from the security and legal implications of employees misusing its equipment.

A code of conduct outlines professional behavior based on ethical standards, such as honesty and fairness.

Some professions may have developed codes of ethics to cover difficult situations; some businesses may also have a code of ethics to communicate the values it expects its employees to practice.
# 19
Capture the Flag (CTF) is usually used in ethical hacker training programs and gamified competitions. Participants complete a series of challenges within a virtualized computing environment to discover a flag that represents a vulnerability or attack to overcome.

Computer-based training (CBT) allows a student to acquire skills and experience by completing practical simulations or branching choice scenarios. CBT might use video game elements to improve engagement.

If the penetration test were a purple team exercise then it would be considered scenario based learning, but because it was part of a mandatory requirement it would not be considered.

Staff training should focus on user roles, which require different levels of security training, education, or awareness.
# 20
A clean desk policy means that each employee's work area should be free from any documents left there. The policy aims to prevent sensitive information from being obtained by unauthorized staff or guests at the workplace.

A clean desk policy pertains to a user’s physical workspace, rather than a virtual workspace, such as a web browser.

The purpose of a clean desk policy is to reduce the chances of compromising sensitive information.

Some companies may try to prevent staff from bringing personal devices on site, because such devices represent a data exfiltration risk. When connected to an enterprise system, personal electronic devices pose security complications.
# 21
In DAC, the owner has full control over the resource, meaning that he or she can modify its ACL to grant rights to others. DAC is the most flexible and weakest control model.

With DAC, decision-making lies with the resource owner. In rule-based access control (RBAC) and mandatory access control (MAC), it lies with the system owner (that is, the controls are enforced system-wide and cannot be countermanded or accepted by users "within" the system).

DAC is the easiest model to compromise, as it is vulnerable to insider threats and abuse of compromised accounts.

Attribute-based access control (ABAC) is a fine-grained, strong access control mechanism, making access decisions based on a combination of subject, object, and context-sensitive or system-wide attributes.