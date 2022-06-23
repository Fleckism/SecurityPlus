A proxy server is a computer system or router that functions as a relay between client and server. It helps prevent an attacker from invading a private network and is one of several tools used to build a firewall.

The word proxy means "to act on behalf of another," and a proxy server acts on behalf of the user. All requests to the Internet go to the proxy server first, which evaluates the request and forwards it to the Internet. Likewise, responses come back to the proxy server and then to the user.

![VPN2.JPG](https://i.pcmag.com/imagery/encyclopedia-terms/proxy-server-vpn2.fit_lim.size_640x.jpg)

**Proxy Servers Hide the IP Address**

Like a virtual private network (VPN), a proxy server hides the user's IP address when accessing the Internet. Depending on the protocol used, it may or may not encrypt the transmission. See [VPN](https://www.pcmag.com/encyclopedia/term/vpn) and [TLS](https://www.pcmag.com/encyclopedia/term/tls).

**Address Translation and Caching**

The proxy server is a dual-homed host with two network IP addresses. The address on the outbound side is the one the Internet sees. Proxies are often used in conjunction with network address translation (NAT), which hides the users' IP addresses on the internal network. Proxy servers may also cache Web pages so that the next request for that page can be retrieved much faster. See [NAT](https://www.pcmag.com/encyclopedia/term/nat) and [proxy cache](https://www.pcmag.com/encyclopedia/term/proxy-cache).

**Other Proxies**

Anonymous proxy servers let users surf the Web and keep their IP address private (see [anonymous proxy](https://www.pcmag.com/encyclopedia/term/anonymous-proxy)). Although not specifically called proxies, Internet email (SMTP) and the Usenet new system (NNTP) are somewhat similar because messages are relayed from sender to recipient. See [firewall](https://www.pcmag.com/encyclopedia/term/firewall).

**Application Level and Circuit Level**

"Application-level" proxies or "application-level gateways" are dedicated to specific content such as HTTP (Web) and FTP (file transfer). In contrast, a "circuit-level" proxy supports every application (see [SOCKS](https://www.pcmag.com/encyclopedia/term/socks)).

**Forward and Reverse Proxies**

In this definition, the proxy servers are "forward proxies" that hide the details of the clients from the servers. However, proxies can also reside at the website to hide details from the clients (see [reverse proxy](https://www.pcmag.com/encyclopedia/term/reverse-proxy)).

![LAN2.GIF](https://i.pcmag.com/imagery/encyclopedia-terms/proxy-server-lan2.fit_lim.size_640x.gif)

**A Proxy Server in a LAN**

In this example, the proxy server functions as a firewall in the public side of a company network, which is called the "demilitarized zone" (see [DMZ](https://www.pcmag.com/encyclopedia/term/dmz)).

[[DMZ]]