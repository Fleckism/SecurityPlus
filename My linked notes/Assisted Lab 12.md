# Assisted Lab 12: Configuring a System for Auditing Policies

## Scenario

In this activity, you will display processes running on the server, confirm applied Group Policy Objects, and then use Group Policy Objects to configure auditing.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   3.7 Given a scenario, implement identity and account management controls.


## Browse running processes

There are many ways of viewing security-oriented information on the system. One aspect of malicious software mitigation is process management. Use the Sysinternals Process Explorer tool ([docs.microsoft.com](https://docs.microsoft.com/en-us/sysinternals)) to view which accounts are running processes.

1.  On the [DC1](https://labclient.labondemand.com/Instructions/10c81be6-b086-4386-973a-9fb9e7936295?rc=10#) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/10c81be6-b086-4386-973a-9fb9e7936295?rc=10#) and sign in as 515support\Administrator with the password 
    
2.  Open File Explorer and browse to C:\LABFILES\Sysinternals.
    
3.  Right-click **procexp64.exe** and select **Run as administrator**. Select **Yes** at the UAC prompt.
    
    In the output, you can see the hierarchy of processes and the various containers for user-mode processes. Kernel processes and critical services are run by SYSTEM whereas less-privileged services are run by either the LOCAL SERVICE or NETWORK SERVICE accounts. User-initiated processes and services are run by the named account (515support\Administrator in the example).
    
    Process Explorer![Process Explorer tool](https://labondemand.blob.core.windows.net/content/lab84046/Screen%20Shot%202020-11-07%20at%203.14.03%20PM.png)
    
    > Try to spend time observing Process Explorer on different Windows systems with different applications and servers running. Understanding what should be running is critical to identifying what shouldn't.
    
4.  Close the Process Explorer window. Minimize the File Explorer window.
    
    One of the key points to understand is that any malware that gets executed on this machine will run with at least the privileges of the logged-on user, and as the current user is a domain administrator, that's quite a lot of privileges.
    
5.  From the **Start** menu, right-click **Windows PowerShell**, and then select **Run as Administrator**. Select **Yes** to confirm the UAC prompt.
    
6.  Enter the following command to generate similar information:
    
    ```
    tasklist
    ```
    
    As most systems run a large number of processes, it is common to run tasklist with filters.
    
7.  Run the tasklist command again, and this time filter for running services. Redirect the output of the command to a text file named C:\services-running.txt.
    
    ```
    tasklist /SVC /FI "STATUS eq RUNNING" > C:\services-running.txt
    ```
    
8.  Does the C:\services-running.txt file exist?
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
    The services-running.txt file.
    
    ![SThe services-running.txt file](https://labondemand.blob.core.windows.net/content/lab84046/Screen%20Shot%202020-11-07%20at%203.15.58%20PM%20copy.png)
    
9.  Minimize the PowerShell window.



## Auditing effective permissions

In this activity, you will use the existing user account **Bobby** to configure and audit NTFS permissions.

1.  In Server Manager, select **Tools**, and then select **Active Directory Users and Computers**.
    
2.  Select the **Users** container, right-click the **Bobby** account, and select **Add to a group**.
    
3.  Enter Sales and then select **Check Names**.
    
4.  Select **OK** to confirm both dialog boxes.
    
5.  Confirm that the Bobby user account is a member of the Sales group.
    
    ![Add Bobby to Sales](https://labondemand.blob.core.windows.net/content/lab84046/Screen%20Shot%202020-11-07%20at%203.18.58%20PM.png)
    
6.  Minimize **Active Directory Users and Computers** open.
    
7.  In File Explorer, right-click C:\ and create a folder named data1.
    
8.  Select the data1 folder. Right-click within the folder and select **New > Text Document**. Enter the name fileA and press **ENTER**.
    
9.  Right-click the **C:\data1** folder, and then select **Properties**.
    
10.  Select the **Security** tab to configure NTFS permissions.
    
11.  On the Security tab, select the **Edit** button. In the Permissions for data1 dialog box, select the **Add** button.
    
12.  Type Sales, and then select the **Check Names** button. Select **OK**.
    
    Grant permissions to the Sales group.![Grant permissions to the Sales group](https://labondemand.blob.core.windows.net/content/lab84046/Screen%20Shot%202020-11-07%20at%203.22.02%20PM.png)
    
13.  With the **Sales** group highlighted in the Permissions for data1 dialog box, select the **Modify** check box in the Allow column. Select **OK** to confirm each dialog box.
    
14.  In C:\data1, right-click **fileA.txt**, and then select **Properties**.
    
15.  On the **Security** tab, observe that the **Sales** group is listed.
    
16.  Does the Sales group have the Modify permission to fileA.txt?
    
    Yes
    
    No
    
17.  What causes the permissions to be configured this way on fileA.txt?
    
    The permissions of the parent object C:\data1 were automatically inherited by the fileA child object.
    
    You manually configured the Sales group to have the Modify permissions on fileA.
    
    These settings are the normal Windows default permissions for new files.
    
    Group Policy has configured the permissions this way.
    
    Permissions
    
18.  Select **Cancel** to close the fileA.txt Properties box.
    
19.  In File Explorer, right-click the **C:\data1** folder, select **Properties**, select the **Security** tab, and then select the **Advanced** button.
    
20.  Select the **Effective Access** tab.
    
21.  In the **Select a user** interface, enter Bobby, select **Check Names**, and then select **OK**.
    
22.  Select **View effective access** and note the permissions.
    
23.  Assuming this group membership, does Bobby have Full Control access?
    
    Yes
    
    No
    
    Impossible to determine
    
24.  In the interface, at **Include group membership**, select **Add items**.
    
25.  Enter Administrators, select **Check Names**, and then select **OK**.
    
26.  Select **View effective access** again.
    
    You are simulating the effective permissions on C:\data1 if Bobby were a member of the **Administrators** group.
    
27.  Assuming this group membership, does Bobby have Full Control access?
    
    Yes
    
    No
    
    Impossible to determine
    
28.  Select **Cancel** to exit each dialog box. Close File Explorer.
    
29.  Run the following PowerShell cmdlet to display permissions information for **fileA.txt**:
    
    ```
    get-acl C:\data1\fileA.txt | format-list | out-file C:\permissions.txt
    ```
    
30.  Confirm that the C:\permissions.txt file exists.
    
31.  Minimize the PowerShell window.


## Create file system audit policy

Create a GPO to enforce a file system audit policy.

1.  In Server Manager, select **Tools**, and then select the **Group Policy Management** console.
    
2.  In the Group Policy Management console, select the **Domain Controllers** organizational unit. Right-click it and select **Create a GPO in this domain, and Link it here**.
    
3.  In the Name box, enter Audit Policy and select **OK**.
    #searchForTheBelowSymbols
    > We need to attach the policy to the Domain Controllers OU because this VM is the DC. You would attach the policy to a different OU to configure audit settings for other types of computer object.
    
4.  Right-click **Audit Policy** and select **Edit**.
    
5.  In the Group Policy Management Editor console, expand **Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options**.
    
6.  Select **Audit: Force audit policy subcategory settings**. Check the **Define this policy setting** check box and select the **Enabled** option button. Select **OK**.
    
7.  In the Group Policy Management Editor console, expand **Computer Configuration > Policies > Windows Settings > Security Settings > Advanced Audit Policy Configuration > Audit Policies > Object Access**.
    
8.  Double-click **Audit File System**. Check the **Configure the following audit events** check box, and then check the boxes for both **Success** and **Failure**.
    
9.  Select **OK** to close the interface.
    
    > As you can see, there is a huge number of potentially auditable events. Tuning the audit policy effectively is a critical security administration challenge.
    
10.  In the elevated PowerShell console, run the following command to immediately apply the new GPO to the Domain Controllers Organizational Unit:
    
    ```
    gpupdate /force
    ```
    
11.  Leave the PowerShell window open.


## GPO reporting

Use the gpresult command to generate a file containing the Group Policy settings that are applied to DC1.

1.  Run the following command to create an HTML file containing the applied Group Policy settings:
    
    ```
    gpresult /H C:\audit.html
    ```
    
2.  Confirm that the Audit Policy has been configured
    
    The gpresult command
    
3.  Close the Group Policy Management Editor window.


## Displaying audit policy results by using Event Viewer

You will generate log file entries based on the auditing policy, and then confirm the entries are displayed in Event Viewer.

1.  In File Explorer, right-click the **C:\data1** folder and select **Properties**.
    
2.  In the data1 Properties dialog box, select the **Security** tab, and then select the **Advanced** button.
    
3.  On the **Auditing** tab, select **Continue**, and then select **Add**.
    
4.  Select the **Select a principal** link, and then in the dialog box, type Authenticated Users and select **OK**.
    
5.  Set the **Type** of audit at **All** from the pull-down menu.
    
6.  Select all six available check boxes under **Basic permissions**.
    
7.  Select **OK** to confirm each dialog box.
    
    > Access to file system objects will be recorded in the Security log of Event Viewer.
    
8.  Open **C:\data1\fileA.txt**, add today's date to the file, and then save and close it.
    
9.  From Server Manager, select **Tools**, and then select **Event Viewer**.
    
10.  Expand the **Windows Logs** node, and then select the **Security** log.
    
11.  Select the event at the top of the list.
    
    The event should read "An attempt was made to access an object."
    
12.  Confirm that the file access audit log entry exists for event ID 4663.
    
13.  Was the event logged as a success or a failure?
    
    Success
    
    Failure
    
    Undetermined


## Comprehensive questions

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following best describes a reason to audit or display running processes on the server?
    
    To check for high resource utilization, which could indicate a security, performance, or reliability issue.
    
    To ensure users are running work-related processes and not games.
    
    To discover who is logged on to the system.
    
    To make sure the system is up to date.
    
    Correct
    
2.  Which of the following best describes why it is useful to audit effective permissions?
    
    To view a history of the user's access to the resource.
    
    To see what effect placing a user in a different group will have on their access to the resource.
    
    To display the user's Share permissions on the file.
    
    So that users can verify their permissions are set correctly.
    
    Correct
    
3.  Which of the following best describes why auditing for failed access attempts to folders and files is a good security practice?
    
    To see which users are trying to access resources, indicating either a permissions misconfiguration or unauthorized users.
    
    To see which processes users are attempting to run on the server.
    
    To see which users are accessing folders on a daily basis.
    
    To see which users are viewing the folder and file contents.
    
    Correct