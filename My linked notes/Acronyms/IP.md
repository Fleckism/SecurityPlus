**Internet #protocol **
- Provides the addressing mechanism for logical networks and subnets
- IPv4
	- 32-bit
	- Dotted decimal notation
	-  172.16.1.101/16, ?  Is this correct
- IPv6
	- 128-bit
	- Hex notation
	- 2001:db8::abc:0:def0:1234. 

The ==ip command== is a more powerful command in Linux and gives options for managing routes as well as the local interface configuration


32-bit IPv4 address is written in dotted decimal notation, with either a network suffix or subnet mask to divide the address into network ID and host ID portions. **For example, in the IP address 172.16.1.101/16, the /16 suffix indicates that the first half of the address (172.16.0.0) is the network ID, while the remainder uniquely identifies a host on that network. This /16 suffix can also be written as a subnet mask in the form 255.255.0.0.**

Networks also use 128-bit IPv6 addressing. IPv6 addresses are written using hex notation in the general format: 2001:db8::abc:0:def0:1234. In IPv6, the last 64-bits are fixed as the host's interface ID. The first 64-bits contain network information in a set hierarchy. For example, an ISP's routers can use the first 48-bits to determine where the network is hosted on the global Internet. Within that network, the site administrator can use the 16 bits remaining (out of 64) to divide the local network into subnets.