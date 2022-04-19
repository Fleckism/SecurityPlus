**Detailed analysis of services** on a particular host is called fingerprinting.
- report host configurations
- [[Protocol]]—do not assume that a port is being used for its "well known" application protocol. 
- Application name and version—the software operating the port.
- [[Device]] type—not all network devices are PCs. 
	- This is because each OS or application software that underpins a network service **responds** to probes in a unique way. This allows the scanning software to guess at the software name and version, without having any sort of privileged access to the host. This can also be described as **banner grabbing**, where the banner is the header of the response returned by the application.
- Having identified active IP hosts on the network and gained an idea of the network topology, the next step in [[network reconnaissance]] 
- Fingerprinting is step 2? is to work out which operating systems are in use, which network services each host is running, and, if possible, which application software is underpinning those services. This process is described as service discovery. Service discovery can also be used defensively, to probe potential rogue systems and identify the presence of unauthorized network service ports.

aka banner grabbing, where the banner is the header of the response returned by the application

see  [[reconnaissance]]  
# full 
The detailed analysis of services on a particular host is called fingerprinting.
-   report host configurations
-   Protocol—do not assume that a port is being used for its "well known" application protocol. Nmap can scan traffic to verify whether it matches the expected [[signature]] (HTTP, DNS, SMTP, and so on).
-   Application name and version—the software operating the port, such as Apache web server or Internet Information Services (IIS) web server.
-   Device type—not all network devices are PCs. Nmap can identify switches and routers or other types of networked devices, such as NAS boxes, printers, and webcams.
-   The detailed analysis of services on a particular host is often called [[fingerprinting]]. This is because each OS or application software that underpins a network service responds to probes in a unique way. This allows the scanning software to guess at the software name and version, without having any sort of privileged access to the host. This can also be described as banner grabbing, where the banner is the header of the response returned by the application.
-   
- Having identified active IP hosts on the network and gained an idea of the network topology, the next step in network [[reconnaissance]] is to work out which operating systems are in use, which network services each host is running, and, if possible, which application software is underpinning those services. This process is described as service discovery. Service discovery can also be used defensively, to probe potential rogue systems and identify the presence of unauthorized network service ports.

aka banner grabbing, where the banner is the header of the response returned by the application