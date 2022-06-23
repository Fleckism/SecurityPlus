# 1
Analyze the features of Microsoft's Information Rights Management (IRM) and choose the scenarios that accurately depict IRM. **(Select all that apply.)**

1.  File permissions are assigned based on the roles within a document.
2.  A document is emailed as an attachment, but cannot be printed by the receiver.
4.  An email message cannot be forwarded to another employee.

Solution

A benefit of IRM is that file permissions can be assigned for different document roles, such as author, editor, or reviewer. Each role can have specific access such as sending, printing, and editing.

Printing and forwarding of documents can be restricted even when the document is sent as a file attachment. This means that just because a document is forwarded it may not have printing capabilities.

Printing and forwarding of email messages can be restricted.

One disadvantage is that a document protected with IRM is not immune to screen captures. These captures can be done with a camera phone, third party software, or a workaround using an Apple system.
# 2
A document contains information about a company that is too valuable to permit any risks, and viewing is severely restricted. Analyze levels of classification and determine the appropriate classification for the document.

1.  Critical

Solution

Documents labeled as critical contain information that is too valuable to permit any risk of its capture, and viewing is severely restricted.

Documents labeled as confidential contain information that is highly sensitive and is for viewing only by approved persons within the organization or possibly by third parties under a Nondisclosure Agreement (NDA). This classification may also be called low.

Documents labeled as classified contains information that limits viewing by only persons within an organization or by third parties that are under an NDA. This classification may also be called private, restricted, internal use only, or official use only.

Unclassified documents are unrestricted and anyone can view the document. This document does not contain information that will harm the company if released. This classification is also known as public.
# 3
A company utilizing formal data governance assigns the role of data steward to an employee. Evaluate the roles within data governance and conclude which tasks the employee in this role performs.

2.  The employee ensures data is labeled and identified with appropriate metadata.


Solution

The data steward is primarily responsible for data quality. This involves tasks such as ensuring data is labeled and identified with appropriate metadata, and data is collected and stored in a format with values that comply with applicable laws and regulations.

A privacy officer is responsible for oversight of any Personally Identifiable Information (PII) assets managed by the company. This includes ensuring that the processing and disclosure of PII comply with legal and regulatory frameworks.

The data custodian is responsible for managing the system where data assets are stored. This includes responsibility for enforcing access control, encryption, and recovery measures.

The data owner is a senior role with ultimate responsibility for maintaining the confidentiality, integrity, and availability of the information asset. The owner is responsible for labeling the asset and ensuring it is protected with appropriate controls.
# 4
Data exists in several states, each requiring different security considerations. Evaluate the following items and select which data state presents the greatest risk due to decryption.

1.  Data in use

Solution

Data in use is when data is present in volatile memory. When a user works with data, that data needs to be decrypted, which puts it at risk.

Transmitting data over a network refers to data in transit. The encryption challenge is not as great as with data in use.

Data in motion is another name for data in transit.

When data is at rest, it is usually possible to encrypt the data using a variety of techniques, such as whole disk encryption, database encryption, and file- or folder-level encryption.
# 5
A new cloud-based application will replicate its data on a global scale, but will exclude residents of the European Union. Which concerns should the organization that provides the data to consumers take into consideration? **(Select all that apply.)**

2.  Sovereignty
3.  Location

Solution

Data sovereignty refers to a jurisdiction preventing or restricting processing and storage from taking place on systems that do not physically reside within that jurisdiction.

Storage locations might have to be carefully selected to mitigate data sovereignty issues. Most cloud providers allow a choice of data centers for processing and storage.

GDPR protections extend to any EU citizen while they are within EU or EEA (European Economic Area) borders.

There are important institutional governance roles for oversight and management of information assets within a data life cycle. These roles help to manage and maintain data.
# 6
A network manager assists with developing a policy to protect the company from data exfiltration. The employee devises a list of focus points to include. Which plans, when consolidated, provide the best protection for the company? **(Select all that apply.)**

2.  Creating a training program for all employees that reiterates the importance of knowing how to use encryption to secure data.
3.  Only allow removable media if it is company property, if it is required to perform a task, and if it has been cleared through the proper channels
4.  Encrypt all sensitive data at rest and disconnect systems that are storing archived data from the network

Solution

Employees need training in document confidentiality and how to use encryption to store and transmit data securely. Annual refresher training will remind employees of its importance.

One mechanism for data exfiltration is by copying data to removable media or other device storage, such as USB drives or memory cards. Limiting the use of these to company property and only for job-related tasks helps reduce this risk.

Always encrypt sensitive data at rest. Transferring data outside of the network will likely be useless without the decryption key.

Offsite backups are the most secure for data that may be targeted for destruction or ransom. The data will remain on site, but the backups are offsite and provide redundancy for the company in the event of destruction or ransom demands.
# 7
An employee is working on a project that contains critical data for the company. In order to meet deadlines, the employee decides to email the document containing the data to their personal email to work on at home. Consider the traits of Data Loss Prevention (DLP) and evaluate the scenario to select the DLP remediation the company should utilize.

2.  The user should be blocked from sending the email but retain access to it. The user is alerted to the policy violation, and it is logged as an incident.


Solution

The best solution for the company in this scenario is to block the email from sending the file to the personal email account. This action protects the data and notifies the user of the policy violation. It is likely that user training is needed so that the employee is aware of the policy and the reasons why the policy is in place.

If an alert only remediation is used for this scenario the data is in danger of being compromised. A personal email will not provide protection and will be vulnerable to attack. This action is not in the best interest of the company.

Quarantine will prohibit employees from accessing the file and will reduce work output. The policy violation was not malicious and the intent was not to harm the company.

The tombstone remediation technique is one step further from quarantine and is also not conducive to the workflow of the company. The block technique will still create the alert, notify administrators, and allow for retraining the employee without stopping workflow.
# 8
An organization suspects that a visitor is performing data exfiltration while on the premises. The organization knows that the visitor does not have physical access to any computer system. Which of the following methods does the organization suspect the visitor of using? **(Select all that apply.)**

1.  Phone
4.  Camera

Solution

Data exfiltration can happen by communicating information orally over a telephone, cell phone, or Voice over IP (VoIP) network. Cell phone text messaging is another possibility.

Copying the data to removable media or other devices with storage, such as USB drive, the memory card in a digital camera, or a smartphone is not possible as the visitor has no access to computer systems.

Using a network protocol, such as HTTP, FTP, SSH, email, or remote access is useful for data exfiltration. Remote access is not possible as the visitor has no access to computer systems.

A camera can capture images or video of data. This data may be computer data. Since the visitor has no access to computer systems, other targets may be paper documents, post-it notes on desks, building layouts, and more.
# 9
Choose which of the following items classify as Personally Identifiable Information. **(Select all that apply.)**

3.  Full name
4.  Date of birth

Solution

A full name can be used to identify, contact, or locate an individual. A full name is an identifier and can be used to search for a person to locate more PII that can be used to contact or locate a person.

A date of birth can be used to identify, contact, or locate an individual. This information is often used when verifying identity and may be used by an attacker to obtain unauthorized access into accounts and obtain other PII.

A job position is not considered PII. The position is not considered a person and is typically categorized as public information. Having the sole information of the name of a job position does not arm an attacker with the ability to identify, contact, or locate an individual.

Gender is not considered PII and is not unique to an individual. This information will not assist an attacker with contacting, identifying, or locating an individual.
# 10
Analyze and determine the role responsible for managing the system where data assets are stored, and is responsible for enforcing access control, encryption, and backup measures.

3.  Data custodian

Solution

A data custodian is responsible for managing the system where data assets are stored, including responsibility for enforcing access control, encryption, and backup or recovery measures.

A data owner has the ultimate responsibility for maintaining the confidentiality, integrity, and availability of the information asset.

The data steward is primarily responsible for data quality, such as ensuring data is labeled and identified with appropriate metadata.

The privacy officer is responsible for oversight of any Personally Identifiable Information (PII) assets managed by the company and ensures that the processing and disclosure of PII comply with the legal and regulatory frameworks.
