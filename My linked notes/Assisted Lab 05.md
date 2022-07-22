# Assisted Lab 05: Installing, Using, and Blocking a Malware-based Backdoor

## Scenario

In this activity, you will disable Windows Defender, leaving a server vulnerable. You will then simulate the accidental installation of malware and view the changes. You will take on the role of a pen tester or hacker, and determine whether the malware was installed based on open network ports. Next, you'll connect to the infected server, proving you having the ability to exploit it. Finally, in the role of security administrator, you will remove the malware.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   1.2 Given a scenario, analyze potential indicators to determine the type of attack.


05: Assisted Lab: Installing, Using, and Blocking a Malware-based Backdoor

45 Minutes Remaining

Instructions Resources Help  100%

## Disable Windows Defender

In the first part of this activity, you will disable Windows Defender protection, leaving the server vulnerable to malware.

1.  Select the MS1
    
2.  Select **Start**, and right-click **Windows PowerShell** and select **Run as Administrator**.
    
3.  When prompted, select **Yes** to confirm the UAC.
    
4.  Type the following command, then press **ENTER**:
    
    ```
    Set-MpPreference -DisableRealTimeMonitoring $True
    ```
    
    This PowerShell cmdlet disables Windows Defender online scanning.
    
5.  Close the PowerShell window.



## Install program from Odysseus.iso

Pretend that you are installing the program on the Odysseus.iso disc image, thinking that it is a legitimate piece of software. Insert the disc image and use its autoplay settings to start the installation.

1.  Select [ODYSSEUS](https://labclient.labondemand.com/Instructions/0a7acc95-84bf-4807-b110-b27114545418?rc=10#) to load the ISO image in the current VM.
    
2.  In the [MS1](https://labclient.labondemand.com/Instructions/0a7acc95-84bf-4807-b110-b27114545418?rc=10#) VM window, click the notification and then select **Run setup.exe** (it may take up to one minute for the notification to appear).
    
    > If you don't see the notification pop-up, right click on Start, Run and type **d:\setup.exe** then Enter.
    
    A User Account Control (UAC) warning is shown because a setup.exe process is trying to execute. The process' image file is unsigned (the publisher is listed as unknown).
    
3.  If necessary, select **Show more details**. Note that the install script is set to run in silent mode.
    
4.  You would not normally proceed, but for this activity, select **Yes**.
    
5.  The installer runs silently, with no visible window. When installation is complete, you will see two new icons on the desktop. Open either of the **SimpleHash** or **SimpleSalter** shortcuts from the desktop.
    
6.  Close the utility window.


## Identify system changes

The program seems to have installed two innocuous utilities, but what else might have changed on the computer? Use Task Manager to identify unauthorized system changes.

1.  Right-click the taskbar and select **Task Manager**. If necessary, select **More details** to view the full interface. Inspect the list of processes. Can you spot anything unusual?
    
2.  What process seems suspicious?
    
    ncat (32 bit)
    
    Microsoft OneDrive (32 bit)
    
    Spooler SubSystem App
    
    RDP Clipboard Monitor
    
    Correct
    
    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    
    Task Manager.![Task Manager and the ncat (32 bit) process](https://labondemand.blob.core.windows.net/content/lab84040/Screen%20Shot%202020-11-07%20at%209.41.24%20AM.png) Ncat is a well-known attack tool. When searching for suspicious processes, filter out known Windows porcesses (unless they are typospoofed) and investigate the exceptions. Note that the hMailServer process is a legitimate third-party application for this server role.
    
3.  Confirm that the malware has been installed by verifying that ncat.exe is running in the process list.
    
    Correct
    
    > You need a good understanding of what should be running or is authorized on your hosts and network to have a better chance of spotting what should not be there. The more authorized software and ports you allow, the harder the job of spotting the bad stuff becomes, especially when it comes to training new security staff. This is one of the reasons the principle of running only necessary services is so important.
    
4.  Close **Task Manager**.

## Identify network ports

The Odysseus software has installed a backdoor application called Netcat on the computer. This runs with the privileges of the logged-on user (currently Administrator) and allows a remote machine to access the command prompt on MS1. Use the DC1 VM to run a posture assessment and see if the backdoor can be discovered. To discover the port that the backdoor is listening on, you can use a network scanner called **Angry IP Scanner** ([angryip.org](http://angryip.org/)).

1.  Switch to the [DC1](https://labclient.labondemand.com/Instructions/0a7acc95-84bf-4807-b110-b27114545418?rc=10#) VM.
    
2.  Click [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/0a7acc95-84bf-4807-b110-b27114545418?rc=10#) to send the Ctrl+Alt+Delete sequence to the VM and show the login page. Sign in as 515support\Administrator using Pa$$w0rd as the password.
    
3.  From the desktop, open the **AngryIP** shortcut.
    
4.  In the IP Range: boxes type `10.1.0.2` (you will do this in both boxes) to target the **MS1** virtual machine.
    
5.  Select the **Preferences** icon to open the Preferences dialog box.
    
6.  Select the **Ports** tab and enter `1-1024,4400-4500` in the Port selection box. Select **OK**.
    
    Configuring AngryIP scanner![Configuring AngryIP scanner](https://labondemand.blob.core.windows.net/content/lab84040/Screen%20Shot%202020-11-07%20at%209.45.49%20AM.png)
    
7.  Select **Start** to begin the scan.
    
    The scan takes about one minute.
    
8.  When the scan is complete, select **Close**.
    
9.  Look at the open ports on the MS1 VM—how many of them can you identify?
    
10.  Which port is associated with the trojan?

    
    4450
    
    Well-known port numbersYou should recognize these well-known ports:
    
    > -   80—HTTP.
    > -   135, 139, 445—RPC/NetBIOS/SMB.
    > -   25, 143, 587—email (SMTP, IMAP, and SMTP).
    
    Do you see any port numbers that are not accounted for here and might therefore be suspicious?
    
11.  Close the **Angry IP Scanner** window.