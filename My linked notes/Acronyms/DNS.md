**Domain Name System** aka **name server** 
- Used to identify computers, services and other resources reachable through the internet or other internet protocol (IP)
- [[protocol]] that makes the Internet usable by allowing the use of domain names. 
- DNS is widely trusted by organizations, and DNS traffic is typically allowed to pass freely through network firewalls.

Security Extensions (DNSSEC) help to **[[mitigate]] against spoofing and poisoning attacks by providing a validation process for DNS responses**. With DNSSEC enabled, the authoritative server for the zone creates a "package" of resource records (called an RRset) signed with a private key (the Zone Signing Key). When another server requests a secure record exchange, the authoritative server returns the package along with its public key, which can be used to verify the signatu