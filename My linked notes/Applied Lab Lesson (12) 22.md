# APPLIED LAB 22: Securing the Network Infrastructure

## Scenario

In this activity, you will use your knowledge of secure protocols and practices to implement network configurations. First, you will establish SSH connectivity to meet written security policy standards. Next, you will configure a VPN server solution, and then test connectivity by using a VPN client. You will then configure DHCP security settings, including MAC address filtering. Finally, you will set a fine grained password policy for the IT staff, enforcing stronger passwords for these critical administrative accounts.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   1.4 Given a scenario, analyze potential indicators associated with network attacks
    
-   3.1 Given a scenario, implement secure protocols
    
-   3.2 Given a scenario, implement host or application security solutions
    
-   3.3 Given a scenario, implement secure network designs

## Configure secure SSH connectivity

Configure a Linux SSH server to display a banner message and require passwords for connectivity. Test the connectivity from a Linux SSH client. Finally, display SSH log file entries.

1.  On the PT1-Kali
    
2.  Run an nmap scan to display the VM's own open ports.
	1. ifconfig to get IP 
	2. then nmap eth0 inet 
	    
3.  Open a terminal, and then establish an **SSH** connection as the centos user to 10.1.0.10 (the LX1 Linux VM). Use Paw0rd as the password.
    
    SSH connections.
    
    -   ssh centos@10.1.0.10
    -   Select **Yes** when prompted to make the connection.
    
4.  Disconnect from the LX1 SSH server.
    
    You have connected via default SSH settings.
    
5.  Switch to the LX1 SSH server. Sign in with the preconfigured centos account and a password of Paw0rd.
    
    You will configure increased security settings for the SSH server.
    
6.  Open a terminal, and then elevate your credentials to root:
    
    ```bash-notab-nocopy
    su - root
    ```
    
    > Note that there is a space on each side of the dash.
    
7.  Type Paw0rd when prompted.
    
    > Recall that Linux does not print any characters to the display when you enter a password. It may appears as though the passwd is not receiving your keystrokes, but it is.
    
8.  Use the Vim text editor to edit the **/etc/ssh/sshd_config** SSH configuration file.
    
    Vim quick reference  
      
      
    
      
      
    
    -     
        
    
9.  Edit the SSH configuration file to implement the following SSH configurations defined by your company's written security policy:
    
    -   Empty passwords are not allowed for SSH authentication. **Disable the empty password** option.
        
    -   Uncomment the **Banner** line and type **/etc/issue.net** as the banner file path.
        
    
    You will need to uncomment some lines and then edit them. Other lines you may simply edit.
    
    > The **#** hash character identifies comment lines. Comments are ignored by the system and used to provide administrators with examples, explanations, and additional information within the body of a configuration file or script.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
    Here are the specific lines to edit:
    
    ![Banner message configuration](https://labondemand.blob.core.windows.net/content/lab84065/Screen%20Shot%202020-11-07%20at%205.51.22%20PM.png)
    
10.  Save your changes by pressing **ESC** in Vim, and then typing :wq.
    
11.  Use Vim to edit the **/etc/issue.net** file. Remove all of the existing content in the file, and then add the following warning:
    
    ```notab-nocopy-nocolor
    Authorized use only!
    ```
    
12.  Press **ESC** in Vim, and then type :wq to save your changes to the **/etc/issue.net** file and then exit Vim.
    
    The /etc/issue.net banner message.![The /etc/issue.net file](https://labondemand.blob.core.windows.net/content/lab84065/Screen%20Shot%202020-11-08%20at%208.45.52%20AM.png)
    
    > Don’t forget to use exactly the same names as specified in the instructions.
    
13.  In the terminal, run the systemctl restart sshd command to restart the SSH service.
    
    > Recall that each time you change a Linux configuration file, you must restart the service for the change to take effect.
    
14.  Switch to the [PT1-Kali](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#) SSH client VM.
    
    > If the VM's privacy screen is enabled, click it once, and then sign in using Pa$$w0rd as the password.
    
15.  Attempt the SSH connection by using the centos credentials. Use Paw0rd as the password.
    
16.  Does the banner message appear?
    
    Yes
    
    No
    
    The banner message.![SSH login with banner](https://labondemand.blob.core.windows.net/content/lab84065/Screen%20Shot%202020-11-08%20at%208.48.16%20AM.png)
    
17.  Type exit to disconnect from the remote LX1 SSH server.
    
18.  Switch to the [LX1](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#) VM. If the VM's privacy screen is enabled, press **ENTER**. A login prompt should appear. Sign in as the preconfigured centos user with a password of Paw0rd.
    
19.  If a Terminal window is not already open, right-click on the desktop, and select **Open Terminal**.
    
20.  To test log file functionality, run the following command to generate an entry in the **/var/log/messages** log file:
    
    ```bash-notab-nocopy
    logger "test message"
    ```
    
    > Don’t forget to use exactly the same names as specified in the instructions.
    
21.  Run the following command to view the lines at the bottom of the **/var/log/messages** log file:
    
    ```bash-notab-nocopy
    tail /var/log/messages
    ```
    
    You should see the "test message" string near the bottom of the output.
    
    > The most recent log file entries are written at the bottom of the files, so tail is a great tool to use to see the most current information. The head command displays the entries at the top of the file.
    
22.  Run the following command to display the lines at the bottom of the **/var/log/secure** log file:
    
    ```bash-notab-nocopy
    tail /var/log/secure | grep -i ssh
    ```
    
23.  What is the source IP address in the "Accepted password" entry for the inbound SSH connections? (Format: 1.2.3.4)
    
    The tail command.


## Configure the VPN server

Create a new Sales VPN group and add a Sales user. Using the Routing and Remote Access and Network Policy Server roles, configure a remote access policy that permits only members of the Sales VPN group to authenticate.

1.  On the [DC1](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#) virtual machine, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#), and then sign on a 515support\Administrator with Paw0rd.
    
2.  Use **Active Directory Users and Computers** to create a new global security group in the **Users** container named Sales VPN.
    
3.  Add **Bobby** to the Sales VPN group.
    
4.  Close Active Directory Users and Computers after adding Bobby to the Sales group.
    
5.  In Server Manager, select **Tools > Routing and Remote Access**. Right-click **DC1 (local)** and then select **Configure and Enable Routing and Remote Access**.
    
6.  Set the following configurations in the wizard:
    
    -   **Remote access (dial-up or VPN)**
        
    -   **VPN**
        
    -   Select the **INTERNET** interface as the Internet connection.
        
    -   Accept all remaining defaults.
        
    -   Acknowledge the policy message and DHCP notification when prompted.
	    - **This will populate underneath selected server**
        
7.  Select and then right-click **Remote Access Logging & Policies**, and then select **Launch NPS**.
    
8.  Select the **Network Policies** node.
    
9.  Create a new policy by right-clicking the **Network Policies** node. Use the following settings (unless otherwise stated, accept the defaults):
    
    -   Policy name: Sales VPN access
    -   Type of network access server: **Remote Access Server(VPN-Dial up)**
    -   Conditions: select **User Groups** and then add the Sales VPN group  **The name will be underlined if checked**
    -   Specify Access Permission: **Access Granted**
    -   Configure Authentication Methods: check the box for **Encrypted authentication (CHAP)** and leave the MS-CHAP and MS-CHAPv2 boxes at their default (checked)
    -   Acccept all remaining defaults, and then select **Finish**
10.  Observe the new policy in the **Network Policies** console.
    
    The VPN server is now configured to accept VPN clients.

## Configure the VPN client

You are using the MS1 server to act as the VPN client in this proof of concept scenario. You will configure the VPN connection software and establish the connection by using the Bobby user account. You will also evaluate connection information that is displayed on the DC1 VPN server.

1.  Switch to the MS1 virtual machine. Send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#).
    
2.  Sign on as Bobby using Paw0rd as the password.
    
    > You are not signing in with the administrator account for this task.
    
3.  Open **Network settings**, and from the **Settings** page, select **VPN**, and then select **Add a VPN connection**. Configure the following values:
    
    -   VPN provider: **Windows (built-in)**
    -   Connection name: Sales VPN
    -   Server name or address: 10.1.0.1
    -   VPN type: **Automatic**
    -   Type of sign-in info: **User name and password**
    -   User name (optional): 515support\bobby
    -   Password (optonal): Paw0rd
    -   When all values are configured, select **Save**.
4.  In the Settings window, select the link for **Change adapter options**.
    
5.  Right-click the **Sales VPN**, select **Properties**, and then select **Security** tab.
    
6.  Select the radio button for **Allow these protocols**, and then check the boxes for the following protocols
    
    -   **Challenge Handshake Authentication Protocol (CHAP)**
    -   **Microsoft CHAP Version 2 (MS-CHAP v2)**.
    -   **Automatically use my Windows logon name and password (and domain, if any)**.
7.  Select **OK** to close the **Sales VPN** adapter properties. When prompted, confirm the changes.
    
8.  On the network **Settings** page, select the **Sales VPN** icon, and then select **Connect**
    
    The authentication process begins. After a few seconds the connection should display _Connected_.
    
9.  Which of the following answers best describes why the Bobby user account is allowed to authenticate via the Sales VPN connection?
	1. Bobby is a member of the Sales VPN group, and the Sales VPN group has been granted access to authenticate via VPN.
    
  
    
10.  Switch to [DC1](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#). Select the **Routing and Remote Access** console.
    
11.  View the active connection in the **Remote Access Clients** pane.
    
12.  Return to the [MS1](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#) VM, and then disconnect the VPN connection.
    
13.  Sign out of the [MS1](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#) VM. In the next task you will sign in as the Administrator, instead of Bobby.
    
14.  Select the [DC1](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#) VM.
    
15.  In the **Routing and Remote Access** console, right-click the **DC1 (local)** server, and then select **Disable Routing and Remote Access**. When prompted, confirm the action.



## Implement network addressing security configurations

Modify DHCP security by enabling MAC address filtering and updating reservation information.

1.  Select the [MS1](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#) VM.
    
2.  Make sure you are not signed in as Bobby. Send Ctrl+Alt+Delete
    
3.  Launch the **DHCP** console.
    
4.  Which of the following IP addresses are reserved in DHCP? (Choose two)
    
    10.1.0.10
    10.1.0.192
    
5.  In the **Scope [10.1.0.0] 515 Support Scope**, display the Properties of the reservation for the LX1 VM. Accomplish the following tasks:
    
    -   Set **Description** to Dev Workstation
        
    -   Copy the MAC address for LX1.
        
6.  Select the **Properties** of the **IPv4** node. On the **Filters** tab, check the **Enable Allow List** box. Select **OK**.
    
7.  In the **Filters > Allow** node, right-click and select **New Filter**. Accomplish the following tasks:
    
    -   Paste MAC from lx1.corp.515support.com
        
    -   Set **Description** to Dev Workstation
        
8.  Which of the following answers best describes the effect of the Allow Filter you just configured?
    
    The filter explicitly disallows certain MAC addresses, and allows any MAC address not listed.
    
    The filter explicitly allows certain MAC addresses, and disallows any MAC addresses not listed.
    
    The filter logs the IP address reservation.
    
    The filter reserves a particular IP address for a particular client by hostname.
    
9.  Close the DHCP console.

# Create a fine-grained password policy for IT staff accounts

The Default Domain Policy defines password requirements for all user accounts in the domain. Fine-grained password policies, however, assign particular password policies to individual user accounts or Active Directory Global groups. You will use fine-grained passwords to define a more restrictive password policy for IT staff member user accounts.

1.  Switch to the the [DC1](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#) virtual machine. If necessary, sign on by sending [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/b0e092e0-c7f5-418f-b6aa-313df4c29767?rc=10#). Use Pa$$w0rd as the password.
    
2.  Open the **Active Directory Users and Computers** console, and then create a new ITStaff Global group in the **Users** container.
    
3.  Add the Domain Admins and LocalAdmin objects to the new ITStaff group.
    
4.  Close Active Directory Users and Computers.
    
5.  Open the **Active Directory Administrative Center** console.
    
6.  In the left-hand pane, select **corp (local) > System > Password Settings Container**.
    
7.  Review the following security policy summary for IT staff user account password management:
    
    -   All IT staff privileged accounts must contain a minimum of _20 characters_ and be _complex_.
        
    -   Passwords must be changed every _30 days_. Passwords may not be changed more than _once per day_ and the _24_ most recent passwords cannot be repeated.
        
    -   IT staff privileged accounts are subject to an _account lockout policy_, with a maximum of _three_ failed login attempts allowed. Accounts will be locked out for a duration of _20 minutes_.
        
8.  Create a password policy named IT Account Policy that meets the requirements listed in the security policy. Set a precedence level of 10 on the policy.
    
    Here are the specific fine-grained password policy settings if you need help configuring the policy.
    
9.  Under Directly Applies To, add the ITStaff group.
    
10.  Confirm that the ITStaff fine grained password policy exists
    
    The fine grained password policy
    

  

1. Which of the following answers best describes why you must create a remote access policy for VPN connectivity?
	1. By default, all remote access connection attempts are denied for security reasons. You must create an allow policy for any connectivity.
2. Which of the following answers best describes the purpose of a DHCP Filter "allow" policy?
	1. It permits only DHCP clients with listed MAC addresses to lease IP address configurations.
3.   Which of the following answers best describes the purpose of fine grained password policies in Windows?
	1. Fine grained password policies implement password settings for specific users or groups, superseding of the domain-wide Default Domain Policy.
