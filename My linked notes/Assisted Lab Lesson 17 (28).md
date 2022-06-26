# Assisted Lab 28: Managing Data Sources for Incident Response

## Scenario

As part of 515 Support's incident response planning, centralized log files are being implemented on the various services and appliances on the network. You have been tasked with establishing a central storage location for log files on the LX1 CentOS Linux server. Next, you will configure the Kali and VyOS devices to forward their log files to this central server. Such centralization will make searching for and responding to incidents more efficient. It will also aid in log file archiving. You have also been asked to confirm the location of dump files for the Linux and Windows servers. Finally, you will configure a basic remote monitoring solution for the DC1 virtual machine by using the MS1 server.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objective:

-   4.3 Given an incident, utilize appropriate data sources to support an investigation.



## Configure a server for centalized log files

Configure the LX1 virtual machine as central rsyslog log file storage server.

1.  Log on to the [LX1](https://labclient.labondemand.com/Instructions/bd6fb4c2-3f08-48c8-8ab3-469206d3200e?rc=10#) Linux VM with the CentOS with a password of Pa$$w0rd.
    
    > The CentOS account is a non-privileged account. In the real world you could use sudo to run root level commands. You can also use the su - root option, as you will in this activity.
    
2.  Select **Applications > Favorites > Terminal** to open a Terminal window.
    
    > You may find it beneficial to maximize the Terminal window.
    
3.  Enter su - root to get root credentials. Enter Pa$$w0rd when prompted.
    
    > There is a space on each side of the dash character.
    
    > In the Linux vernacular, the phrase "get root" means to use su to gain root privileges.
    
4.  Use vim to open the /etc/rsyslog.conf configuration file.
    
    Vim quick reference  
      
      
    
      
      
    
    -     
        
    
5.  Uncomment the following two lines by selecting the **#** sign and pressing **x** in Vim's Command mode. These two lines enable the LX1 server's rsyslog service to accept inbound connections.
    
    ```nocopy
    $ModLoad imudp    
    $UDPServerRun 514    
    ```
    
    > Be sure to uncomment the lines in the _#Provides UDP syslog reception_ and not the lines for TCP.
    
    > The configuration is technically complete. However, all inbound log file entries from all remote servers would be combined into a single log file. Such a log file would be cumbersome to search. In the next section, you'll use a template to separate inbound log file entries by hostname.
    
6.  Use the **DOWN ARROW** key to navigate to the empty line just before  
    #### GLOBAL DIRECTIVES ####
    
7.  Enter the following text on three separate lines:
    
    ```bash-notab-nocopy
    $template DynamicFile,"/var/log/%HOSTNAME%.log"
    ```
    
    ```bash-notab-nocopy
    *.* ?DynamicFile
    ```
    
    ```bash-notab-nocopy
    & ~
    ```
    
    -   The line _$template DynamicFile,"/var/log/%HOSTNAME%.log"_ defines a template format named DynamicFile that creates a log named for the server's hostname. In this scenario, it will generate a log file named KALI.log that originates from the KALI Linux server.
    -   The line _*.* ?DynamicFile_ states that all Rsyslog facilities (services and applications) of all severities (alert levels) will be sent via the template.
    -   The line _& ~_ stops any process matching after this point.
    
    The /etc/rsyslog.conf file.![edits to /etc/rsyslog.conf](https://labondemand.blob.core.windows.net/content/lab84059/Screen%20Shot%202020-11-08%20at%2011.21.22%20AM.png)
    
8.  Press **ESC**, and then enter :wq to write your changes to the file and quit Vim.
    
9.  Confirm that the $template entry exists in /etc/rsyslog.conf on LX1
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
10.  Run the following command to restart the rsyslog service:
    
    ```bash-notab-nocopy
    systemctl restart rsyslog
    ```
    
11.  Configure the firewall by entering the following three commands:
    
    ```bash-notab-nocopy
    firewall-cmd --add-port=514/udp --permanent    
    ```
    
    ```bash-notab-nocopy
    firewall-cmd --reload    
    ```
    
    ```bash-notab-nocopy
    firewall-cmd --list-all    
    ```
    
    The output of the firewall-cmd --list-all command should contain a line "ports:" that displays _514/udp_
    
12.  Confirm that the 514/udp port is open on the firewall on LX1.
    
    Firewall configurations.![Firewall configurations](https://labondemand.blob.core.windows.net/content/lab84059/Screen%20Shot%202020-11-08%20at%2011.25.18%20AM.png)
    


## Forward log files from Kali

In this task, you will configure the Kali Linux virtual machine to forward its log files to the LX1 VM. You must edit the /etc/rsyslog.conf file to accomplish this task.

1.  Switch to the [PT1-Kali](https://labclient.labondemand.com/Instructions/bd6fb4c2-3f08-48c8-8ab3-469206d3200e?rc=10#) VM, and then sign in as root, using Pa$$w0rd as the password.
    
    > Windows operating systems do not natively use rsyslog to manage log files. You can add utilities to Windows to enable the OS to use rsyslog.
    
2.  Open a terminal and use vim to open the /etc/rsyslog.conf configuration file.
    
3.  Use the **DOWN ARROW** key to find the first _uncommented_ line in the #### RULES #### section.
    
4.  Add the following line before any other lines to forward all messages via UDP to LX1:
    
    ```bash-notab-nocopy
    *.* @10.1.0.10:514    
    ```
    
    Edit /etc/rsyslog.conf![Edit /etc/rsyslog.conf](https://labondemand.blob.core.windows.net/content/lab84059/Screen%20Shot%202020-11-08%20at%2011.27.54%20AM.png)
    
    You need to place the configuration line such that it is the first line in the RULES section. This causes it to be processed before all other rules.
    
5.  Select **ESC**, and then enter :wq to write your changes to the file and quit Vim.
    
6.  Confirm that the PT1-Kali virtual machine is configured to forward log files to the LX1 virtual machine.
    
7.  Run the following command to restart the rsyslog service:
    
    ```bash-notab-nocopy
    systemctl restart rsyslog
    ```
    
8.  Run the following command to generate a test message:
    
    ```bash-notab-nocopy
    logger "Test from Kali"
    ```
    
    > Don’t forget to use exactly the same names as specified in the instructions.
    
9.  Run the following command to display the test message from the _local_ log file:
    
    ```bash-notab-nocopy
    cat /var/log/messages | grep -i test
    ```
    
10.  Switch to the [LX1](https://labclient.labondemand.com/Instructions/bd6fb4c2-3f08-48c8-8ab3-469206d3200e?rc=10#) VM.
    
    > If the privacy shade is active, use your mouse to click anywhere in the screen, and then press **ENTER**. The login prompt should be displayed. You may need to enter Pa$$w0rd again.
    
11.  Run the following command to switch to the /var/log directory:
    
    ```bash-notab-nocopy
    cd /var/log
    ```
    
    > The /var/log directory is the default storage location for Linux log files.
    
12.  Run the following command to display the contents of the **/var/log** directory:
    
    ```bash-nocopy-notab
    ls
    ```
    
    You should see a log file named _KALI.log_.
    
13.  Run the following command to display the test message on the central log server:
    
    ```bash-notab-nocopy
    cat /var/log/KALI.log | grep -i "test"
    ```
    
14.  Confirm that the KALI.log file exists in /var/log on the LX1 server.
    
    KALI.log![KALI.log](https://labondemand.blob.core.windows.net/content/lab84059/Screen%20Shot%202020-11-08%20at%2011.31.13%20AM.png)
    
    If the KALI.log file does not appear on LX1, check the following configurations:
    
    -   LX1 /etc/rsyslog - review the entries for UDP logging
    -   LX1 /etc/rsyslog.conf - review the entries for the $template
    -   LX1 - confirm the firewall settings
    -   LX1 - restart the rsyslog service
    -   PT1-Kali /etc/rsyslog.conf - confirm that _._ @10.1.0.10:514 appears in the RULES section
    -   PT1-Kali - restart the rsyslog service
    

> The RT1-LOCAL VyOS router used in the lab environment is also Linux-based. You could repeat the above process to cause the router to forward its log files to the LX1 VM. Doing so from all the Linux, Unix, and macOS devices in your environment would provide you with centralized logging for more efficient monitoring, archiving, and auditing.

## Display the default dump file location on a Linux server

The system dump file contains information that is useful when troubleshooting system crashes. This information includes the kernel state, helping to identify driver or application issues related to the crash. You have decided to confirm the kernel dump location on the LX1 virtual machine. You will display this information by searching the /etc/kdump.conf configuration file.

1.  On the [LX1](https://labclient.labondemand.com/Instructions/bd6fb4c2-3f08-48c8-8ab3-469206d3200e?rc=10#) VM, search the /etc/kdump.conf file to discover the default location of kernel dump crash files on a RHEL-based Linux distribution.
    
    ```bash-notab-nocopy
    cat /etc/kdump.conf | grep -i "path" 
    ```
    
    Many results will be displayed. The one you need has no hash **#** character at the start of the line.
    
2.  Which of the following is the path for the kernel dump file on the LX1 virtual machine?
    
    
    /var/crash
    

    
    Correct
    
    Kernel dump path![Kernel dump path](https://labondemand.blob.core.windows.net/content/lab84059/Screen%20Shot%202020-11-08%20at%2011.33.33%20AM.png)
    
    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    


## Display the default dump file location on a Windows server

You also need to confirm the kernel dump location on the MS1 virtual machine. You will display this information by using the system properties.

1.  Select the [MS1](https://labclient.labondemand.com/Instructions/bd6fb4c2-3f08-48c8-8ab3-469206d3200e?rc=10#) virtual machine. Send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/bd6fb4c2-3f08-48c8-8ab3-469206d3200e?rc=10#) and sign in as 515support\Administrator, using Pa$$w0rd as the password.
    
2.  From Server Manager, select **Local Server**, and then select the **MS1** computer name.
    
3.  Select the **Advanced** tab, and then under Startup and Recovery, select **Settings**.
    
4.  What is the path to the dump file location?
    

    
    %SystemRoot%\MEMORY.DMP
    
    Correct
    
    Windows dump path![Windows dump path](https://labondemand.blob.core.windows.net/content/lab84059/Screen%20Shot%202020-11-08%20at%2011.35.57%20AM.png)
    
5.  Cancel all dialog boxes, and then minimize Server Manager.


## Configure a Windows remote administrator console

Monitoring and managing servers remotely can be more secure and easier. You can configure a single workstation to remotely connect to Microsoft Management Console (MMC) tools on other servers, providing you with access to server information quickly. In this task, you will configure an MMC console on the MS1 virtual machine that connects to the DC1 virtual machine.

1.  On the [MS1](https://labclient.labondemand.com/Instructions/bd6fb4c2-3f08-48c8-8ab3-469206d3200e?rc=10#) VM, right-click the **Start** menu, and then select **Run**.
    
2.  In the Run dialog, type `mmc` and then press **ENTER**. Select **Yes** when prompted to confirm UAC.
    
    A blank Microsoft Management Console opens.
    
    > You can customize MMC consoles by adding snap-ins. Snap-ins are tools and interfaces. Many of these snap-ins can connect across the network to remote servers.
    
3.  From the **File** menu, select **Add/Remove Snap-in**.
    
4.  Select the following snap-ins, and select the **Add** button to place them in the Selected snap-ins column:
    
    -   Computer Management
    -   Event Viewer
    -   Services
    -   Windows Firewall with Advanced Security
5.  For each console, select the radio button for **Another computer**, and then type DC1. Select **Finish** to complete the setting for that console.
    
6.  Select **OK** after you have added the specified consoles.
    
7.  From the **File** menu, select **Save**. Save the new console to the Desktop with DC1-console as the name.
    
    > You may add or remove snap-ins from this console. You may also add snap-ins that point to other computers. Doing so provides a single console with management and monitoring tools that point to multiple servers, allowing you to administer many servers from a single interface.
    
8.  Leave the console open.
    
9.  Which of the following answers best approximates the total size of the C:\ drive on DC1? (Hint: Use the Computer Management snap-in)


## Comprehensive questions

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following best describes the reason for centralizing log files on a single server?
    
    
    Centralized log files are easier to search and archive.
  
2. Why are Kali and VyOS able to forward log files to a central CentOS Linux server?


	rsyslog is common to Unix and Linux operating systems.

  

3. When configuring the rsyslog service on the Linux virtual machines, why did you have to restart rsyslog after making changes to the /etc/rsyslog.conf configuration file?

	Restarting Linux services causes the service to re-read the configuration file and integrate changes.