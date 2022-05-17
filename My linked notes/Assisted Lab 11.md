# Assisted Lab 11: Managing Access Controls in Windows Server

## Scenario

In this activity, you will explore the use of different kinds of accounts for managing objects in Active Directory and the use of GPO to apply account policies.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   3.7 Given a scenario, implement identity and account management controls.


## Examine Administrator account properties

Implement some Microsoft best practices for securing administrative accounts and learn how not-such-best-practice can compromise organizational security. First, examine the properties of the current Administrator account.

1.  On the [DC1](https://labclient.labondemand.com/Instructions/cbbc5195-100c-4191-bbdc-b5cfcc621478?rc=10#) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/cbbc5195-100c-4191-bbdc-b5cfcc621478?rc=10#) and then sign in as 515support\Administrator using Pa//$//$w0rd as the password.
    
2.  Select the **Start** menu, right-click **Windows Powershell**, and then select **Run as Administrator**. Confirm the UAC prompt by selecting **Yes**
    
3.  Run the following command to display the Security ID (SID) and other information for the current user:
    
    ```
    whoami /user
    ```
    
    > User accounts are actually identified to the system by number, not by name. In Windows, this number is the Security Identifier (SID). In Linux, it is the User Identifier (UID).
    
4.  What are the final three digits of the administrator's SID?
    
    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    
    Administrator account information.![whoami output](https://labondemand.blob.core.windows.net/content/lab84045/Screen%20Shot%202020-11-07%20at%2012.11.37%20PM.png)
    
    > You can use the **/all** switch with **whoami** to display additional group and privilege information.
    
5.  Run the **get-aduser** cmdlet to display account information:
    
    ```
    get-aduser -identity administrator -properties *
    ```
    
6.  Which of the following is the DistinguishedName for the Administrator account? (You may have to scroll up in PowerShell to display this information)
    
    administrator
    
    administrator.corp.515support.com
    
    CN=Administrator,CN=Users,DC=corp,DC=515support,DC=com
    
    515support\Administrator
    
    administrator@corp.515support.com
    
    500
    
    root
    
    DistinguishedName value.![DistinguishedName](https://labondemand.blob.core.windows.net/content/lab84045/Screen%20Shot%202020-11-07%20at%2012.14.34%20PM.png)
    
7.  Minimize the **Administrator: Windows PowerShell** window.




## Manage user, group, and computer objects

Active Directory stores and manages objects that represent common entities, such as user accounts or computers. You will manage users, groups, and computer objects in this activity.

1.  In **Server Manager**, from the **Tools** menu, open the **Active Directory Users and Computers** console.
    
2.  Expand the **corp.515support.com** domain node.
    
3.  Right-click the **corp.515support.com** domain node, select **New**, and then select **Organizational Unit**. Name the new OU ITAdmins.
    
    > Microsoft differentiates between the terms _container_ and _organizational unit_. An OU can have a Group Policy Object linked to it, which results in it being easier and more flexible to manage. Containers cannot have linked GPOs and are not typically used for day-to-day AD administration. Observe the difference in the icons between the _Computers_ container and the _ComputersOU_ organizational unit.
    
4.  Confirm that the ITAdmins organizational unit account exists
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
    ITAdmins Organizational Unit
    
5.  Right-click the **ITAdmins** OU, select **New**, and select **User**. Create a new user named `IT_Consultant`.
    
    -   First name: Temp
        
    -   Last name: Contractor
        
    -   User login name: IT_Consultant
        
    -   Password: 
        
    
    Confirm that the IT_Consultant account exists.
    
    IT_Consultant![The IT_Consultant account](https://labondemand.blob.core.windows.net/content/lab84045/Screen%20Shot%202020-11-07%20at%2012.18.20%20PM.png)
    
6.  Create a global security group within the **ITAdmins** OU and name it DesktopSupport.
    
7.  Add the **IT_Consultant** account to the **DesktopSupport** group.
    
8.  From the **corp.515support.com** domain object, browse to the **ComputersOU** Organizational Unit, right-click it, select **New** and then create a new computer account named laptop01.
    
9.  Run the following PowerShell cmdlet to generate a report of all computer objects in the domain.
    
    ```
    get-adcomputer -filter * | out-file C:\computers.txt
    ```
    
10.  Confirm that the computers.txt file exists. in the C drive
    
    The get-adcomputer cmdlet.
    
    > You have created several types of Active Directory objects: users, groups, and computer accounts. You have also stored these objects in the appropriate Organizational Units so that Group Policy Object configurations can be easily applied to the correct OUs and impact the correct users and computers.
    
11.  Minimize the **Administrator: Windows PowerShell** window.


## Modify an existing GPO to match password requirements

Group Policy is a powerful tool enabling custom user and computer settings to be deployed to objects across Active Directory. Use the Group Policy Management console to examine the 515 Support Local Admin Policy.

1.  In **Server Manager**, select **Tools > Group Policy Management**.
    
2.  In the Group Policy Management console, expand **Forest > Domains > corp.515support.com** and select the **Default Domain Policy**.
    
    > The Default Domain Policy defines a single password policy for all members of the entire domain. Microsoft recommends that password management is the only use of the Default Domain Policy.
    
3.  Right-click the **Default Domain Policy**, and then select **Edit**.
    
4.  Browse to the **Password Policy** node by following this path: **Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies**.
    
5.  You have reviewed your company's written security policy regarding passwords. You must now configure the **Default Domain Policy** to match the following requirements. Double-click each **Policy** value to edit the settings.
    
    Setting
    
    Value
    
    Explanation
    
    Minimum Password Length
    
    14 characters
    
    All passwords must contain at least 14 characters
    
    Complexity Requirements
    
    Enabled
    
    Passwords must contain at least three of the following four characteristics: uppercase, lowercase, letters, numbers
    
    Maximum Password Age
    
    90 days
    
    Passwords must be changed every 90 days
    
    Minimum Password Age
    
    1 day
    
    Passwords can only be changed once daily
    
    Enforce Password History
    
    20
    
    Unique passwords that must be used before an old password may be repeated
    
    Enforce Reversible Encyrption
    
    Disabled
    
    Makes it possible to decrypt passwords (not recommended)
    
    Password policy.![Password policy](https://labondemand.blob.core.windows.net/content/lab84045/Screen%20Shot%202020-11-07%20at%2012.23.24%20PM.png)
    
6.  In the Administrator: Windows PowerShell window, run the following command to produce a report of the password policy settings to updating configuration documentation:
    
    ```
    gpresult /H C:\passwords-gpresults.html
    ```
    
7.  Confirm that the C:\passwords-gpresults.html file exists.
    
    The C:\passwords-gpresult.html file.
    
    > The Default Domain Policy (DDP) applies to ALL domain members, offering no flexibility to have different password polices for different kinds of users (stricter for high-privilege administrators but looser for non-privileged standard users, for instance). Fine grained password policies provide flexibility by enforcing different password requirements for specific users and groups. You will work with fine grained password policies in a later activity.
    



## Comprehensive questions

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following answers describes a key difference between Organizational Units and Containers in Active Directory?
    
    Containers can only hold default Active Directory objects.
    
    Organizational Units can only hold default Active Directory objects.
    
    Group Policy Objects (GPOs) can be linked to Containers, but not to Organizational Units.
    
    Group Policy Objects (GPOs) can be linked to Organizational Units, but not to Containers.
    
    Correct
    
2.  To which accounts do the Default Domain Policy password settings apply?
    
    Only members of the Built-in Computers Container.
    
    Only members of the Built-in Users Container.
    
    All domain members.
    
    Only domain members stored in the default containers.
    
    Correct