Transport Layer Security

(**T**ransport **L**ayer **S**ecurity) A security **protocol** from the IETF that is used to create an encrypted connection between the user's browser and a Web server. TLS also uses digital certificates to authenticate the server. For certain transactions, the client can be authenticated as well, but this is not necessary with normal browser interaction as public websites accept all visitors.

TLS is based on and supersedes Secure Sockets Layer 3.0 (SSL 3.0). Using stronger encryption algorithms than SSL, which has since been deprecated, TLS and SSL are not interoperable.

**HTTPS Protocol and Port Number 465**

A TLS session starts by sending a request to the Web server with an HTTPS prefix in the URL, which inserts TLS port number 465 into the packets. See [well-known port](https://www.pcmag.com/encyclopedia/term/well-known-port) and [HTTPS](https://www.pcmag.com/encyclopedia/term/https).

The TLS client uses the public key to encrypt a random number and send it back to the server. The random number, combined with additional random numbers previously sent to each other, is used to generate a secret session key to encrypt the subsequent message exchange. See [HMAC](https://www.pcmag.com/encyclopedia/term/hmac), [digital certificate](https://www.pcmag.com/encyclopedia/term/digital-certificate) and [EAP](https://www.pcmag.com/encyclopedia/term/eap).

![SSL.GIF](https://i.pcmag.com/imagery/encyclopedia-terms/tls-ssl.fit_lim.size_640x.gif)

**The Handshake**

These steps take place to negotiate a TSL (or SSL) session before any user data are transmitted. The algorithm mentioned is the encryption method. In steps 5 and 6, the checksums ensure that the message was not tampered with (see [MAC](https://www.pcmag.com/encyclopedia/term/mac)).

Point-to-Point Tunneling Protocol (PPTP) have been deprecated because they do not offer adequate security.