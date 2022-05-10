Performing Network Reconnaissance and Vulnerability Scanning

## Kali 
- ifconfig
	- eth0
		- [[inet]] 10.1.0.192
- ip addr
	- Shows lo: first then eht0
- nmap 10.1.0.192  -A
	- nmap 10.1.0.254 -A  {shows OS,port,service detection}
	- nmap identified non-standard port number 4450
		- Shows 2 open ports 22/tcp
			- and 53/tcp open tcpwrapped
			- nslookup [domain name or ip]
	- nmap --top-ports 20  ####
- [[curl]] -s -I 10.1.0.2
	- Server
- tcpdump:  Is a packet sniffer
tcpdump added files to a  auth.txt file
Opened that in wireshark, looked at the HTTP with GET in the info box
- in the box below that I expanded the Hypertext transfer protocol tab
	- Then Authorization it had a **Credentials** section 
1.  ```bash-notab-nocopy
    tcpdump -vv dst 10.1.0.2 and port www -w auth.txt
    ```

## CentOS
- ipconfig
	- etho0
		- inet
![[Pasted image 20220509214434.png]]

![[Pasted image 20220509214621.png]]
using 
- openvas-start
# OpenVas
## Run OpenVAS scanner

OpenVAS can be managed using a web application called Greenbone Security Assistant. You will create a targeted, credentialed scan against the web server discovered above.

1.  If necessary, sign on to the [PT1-Kali](https://labclient.labondemand.com/Instructions/d04b1098-4593-4ac6-baa3-46da5325fa25?rc=10#) VM, and then sign in as root using Pa$$w0rd as the password.
    
    You may already be signed in.
    
2.  In the menu at the top of the desktop, select the **Terminal**.
    
3.  In the terminal window, type openvas-start and press **ENTER**. Wait for the prompt to return.
    
    If you receive a timeout error, run openvas-start again.
    
    > It may take one to two minutes for the service to start. You must wait before proceeding to the next steps.
    
4.  The **Firefox** browser automatically launches when the openvas-service starts. It connects to https://127.0.0.1:9392
    
5.  Log on with the Username admin and Password as Pa$$w0rd.
    
6.  From the **Configuration** menu, select **Credentials** to create a credentialed scan.
    
    > If at any time you receive an error message from Greenbone stating "Internal error" with the reference "Could not authenticate to the manager daemon" then retry the step again.
    
7.  Select the blue star icon on the left to open the _New Credential_ web dialog box.
    
    The New Credential button.![The New Credential button](https://labondemand.blob.core.windows.net/content/lab84063/Screen%20Shot%202020-11-07%20at%208.59.16%20AM.png)
    
8.  Complete the dialog box with the following information:
    
    -   Name—enter 515support
        
    -   Allow insecure use—select **Yes**
        
    -   Username—enter 515support\Administrator
        
    -   Password—enter Pa
        
9.  Select **Create**.
    
    > Note that tasks are simplified for the activity. You would _NEVER_ use the domain admin credentials for this task (just as you would never use the same password across multiple accounts in multiple contexts). Create a dedicated account for vulnerability scanning.
    
10.  Configure a scan target. From the **Configuration** menu, select **Targets**.
    
11.  Select the blue star icon on the left to open the _New Target_ web dialog box.
    
12.  Complete the dialog box with the following information:

    -   Name—enter 515support web server
        
    -   Hosts—select **Manual** and enter 10.1.0.2 in the box.
        
    -   Credentials—from the _SMB_ list box, select **515support**.
        
13.  Select **Create**.
    
14.  Next, configure a scan task. From the **Scans** menu, select **Tasks**.
    
    You may close the "Welcome to the scan task" dialog box that opens.
    
15.  Select the blue star icon on the left to open the _New Task_ web dialog box.
    
16.  Complete the dialog box with the following information:
    
    -   Name—515support web scan
        
    -   Scan Targets—**515support web server**
        
    -   Scan Config—**Full and fast**
        
17.  Select **Create**.
    
    You will run the scan manually to ensure that it works as expected.
    
18.  Under _Name_ at the bottom of the screen, select the **515support web scan** task.
    
19.  Select the **Start** green arrow button to run the scan manually.
    
    > Now that you have begun a scan, you need to let it run for _three to four minutes_. You may continue with the next steps while the scan runs.
    
20.  From the _No auto-refresh_ box in the green header bar, select **Refresh every 30 seconds**. Let the scan to execute while you complete the next step.
    
21.  Select **Scans→Reports**.
    
    Observe the **Scan Results** columns. Do not continue to the next task until there are results in the **High**, **Medium**, or **Low** columns.
    
    You can use this screen to monitor the status of tasks and preview scan results even if the task is not complete.
    
22.  In the **Date** column at the bottom of the Reports page, select the task with today's date to view the results.
    
    If there are no entries in the report yet, wait a few more minutes.
    
    There must be entries in the report.![Screen Shot 2020-11-07 at 9.19.09 AM.png](https://labondemand.blob.core.windows.net/content/lab84063/Screen%20Shot%202020-11-07%20at%209.19.09%20AM.png)
    
23.  From the small triangle pull down menu by the "Report:Results" title, choose **Report:Hosts** to display the discovered hosts and their related vulnerability information.
    
24.  In the pull-down menu at the upper left of the page, select **HTML** (the menu current reads **Anonymous XML**), and then select the green **Download filtered Report** button.
    
25.  When prompted, select **Save File** to download the report to the default **Downloads** folder (so it can be scored).
    
26.  Close the **OpenVAS** administration site in Firefox.
    
27.  Open the **Home** directory for the user, and then double-click the **Downloads** directory.
    
28.  Double-click the HTML file and view the report.
    
    The file name will begin with **report-** and contain a long string of characters, concluding with **.html**
    
29.  Confirm that the report HTML file exists.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
30.  Close **Firefox** to interrupt the scan.
## DC1
- ipconfig
	- IPv4 Address

## MS1
- ipconfig
	- IPv4 Address

# Backdoor
## Establish connectivity by using the backdoor

You believe the malware has been installed on the web server, perhaps by an administrator being fooled into running a setup program without investigating its source. You will search for and establish connectivity. You'll also exploit the vulnerable server.

1.  Select the [PT1-Kali](https://labclient.labondemand.com/Instructions/d04b1098-4593-4ac6-baa3-46da5325fa25?rc=10#) VM, and then log in as root with the password Pa$$w0rd
    
2.  Run an Nmap port scan of 10.1.0.2 (MS1) to discover whether port **4450** is open, indicating the successful installation of the malware. Use the correct option for Nmap to discover the port.
    
    Recall that you can scan for a specific port with the -p option.
    
    Use the following chart as a reference for nmap options during this activity.
    
3.  Switch to [DC1](https://labclient.labondemand.com/Instructions/d04b1098-4593-4ac6-baa3-46da5325fa25?rc=10#) virtual machine, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/d04b1098-4593-4ac6-baa3-46da5325fa25?rc=10#), and then sign on as 515support\Administrator using the password Pa$$w0rd.
    
    To connect to the backdoor on **MS1**, you will use a terminal emulation client called **PuTTY** ([chiark.greenend.org.uk](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)).
    
4.  From the Desktop, open the **LABFILES** folder, and then run **putty** with the following settings:
    
    Name: 10.1.0.2  
    Port: 4450  
    Connection Type: **RAW**
    
    The PuTTY settings.![PuTTY settings](https://labondemand.blob.core.windows.net/content/lab84063/Screen%20Shot%202020-11-07%20at%209.50.22%20AM.png)
    
5.  Run the following command to create the user account:
    
    `net user /add mal Pa$$w0rd`
    
6.  Confirm that the mal user account exists on MS1
    
    Correct
    
7.  Run the following command to add the mal user account to the local administrators group:.
    
    `net localgroup administrators mal /add`
    
8.  Confirm that the mal user account is a member of the administrators group.
    
    Correct
    
    > These two commands have given you administrative access on the remote server. You have successfully elevated your privileges.
    
9.  Use the connection to delete the CONFIDENTIAL.txt file from the **C:\LABFILES** folder on **MS1**.
    
    > To navigate at the command line, use the `cd` command to change directories and the `del` command to delete files.
    
10.  Type exit to close the connection.
# Questions
- What is FQDN