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
- **web application firewall** ([[WAF]]) is designed specifically to protect 
	- software running on web servers and back-end databases from
		- Code injection  
		- DoS attacks
	- Output can be logged
	- Can be a appliance or plug in software 
	
**Network operating system** ([[NOS]]) firewall—a software-based firewall running under a network server OS, such as Windows or Linux. The server would function as a gateway or proxy for a network segment.
Five types of firewall include the following:

1.  packet filtering firewall
2.  circuit-level gateway
3.  application-level gateway (aka proxy firewall)
4.  stateful inspection firewall
5.  next-generation firewall (NGFW)

The primary method for keeping a computer secure from intruders. A firewall allows or blocks traffic into and out of a private network or the user's computer. Firewalls are widely used to give users secure access to the Internet as well as to separate a company's public Web server from its internal network. Firewalls are also used to keep internal network segments secure; for example, the accounting network might be vulnerable to snooping from within the enterprise.

In the home, a personal firewall typically comes with or is installed in the user's computer (see [Windows Firewall](https://www.pcmag.com/encyclopedia/term/windows-firewall)). Personal firewalls may also detect outbound traffic to guard against spyware, which could be sending your surfing habits to a website. They alert you when software makes an outbound request for the first time (see [spyware](https://www.pcmag.com/encyclopedia/term/spyware)).

In the organization, a firewall can be a stand-alone machine (see [firewall appliance](https://www.pcmag.com/encyclopedia/term/firewall-appliance)) or software in a router or server. It can be as simple as a single router that filters out unwanted packets, or it may comprise a combination of routers and servers each performing some type of firewall processing. For more about the various firewall techniques, see [firewall methods](https://www.pcmag.com/encyclopedia/term/firewall-methods). See [WAF](https://www.pcmag.com/encyclopedia/term/waf).