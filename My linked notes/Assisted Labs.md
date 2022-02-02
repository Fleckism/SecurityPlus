## The Windows network contains a domain controller and member server both running Windows Server 2016.

-   [DC1](https://labclient.labondemand.com/Instructions/e32cbc8a-ace3-4dca-a698-ba8475de1963?rc=10#) is configured as the network's domain controller (DC). Normally the DC role should not be combined with other roles, but to minimize the number of VMs you have to run, this machine is also configured as a DNS server and CA (certificate authority) server and will be used for a number of other services and configurations. This VM is configured with a static IP address (10.1.0.1).
    
-   [MS1](https://labclient.labondemand.com/Instructions/e32cbc8a-ace3-4dca-a698-ba8475de1963?rc=10#) is configured as a member server for running applications. It runs a DHCP service to perform auto addressing for clients connecting to the network. It has the web server IIS and the email server hMail installed. This VM is also configured with a static IP address (10.1.0.2).
    

You will usually use the username 515support\Administrator to log on to the Windows PCs. Each user account uses the password Pa$$w0rd (awful security practice, but it makes the activities simpler for you to complete).