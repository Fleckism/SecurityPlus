# Assisted Lab 18: Implementing Secure Network Addressing Services

## Scenario

Attacks against core network services such as DHCP and DNS can represent powerful exploits. In this activity, you will display and confirm network time services in Active Directory, configure Dynamic Host Configuration Protocol (DHCP) service settings, and test for secure zone transfer settings in Domain Name System (DNS).

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   1.4 Given a scenario, analyze potential indicators associated with network attacks.
    
-   3.1 Given a scenario, implement secure protocols.


## Time management

Time synchronization is critical to a network. Services such as Kerberos (authentication) use time as part of the authentication criteria, and scheduled events such as backups rely on accurate time settings. You will confirm time configurations in an Active Directory environment as part of implementing network security.

1.  On the [MS1]
    
2.  Select the **Start** menu, right-click **Windows PowerShell** and select **Run as Administrator**. When prompted, select **Yes** in the UAC dialog box.
    
3.  (Windows powerShell) One Domain Controller (directory services server) per Active Directory domain holds the role of PDC Emulator. One aspect of this role is time management. Run the following commands to display which server is the role holder:
    
    ```
    netdom query fsmo
    ```
    
    FSMO roles.![The netdom command](https://labondemand.blob.core.windows.net/content/lab84050/Screen%20Shot%202020-11-07%20at%205.04.02%20PM.png)
    
4.  Which server is the master time server for the domain? (Note: the time server role is part of the **PDCemulator role)**
    

    
    dc1.corp.515support.com
    
5.  Display the time server used by MS1 to get receive the accurate domain time (this command takes several seconds to execute):
    
    ```
    w32tm /monitor
    ```
    
6.  With which server does MS1 synchronize to get the correct domain time?
    
    dc1.corp.515support.com
    
   
    
7.  What IP address and port number is displayed as the time source? (Note: the format is IP:Port)
    
   *** PDC *** 10.1.0.1:123
    

    
8.  Close the **Windows PowerShell** console.
    
9.  Switch to [PT1-Kali
    
10.  Open a **Terminal**, and then run the following command to scan the 10.1.0.1 server for the default NTP port number:
    
    ```bash-notab-nocopy
    nmap -p 123 10.1.0.1
    ```
    
11.  In what state is port 123?
    

    STATE  under line STATE
    Filtered

Filtered ports are managed by a firewall and do not permit Nmap to discover whether they are open or closed.


## DHCP configuration

The Dynamic Host Configuration Protoc0l (DHCP) service permits clients to lease an IP configuration, simplifying client management. The configuration usually includes IP address, subnet mask, router (default gateway), DNS name servers, etc. If any of this information is spoofed or unavailable, clients are at risk for losing access to data or accessing compromised services. you will configure DHCP Failover to ensure the service remains available.

1.  Select the [MS1](https://labclient.labondemand.com/Instructions/dcc179e3-c0e4-4cc9-9c99-2ea84020a6cc?rc=10#) VM. If necessary, sign back in by sending [Ctrl+Alt+Delete]
    
2.  From Server Manager, select **Tools > DHCP** menu.
    
3.  Select the **MS1.corp.515support.com** node, and then right-click it to observe the context menu and answer the following question:
    
4.  Based on the information in the context menu, what is the server's authorization status in Active Directory?
    
    ==Unauthorize, indicating the server is already authorized.==
    
5.  Switch to [DC1
6.  From Server Manager, select **Add roles and features**.
    
7.  Complete the wizard to add the **DHCP Server** role, using the defaults.
    
8.  Wait for the installation of DHCP to complete - about one minute. Select **Close**.
    
9.  Switch back to the [MS1](https://labclient.labondemand.com/Instructions/dcc179e3-c0e4-4cc9-9c99-2ea84020a6cc?rc=10#) virtual machine.
    
10.  In the DHCP console, expand the **IPv4** node and select the **10.1.0.0** scope.
    
11.  Right-click the **10.1.0.0** scope, and then select **Configure Failover**
    
12.  Use the following values to configure DHCP failover:
    
    -   Partner Server: 10.1.0.1
    -   Shared secret: Pa$$w0rd
    -   Accept all other defaults
13.  Switch back to [DC1](https://labclient.labondemand.com/Instructions/dcc179e3-c0e4-4cc9-9c99-2ea84020a6cc?rc=10#).
    
14.  From Server Manager, select **Tools > DHCP**. Select the **DC1.corp.515support.com** node, and then right-click it and select **Authorize** to register the DHCP service with Active Directory.
    
    Active Directory authorization helps prevent rogue DHCP server in Windows network environments.
    
    DHCP on DC1![Screen Shot 2020-11-07 at 5.09.10 PM.png](https://labondemand.blob.core.windows.net/content/lab84050/Screen%20Shot%202020-11-07%20at%205.09.10%20PM.png)
15.  Expand the nodes in the DHCP console to display the 10.1.0.0 scope.
    
    The scope was automatically replicated as part of the DHCP Failover configuration.
    
16.  Close the **DHCP** console.
    
    > You would not normally configure the DHCP service on an Active Directory Domain Controller. The lab environment is configured this way because we can only run a limited number of VMs.
    
17.  Switch to [MS1](https://labclient.labondemand.com/Instructions/dcc179e3-c0e4-4cc9-9c99-2ea84020a6cc?rc=10#), right-click the IPv4 node, and then select **Properties**. Use the **Advanced** tab to answer the following question:
    
18.  Which of the following answers displays the default location of the DHCP log files?
    
    C:\Windows\system32\dhcp


## DNS

DNS name resolution is one of the most essential network services. DNS zones contain hostname-to-IP address records (along with other record types). You will confirm that zone transfer settings are secure.

1.  Switch to [DC1]
    
2.  From Server Manager, select **Tools > DNS**.
    
    > DNS is another service that is usually not installed on a Domain Controller.
    
3.  Expand **DC1 > Forward Lookup Zones** and select the **corp.515support.com** node. Right-click it and select **Properties**.
    
4.  Select the **Zone Transfers** tab.
    
5.  What is current zone transfer configuration?
    
    Allow zone transfers: To any server
    
    
    Zone transfer configuration![Zone Transfers tab](https://labondemand.blob.core.windows.net/content/lab84050/Screen%20Shot%202020-11-07%20at%205.11.53%20PM.png)
    
6.  Leave the properties dialog open.
    
7.  Switch to the [PT1-Kali]
    
8.  In a terminal window, run an Nmap port scan for port 53 against the DC1 server (10.1.0.1):
    
    ```bash-notab-nocopy
    nmap -p 53 10.1.0.1
    ```
    
9.  What is the state of 53?

    
    Open
    
10.  Run the following command to request a zone transfer from the DC1 DNS server to the PT1-Kali penetration testing workstation:
    
    ```bash-notab-nocopy
    dig axfr @dc1.corp.515support.com corp.515support.com
    ```
    
    Zone transfer attempt![Zone transfer attempt](https://labondemand.blob.core.windows.net/content/lab84050/Screen%20Shot%202020-11-07%20at%205.14.39%20PM.png)
    
11.  Was the zone transfer attempt successful?
    
    Yes
    
    No
    
12.  Switch back to the [DC1]
    
13.  In the (Tools ->) DNS console, adjust the server properties to clear the check box for **Allow zone transfers** to prevent any zone transfers. Select **Apply**.
    
    In this lab environment, there is only one DNS server. A single DNS server is a single point of failure, so in a production environment there will usually be at least two DNS servers. In that case, you would explicitly list the other DNS server(s) in the zone properties.
    
14.  Switch back to the [PT1-Kali](https://labclient.labondemand.com/Instructions/dcc179e3-c0e4-4cc9-9c99-2ea84020a6cc?rc=10#) virtual machine, and run the original dig command.
    
    > Don't forget to use the **UP ARROW** key to repeat recent Linux commands. You should be able to repeat the command you ran earlier without having to re-type it.
  
15.  Does the zone transfer work this time?
    
    
    No
    
16.  Close the **DNS** console.
17.   #NoIdeaWhatImLookingAt



## Comprehensive questions

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following answers best describes why time management is important in an Active Directory network?
    
    Many services depend on accurate time synchronization.
    
    Correct
    
2.  What kind of DHCP attack does Active Directory Authorization help to mitigate?
    
    Rogue DHCP server

    Correct
    
3.  Which of the following answers best describes how DNS zone transfers might be used against a network?

    Zone information provides name and IP address information for the entire zone.

    
    Correct