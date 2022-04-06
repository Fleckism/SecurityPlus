---
tags: [OIR,section]
---
# ## 
[[OIR]]
LESSON INTRODUCTION

Automation strategies for resiliency, disaster recovery, and incident response put **development (programming and scripting)** at the heart of secure network administration and operations (DevSecOps). As well as automating operations, more companies are having to maintain bespoke code in customer-facing software, such as web applications. Consequently, secure application development is a competency that will only grow in importance over the course of your career.

## 

LESSON OBJECTIVES

In this lesson, you will:

-   Analyze indicators of application attacks.
-   Analyze indicators of web application attacks.
-   Summarize secure coding practices.
-   Implement secure script environments.
-   Summarize deployment and automation concepts.
# EXAM OBJECTIVES COVERED

1.3 Given a scenario, analyze potential indicators associated with application attacks

Attacks against desktop and server applications allow threat actors to run arbitrary code on trusted hosts, allowing them to gain a foothold on the network or move laterally within it. With sufficient privileges and access, an attacker can quickly move to compromising data assets or causing denial of service against critical servers. Not all of these attacks will be detected automatically, so as a security professional, you must be able to identify indicators of arbitrary code execution and privilege escalation from your host monitoring and logging systems.
# APPLICATION ATTACKS
[[Attack]]
 An application attack targets a vulnerability in OS or application software. An application vulnerability is a design flaw that can cause the application security system to be circumvented or that will cause the application to crash.

 **Privilege Escalation**

The purpose of most application attacks is to allow the threat actor to run his or her own code on the system. This is referred to as **arbitrary code execution**. Where the code is transmitted from one machine to another, it can be referred to as **remote code execution**. The code would typically be designed to install some sort of backdoor or to disable the system in some way (denial of service).

An application or process must have privileges to read and write data and execute functions. Depending on how the software is written, a process may run using a system account, the account of the logged-on user, or a nominated account. If a software exploit works, the attacker may be able to execute arbitrary code with the same privilege level as the exploited process. There are two main types of [[privilege escalation]]:

-   **Vertical privilege escalation** (or elevation) is where a user or application can access functionality or data that should not be available to them. For instance, a process might run with local administrator privileges, but a vulnerability allows the arbitrary code to run with higher system privileges.
-   **Horizontal privilege escalation** is where a user accesses functionality or data that is intended for another user. For instance, via a process running with local administrator privileges on a client workstation, the arbitrary code is able to execute as a domain account on an application server.

**Without performing detailed analysis of code or process execution in real-time, it is privilege escalation that provides the simplest indicator of an application attack.** If process logging has been configured ([varonis.com/blog/sysmon-threat-detection-guide](https://www.varonis.com/blog/sysmon-threat-detection-guide/)), the audit log can provide evidence of privilege escalation attempts. These attempts may also be detected by incident response and endpoint protection agents, which will display an alert.

 Error Handling

 An application attack may cause an **error message**. In Windows, this may be of the following types: "Instruction could not be read or written," "Undefined exception," or "Process has encountered a problem." One issue for **error handling is that the application should not reveal configuration or platform details** that could help an attacker. For example, an unhandled exception on a web application might show an error page that reveals the type and configuration of a database server.

 Improper Input Handling 

 Most software accepts user input of some kind, whether the input is typed manually or passed to the program by another program, such as a browser passing a URL to a web server or a Windows process using another process via its application programming interface. **Good programming practice dictates that input should be tested to ensure that it is valid;** that is, the sort of data expected by the receiving process. Most application attacks work by passing invalid or maliciously constructed data to the vulnerable process. There are many ways of exploiting improper input handling, but many [[attacks]] can be described as either overflow-type attacks or injection-type attacks.
# OVERFLOW VULNERABILITIES

In an overflow attack, the threat actor submits input that is too large to be stored in a variable assigned by the application. Some of the general overflow vulnerabilities are discussed here. To keep up to date with specific attack methods and new types of attack, monitor a site such as [[OWASP]] ([owasp.org/www-community/attacks](http://www.owasp.org/www-community/attacks)). Ideally, the code used to attempt these attacks will be identified by network [[IDS]] or by an endpoint protection agent. **Unsuccessful attempts may be revealed through unexplained crashes or error messages following a file download, execution of a new app or a script, or connection of new hardware.** 

### Buffer Overflow 

A buffer is an area of memory that the application reserves to store expected data. To exploit a buffer overflow vulnerability, the attacker passes data that deliberately overfills the buffer. One of the most common vulnerabilities is a stack overflow. **The stack is an area of memory used by a program subroutine.** It includes a return address, which is the location of the program that called the subroutine. An attacker could use a buffer overflow to change the return address, allowing the attacker to run arbitrary code on the system. 

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5515-1599771808724.png)

When executed normally, a [[function will return control to the calling function. ]]If the code is vulnerable, an attacker can pass malicious data to the function, overflow the stack, and run arbitrary code to gain a shell on the target system.

### Integer Overflow

An integer is a positive or negative number with no fractional component (a whole number). **Integers are widely used as a data type, where they are commonly defined with fixed lower and upper bounds.** An integer overflow attack causes the target software to calculate a value that exceeds these bounds. This may cause a positive number to become negative **(changing a bank debit to a credit, for instance)**. It could also be used where the software is calculating a buffer size; if the attacker is able to make the buffer smaller than it should be, he or she may then be able to launch a buffer overflow attack.

EternalBlue is an example of an exploit that uses vulnerabilities in integer overflow to effect a buffer overflow and gain system privileges on a Windows host ([sentinelone.com/blog/eternalblue-nsa-developed-exploit-just-wont-die](https://www.sentinelone.com/blog/eternalblue-nsa-developed-exploit-just-wont-die/)).
# NULL POINTER DEREFERENCING AND RACE CONDITIONS 

In C/C++ programming, a pointer is a variable that stores a memory location, rather than a value. Attempting to read or write that memory address via the pointer is called dereferencing. If the memory location is invalid or null (perhaps by some malicious process altering the execution environment), this creates a null pointer dereference type of exception, and the process will crash, probably. In some circumstances, this might also allow a threat actor to run arbitrary code. **Programmers can use logic statements to test that a pointer is not null before trying to use it.**

A race condition is one means of engineering a null pointer dereference exception. **Race conditions occur when the outcome from an execution process is directly dependent on the order and timing of certain events**, and those events fail to execute in the order and timing intended by the developer. In 2016, the Linux kernel was discovered to have an exploitable race condition vulnerability, known as Dirty COW ([theregister.com/2016/10/21/linux_privilege_escalation_hole](https://www.theregister.com/2016/10/21/linux_privilege_escalation_hole)).

Race condition attacks can also be directed at databases and file systems. A time of check to time of use ([[TOCTTOU]]) race condition occurs when there is a change between when an app checked a resource and when the app used the resource. This change invalidates the check. An attacker that can identify a TOCTTOU vulnerability will attempt to manipulate data after it has been checked but before the application can use this data to perform some operation. **For example, if an application creates a temporary file to store a value for later use, and an attacker can replace or delete this file between the time it is created and the time it is used, then the attacker is exploiting a TOCTTOU vulnerability.**
# MEMORY LEAKS AND RESOURCE EXHAUSTION

If a process is operating correctly, when it no longer requires a block of memory, it should release it. If the program code does not do this, it could create a situation where the system continually leaks memory to the faulty process. This means less memory is available to other processes and the system could crash. Memory leaks are particularly serious in service/background applications, as they will continue to consume memory over an extended period. Memory leaks in the OS kernel are also extremely serious. A memory leak may itself be a sign of a malicious or corrupted process.

**More generally, a malicious process might cause denial of service or set up the conditions for privilege escalation via resource exhaustion.** Resources refers to CPU time, system memory allocation, fixed disk capacity, and network utilization. A malicious process could spawn multiple looping threads to use up CPU time, or write thousands of files to disk. Distributed attacks against network applications perform a type of resource exhaustion attack by starting but not completing sessions, **causing the application to fill up its state table**, leaving no opportunities for genuine clients to connect.
# DLL INJECTION AND DRIVER MANIPULATION

A **dynamic link library (DLL) is a binary package** that implements some sort of standard functionality, such as establishing a network connection or performing cryptography. The main process of a software application is likely to load several DLLs during the normal course of operations.

**DLL injection is a vulnerability in the way the operating system allows one process to attach to another. This functionality can be abused by malware to force a legitimate process to load a malicious link library**. The link library will contain whatever functions the malware author wants to be able to run. Malware uses this technique to move from one host process to another to avoid detection. **A process that has been compromised by DLL injection might open unexpected network connections, or interact with files and the registry suspiciously.**

To perform DLL injection the malware must already be operating with **sufficient privileges**, typically local administrator or system privileges. It must also **evade detection** by anti-virus software. One means of doing this is code refactoring. Refactoring means that the code performs the same function by using different methods (control blocks, variable types, and so on). **Refactoring means that the A-V software may no longer identify the malware by its signature.**

OS function calls to allow DLL injection are legitimately used for operations such as debugging and monitoring. Another opportunity for malware authors to exploit these calls is the Windows Application Compatibility framework. This allows legacy applications written for an OS, such as Windows XP, to run on later versions. **The code library that intercepts and redirects calls to enable legacy mode functionality is called a shim. The shim must be added to the registry and its files (packed in a shim database/.SDB file) added to the system folder**. The shim database represents a way that malware with local administrator privileges can **run on reboot (persistence)**.
# PASS THE HASH ATTACK

A threat actor has to be either relatively lucky to find an unpatched vulnerability, or well-resourced enough to develop a zero-day exploit. Once an initial foothold has been gained, the threat actor may try to find simpler ways to move around the network.

Attackers can extend their lateral movement by a great deal if they are able to compromise host credentials. One common credential exploit technique for lateral movement is called pass the hash ([[PtH]]). This is the process of harvesting an account's cached credentials when the user is logged into a single sign-on ([[SSO]]) system so the attacker can use the credentials on other systems. If the threat actor can obtain the **hash of a user password**, it is possible to present the hash (without cracking it) to authenticate to network protocols such as the Windows File Sharing protocol Server Message Block ([[SMB]]), and other protocols that accept Windows NT LAN Manager (NTLM) hashes as authentication credentials. For example, most Windows domain networks are configured to allow [[NTLM]] as a **legacy authentication** method for services. The attacker's access isn't just limited to a single host, as they can pass the hash onto any computer in the network that is tied to the domain. This drastically cuts down on the effort the threat actor must spend in moving from host to host.

Pass the hash is relatively difficult to detect, as it exploits legitimate network behavior. A detection system can be configured to correlate a sequence of security log events using NTLM-type authentication, but this method can be prone to false positives ([blog.stealthbits.com/how-to-detect-pass-the-hash-attacks](https://blog.stealthbits.com/how-to-detect-pass-the-hash-attacks/)).

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1885-1599771808810.png)

The pass the hash process. (Images © 123RF.com)
