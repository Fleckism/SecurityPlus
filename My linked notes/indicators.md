[[Privilege escalation]]: **Without performing detailed analysis of code or process execution in real-time, it is privilege escalation that provides the simplest indicator of an application attack.**
-  An **error message**. In Windows, this may be of the following types: "Instruction could not be read or written," "Undefined exception," or "Process has encountered a problem.

**Resource exhaustion**
- A memory leak may itself be a sign of a malicious or corrupted process.
- Distributed attacks against network applications perform a type of resource exhaustion attack by starting but not completing sessions, **causing the application to fill up its state table**, 

**Open unexpected network connections**
- A process that has been compromised by DLL injection might open unexpected network connections, or interact with files and the registry suspiciously.
	- be operating with **sufficient privileges**, typically local administrator or system privileges.
	- OS function calls to allow DLL injection are legitimately used for operations such as debugging and monitoring.
	- Windows Application Compatibility framework. This allows legacy applications written for an OS, such as Windows XP, to run on later versions.

Pass the hash is relatively difficult to detect, as it exploits legitimate network behavior.
[[IoC]]
[[Botnet]]
- Resource consumption
[[Crypto]]-malware
- Resource consumption
[[DDoS]]
- Resource consumption
- Traffic spikes
	- Mitigation: Load Balancers