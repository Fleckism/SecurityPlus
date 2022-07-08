**Address Resolution #Protocol**  is Windows network command-line utility 
- Used to obtain a node's physical address in the traditional IP address system IPv4
- Returns the layer 2 address
- 
- ARP **poisoning** attack uses a packet crafter, such as Ettercap, to broadcast **unsolicited ARP reply packets**. then using [[MITM]] attacker intercepts packets Dsniff can also be used
- 

- A client station broadcasts an ARP request onto the network with the IP address of the target node it wishes to communicate with, and the node with that IP address responds by sending back its physical MAC address so that packets can be transmitted. ARP returns the layer 2 address for a layer 3 address. See [NDP](https://www.pcmag.com/encyclopedia/term/ndp), [ARP cache](https://www.pcmag.com/encyclopedia/term/arp-cache), [ARP cache poisoning](https://www.pcmag.com/encyclopedia/term/arp-cache-poisoning), [RARP](https://www.pcmag.com/encyclopedia/term/rarp) and [TCP/IP abc's](https://www.pcmag.com/encyclopedia/term/tcpip-abcs).

You must recover the contents of the ARP cache as vital evidence of a man-in-the-middle attack. Should you shut down the PC and image the hard drive to preserve it?

No, the ARP cache is stored in memory and will be discarded when the computer is powered off. You can either dump the system memory or run the arp utility and make a screenshot. In either case, make sure that you record the process and explain your actions.