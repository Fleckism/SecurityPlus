**(1)** (**T**ime **T**o **L**ive) A counter in a network packet that sets a limit to its validity. In order to prevent an IP packet from propagating endlessly through the network, the value in the TTL field is reduced by each router. When TTL reaches 0, the packet is discarded.

**(2)** (**T**ime **T**o **L**ive) A timestamp in the DNS system, which converts hostnames to IP addresses. Responses use a TTL field to keep the IP address in the user's cache for a limited amount of time. After the time is up, the next request for that IP address must go back to the DNS system. See [DNS](https://www.pcmag.com/encyclopedia/term/dns) and [DNS rebinding](https://www.pcmag.com/encyclopedia/term/dns-rebinding).

Layer 4 load balancer—basic load balancers make forwarding decisions on IP address and TCP/UDP port values, working at the transport layer of the OSI model.
-   Layer 7 load balancer (content switch)—as web applications have become more complex, modern load balancers need to be able to make forwarding decisions based on application-level data, such as a request for a particular URL or data types like video or audio streaming. This requires more complex logic, but the processing power of modern appliances is sufficient to deal with this. 

- Layer 4 load balancers can only make basic connectivity tests while layer 7 appliances can test the application's state, as opposed to only verifying host availability.

Is a load balancer hardware or software?
**Its an appliance** I think it is both hardware and software.