#zFleck 
The Windows network contains a domain controller and member server both running Windows Server 2016.

-   [DC1](https://labclient.labondemand.com/Instructions/64bf2042-0338-4a1c-934f-ba959d1b0d1c?rc=10#) is configured as the network's domain controller (DC). Normally the DC role should not be combined with other roles, but to minimize the number of VMs you have to run, this machine is also configured as a DNS server and CA (certificate authority) server and will be used for a number of other services and configurations. This VM is configured with a static IP address (10.1.0.1).
    
-   [MS1](https://labclient.labondemand.com/Instructions/64bf2042-0338-4a1c-934f-ba959d1b0d1c?rc=10#) is configured as a member server for running applications. It runs a DHCP service to perform auto addressing for clients connecting to the network. It has the web server IIS and the email server hMail installed. This VM is also configured with a static IP address (10.1.0.2).

## LookUp
- DHCP
- UAC prompt
- Kali VM 
	- Dash
- security appliance
[[PowerShell]]

## Identify Appliance VMs

In the activities, you will use various security appliance VMs to implement network routing and security functions. These appliance VMs are as follows:
[RT1-LOCAL](https://labclient.labondemand.com/Instructions/64bf2042-0338-4a1c-934f-ba959d1b0d1c?rc=10#) | [RT2-ISP](https://labclient.labondemand.com/Instructions/64bf2042-0338-4a1c-934f-ba959d1b0d1c?rc=10#) | [RT3-INT](https://labclient.labondemand.com/Instructions/64bf2042-0338-4a1c-934f-ba959d1b0d1c?rc=10#) VMs — these VMs are running the VyOS Linux distribution ([vyos.io](http://vyos.io/)) and are used to route traffic between the different subnets configured on the various virtual switches. You will be discovering more about the network topology in later activities so we will not explain more here.

-   UTM1 — this is a UTM security appliance created by Netgate ([pfsense.org](https://pfsense.org/)) from the OpenBSD version of UNIX. pfSense is operated using a web GUI (http://10.1.0.254). The username is admin and the password is Pa$$w0rd. This VM is not included in this orientation lab.
    
-   SIEM1 — Security Onion ([securityonion.net](https://securityonion.net/)) is a network security monitoring (NSM) tool. It provides various GUI and web interfaces to its intrusion detection and incident monitoring tools. The username is administrator and the password is Pa$$w0rd. This VM is not included in this orientation lab.
## Identify Linux Server VMs

There are also two Linux servers:

-   LAMP is built on the Ubuntu Server distribution ([ubuntu.com](https://ubuntu.com/)) and runs the familiar Linux, Apache, MySQL, and PHP functions of a web server. LAMP is also installed with email and DNS servers. As a server distribution, this VM has no GUI shell. The username is lamp and the password is Pa$$w0rd. This VM is not included in this orientation lab.
    
-   [LX1](https://labclient.labondemand.com/Instructions/64bf2042-0338-4a1c-934f-ba959d1b0d1c?rc=10#) is a CentOS Linux distribution ([centos.org](https://www.centos.org/)) that has been installed with intentionally vulnerable web services. This VM is usually positioned on the local network with the Windows VMs and has a DHCP reservation for the address 10.1.0.10. The username is centos and the password is P