# Assisted Lab 21: Implementing Endpoint Protection

## Scenario

In this activity, you will harden administrator accounts and workstations. First, you will create a fine-grained password policy that enforces stricter password setting than the Default Domain Policy. These settings will be applied to an IT-specific Global group. In the second task, you will use Group Policy to configure several security-oriented settings. The GPO created will be linked to an Organizational Unit in Active Directory where IT computer accounts reside.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   3.2 Given a scenario, implement host or application security solutions.

# Create a fine-grained password policy for IT staff accounts

The Default Domain Policy defines password requirements for all user accounts in the domain. Fine-grained password policies, however, assign particular password policies to individual user accounts or Active Directory Global Groups. You will use fine-grained passwords to define a more restrictive password policy for IT staff member user accounts.

1.  Sign on to the [DC1]
    
2.  From Server Manager, select **Tools > Active Directory Users and Computers**.
    
3.  Right-click the **Users** container and select **New > Group**. In the Group name box, type ITStaff then select **OK**.
    
4.  Select the **Users** node. **CTRL**+click to select the **Domain Admins** and **LocalAdmin** objects, then right-click and select **Add to a group**. Type ITStaff group then select **OK**. Select **OK**.
    
5.  Leave the Active Directory Users and Computers console open. From Server Manager, select **Tools > Active Directory Administrative Center**.
    
6.  In the left-hand pane, select **corp (local)**. In the main pane, select **System > Password Settings Container**.
    
    Password Settings Container.![Password settings container](https://labondemand.blob.core.windows.net/content/lab84053/Screen%20Shot%202020-11-08%20at%208.18.00%20AM.png)
    
7.  Review the following security policy summary for IT staff user account password management:
    
    -   All IT staff privileged accounts must contain a minimum of _20 characters_ and be _complex_.
        
    -   Passwords must be changed every _30 days_. Passwords may not be changed more than _once per day_ and the _24_ most recent passwords cannot be repeated.
        
    -   IT staff privileged accounts are subject to an _account lockout policy_, with a maximum of _three_ failed login attempts allowed. Accounts will be locked out for a duration of _20 minutes_. Reset failed attempts after _10 minutes_.
        
8.  Right-click some empty space and select **New > Password Settings**. Enter the name IT Account Policy and set a precedence level of 10 on the policy.
    
9.  Configure settings that meet the requirements listed in the organization's security policy:
    
    Here are the specific fine-grained password policy settings if you need help configuring the policy.
    
    ![ITStaff fine grained password policy](https://labondemand.blob.core.windows.net/content/lab84053/Screen%20Shot%202020-11-08%20at%208.21.35%20AM.png)
    
10.  Under Directly Applies To, select the **Add** button.
    
11.  Type ITStaff then select **OK**.
    
12.  Select **OK**.
    
13.  Does the IT Account Policy fine-grained password policy exist?
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
    The IT Account Policy.
    
14.  Close the Active Directory Administrative Center.

# Implement GPO settings

An organizational unit (OU) is created to store the computer accounts assigned to IT staff members. You will create a Group Policy Object (GPO) with specific settings designed to harden IT staff member workstations. First, you will create the appropriate Organizational Unit in Active Directory, and then you will configure the GPO.

1.  In the Active Directory Users and Computers console, right-click the **corp.515support.com** domain object, select **New**, and then create an OU for ITComputers.
    
2.  Close Active Directory Users and Computers.
    
3.  From Server Manager, select **Tools > Group Policy Management**.
    
4.  Browse to the **corp.515support.com** object, right-click the **ITComputers** OU, and select **Create a GPO in this domain, and Link it here**. Name the new GPO SecureAdminWorkstation.
    
    > Group Policy Objects can only be linked to Sites, Organizational Units, and the Domain.
    
    > Don’t forget to use exactly the same names as specified in the instructions.
    
5.  Expand the **ITComputers** OU, right-click the **SecureAdminWorkstation** OU, and then select **Edit**.
    
6.  Browse to **Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options**. Configure the following settings:
    
    -   Accounts: Guest account status: **Disabled**
    -   Accounts: Rename administrator account: Syd Jones
    -   Interactive logon: Do not display last user name: **Enabled**
    -   Interactive logon: Message text for users attempting to logon: Authorized use only
    -   Interactive logon: Message title for users attempting to logon: Warning!
    
    > There are several thousand different Group Policy settings available. This activity contains only a small number of possible security settings.
    
    Security settings![Security settings](https://labondemand.blob.core.windows.net/content/lab84053/Screen%20Shot%202020-11-08%20at%208.26.48%20AM.png)
    
7.  In the navigation pane of the Group Policy Management Editor window, expand **Computer Configuration > Policies > Administrative Templates > Windows Components > Windows Defender**.
    
8.  In the detail pane, open **Turn off Windows Defender**, read the help text in the Turn off Windows Defender window, then select **Disabled** and select **OK**.
    
    > In Group Policy, you often have to use the logic of double negatives. For example, you want to ensure that Windows Defender is always running, but there isn’t a policy to enable for that. So, you must disable turning Windows Defender off, which has the same overall effect.
    
9.  Within the same group of settings, set **Turn off routine remediation** to **Disabled**.
    
    Windows Defender settings.![Windows Defender settings](https://labondemand.blob.core.windows.net/content/lab84053/Screen%20Shot%202020-11-08%20at%208.30.56%20AM.png)
    
10.  Expand the **Real-time Protection** node within Windows Defender. Set **Turn off real-time protection** to **Disabled**.
    
11.  Close the Group Policy Management Editor.
    
    > Changes made in Group Policy Editor are saved immediately, but this can take up to two hours to roll out to all clients. Restarting the clients (sometimes twice in a row) is one simple way to force the issue.
    
12.  In the Group Policy Management console, right-click the **SecureAdminWorkstation** GPO and select **Save Report**. Save the report to the **desktop**.
    
    The report automatically saves in a .htm format.
    
13.  Confirm that the SecureAdminWorkstation report has been saved to the desktop.
    
    Group Policy report file.
    

47% Tasks Complete

PreviousNext: Comprehensive questions

  ## Comprehensive questions

1. True or false: the Default Domain Policy GPO defines password settings for all domain members.

True

  

2. Fine-grained password policies may be applied to what two Active Directory object types?

Global groups


User accounts

3.   Which of the following best defines a benefit of linking GPOs to OUs?

Linking a Group Policy Object to an Active Directory Organizational Unit allows administrators to tailor settings specifically for the users and computers stored in that OU