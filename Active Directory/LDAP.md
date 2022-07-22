Lightweight Directory Access Protocol
[[port]] 636 & 389
(**L**ightweight **D**irectory **A**ccess **P**rotocol) A protocol used to access a directory listing in a TCP/IP network. LDAP is used to query network directories, email servers and other information repositories. It is a sibling protocol to HTTP and FTP and uses the ldap:// prefix in its URL.

LDAP is a simpler version of the DAP protocol, which is used to gain access to X.500 directories. Although X.500 and DAP are more comprehensive than LDAP and offer more features, it is easier to code a query in LDAP. See [X.500](https://www.pcmag.com/encyclopedia/term/x500), [DSML](https://www.pcmag.com/encyclopedia/term/dsml) and [ADSI](https://www.pcmag.com/encyclopedia/term/adsi).

LDAP Secure (LDAPS)—the server is installed with a digital certificate, which it uses to set up a [[secure tunnel]] for the user credential exchange. LDAPS uses 



LDAP services listen on port 389. You can verify this by typing "netstat -an" in a Windows command line on the server that hosts LDAP. LDAP services are a critical component of AD DS and should not be neglected during troubleshooting. The protocol provides the methods in which Active Directory communicates with and manipulates the large data sets involved with the networking and user information.

###  Reference
