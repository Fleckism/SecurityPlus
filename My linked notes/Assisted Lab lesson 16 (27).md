# APPLIED LAB 27: Identifying Application Attacks

## Scenario

In this activity, you will intercept and alter a URL that manages an email password function. Next, you will create a performance baseline, and then stress the server to simulate the effect of an application attack that consumes resources. Finally, you will implement a domain-wide Windows PowerShell policy to enforce code signing for scripts.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   1.3 Given a scenario, analyze potential indicators associated with application attacks.
    
-   3.2 Given a scenario, implement host or application security solutions.

## Configure interception proxy and test URL interception vulnerability

In this task, you will intercept a mock email password reset attempt. The URL is configured to forward the reset option to the user's alternate email address. You will replace that alternate email address with a different one.

To configure the browser to use Burp Suite as an interception proxy, complete the following steps.

1.  Select the [PT1-Kali](https://labclient.labondemand.com/Instructions/3348a9ec-492b-4353-9fa1-134e3fd7ea0c?rc=10#) VM. Log on with the credentials root and Pa$$w0rd
    
2.  In **Firefox** open the configuration page about:preferences#advanced. At the bottom of the page, select **Settings**. Set the following proxy values:
    
    -   HTTP Proxy: 127.0.0.1
        
    -   Port: 8080
        
    -   Check **Use this proxy server for all protocols**
        
3.  Start **Burp Suite** from the desktop. Accept the default settings in the startup wizard.
    
4.  Try to arrange the Firefox and Burp Suite windows so that you can use them both together easily.
    
5.  Type the following URL into Firefox:
    
    ```nocopy-nocolor
    http://pwd-reset.515web.net/resetpassword.php?username=jansmith&altemail=jsmith%40email.foo
    ```
    
    The URL simulates a reset request to be sent to jsmith@email.foo for jansmith@515web.net.
    
6.  Switch to **Burp Suite**, select the **Proxy** tab, select the **HTTP history** tab.
    
    The GET record corresponds to the email reset attempt.
    
    > You are given detailed instructions for this task because the focus is on the attack method, rather than the specific tool options.
    
7.  Right-click the **GET** record and then select **Send to Repeater**.
    
8.  Select the **Repeater** tab. In the Request panel, select the **Params** tab.
    
9.  In the **altemail** _Value_ field, replace the existing address with maluser%40evil.foo and then press **ENTER**.
    
10.  Right-click the **altemail** line and select **Request in browser > In original session**. Select the **Copy** button.
    
11.  Switch to Firefox and paste the copied URL into the address bar. Press **ENTER**.
    
    The page will fail to load. The goal was to simulate a password reset that could be intercepted.
    
12.  Return to **Burp**, select **Proxy**, and then select **HTTP history**.
    
13.  Display the second host connection, select the **Params** tab, and use the information to answer the following question.
    
14.  What email address is the password reset attempt now being sent to?
    
    maluser@evil.foo
    
    jsmith@515web.net
    
    jsmith@email.foo
    
    maluser@515web.net
    
    > The purpose behind Applied Labs is to prove your ability to configure given settings and display knowledge of concepts, tools, and options. If you get a scored question incorrect, you may not repeat the question or change your answer. You do not need a correct answer to move forward through the lab.
    
15.  In the **Params** window, right-click the line containing the Name **altemail** and the corresponding value. Select **Save item**. Save the entry with the value to the Desktop as a file named altemail.
    
16.  Confirm that the altemail file exists.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
    Altemail fileEnsure that the /root/Desktop/altemail file exists. Recall that you must name the file exactly as specified and to the specified location. Save the script file a second time, if necessary.
    
17.  Which of the following answers best describes the tasks you accomplished in this section?
    
    
    Intercepted and altered a URL so that the password reset information was sent elsewhere.

## Establish a performance baseline and stress test the server

Create a Performance Monitor baseline and then test a server to see the effect of application attacks.

1.  On the [DC1](https://labclient.labondemand.com/Instructions/3348a9ec-492b-4353-9fa1-134e3fd7ea0c?rc=10#) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/3348a9ec-492b-4353-9fa1-134e3fd7ea0c?rc=10#), and then sign on as 515support\Administrator using Pa$$w0rd as the password.
    
2.  Open **Task Manager** and on the **Performance** tab, select the **CPU** pane. Leave Task Manager open. You will use it in later tasks.
    
3.  Open **Performance Monitor** (server manager). Create a new user defined data collector set. Configure the new data collector set with the following settings:
    
    -   Name: CPU baseline
        
    -   Select **Create manually (advanced)**
        
    -   Select **Performance counter**
        
    -   Add the following performance counters from the **Processor** group:
        
        -   % Processor Time
        -   % User Time
        -   Interrupts/sec
4.  Start the **CPU baseline** data collector set.
    
    You will use CPU Stress to place a false load on the VM's processors. You'll use Task Manager and Performance Monitor to monitor the workload. The extreme workload demonstrates the possible effect of an application layer [[attack]].
    
    You will leave the Data Collector Set running through the next several tasks. It gathers information as you accomplish activity steps.
    
5.  From the C:\LABFILES\Sysinternals folder, open **CPUSTRES64**. If prompted, select **Yes** to accept license agreement.
    
6.  Resize and reposition the **Task Manager** and **CPU Stress** windows.
    
    The goal is to view the effect of starting CPU Stress in Task Manager.
    
7.  In the **CPU Stress** console, create one new thread.
    
    There should now be five threads created. Four were created by default, and you created the fifth.
    
8.  Set all five threads at **Activity Level > Medium (50%)**, and then **Activate** the threads.
    
    > The system will become very slow!
    
9.  In Task Manager, note that CPU Utilization should now be nearly 100%.
    
    The _CPU baseline_ data collector set in Performance Monitor is logging the CPU workload.
    
10.  **Deactivate** all five threads to end the false workload. You can select several or all of the threads by holding down the **SHIFT** or **CTRL** keys.
    
11.  In Task Manaager, CPU utlization should be well below 100%.
    
12.  Switch to **Performance Monitor**, right-click the **CPU baseline** data collector set, and select **Stop**.
    
13.  View the **CPU baseline** report.
    
    After viewing the information, you may close the report.
    
14.  Which of the following answers best describes why a performance baseline is essential to security?
    
    Performance baselines alert administrators to malware and viruses.
    
    Without a baseline of normal server activity, it is difficult to know when the server deviates from normal.
    
    Performance baselines prevent the server from operating below an established work level.
    
    Performance baselines prevent server performance issues due to security breaches.
    
15.  Close **File Explorer**, **Performance Monitor**, **CPUSTRES64**, and the **CPU baseline** report file.
    
16.  Confirm that the CPU baseline Data Collector Set exists.

## PowerShell Security

Implement a Group Policy Object to manage Windows PowerShell code signing requirements for all servers and workstations in the corp.515support.com domain.

1.  If necessary, switch to the [DC1](https://labclient.labondemand.com/Instructions/3348a9ec-492b-4353-9fa1-134e3fd7ea0c?rc=10#) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/3348a9ec-492b-4353-9fa1-134e3fd7ea0c?rc=10#), and then sign on as 515support\Administrator using Pa$$w0rd as the password.
    
2.  Use the **Group Policy Management** console to create a new GPO named PowerShell Security GPO to manage the PowerShell Execution Policy. The new GPO should be linked to the **corp.515support.com** domain.
    
    > Don’t forget to use exactly the same names as specified in the instructions.
    
3.  Edit the policy settings at **Computer Configuration > Policies > Administrative Templates > Windows Components > Windows PowerShell**
    
    -   Turn on PowerShell Script Block Logging setting: **Enabled**
        
    -   Turn on Script Execution setting: **Enabled**
        
    -   Set the Execution Policy to **Allow only signed scripts**
        
4.  Close the Group Policy Editor console.
    
5.  In the Group Policy Management console, right-click the **PowerShell Security GPO**, and then select **Save Report**. Save the report to the Desktop.
    
    The file is automatically named **PowerShell Security GPO**.
    
6.  Confirm that the PowerShell Security GPO exists.
    
7.  Right-click the **Start** menu and select **Run**. Enter the following command and select **OK**:
    
    ```
    gpupdate /force
    ```
    
8.  Open PowerShell and run the following cmdlet to display the current execution control policy on the system:
    
    ```
    Get-Executionpolicy
    ```
    
9.  What is the Execution Policy with the new GPO in effect?

Comprehensive questions:
1. Which of the following answers best describes why URLs are vulnerable to interception and alteration?  URLs are not encrypted
2. Which of the following answers best describes how a performance baseline helps to maintain the security of a server?
	1.  Degraded performance is a possible result of a security breach, and the performance baseline indicates the server's normal performance level.
3. Which of the following answers best describes why digitally-signed Windows PowerShell scripts help to mitigate security threats?
	1. Digitally-signed scripts help ensure the script comes from a trusted source.