A network security [[appliance]] that monitors and controls incoming and outgoing network traffic.
- A barrier between trusted and untrusted networks
- apply an access control list ([[ACL]]) to filter traffic passing in or out of a network segment. Firewalls can work at layer 3 of the OSI model or higher.
	- The rules in a firewall's ACL are processed **top-to-bottom**.
	- The most **specific** rules are placed at the top.
	- If the firewall does not have a default implicit deny rule, an explicit deny all rule can be added manually to the end of the ACL.
-  **virtual firewalls** most significant role is to support the east-west security and zero-trust microsegmentation design paradigms. They are able to inspect traffic as it passes from host-to-host or between virtual networks, rather than requiring that traffic be routed up to a firewall appliance and back.
- East-west security: host-to-host or between virtual networks  
- [[NGFW]] and [[UTM]] are not suitable for edge devices due to there lower throughput.
	- Deployed for application server traffic. User traffic is often performed by a separate appliance or proxy host.
- Stateful firewall tracks information(aka preserves data)

Five types of firewall include the following:

1.  packet filtering firewall
2.  circuit-level gateway
3.  application-level gateway (aka proxy firewall)
4.  stateful inspection firewall
5.  next-generation firewall (NGFW)