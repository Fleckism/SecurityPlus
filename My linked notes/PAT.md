(**P**ort **A**ddress **T**ranslation) The most common way network address translation is implemented (see [NAT](https://www.pcmag.com/encyclopedia/term/nat)). Also called "NAT overloading," "network address port translation" (NAPT) and "NAT/PAT."

PAT assigns a different TCP port number to each client session with a server on the Internet. When responses come back from that server, the source port number becomes the destination port number and determines which user to route the packets to. It also validates that the incoming packets were indeed requested. See [NAT traversal](https://www.pcmag.com/encyclopedia/term/nat-traversal), [UDP hole punching](https://www.pcmag.com/encyclopedia/term/udp-hole-punching), [private IP address](https://www.pcmag.com/encyclopedia/term/private-ip-address), [RSIP](https://www.pcmag.com/encyclopedia/term/rsip) and [proxy server](https://www.pcmag.com/encyclopedia/term/proxy-server).

![NAT.GIF](https://i.pcmag.com/imagery/encyclopedia-terms/pat-nat.fit_lim.size_640x.gif)

**NAT/PAT**

By using a different port number for each user, the NAT device knows which client PC to route the incoming packets to. See [TCP/IP port](https://www.pcmag.com/encyclopedia/term/tcpip-port).