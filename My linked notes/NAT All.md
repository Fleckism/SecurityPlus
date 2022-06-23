# A Quick Look at NAT64 and NAT46

**Introduction**

In the best of worlds we would all be using native IPv6 now, or at least dual  
stack. That is not the case however and IPv4 will be around for a long time yet.  
During that time that both protocols exist, there will be a need to translate  
between the two, like it or not.

**Different Types of NAT**

Before we begin, let’s define some different forms of NAT:

NAT44 – NAT from IPv4 to IPv4  
NAT66 – NAT from IPv6 to IPv6  
NAT46 – NAT from IPv4 to IPv6  
NAT64 – NAT from IPv6 to IPv4

The most commonly used type is definitely NAT44 but here we will focus on translating  
between IPv4 and IPv6.

**NAT64**

There are two different forms of NAT64, stateless and statefull. The stateless version  
maps the IPv4 address into an IPv6 prefix. As the name implies, it keeps no state.  
It does not save any IP addresses since every v4 address maps to one v6 address.  
Here is a comparison of stateless and statefull NAT64:

[![Stateless_vs_statefull](http://195.42.105.30/wp-content/uploads/2014/08/stateless_vs_statefull.png)](http://195.42.105.30/wp-content/uploads/2014/08/stateless_vs_statefull.png)

**DNS64**

When resolving names to numbers in IPv4, A records are used. When doing the same  
in IPv6, AAAA records are used. When using NAT64, the device doing the translation  
will translate between A and AAAA records. The function of DNS64 will not be  
described further in this post.

**Documentation**

The configuration guides at Cisco.com are pretty poorly written and there is  
not much else to find on configuring NAT64 on ASA. That’s always one of my goals  
with a blog post, to learn a topic and to help spread knowledge into the networking  
community.

**The Lab**

To demonstrate NAT64, the following topology is used:

[![NAT64_1](http://195.42.105.30/wp-content/uploads/2014/08/nat64_1.png)](http://195.42.105.30/wp-content/uploads/2014/08/nat64_1.png)

The goal is for IOS9 to source traffic from its loopback 2001:db8:0:9::9 to  
IOS7 with the IP address 203.0.113.2. The routers have some basic configuration  
with IP addresses on the interfaces and static routing.

**IOS7:**

interface GigabitEthernet0/0
 ip address 203.0.113.2 255.255.255.248
!
ip route 0.0.0.0 0.0.0.0 203.0.113.1

**IOS8:**

ipv6 unicast-routing
!
interface GigabitEthernet0/0
 ipv6 address 2001:DB8::2/64
!
interface GigabitEthernet0/1
 ipv6 address 2001:DB8:0:1::2/64
!
ipv6 route 2001:DB8:0:9::9/128 2001:DB8:0:1::1
ipv6 route ::/0 2001:DB8::1

**IOS9:**

ipv6 unicast-routing
interface Loopback0
 ipv6 address 2001:DB8:0:9::9/64
!
interface GigabitEthernet0/0
 ipv6 address 2001:DB8:0:1::1/64
!
ipv6 route ::/0 2001:DB8:0:1::2

The ASA is the device that will be doing the NAT64. It has one IPv4 interface and  
one IPv6 interface. It starts with the following configuration:

**ASA1:**

interface GigabitEthernet0/0
 nameif inside
 security-level 100
 ip address 203.0.113.1 255.255.255.248 
!
interface GigabitEthernet0/1
 nameif outside
 security-level 0
 no ip address
 ipv6 address 2001:db8::1/64
!
access-list outside extended permit icmp6 any any 
!
ipv6 route outside 2001:db8:0:9::9/128 2001:db8::2

In newer versions of ASA code, unified ACL is supported. That means we can have  
both IPv4 and IPv6 in the same ACL. In my ACL I am allowing ICMPv6 to come in  
on the “outside” interface.

To translate between IPv6 and IPv4, NAT must be configured. Both object NAT and  
twice NAT is supported but I prefer twice NAT, so that is what I will configure.

When pinging from IOS9, we need to define an address that will represent IOS7 (IPv6).  
This is the destination of the packet. The source address of IOS9 needs to be translated  
to an IPv4 address as well. This picture will show the flow of the traffic:

[![Traffic_flow](http://195.42.105.30/wp-content/uploads/2014/08/traffic_flow.png)](http://195.42.105.30/wp-content/uploads/2014/08/traffic_flow.png)

Time to configure the ASA. The traffic flow is coming in on the interface “outside”  
and exiting on interface “inside”. We need to define network objects, try to name  
them properly because otherwise it can be confusing to understand the traffic flow.

object network REALv6_OUTSIDE
host 2001:db8:0:9::9
object network MAPPED_IPv4_INSIDE
host 192.0.2.1
object network MAPPED_IPv6_OUTSIDE
host 2001:db8:0:a::2
object network REALv4_INSIDE
host 203.0.113.2
nat (outside,inside) source static REALv6_OUTSIDE MAPPED_IPv4_INSIDE destination 
static MAPPED_IPv6_OUTSIDE REALv4_INSIDE net-to-net

The syntax can be a bit confusing so let’s take a closer look:

REALv6_OUTSIDE – This is the source IP(v6) of IOS9  
MAPPED_IPv4_INSIDE – This is what IOS9 gets translated to on the inside  
MAPPED_IPv6_OUTSIDE – This is the destination IOS9 is sending traffic to  
REALv4_INSIDE – This is what the destination gets translated to on the inside

To test our setup, we will ping from IOS9:

IOS9#ping 2001:DB8:0:A::2 so lo0
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 2001:DB8:0:A::2, timeout is 2 seconds:
Packet sent with a source address of 2001:DB8:0:9::9
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/5/11 ms

IOS7#debug ip icmp
ICMP packet debugging is on
IOS7#
*Aug 26 07:28:27.786: ICMP: echo reply sent, src 203.0.113.2, dst 192.0.2.1, topology BASE, dscp 0 topoid 0
*Aug 26 07:28:27.796: ICMP: echo reply sent, src 203.0.113.2, dst 192.0.2.1, topology BASE, dscp 0 topoid 0
*Aug 26 07:28:27.802: ICMP: echo reply sent, src 203.0.113.2, dst 192.0.2.1, topology BASE, dscp 0 topoid 0
*Aug 26 07:28:27.810: ICMP: echo reply sent, src 203.0.113.2, dst 192.0.2.1, topology BASE, dscp 0 topoid 0
*Aug 26 07:28:27.811: ICMP: echo reply sent, src 203.0.113.2, dst 192.0.2.1, topology BASE, dscp 0 topoid 0

That worked! Let’s take a look at the XLATE table:

ASA1#  show xlate
2 in use, 2 most used
Flags: D - DNS, e - extended, I - identity, i - dynamic, r - portmap,
       s - static, T - twice, N - net-to-net
NAT from outside:2001:db8:0:9::9/128 to inside:192.0.2.1
    flags sTN idle 0:01:04 timeout 0:00:00
NAT from inside:203.0.113.2 to outside:2001:db8:0:a::2/128
    flags sTN idle 0:01:04 timeout 0:00:00

That was ICMP. How about TCP? We need to allow TCP through the firewall.

ASA1(config)# access-list outside permit tcp any any

IOS7(config)#username nat password nat
IOS7(config)#line vty 0 4
IOS7(config-line)#login local

IOS9#telnet 2001:DB8:0:A::2 /source-interface lo0
Trying 2001:DB8:0:A::2 ... Open

User Access Verification

Username: 

No matter what you think of NAT, that is pretty cool!

ASA1# show conn
1 in use, 4 most used

TCP outside  192.0.2.1(2001:db8:0:9::9):16809 inside  203.0.113.2:23, idle 0:00:43, bytes 2805, flags UIOB

ASA1# show nat det
Manual NAT Policies (Section 1)
1 (outside) to (inside) source static REALv6_OUTSIDE MAPPED_IPv4_INSIDE   destination static MAPPED_IPv6_OUTSIDE REALv4_INSIDE net-to-net
    translate_hits = 6, untranslate_hits = 24
    Source - Origin: 2001:db8:0:9::9/128, Translated: 192.0.2.1/32
    Destination - Origin: 2001:db8:0:a::2/128, Translated: 203.0.113.2/32

This was NAT64 in action. With our NAT we were doing one to one translation  
between IPv6 and IPv4. If IPv4 addresses are scarce, we can define a NAT  
pool and translate to that.

ASA1(config)# object network IPv4_POOL
ASA1(config-network-object)# range 198.51.100.1 198.51.100.5
ASA1(config-network-object)# exit
ASA1(config)# nat (outside,inside) source dynamic REALv6_OUTSIDE pat-pool IPv4_POOL
destination static MAPPED_IPv6_OUTSIDE REALv4_INSIDE net-to-net

IOS9#telnet 2001:db8:0:a::2 /source-interface lo0
Trying 2001:DB8:0:A::2 ... Open

User Access Verification

Username: 

ASA1# show xlate
2 in use, 3 most used
Flags: D - DNS, e - extended, I - identity, i - dynamic, r - portmap,
       s - static, T - twice, N - net-to-net
NAT from inside:203.0.113.2 to outside:2001:db8:0:a::2/128
    flags sTN idle 0:00:42 timeout 0:00:00

TCP PAT from outside:2001:db8:0:9::9/43376 to inside:198.51.100.1/43376 flags ri idle 0:00:42 timeout 0:00:30
ASA1# show nat detail
Manual NAT Policies (Section 1)
1 (outside) to (inside) source dynamic REALv6_OUTSIDE pat-pool IPv4_POOL  destination static MAPPED_IPv6_OUTSIDE REALv4_INSIDE net-to-net
    translate_hits = 9, untranslate_hits = 10
    Source - Origin: 2001:db8:0:9::9/128, Translated (PAT): 198.51.100.1-198.51.100.5
    Destination - Origin: 2001:db8:0:a::2/128, Translated: 203.0.113.2/32

ASA1# show conn
1 in use, 4 most used

TCP outside  198.51.100.1(2001:db8:0:9::9):20135 inside  203.0.113.2:23, idle 0:00:01, bytes 1382, flags UIOB 

The source got translated to 198.51.100.1 through PAT.

**Conclusion**

IPv6 is here to stay, but so is also IPv4 for a long time to come. Personal  
opinions aside, we may need to translate between IPv6 and IPv4 for a time to  
come. Knowing how to configure NAT64 is just another tool in our belt.