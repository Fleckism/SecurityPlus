# PT1-Kali
## ifconfig
- eth0:
	- [[inet]] Is the IP address
- ip a is a newer ip a tool


ip route show
- If the network uses DHCP it will be configured with a default gateway.
- default via [IP address here]  [[is a gateway a router?]]  [[What is lo:]]  [[what is the / afer the IP]]
[[arp]]  -a
- Displays other hosts local to this subnet (IP here)
- Does arp show you the [[FQDN]] and the [[IP]]
- [[command prompt]]  vs [[PowerShell]]
- [[subnet]]
- [[Is DNS a domain?]]
- nmap -A 10.1.0.254 Lists OS   I believe -A is fingerprinting
-  \ vs / 
- nmap -p 20-200 10.1.0.0/24 ==This command tells about the services and the host==  
- [[Port 25/tcp  smtp]]
- [[Port 143/tcp imap]]
- [[How to get server name from ip]]

- ![[Pasted image 20220507095530.png]]

- ![[Pasted image 20220504214803.png]]
	- What is after the at
ip neighbor is  newer ip tool

The ARP cache shows only machines that have communicated with the local host. To verify whether any other hosts are present, you can perform a "sweep" of the local network. One means of doing this is to use **ping** in a for/next loop. You can also use the **netdiscover** tool bundled with Kali.

### Use nmap to discover hosts

From a penetration tester or threat actor perspective, network reconnaissance will typically aim to discover the following:

-   Default gateway (the router connecting the subnet to other networks).
-   DNS server (used to resolve host names on the network).
-   Whether any network directory/authentication and application servers are present.
-   Whether any host/client access devices are present.
-   Whether any other types of devices (embedded systems or appliances) are present.

- Review the application layer port numbers. Because this is a Linux machine, you can assume that the SSH service is probably running. That would be a great place to start to identify the open port.
- Use the following chart as a reference for nmap options during this activity.

Option: |Explanation: | Example:

(no option) | basic scan | nmap 10.1.0.0

-A | OS, port, service detection | nmap -A 10.1.1.1

-sS | fast scan | nmap -sS 10.1.1.1

-p | specified port numbers | nmap -p 21,23,80 or nmap -p 20-100

--top-ports 20 | scans top 20 common ports (can change the number) | nmap --top-ports 20 10.1.0.0

-sn | scan for up/down hosts | nmap -sn 10.1.0.0

![[Pasted image 20220504220239.png]]
![[Pasted image 20220504220326.png]]
domain is DNS?
nmap -A is fingerprinting
Port 80 is associated with the HTTP application layer protocol. Identify whether the web server service is listening on the server.
1.    
    Run the following command to scan for the **twenty** most common ports:

    nmap --top-ports 20 10.1.0.0/24


## Banner grabbing with curl
- curl -s -I 10.1.0.1   [[Change font to show capital I differently]]
- Web server service information.The web server is a Windows Server. The Microsoft web server service is Internet Information Services (IIS). Though this is not a definitive identification of the web server service, it is probably accurate.

Query DNS
- DNS provides name resolution to internal networks as well as the Internet. DNS is used any time a user or application refers to a host by name. DNS queries name records to find the IP address associated with a hostname or fully qualified domain name. These name records can also reveal information about how a network is configured. In this task, you will gather DNS information by using the **dig** utility.

1.  Run the dig command in the **Terminal** to perform a reverse lookup on the default gateway.
    
    ```bash-notab-nocopy
    dig -x 10.1.0.254
    ```


What is the IP address of the DNS server that answers the query? the number you added after dig???


```bash-notab-nocopy
dig soa corp.515support.com
```

The SOA records.![SOA records returned by dig tool](https://labondemand.blob.core.windows.net/content/lab84034/0r37jijo.png)

The query returns the FQDN of the DNS server responsible for the domain.
==Of course it does I inputed the FQDN==





## Comprehensive questions

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following answers correctly summarizes the steps in this activity?
    
    Identified the Kali Linux and Windows servers, performed basic scans of the network, identified hosts and services, used banner grabbing to identify services, gathered more DNS information.
    
    
    
2.  Which of the following answers best identifies how an administrator might use the information gathered during this activity?
    
    
    To verify expected network and server configurations.

3.  Which of the following answers best identifies how an attacker might use the information gathered during this activity? (Select three)
    
    
    To decide what servers to attack
    
    To check for old services that may be unpatched.
    
    To map the network in preparation for an attack.
    