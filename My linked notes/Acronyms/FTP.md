**File Transfer #protocol** (FTP) 
- server is typically configured with several public directories, hosting files, and user accounts. 
- Most HTTP servers also function as FTP servers, and FTP services, accounts, and directories may be installed and enabled by default when you install a web server. FTP is more efficient compared to file attachments or HTTP file transfer, but has **no security mechanisms**. All authentication and data transfer are communicated as **plaintext**, meaning that credentials can easily be picked out of any intercepted FTP traffic.

You should check that users do not install unauthorized servers on their PCs (a rogue server). For example, a version of IIS that includes HTTP, FTP, and SMTP servers is shipped with client versions of Windows, though it is not installed by default.

Another means of securing FTP is to use the connection security protocol SSL/TLS. There are two means of doing this:

-   Explicit TLS (FTPES)—use the AUTH TLS command to upgrade an unsecure connection established over port 21 to a secure one. This protects authentication credentials. The data connection for the actual file transfers can also be encrypted (using the PROT command).
-   Implicit TLS ([[FTPS]])—negotiate an [[SSL]]/[[My linked notes/Acronyms/TLS]] tunnel before the exchange of any FTP commands. This mode uses the secure port 990 for the control connection.

FTPS is tricky to configure when there are firewalls between the client and server. Consequently, FTPES is usually the preferred method.