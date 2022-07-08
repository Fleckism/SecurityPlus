# PT1-Kali
[[ifconfig]]  
vs.  
[[ip]] 
	Commands see IP for full command list
		- a
		- route show
			- default via ### is the ip address of the router
		- neighbor (newer version of arp -a)

[[arp]]
	Commands
		- a
			- The ARP cache shows only machines that have communicated with the local host. To verify whether any other hosts are present, you can perform a "sweep" of the local network. One means of doing this is to use **ping** in a for/next loop. You can also use the **netdiscover** tool bundled with Kali.
#HowDidTheyGetThe24
netdiscover -i eth0 -r 10.1.0.0/24   works as well without the /#
	- Run the following command to scan the network by using **netdiscover**. The results should discover several other hosts connected to the vLOCAL switch.
	- q to exit


# DC1 Windows machine
Using command prompt(admin) or windows terminal (newer version)
- ipconfig 
	- IPv4 is the IP address not the IPv6 abcd:efgh:#:#::#
- pathping ip address

# PT1- Kali
## Use nmap to discover hosts

From a penetration tester or threat actor perspective, network reconnaissance will typically aim to discover the following:

-   Default gateway (the router connecting the subnet to other networks).
    
-   DNS server (used to resolve host names on the network).
    
-   Whether any network directory/authentication and application servers are present.
    
-   Whether any host/client access devices are present.
    
-   Whether any other types of devices (embedded systems or appliances) are present.

Scan the local host with  /# [[nmap]] localhost
![[Pasted image 20220707204532.png]]

Basic network scan using
/# [[nmap]] 10.1.0.0/24 replace with own IP
- This syntax will scan the default port range (1000 ports) on the target
- Run the following command to scan for open ports **20-200** on the network:

``` #bash-notab-nocopy
nmap -p 20-200 10.1.0.0/24
```
- Run the following command to scan for the **twenty** most common ports:
    
    ```bash-notab-nocopy
    nmap --top-ports 20 10.1.0.0/24
    ```
    
- Run the following command to quickly scan the network for hosts that are **up** or **down** on the network:
    
    ```bash-notab-nocopy
    nmap -sn 10.1.0.0/24
    ```

nmap will scan an entire network using -A but this is a timely process, try using -sS then when you see something interesting use -A

  
Run the following command in the **Terminal** to connect to the 10.1.0.1 HTTP server by using cURL:

```bash-notab-nocopy
curl -s -I 10.1.0.1
```

1.  ```bash-notab-nocopy
    firefox http://10.1.0.1
    ```
Web server service information.The web server is a Windows Server. The Microsoft web server service is Internet Information Services (IIS). Though this is not a definitive identification of the web server service, it is probably accurate.

[[Review the application layer port numbers]]
[[Are open ports the same as ports used?  I believe so!]]

