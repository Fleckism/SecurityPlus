# Assisted Lab 15: Implementing a Secure Network Design

## Scenario

In this activity, you will configure an internal Windows webserver for HTTPS connectivity, providing a secured connection to an internal web application. In part two, you will configure DHCP security settings, including Authorization, an IP address reservation, and audit logs.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   1.4 Given a scenario, analyze potential indicators associated with network attacks.
    
-   3.3 Given a scenario, implement secure network designs.


## Request server certificate

Use IIS Manager to request a certificate for the web server The certificate is used to provide a secure connection.

 
- In Server Manager, select **Tools > Internet Information Services (IIS) Manager**.
- In the Connections pane, select the **MS1** server icon (The server that you are requesting a certificate for). In the Home pane, open the **Server Certificates** applet.
    
- In the Actions pane, select **Create Domain Certificate**.
    
- Complete the Create Certificate wizard with the following responses:
    
    -   Common Name: 
    -   Organization: 
    -   Organizational Unit:
    -   City/locality: 
    -   State/province: 
    -   Country/region:
6.  Select **Next**.
    
7.  On the Online Certification Authority page, select the **Select** button, then select **515support-CA** and select **OK**.
    
8.  In the Friendly name box, type updates.corp.515support.com Domain-issued Certificate and then select **Finish**.
    
    After a few seconds, the certificate request will be granted.
    
9.  Double-click on the **updates.corp.515support.com Domain-issued Certificate**, and use the certificate details to answer the following questions.
    
10.  What is root CA in the Certification Path?
 
The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    

11.  What is the validity period for the newly-issued certificate?
    
    One year.
    
    Two years.
    
    Three years.
    
    Ten years.
    
    Twenty years.
    
    The General tab![General tab](https://labondemand.blob.core.windows.net/content/lab84054/Screen%20Shot%202020-11-07%20at%203.53.16%20PM.png)
    
12.  Close the certificate after you have answered the questions.

## Configure HTTPS

Bind the certificate to a secure HTTP port on the default website. The certificate is now used to guarantee the identity of this web site, ensuring a secured connection.

1.  In IIS Manager, expand the **Sites** node on the server to show the **Default Web Site** node.
    
2.  Right-click **Default Web Site** and select **Edit Bindings**.
    
3.  Select the **Add** button.
    
4.  In the Add Site Binding dialog box, from the Type drop-down list, select **https**.
    
5.  In the Host name box, type updates.corp.515support.com
    
6.  From the SSL certificate drop-down list, select **updates.corp.515support.com Domain-issued certificate**.
    
    Add Site Binding.![Add Site Binding](https://labondemand.blob.core.windows.net/content/lab84054/Screen%20Shot%202020-11-07%20at%203.56.06%20PM.png)
    
7.  Select **OK**.
    
8.  In the Site Bindings dialog box, select **HTTP**, and then select **Remove** to delete HTTP from the list. Select **Yes** when prompted to confirm the removal.
    
9.  Select **Close**.
    
10.  Why did you remove the HTTP option from the Site Bindings list?
    
    You do not wish to permit unsecured HTTP connections to the web server.
    
    IIS can only be configured for HTTP or HTTPS, but not both.
    
    The client computers are not compatible with HTTPS.
    
    HTTPS includes HTTP connections, so it was redundant.
    
    HTTPS
    

19% Tasks Complete

PreviousNext: Configure authentication...
## Configure authentication policy

Configure the web site to require Basic authentication, which uses plaintext authentication.

1.  In IIS Manager, select the **Default Web Site** node.
    
2.  In the Home pane, open the **Authentication** applet.
    
3.  Select **Anonymous Authentication**, then in the Actions pane, select **Disable**.
    
4.  Select **Basic Authentication**, then in the Actions pane, select **Enable**.
    
    > Basic authentication submits plaintext credentials, which (even with the protection of a TLS tunnel) is a risk. On an intranet, there'd be no reason not to use Windows authentication, which is much more secure. In this activity, you want to observe the credentials submitted by the client, however, and Kerberos makes that a bit more complex.
    
    Configure authentication.![Configure Basic authentication](https://labondemand.blob.core.windows.net/content/lab84054/Screen%20Shot%202020-11-07%20at%203.57.42%20PM%20copy.png)
    

34% Tasks Complete

PreviousNext: Test web credentials
## Test web credentials

On the Kali virtual machine, test the authenticated connection to the https://updates.corp.515support.com web site.

1.  Sign in to the [PT1-Kali](https://labclient.labondemand.com/Instructions/49acb7a3-7e4c-4a65-ab67-5f7b978f663b?rc=10#) VM as root using Paas the password.
    
2.  From the menu at the top of the Kali Linux screen, select **Firefox ESR**.
    
3.  Attempt the web connection by using http://updates.corp.515support.com
    
    > Be sure you enter _http_ and not _https_ in this step!
    
4.  Is the HTTP connection successful?
    
    Yes
    
    No
    
    The web connection.![Failed connection attempt](https://labondemand.blob.core.windows.net/content/lab84054/Screen%20Shot%202020-11-07%20at%204.03.32%20PM.png)
    
5.  Attempt the web connection by using https://updates.corp.515support.com
    
    > Be sure you enter _https_ and not _http_ this time!
    
6.  You will receive a _Warning: Potential Security Risk Ahead_ message. Select **Advanced**, then **Accept the Risk and Continue**.
    
7.  Which of the following is stated as the reason for the warning?
    
    The site is on an intranet and therefore cannot use certificates.
    
    The certificate is expired.
    
    The certificate is revoked.
    
    The web site is corrupted.
    
    The site attempts to identify itself with invalid information.
    
    Security information![Advancd information](https://labondemand.blob.core.windows.net/content/lab84054/Screen%20Shot%202020-11-07%20at%204.04.38%20PM.png)
    
8.  If you received a warning from the web browser, why would you accept the certificate anyway?
    
    You know the certificate is not actually expired.
    
    The certificate has nothing to do with the HTTPS connection.
    
    You know the certificate is not actually revoked.
    
    You know the certificate is issued by a trusted, internal CA.
    
    Security information![Advanced information risk accepted](https://labondemand.blob.core.windows.net/content/lab84054/Screen%20Shot%202020-11-07%20at%204.06.15%20PM.png)
    
9.  When prompted by the **Authentication Required** dialog box, enter the 515support\Administrator and P0rd credentials.
    
    The web site is displayed.
    
    > If you see "Page can't be displayed" errors, or if you are not prompted for your credentials, use the Refresh key (**F5**).
    
10.  If prompted to save the login by Firefox, select **Never For This Site**.
    
11.  After the connection is complete, select the browser padlock icon to confirm that you are viewing the page over a secure connection.
    
12.  What status is displayed when you select the padlock icon in the Firefox URL address bar?
    
    Warning!
    
    Connection Is Not Secure
    
    Secure Connection
    
    Name and password accepted
    
    Validated web site
    
    The padlock icon![Connection not secure](https://labondemand.blob.core.windows.net/content/lab84054/Screen%20Shot%202020-11-07%20at%204.08.05%20PM.png)
    
13.  Close the browser.



## DHCP security

You are building a small, isolated network segment to support a new research and development team at 515support. You will configure a new DHCP scope with additional security settings to help protect the segment.

1.  Switch to the [MS1](https://labclient.labondemand.com/Instructions/49acb7a3-7e4c-4a65-ab67-5f7b978f663b?rc=10#) VM.
    
2.  If necessary, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/49acb7a3-7e4c-4a65-ab67-5f7b978f663b?rc=10#), and then unlock the machine using Pa$$w0rd as the password.
    
    > You may close the IIS console if it is still open.
    
3.  In Server Manager, select **Tools**, and then select **DHCP** to open the DHCP management console. Select the **ms1.corp.515support.com** server icon, and then right-click it.
    
4.  Which option is offered in the ms1.corp.515support.com context menu regarding the Active Directory DHCP Authorization status for this server?
    
    Authorize
    
    Unauthorize
    
    Authorization status![Authorized](https://labondemand.blob.core.windows.net/content/lab84054/Screen%20Shot%202020-11-07%20at%204.09.41%20PM.png)
    
5.  Select **IPv4**, and then right-click it and select **New Scope…**.
    
6.  To create a scope for the new R&D segment, use the following responses in the wizard (accept the default settings for any value not specified below). Choose **Next** in each window:
    
    -   Name: Enter Special Project
    -   Start IP address: Enter 10.2.0.10
    -   End IP address: Enter 10.2.0.20
    -   Subnet Mask: Enter 255.255.255.0
    -   Configure DHCP Options: Select **Yes, I want to configure these options now**
    -   Router: Enter 10.2.0.1 and then select **Add**
    -   Activate Scope: Select **Yes, I want to activate this scope now**
7.  Select **Finish** to complete the wizard.
    
8.  Select the **Scope [10.2.0.0] Special Project Scope** node, and then right-click it and select **Display Statistics**.
    
    This information can help you determine if your IP address allocations are as expected. If you see fewer or more than expected, you may have a DHCP incident.
    
9.  How many Total Addresses are available in the new scope?
    
    DHCP statistics.![DHCP statistics](https://labondemand.blob.core.windows.net/content/lab84054/Screen%20Shot%202020-11-07%20at%204.11.41%20PM.png)
    
10.  Close the Statistics box.
    
11.  Expand the **Scope [10.1.0.0] 515 Support Scope**, and then select the **Reservations** node.
    
12.  Select the **10.1.0.10** reservation. In the left-hand pane, right-click **10.1.0.10** and select **Properties**. Copy value from the **MAC address** box and then click **Cancel**.
    
13.  Delete the **LX1 (CentOS)** reservation from the **515 Support Scope**.
    
    > Make sure you have copied the MAC address before you delete this entry! You can paste the address into a Notepad document saved on the Desktop to ensure you have access to the address when needed later in the activity.
    
14.  Select the **Reservations** node in the **Special Project** scope.
    
15.  Right-click the **Reservations** node, and then select **New Reservation**.
    
16.  In the **New Reservation** box, enter the following information:
    
    -   Reservation Name: LX1 (CentOS)
    -   IP address: 10.2.0.15
    -   MAC address: _Paste from the clipboard or Notepad document_
    -   Description: LX1 Consultant - special project
17.  Select **Add**, and then **Close** the New Reservation box.
    
18.  Select the **Filters** node under the **IPv4** node.
    
19.  Select the **Allow** node, and then right-click it and select **New Filter**.
    
20.  Paste in the MAC address value you copied above, and then enter LX1 consultant computer in the **Description** field.
    
    > If for some reason the **LX1** computer's MAC address is no longer on the clipboard to be pasted, you can return to the new scope, select the **Reservations** node, and then copy the MAC address again from the LX1 (CentOS) reservation.
    
21.  Select **Add**, and then **Close**.
    
22.  Right-click **IPv4** and select **Properties**.
    
23.  Select the **Filters** tab, and then check the box for **Enable Allow List**. Select **Apply**.


Exam Results

Score

11 / 11

Passed

Yes

Activities (11)

What is root CA in the Certification Path?

 corp.515support.com

 updates.corp.515support.com

 Microsoft-Root-CA

 515support-CA

```
        Correct
```

Score: 1

What is the validity period for the newly-issued certificate?

 One year.

 Two years.

 Three years.

 Ten years.

 Twenty years.

```
        Correct
```

Score: 1

Why did you remove the HTTP option from the Site Bindings list?

 IIS can only be configured for HTTP or HTTPS, but not both.

 HTTPS includes HTTP connections, so it was redundant.

 You do not wish to permit unsecured HTTP connections to the web server.

 The client computers are not compatible with HTTPS.

```
        Correct
```

Score: 1

Is the HTTP connection successful?

 Yes

 No

```
        Correct
```

Score: 1

Which of the following is stated as the reason for the warning?

 The certificate is expired.

 The web site is corrupted.

 The certificate is revoked.

 The site attempts to identify itself with invalid information.

 The site is on an intranet and therefore cannot use certificates.

```
        Correct
```

Score: 1

If you received a warning from the web browser, why would you accept the certificate anyway?

 You know the certificate is issued by a trusted, internal CA.

 You know the certificate is not actually expired.

 You know the certificate is not actually revoked.

 The certificate has nothing to do with the HTTPS connection.

```
        Correct
```

Score: 1

What status is displayed when you select the padlock icon in the Firefox URL address bar?

 Connection Is Not Secure

 Warning!

 Secure Connection

 Name and password accepted

 Validated web site

```
        Correct
```

Score: 1

Which option is offered in the ms1.corp.515support.com context menu regarding the Active Directory DHCP Authorization status for this server?

 Authorize

 Unauthorize

```
        Correct
```

Score: 1

How many Total Addresses are available in the new scope?

```
        Correct
```

Score: 1

What information is used by DHCP to identify the client computer during the IP address lease attempt.

 Hostname

 IP address

 MAC address

 UUID

 DNS

 Active Directory

```
        Correct
```

Score: 1

Which of the following best describes the purpose of the Allow filter?

 The Allow filter blocks IP address leases to any hosts listed by MAC address.

 The Allow filter permits IP address leases to any hosts listed by MAC address..

 The Allow filter defines the hostnames of computers allowed to lease IP addresses.

 The Allow filter permits the DHCP server to lease IP addresses.

```
        Correct
```

Score: 1
