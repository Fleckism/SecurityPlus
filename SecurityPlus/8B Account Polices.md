---
tags: [GRC, implementation,section]
---
# EXAM OBJECTIVES COVERED
#addTagsIntoBody
3.7 Given a scenario, implement identity and account management controls

Account policies enforce the privilege management policy by setting what users can and cannot do. This helps you to enforce strong credential policies and to detect and manage risks from compromised accounts. Auditing and permission reviews can reveal suspicious behavior and attempts to break through security.

# ACCOUNT ATTRIBUTES AND ACCESS POLICIES

As well as authenticating the user, an account can be configured with attributes as a user profile. Account objects can also be used to assign permissions and access policies.

### Account Attributes

A user account is defined by a unique security identifier (SID), a name, and a credential. Each account is associated with a profile. The profile can be defined with custom identity attributes describing the user, such as a full name, email address, contact number, department, and so on. The profile may support media, such as an account picture.

As well as attributes, the **profile will usually provide a location for storing user-generated data files (a home folder)**. The profile can also store per-account settings for software applications. 

### Access Policies 

Each account can be assigned permissions over files and other network resources and access policies or privileges over the use and configuration of network hosts. These permissions might be assigned directly to the account or inherited through membership of a security group or role. **Access policies determine things like the right to log on to a computer locally or via remote desktop, install software, change the network configuration, and so on**.

On a Windows Active Directory network, access policies can be configured via group policy objects ([[GPOs]]). GPOs can be used to configure access rights for user/group/role accounts. GPOs can be linked to network administrative boundaries in Active Directory, such as sites, domains, and Organizational Units ([[OU]]). 

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4361-1599771800688.png)

Configuring access policies and rights using Group Policy Objects in Windows Server 2016. (Screenshot used with permission from Microsoft.)
# ACCOUNT PASSWORD POLICY SETTINGS 

System-enforced account policies can help to enforce credential management principles by stipulating requirements for user-selected passwords:

-   Password **length**—enforces a minimum length for passwords. There may also be a maximum length.
-   Password **complexity**—enforces password complexity rules (that is, no use of username within password and combination of at least eight upper/lower case alpha-numeric and non-alpha-numeric characters).
-   Password **aging**—forces the user to select a new password after a set number of days.
-   Password **reuse and history**—prevents the selection of a password that has been used already. The history attribute sets how many previous passwords are blocked.

In this context, you should note that the most recent guidance issued by NIST ([nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63b.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/NIST.SP.800-63b.pdf)) deprecates some of the "traditional" elements of password policy:

-   **Complexity rules should not be enforced.** The user should be allowed to choose a password (or other memorized secret) of between 8 and 64 ASCII or UNICODE characters, including spaces. The only restriction should be to block common passwords, such as dictionary words, repetitive strings (like 12345678), strings found in breach databases, and strings that repeat contextual information, such as username or company name.
-   **Aging policies should not be enforced.** Users should be able to select if and when a password should be changed, though the system should be able to force a password change if compromise is detected.
-   **Password hints should not be used. A password hint allows account recovery by submitting responses to personal information, such as first school or pet name.** 

The cartoon at [xkcd.com/936](https://xkcd.com/936) sums up the effect of policies on password entropy.

One approach to a password hint is to treat it as a secondary password and submit a random but memorable phrase, rather than an "honest" answer. The risk in allowing password hints is demonstrated by the data recovered in the Adobe data breach ([nakedsecurity.sophos.com/2013/11/04/anatomy-of-a-password-disaster-adobes-giant-sized-cryptographic-blunder](https://nakedsecurity.sophos.com/2013/11/04/anatomy-of-a-password-disaster-adobes-giant-sized-cryptographic-blunder/)).

**Password reuse can also mean using a work password elsewhere (on a website, for instance). This sort of behavior can only be policed by soft policies.**
# ACCOUNT RESTRICTIONS

To make the task of compromising the user security system harder, account restrictions can be used. 

### Location-Based Policies

A user or device can have a logical network location, identified by an IP address, subnet, virtual LAN (VLAN), or organizational unit ([[OU]]). This can be used as an account restriction mechanism. For example, a user account may be prevented from logging on locally to servers within a restricted OU.

The geographical location of a user or device can also be calculated using a geolocation mechanism. There are several types of geolocation:

-   **IP address**—these can be associated with a map location to varying degrees of accuracy based on information published by the registrant, including name, country, region, and city. The registrant is usually the Internet service provider (ISP), so the information you receive will provide an approximate location of a host based on the ISP. If the ISP is one that serves a large or diverse geographical area, you will be less likely to pinpoint the location of the host Internet service providers ([[ISPs]]). Software libraries, such as GeoIP ([maxmind.com/en/geoip-demo](https://www.maxmind.com/en/geoip-demo)), facilitate querying this data.
-   **Location Services**—these are methods used by the OS to calculate the device's geographical position. A device with a global positioning system (GPS) sensor can report a highly accurate location when outdoors. Location services can also triangulate to cell towers, Wi-Fi hotspots, and Bluetooth signals where GPS is not supported.

Geofencing refers to accepting or rejecting access requests based on location. Geofencing can also be used for push notification to send alerts or advice to a device when a user enters a specific area. Geotagging refers to the addition of location metadata to files or devices. This is often used for asset management to ensure devices are kept with the proper location. 

### Time-Based Restrictions

There are three main types of time-based policies:

-   A time of day policy establishes authorized logon hours for an account.
-   A time-based login policy establishes the maximum amount of time an account may be logged in for.
-   An **impossible travel time/risky login policy** tracks the location of login events over time. If these do not meet a threshold, the account will be disabled. For example, a user logs in to an account from a device in New York. A couple of hours later, a login attempt is made from LA, but this is refused and an alert raised because it is not feasible for the user to be in both locations.
# ACCOUNT AUDITS

Accounting and auditing processes are used to detect whether an account has been compromised or is being misused. A security or audit log can be used to facilitate detection of account misuse:

-   Accounting for all actions that have been performed by users. Change and version control systems depend on knowing when a file has been modified and by whom. Accounting also provides for non-repudiation (that is, a user cannot deny that they accessed or made a change to a file). The main problems are that auditing successful access attempts can quickly consume a lot of disk space, and analyzing the logs can be very time-consuming.
-   Detecting intrusions or attempted intrusions. Here records of failure-type events are likely to be more useful, though success-type events can also be revealing if they show unusual access patterns.

![Screenshot of Event Viewer with Security selected in left pane and Number of events and details in the right pane.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7380-1599771800762.png)

Recording an unsuccessful attempt to take ownership of an audited folder. (Screenshot used with permission from Microsoft.)

Account auditing also refers to more general change control. You need to take account of changes to resources and users. Resources may be updated, archived, or have their clearance level changed. Users may leave, arrive, or change jobs (roles). For example, if a user has moved to a new job, old privileges may need to be revoked and new ones granted. This process is referred to as recertification. Managing these sorts of changes efficiently and securely requires effective standard operating procedures (SOPs) and clear and timely communication between departments (between IT and HR, for instance).
# ACCOUNT PERMISSIONS

Where many users, groups, roles, and resources are involved, managing account permissions is complex and time-consuming. Improperly configured accounts can have two different types of impact. On the one hand, setting privileges that are too restrictive creates a large volume of support calls and reduces productivity. On the other hand, granting too many privileges to users weakens the security of the system and increases the risk of things like malware infection and data breach.

The phrase "authorization creep" refers to an employee who gains more and more access privileges the longer they remain with the organization.

A user may be granted elevated privileges temporarily (escalation). In this case, some system needs to be in place to ensure that the privileges are revoked at the end of the agreed period.

A system of auditing needs to be put in place so that privileges are reviewed regularly. Auditing would include monitoring group membership and reviewing access control lists for each resource plus identifying and disabling unnecessary accounts.

![Screenshot of Advanced Security Settings for LABFILES folder. The Effective Access tab is selected.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7460-1599771800962.png)

Determining effective permissions for a shared folder. (Screenshot used with permission from Microsoft.)
# USAGE AUDITS 

Usage auditing means configuring the security log to record key indicators and then reviewing the logs for suspicious activity. Determining what to log is one of the most considerable challenges a network administrator can face. For Active Directory, Microsoft has published audit policy recommendations for baseline requirements and networks with stronger security requirements ([docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/audit-policy-recommendations](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/audit-policy-recommendations)). Some typical categories include:

-   Account logon and management events.
-   Process creation.
-   Object access (file system/file shares).
-   Changes to audit policy.
-   Changes to system security and integrity (antivirus, host firewall, and so on).

![Screenshot of Auditing Entry for LABFILES folder.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2363-1599771801015.png)

Configuring audit entries for a folder in Windows. (Screenshot used with permission from Microsoft.)
# ACCOUNT LOCKOUT AND DISABLEMENT 

If account misuse is detected or suspected, the account can be manually disabled by setting an account property. This prevents the account from being used for login. Note that disabling the account does not close existing sessions. You can issue a remote logoff command to close a session. Account disablement means that login is permanently prevented until an administrator manually re-enables the account.

![Account properties dialog shown in front of Active Directory Users and Computers console with Account is disabled property checked](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2139-1599771801102.png)

Setting a property to disable an account. (Screenshot used with permission from Microsoft.)

An account lockout means that login is prevented for a period. This might be done manually if a policy violation is detected, but there are several scenarios for automatically applying a lockout:

-   An incorrect account password is entered repeatedly.
-   The account is set to expire. Setting an account expiration date means that an account cannot be used beyond a certain date. This option is useful on accounts for temporary and contract staff.
-   When using time- or location-based restrictions, the server periodically checks whether the user has the right to continue using the network. If the user does not have the right, then an automatic logout procedure commences.

![Screenshot of Group Policy Management Editor with Account Lockout Policy selected in left pane and lockout duration and threshold policies shown with default values in the right pane.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9474-1599771801220.png)

Configuring an account lockout policy. (Screenshot used with permission from Microsoft.)
