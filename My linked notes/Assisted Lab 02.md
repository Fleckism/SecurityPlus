# PT1-Kali
ifconfig
- [[inet]] Is the IP address
- ip a is a newer ip a tool
ip route show
- If the network uses DHCP it will be configured with a default gateway.
- default via [IP address here]
arp  -a
- Displays other hosts local to this subnet (IP here)
- ![[Pasted image 20220504214803.png]]
	- What is after the at
ip neighbor is  newer ip tool

## Use nmap to discover hosts

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
    