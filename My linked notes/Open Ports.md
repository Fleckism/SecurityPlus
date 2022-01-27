Network applications and services allow client connections via Transport Control Protocol ([[TCP]] or User Datagram Protocol [[UDP]] port numbers. The clients and servers are identified by Internet Protocol (IP) addresses. Servers must operate with at least some open ports, but security best practice dictates that these should be restricted to only necessary services. Running unnecessary open ports and services increases the attack surface. Some generic steps to harden services to meet a given role include:

-   If the service is security-critical (such as a remote administration interface), restrict endpoints that are allowed to access the service by IP address or address range. Alternatively, prevent suspect endpoints from connecting by adding them to the block list, but otherwise allow access.
-   Disable services that are installed by default but that are not needed. Ideally, disable the service on the server itself, but in some circumstances it may be necessary to block the port using a firewall instead.
-   For services that should only be available on the private network, block access to ports at border firewalls or segment the network so that the servers cannot be accessed from external networks.