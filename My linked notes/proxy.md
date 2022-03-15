A proxy **server** is a computer system or router.
- Functions as a relay between client and server
- Prevents attacker from invading private network
- Part of a firewall
- **A proxy server must understand the application it is servicing.**
- Must be able to parse and modify protocols and scripts
	- HTTP
	- HTTPS
	- HTML
	- Scripts
	- FTP
	- SMTP
- Two types
	- Non-transparent proxy must be configured to/for the client [[port]] 8080
	- Transparent (forced or intercepting) proxy intercepts client traffic without the client having to be reconfigured.
		- Must be implemented on a switch or router or other inline network appliance.


The word proxy means "to act on behalf of another," and a proxy server acts on behalf of the user. All requests to the Internet go to the proxy server first, which evaluates the request and forwards it to the Internet. Likewise, responses come back to the proxy server and then to the user.