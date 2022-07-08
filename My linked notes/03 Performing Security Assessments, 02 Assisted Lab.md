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


## Use nmap to discover hosts

From a penetration tester or threat actor perspective, network reconnaissance will typically aim to discover the following:

-   Default gateway (the router connecting the subnet to other networks).
    
-   DNS server (used to resolve host names on the network).
    
-   Whether any network directory/authentication and application servers are present.
    
-   Whether any host/client access devices are present.
    
-   Whether any other types of devices (embedded systems or appliances) are present.

Scan the local host with  /# [[nmap]] localhost
![[Pasted image 20220707204532.png]]
Basic network scan using /# nmap 10.1.0.0/24 replace with own IP
- This syntax will scan the default port range (1000 ports) on the target

[[Review the application layer port numbers]]
[[Are open ports the same as ports used?  I believe so!]]

