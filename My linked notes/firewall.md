A network security [[appliance]] that monitors and controls incoming and outgoing network traffic.
- A barrier between trusted and untrusted networks
- apply an access control list ([[ACL]]) to filter traffic passing in or out of a network segment. Firewalls can work at layer 3 of the OSI model or higher.
	- The rules in a firewall's ACL are processed **top-to-bottom**.
	- The most **specific** rules are placed at the top.
	- If the firewall does not have a default implicit deny rule, an explicit deny all rule can be added manually to the end of the ACL.