# Assisted Lab 10: Managing Centralized Authentication

## Scenario

RADIUS permits centralized authentication. In this activity, you will rely on Active Directory (on DC1) as the authentication server. It will also act as the RADIUS server—the point where all authentication attempts get forwarded. The UTM1 virtual machine, running the pfSense security appliance, will be configured as a RADIUS client. It will pass authentication attempts to DC1. In this scenario, RADIUS is being used to authenticate administrative users who manage the pfSense firewall appliance itself, rather than authentication of remote access VPN or wireless users.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   3.8 Given a scenario, implement authentication and authorization solutions.



## Register RADIUS client

RADIUS can be used with VPN, wireless, and appliance authentication. In Windows Server, the RADIUS role is configured using Network Policy Server (NPS). Use NPS to configure the UTM1 VM as an authorized RADIUS client of DC1.

1.  Select the [DC1](https://labclient.labondemand.com/Instructions/100cf6a7-181b-4936-b2d5-6d12538aafdd?rc=10#) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/100cf6a7-181b-4936-b2d5-6d12538aafdd?rc=10#), and log on with the credentials 515support\Administrator and Pa
    
2.  In Server Manager, select **Tools > Network Policy Server**.
    
3.  Expand **RADIUS Clients and Servers** to select **RADIUS Clients**. Right-click **RADIUS Clients** and select **New**.
    
    The RADIUS client is the network appliance accepting the user's credentials (in this case, the UTM1 VM).
    
4.  In the New RADIUS Client dialog box, in the Friendly name box, enter pfsense.corp.515support.com.
    
5.  In the Address box, type 10.1.0.254
    
6.  Under Shared Secret, select the **Generate** radio button, then select the **Generate** button.
    
	 The New RADIUS Client dialog box
    
    ![New RADIUS Client](https://labondemand.blob.core.windows.net/content/lab84044/Screen%20Shot%202020-11-07%20at%2011.45.13%20AM%20copy.png) The shared secret means that a RADIUS server can trust a RADIUS client and vice versa. This prevents a rogue RADIUS client from requesting authentication information from a legitimate server, provided the shared secret has not been compromised.
    

7.  Copy the shared secret string.
    
    > You need to keep this value on the Clipboard for a while—alternatively, you can paste it into a Notepad file.
    
8.  Select **OK** to close the dialog box.

## Configure network policy

Configure a policy that allows users in the LocalAdmin security group to authenticate with pfSense by using unencrypted authentication. Use the Class attribute to transmit the LocalGroup property from the RADIUS server to the RADIUS client when a user authenticates.

1.  In the Network Policy Server console, expand **Policies** to select **Network Policies**. Right-click **Network Policies** and select **New**.
    
2.  In Policy name, type pfSense Network Security Appliance Administration
    
3.  Select **Next**. On the Specify conditions page, select the **Add** button.
    
4.  Select **Windows Groups** and select **Add**.
    
5.  Select the **Add Groups** button then type localadmin and select **Check Names**.
    
    Select Windows Groups.![Screen Shot 2020-11-07 at 11.52.03 AM.png](https://labondemand.blob.core.windows.net/content/lab84044/Screen%20Shot%202020-11-07%20at%2011.52.03%20AM.png)
    
6.  Select **OK** then select **OK** again to confirm the Windows Groups dialog box.
    
7.  Select **Next**.
    
8.  On the Specify Access Permission page, leave **Access granted** selected and select **Next**.
    
9.  On the Configure Authentication Methods page, leave the existing MS-CHAPv2 and MS-CHAP boxes selected, as shown in this screenshot.
    
    Configure authentication methods.![Authentication methods dialog](https://labondemand.blob.core.windows.net/content/lab84044/authentication%20methods.png)
    
10.  Select **Next**.
    
    > We are not implementing it for this lab, but because the credential is being passed using [weak MS-CHAP encryption](https://msrc-blog.microsoft.com/2012/08/20/weaknesses-in-ms-chapv2-authentication/), you must configure the management interface to use HTTPS encrypted connection security rather than plain HTTP. You would achieve this by installing a trusted root certificate to the pfSense appliance and disabling HTTP-only access.
    
11.  On the Configure Constraints page, select **Next**.
    
12.  On the Configure Settings page, with **Standard** selected, select the **Add** button.
    
13.  In the Add Standard RADIUS Attribute dialog box, from the Attributes box, select **Class**. Select the **Add** button.
    
14.  Type LocalAdmin in the box and select **OK**. Select **Close**. pfSense uses the Class attribute to communicate group membership.
    
    Custom RADIUS attribute.![Custom RADIUS attribute](https://labondemand.blob.core.windows.net/content/lab84044/Screen%20Shot%202020-11-07%20at%2011.56.06%20AM.png)
    
15.  Select **Next** then **Finish**.

## Configure RADIUS client

Configure the pfSense VM as a RADIUS client by inputting the RADIUS server details. This permits pfSense to forward authentication requests to DC1.

1.  Still on the [DC1](https://labclient.labondemand.com/Instructions/100cf6a7-181b-4936-b2d5-6d12538aafdd?rc=10#) VM, open http://10.1.0.254 in the browser.
    
    You will be connected to the pfSense virtual machine.
    
2.  Log on with the credentials admin and Pa. When prompted to save the password, select **Not for this site**.
    
3.  Maximize the browser window. Select **System > User Manager**. Select the **Authentication Servers** tab, then select the **Add** button.
    
4.  In the Descriptive name box, type 515support AD
    
5.  From the Type list, select **RADIUS**.
    
6.  Under RADIUS Server Settings, note that the Protocol is set to MS-CHAPv2 by default. This is the authentication protocol that determines the format for the user credential. The RADIUS server and client must be able to match at least one authentication method.
    
7.  In the **Hostname or IP address** box, enter 10.1.0.1
    
8.  In the **Shared Secret** box, paste the Clipboard contents.
    
    You are pasting in the shared secret generated on DC1 in an earlier task.
    
    Authentication server![Configuring a RADIUS Server connection on the RADIUS Client](https://labondemand.blob.core.windows.net/content/lab84044/Screen%20Shot%202020-11-07%20at%2012.00.15%20PM.png)
    
9.  Select the **Save** button.
    
10.  Which of the following best describes the reason for the shared secret configured on DC1 and pfSense?
    
    To authenticate pfSense to DC1.
    
    Shared secret.The shared secret is a passphrase set on the RADIUS server (DC1) that must be configured on each RADIUS client (just pfSense in this example). This means that the server does not accept requests from unauthenticated RADIUS clients.
    

46% Tasks Complete

PreviousNext: Configure role-based permissions


## Configure role-based permissions

Configure a basic least permissions role for the LocalGroup security group account so that users do not have access to advanced system configuration pages.

1.  Select the **Groups** tab, then select the **Add** button.
    
2.  In the **Group name** box, type LocalAdmin
    
3.  Select the **Save** button.
    
4.  In the **Actions** column, select the **Edit group** pen icon to edit the **LocalAdmin** group.
    
5.  Under Assigned Privileges, select the **Add** button.
    
6.  **SHIFT**-click to select from **WebCfg—Dashboard (all)** down to the last **WebCfg—Status: UPnP Status** item.
    
    This is a very long list of privilege names!
    
    Privileges![Privileges](https://labondemand.blob.core.windows.net/content/lab84044/Screen%20Shot%202020-11-07%20at%2012.03.50%20PM.png)
    
7.  Locate the item **WebCfg—pfSense wizard subsystem** and **CTRL**+click to de-select it.
    
8.  Select the **Save** button.
    
9.  Select the **Settings** tab then from the Authentication Server box, select **515support AD**. Select the **Save** button.
    
10.  From the upper right corner of the page, select the **Logout** button.



To check Windows user authorization level 
To check user account member of LocalAdmin group

Go to Windows Administrative tools
- Active Directory users and Computers
	- Users
		- Right click on user
			- Member Of page


Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following best describes where Bobby's user account is stored?
    
    In a user database in pfSense.
    
    As a local user account on DC1.
    
    In the Active Directory database on DC1.
    
    As a local user account on MS1.
    
    Correct
    
2.  Which of the following best describes the purpose of the RADIUS client registration task in this activity?
    
    To configure Bobby's user account in Active Directory.
    
    To configure pfSense to accept authentication attempts sent through DC1.
    
    To configure DC1 to accept authentication attempts sent through pfSense.
    
    To install the RADIUS client software on pfSense.
    
    To install Network Policy and Access Services on DC1.
    
    Correct




Exam Results

Score

4 / 4

Passed

Yes

Activities (4)

Which of the following best describes the reason for the shared secret configured on DC1 and pfSense?

 To authenticate pfSense to DC1.

 To authenticate DC1 to pfSense.

 To authenticate Bobby on pfSense.

 To authenticate Bobby on DC1.

```
        Correct
```

Score: 1

Is Bobby's user account a member of the LocalAdmin group?

 Yes

 No

```
        Correct
```

Score: 1

Which of the following best describes where Bobby's user account is stored?

 In a user database in pfSense.

 As a local user account on DC1.

 In the Active Directory database on DC1.

 As a local user account on MS1.

```
        Correct
```

Score: 1

Which of the following best describes the purpose of the RADIUS client registration task in this activity?

 To configure DC1 to accept authentication attempts sent through pfSense.

 To configure pfSense to accept authentication attempts sent through DC1.

 To configure Bobby's user account in Active Directory.

 To install Network Policy and Access Services on DC1.

 To install the RADIUS client software on pfSense.

```
        Correct
```

Score: 1