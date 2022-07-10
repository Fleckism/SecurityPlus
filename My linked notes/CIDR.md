(**C**lassless **I**nter-**D**omain **R**outing) An expansion of the original IPv4 addressing system that allows for a more efficient allocation of addresses. The original class-based method used fixed fields for network IDs, which was wasteful. For example, Class A and B networks can address 16 million and 65 thousand hosts respectively, and most organizations given those addresses never had intentions of putting that many computers on the Internet. See [IP address](https://www.pcmag.com/encyclopedia/term/ip-address).

**From Fixed to Variable**

CIDR changed the fixed fields into variable-length fields, allowing addresses to be assigned with finer granularity. The CIDR IP address includes a number that tells how the address is split between networks and hosts. For example, in the CIDR address 204.12.01.42/18 the /18 indicates that the first 18 bits are used for network ID and the remaining 14 (there are 32 bits in an IPv4 address) are used for host ID (see [supernetting](https://www.pcmag.com/encyclopedia/term/supernetting)).

**Routing Is More Manageable**

Blocks of CIDR addresses have been given to ISPs, who in turn disseminate them to their customers, which may be end users or smaller ISPs. CIDR reduces the burden on Internet routers by aggregating routes so that one IP address represents all the thousands of customers serviced by a single ISP. All packets sent to any of those customer addresses are routed via the one IP address, requiring only one entry in the routing table. In 1990, there were about 2,000 routes on the Internet. By 1995, there were more than 30,000, and without CIDR, the core routers on the Internet backbone would have been overloaded. See [private IP address](https://www.pcmag.com/encyclopedia/term/private-ip-address).

**CIDR Prefixes**

The following table shows the number of hosts allotted to each CIDR block. Note that the CIDR number /13, /14, etc. is called the CIDR "prefix" even though it is written at the end of the IP address. It is called the prefix because it represents the number of bits in the network ID, and the network ID is the "first" part of the IP address.

 **CIDR      Number of**
**Prefix    Hosts**

    /13       524,288
    /14       262,144
    /15       131,072
     /16        65,536
     /17        32,768
     /18        16,384
     /19         8,192
     /20         4,096
     /21         2,048
     /22         1,024
     /23           512
     /24           256
     /25           128
     /26            64
     /27            32

