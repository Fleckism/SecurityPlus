# Assisted Lab 19: Implementing a Virtual Private Network

## Scenario

You are tasked with configuring a Virtual Private Network 
[[VPN]] solution for the sales team at 515 Support. You have access to two Windows servers, which will permit you to demonstrate the process. First, you will add Routing and Remote Access functionality and configure the Sales users on the DC1 server. Next, you'll configure an access policy. You will then test the VPN connection. Finally, you'll use Nmap to discover what ports are exposed on the VPN server.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   3.3 Given a scenario, implement secure network designs.

## Configure the VPN server

Create a new Sales VPN group and add a Sales user. Next, configure the Routing and Remote Access and Network Policy Server roles on DC1.

> It is not recommended that you configure an Active Directory Domain Controller as a VPN server. DC1 is configured this way in the lab environment for convenience only.

1.  On the [DC1]


2.  From Server Manager, select **Tools > Active Directory Users and Computers** from **Server Manager** (window on left). Browse to the **Users** container.
    
3.  Create a new global security group named Sales VPN.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
4.  Open the **Bobby** account, select the **Member Of** tab, and then add **Bobby** to the **Sales VPN** group.
    
    Add Bobby to Sales VPN![Add Bobby to Sales VPN](https://labondemand.blob.core.windows.net/content/lab84051/Screen%20Shot%202020-11-07%20at%205.24.39%20PM.png)
    
5.  Close Active Directory Users and Computers after adding Bobby to the Sales group.
    
6.  From Server Manager, select **Tools > Routing and Remote Access**.
    
7.  Right-click **DC1 (local)** and then select **Configure and Enable Routing and Remote Access**. Select **Next** to start the wizard.
    
8.  Select **Remote access (dial-up or VPN)**, and then select **Next**.
    
9.  Check the box for **VPN**, and select **Next**,
    
10.  When prompted select the **INTERNET** interface as the Internet connection.
    
11.  Accept all remaining defaults, and then select **Finish**.
    
12.  Acknowledge the policy message, and accept the DHCP message when prompted.
    
13.  When the RRAS service has started, right-click the **DC1 (local)** node, select **Properties**. Select the **Logging** tab.
    
14.  Select the radio button for **Log all events**, and then select **OK** to close the properties box.
    
15.  Select the **Remote Access Logging & Policies** node, and then right-click it and select **Launch NPS**.
    
16.  In the Network Policy Server console, select the **Network Policies** node.
    
17.  What is the purpose or effect of the default rules?
    
    To match all connection attempts, and then deny them.
    
    
    Network Policies.
    
    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    
18.  Right-click the **Network Policies** node, and then select **New**. Use the following settings (unless otherwise stated, accept the defaults):
    
    -   Policy name: Enter Sales VPN access
    -   Type of network access server: Select **Remote Access Server(VPN-Dial up)**
    -   Conditions: Select **User Groups** and then add the Sales VPN group
    -   Specify Access Permission: Select **Access Granted**
    -   Configure Authentication Methods: Check the box for **Encrypted authentication (CHAP)** and leave the MS-CHAP and MS-CHAPv2 boxes at their default (checked)
    -   Select **Next** multiple times until the **Finish** button is available, and then select **Finish**.
19.  Observe the new policy in the Network Policies console.
    
20.  In the NPS console, select **Accounting**, and then select **Configure Accounting**.
    
21.  Select **Log to a text file on the local computer**, accept the rest of the defaults, and then complete the configuration.
    
22.  Which of the following answers displays the path to the log files?
    
    
    C:\Windows\System32\LogFiles
    
    Log files.
    

## Configure the VPN client

You are using the MS1 server to act as the VPN client in this proof of concept scenario. You will configure the VPN connection software and establish the connection by using the Bobby user account. You will also evaluate connection information that is displayed on the DC1 VPN server.

1.  Switch to the MS1
2.  Select **Other user**. 
    
    You are _not_ signing in with the administrator account for this task.
    
3.  Minimize Server Manager. On the taskbar, in the notification area, click on the **Networks** icon, and then select **Network settings**.
    
4.  From the Settings page, select **VPN**, and then select **Add a VPN connection**. Configure the following values:
    
    -   VPN provider: Select **Windows (built-in)**
    -   Connection name: Enter Sales VPN
    -   Server name or address: Enter 10.1.0.1
    -   VPN type: Select **Automatic**
    -   Type of sign-in info: Select **User name and password**
    -   User name (optional): Enter 515
    -   Password (optional): Enter Pa
5.  When all values are configured, select **Save**.
    
    VPN client configuration.![VPN Client configuration](https://labondemand.blob.core.windows.net/content/lab84051/Screen%20Shot%202020-11-07%20at%205.31.54%20PM.png)
    
6.  In the Settings window, select the link for **Change adapter options**.
    
7.  Right-click the **Sales VPN**, select **Properties**, and then select **Security** tab.
    
8.  Select the radio button for **Allow these protocols**, and then check the boxes for the following:
    
    -   **Microsoft CHAP Version 2 (MS-CHAP v2)**.
    -   **Automatically use my Windows logon name and password (and domain, if any)**.
    
    Connection configuration![VPN client configuration](https://labondemand.blob.core.windows.net/content/lab84051/vpn%20client%20config.png)
    
9.  Select **OK** to close the **Sales VPN** Properties.
    
10.  On the network settings page, select the **Sales VPN** icon, and then select **Connect**
    
    The authentication process begins. The connection should display as _Connected_.
    
11.  Switch to [DC1](https://labclient.labondemand.com/Instructions/87146486-805b-449d-85eb-fca4820b49c1?rc=10#). In the Routing and Remote Access console, select the **Remote Access Clients** node.
    
12.  Is an active VPN connection present?
    
    Yes
    
    No
    
    Active connections.
    
13.  Switch to the [MS1](https://labclient.labondemand.com/Instructions/87146486-805b-449d-85eb-fca4820b49c1?rc=10#) virtual machine, and then select **Disconnect** to end the VPN configuration test.
    
14.  Switch back to [DC1](https://labclient.labondemand.com/Instructions/87146486-805b-449d-85eb-fca4820b49c1?rc=10#), and from Server Manager, select **Tools > Event Viewer**.
    
15.  Open the **System** log.
    
16.  Which of the following best describes the information provided by Event ID 20274?
    

    VPN connection
    
    
17.  Which of the following best describes the information provided by Event ID 20275?
    

    
    VPN disconnection
    
18.  Which of the following best describes the information provided by Event ID 20272?
    
    VPN connection/disconnection summary


## Investigate the VPN server

You will use Nmap on the PT1-Kali virtual machine to scan the DC1 VM. This will display VPN port information.

1.  Switch to thKaili e password.
    
2.  Open a terminal using the menu at the top of the desktop.
    
3.  Run the following Nmap scan to determine what VPN port is open:
    
    ```bash-notab-nocopy
    nmap 10.1.0.1
    ```
    
4.  Which of the following ports is the open VPN port displayed in the Nmap results?
    

    
    1723/tcp  : 
    
    VPN port.![Ports on DC1](https://labondemand.blob.core.windows.net/content/lab84051/Screen%20Shot%202020-11-07%20at%205.36.52%20PM.png)
    

## Comprehensive questions

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following answers best describes the purpose of NPS policies?
    
    To allow administrators to define VPN connection criteria.

  

2. In the tasks above, what criteria is used by NPS to determine who is allowed to establish a VPN connection?



Group membership

3.   Which service authenticated the VPN connection?

	Active Directory