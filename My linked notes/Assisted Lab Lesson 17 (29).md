# Assisted Lab 29: Configuring Mitigation Controls

## Scenario

Across the organization, computer images include test and experimental software in the folder C:\LABFILES. All users, including local administrators, should be prevented from installing or running this software on hosts within a given OU by configuring an AppLocker policy.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objective:

-   4.4 Given an incident, apply mitigation techniques or controls to secure an environment.



## Organize Active Directory resources for Group Policy

Review the 515 Support security policy entry regarding software execution, and then create an Organizational Unit and populate it with computer accounts. Group Policy Objects (GPOs) can only be linked to OUs, sites, and domains.

1.  Review the following security policy:
    
    -   _Developer servers will not have unapproved software installed. Along with other remediations, Group Policy AppLocker will be used to prohibit the execution of .exe files and Microsoft Installer files located in the C:\LABFILES folder._
    
    For this activity, assume that the developer server is MS1.
    
2.  On the [DC1](https://labclient.labondemand.com/Instructions/bd516187-272b-40bc-9f9a-b4f8e0175b58?rc=10#) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/bd516187-272b-40bc-9f9a-b4f8e0175b58?rc=10#), and then log on as 515support\Administrator, with the password Paw0rd.
    
3.  From Server Manager, select **Tools > Active Directory Users and Computers**.
    
4.  Directly under **corp.515support.com**, create a new OU for DevDept.
    
5.  Confirm that the DevDept organizational unit exists.
    
    Creating Group Policy Objects
	    To create a new OU, right-click the **corp.515support.com** domain, select **New**, and then select **Organizational Unit**.
    
6.  Select the **ComputersOU**, right-click the **MS1** computer account, and then move it to the **DevDept** OU.
    
    > You can right-click the MS1 computer object and select **Move**, or you can click and drag the object to the DevDept OU.
    



## Create a GPO to enforce the software installation policy

Create a Group Policy object to enforce the written security policy you reviewed previously. You will configure AppLocker and the required Application Identity service.

1.  From Server Manager, select **Tools > Group Policy Management**.
    
2.  Select the **corp.515support.com** domain object, right-click the **DevDept** OU, and select **Create a GPO in this domain, and Link it here**. Name the new GPO DevSettings.
    
3.  Select the **DevDept** OU to display the DevSettings GPO, and then right-click **DevSettings** and select **Edit**.
    
4.  Browse to the **Computer Configuration > Policies > Windows Settings > Security Settings > Application Control Policies > AppLocker** node.
    
5.  Expand **AppLocker**, select **Windows Installer Rules**. Right-click **Windows Installer Rules**, and then select **Create default rules**.
    
6.  Right-click the **Windows Installer Rules** again, and then select **Create New Rule**.
    
7.  Fill in the following values for the new AppLocker rule (select **Next** to navigate the screens and accept the defaults for any values not specified below):
    
    -   Action: Deny
        
    -   User or group: Everyone
        
    -   Conditions: Path
        
    -   Path: C:\LABFILES*
        
    -   Exceptions: none
        
    
    > AppLocker does not uninstall existing software. It blocks the execution of specified software.
    
8.  Select **Executable Rules**. Right-click **Executable Rules**, and then select **Create default rules**.
    
9.  Right-click the **Executable Rules** again, and then select **Create New Rule**.
    
10.  Fill in the following values for the new AppLocker rule:
    
    -   Action: Deny
        
    -   User or group: Everyone
        
    -   Path: C:\LABFILES*
        
    -   Exceptions: none
        
    
11.  Right-click the **AppLocker** node, select **Properties**, and then check the **Configured** boxes to enforce **Executable** and **Windows Installer** rules. Select **OK**.
    
12.  Browse to **System Services** node (also under _Security Settings_).
    
13.  Configure the **Application Identity** service to the **Automatic** startup mode.
    
    > The Application Identity service must be running for AppLocker policies to function.
    
14.  Close the Group Policy Management Editor.
    
15.  Right-click the **DevSettings** GPO, select **Save Report**, and the save it to Desktop.
    
    It will automatically save as an .htm file with the DevSettings name.
    
16.  Confirm that the DevSettings GPO report exists.
    
    Save the GPO reportEnsure the GPO was created correctly, and with the "DevSettings" name. Save the report again and ensure that it is located on the Desktop.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
17.  In Group Policy Management, right-click the **DevDept** OU and select **Link an Existing GPO**.
    
18.  Select **515 Support Local Admin Policy** and select **OK**.
    
19.  Select the **515 Support Local Admin Policy**. In the main pane, select the **Settings** tab. Select **Show all** and inspect the policy settings.
    
    This policy configures the domain-scope LocalAdmin security group as a member of the built-in administrators group (local machine scope) for each host that the policy applies to. The user account Bobby is a member of the LocalAdmin security group, so the effect of applying this policy to DevDept is to make Bobby a local administrator on MS1. Despite this privilege, Bobby should not be able to install or run software in C:\LABFILES.

  
Comprehensive questions

Does the AppLocker policy remove existing software?


No, it does not remove installed software.