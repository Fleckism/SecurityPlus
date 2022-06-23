(**I**nternet **P**rotocol **CONFIG**uration) A command line utility ( #tool ) that is used to display and manage the IP address assigned to the machine. In Windows, typing **ipconfig** without any parameters displays the computer's currently assigned IP, subnet mask and default gateway addresses.

In the Mac, **ipconfig getifaddr en0** and **ipconfig getifaddr en1** display the Wi-Fi and Ethernet IP addresses respectively (getifaddr stands for Get Interface Address). See [IFCONFIG](https://www.pcmag.com/encyclopedia/term/ifconfig), [NSLOOKUP](https://www.pcmag.com/encyclopedia/term/nslookup) and [netstat](https://www.pcmag.com/encyclopedia/term/netstat).

 **IPCONFIG COMMANDS IN WINDOWS**

 **Reporting      Displays**

 no switch      IP, subnet mask & default
                 gateway addresses

 /all           the above +
                 hostname, MAC address,
                 DNS server addresses, etc.

 /displaydns    contents of DNS cache

 /showclassid   all DHCP class IDs
                 for adapter


 **Management     Action**

 /release       release IP address

 /renew         renew IP address

 /flushdns      purge DNS cache

 /registerdns   refresh leases & 
                 reregister DNS

 /setclassid    update DHCP class ID

The ipconfig command is used to report the configuration assigned to the network adapter in Windows.

show the configuration assigned to network interface(s) in Windows, including the hardware or media access control (MAC) address, IPv4 and IPv6 addresses, **default gateway, and whether the address is static or assigned by DHCP. If the address is DHCP-assigned, the output also shows the address of the DHCP server that provided the lease (To detect spoofing). 

ipconfig returns information about local interfaces, such as IP address and netmask, default gateway, DNS servers, static or DHCP-assisgned configuration, MAC addresses, and host name.