# 1


An attacker finds a way to exploit a vulnerability in a target application that allows the attacker to bypass a password requirement. Which method did the attacker most likely use?

1.  The attacker added LDAP filters as unsanitized input by creating a condition that is always true.


Solution

An attacker could exploit the vulnerability with an LDAP injection attack, inserting the (&) operator to return a condition that is always true, dropping the password filter for a name=value pair.

A stored/persistent cross-site scripting (XSS) attack aims to insert unsanitized code into a back-end database a trusted site uses. When other users view the posted message, the malicious script executes.

Data submitted via extensible markup language (XML) with no encryption or input validation is vulnerable to spoofing, request forgery, and injection of arbitrary data or code.

In a SQL injection attack, the attacker modifies basic SQL functions by adding code. This could be with input an app accepts. In this case, LDAP was compromised and not an input to an application.
# 2
A network user calls the help desk after receiving an error message. The caller complains that the error message does not indicate whether the username or password input was incorrect but simply states there was an authentication error. What does this situation illustrate?

1.  Effective exception handling


Solution

Invalid user input can cause an error or exception. A structured exception handler (SEH) dictates what the application should then do. The application must not fail in a way that allows an attacker to execute code or perform some sort of injection attack.

Dynamic analysis tests the application under "real world" conditions using a staging environment.

Data exposure is a fault that allows privileged information (such as a token, password, or personal data) to be read without being subject to the appropriate access controls.

A web application can be designed to perform code execution and input validation. An example is a document object model (DOM) script to render the page using dynamic elements from user input.
# 3
A system administrator suspects a memory leak is occurring on a client. Determine which scenario would justify this finding.

4.  Software does not release allocated memory when it is done with it.

Solution

A memory leak is a process that takes up memory without subsequently freeing it up, which a worm or other type of malware can cause. Looking for decreasing available bytes and increasing committed bytes can detect this type of memory leak.

A rapid decrease in disk space is related to storage usage rather than memory usage. This may occur during data migration or archival.

High page file utilization occurs when there is insufficient physical memory to support multiple running applications. This could indicate the existence of malware.

High utilization out-of-hours can be suspicious if no scheduled activities are occurring, such as backup or virus scanning.
# 4
A system administrator is working to restore a system affected by a stack overflow. Analyze the given choices and determine which overflow vulnerability the attacker exploited.

1.  An attacker changes the return address of an area of memory used by a program subroutine.


Solution

A stack is an area of memory used by a program subroutine. It includes a return address, which is the location of the program that is called the subroutine. An attacker could use a buffer overflow to change the return address, which is called a stack overflow.

A heap is an area of memory allocated by an application during execution to store a variable. A heap overflow can overwrite the variables with unexpected effects.

An array is a type of variable designed to store multiple values. It is possible to create an array index overflow by exploiting unsecure code to load the array with more values than it expects.

An integer overflow attack causes the target software to calculate a value that exceeds bounds that are set by the software.
# 5

Compare and contrast the types of Cross-Site Scripting (XSS) attacks, and select the option that accurately distinguishes between them.


2.  Reflected and stored XSS attacks exploit server-side scripts, while the DOM is used to exploit vulnerabilities in client-side scripts.


Solution

Both reflected and stored Cross-Site Scripting (XSS) attacks exploit server-side scripts. The third type of XSS attack exploits vulnerabilities in client-side scripts, and these scripts often use the Document Object Model (DOM) to modify the content and layout of a web page.

Both reflected and stored Cross-Site Scripting (XSS) attacks exploit server-side scripts, not client-side. Document Object Model (DOM) modifies the content and layout utilizing client-side scripts.

While reflected Cross-Site Scripting (XSS) attacks exploit server-side scripts, Document Object Model (DOM) exploits client-side scripts. A stored attack exploits server-side scripts.

A nonpersistent attack is another name for reflected, and a persistent attack is another name for a stored attack. Both of these attacks exploit server-side scripts. DOM exploits client-side scripts.
# 6
Which of the following statements differentiates between input validation and output encoding?

1.  Input validation ensures that data input into an application is in a compatible format for the application, while output encoding re-encodes data that transfers between scripts.

Solution

Input validation ensures that an application can appropriately handle the data entered into a field or variable in the application. Output encoding occurs when a script passes data to another script. Output encoding ensures it is not passing any malicious "script" contents.

Input validation occurs when a script takes data passed to it by some other process. Client-side code, server-side code, or both, can perform input validation.

Output encoding avoids the assumption that input will have been sanitized already.

HTTP Strict Transport Security (HSTS) forces a browser to connect using HTTPS only, mitigating downgrade attacks, such as SSL stripping. Cache-control sets whether the browser can cache responses.
# 7
Evaluate the Agile paradigm within a Software Development Lifecycle (SDLC) to determine which statement demonstrates the idea of continuous tasks.


3.  Releasing well-tested code in smaller blocks


Solution

Agile development flips the waterfall model by iterating through phases concurrently on smaller modules of code.  In this model, development and provisioning tasks are conceived as continuous.

The concept phase includes devising the initial scope and vision for the project and to determine its feasibility.

The iteration phase consists of prioritizing requirements and working through cycles of designing, developing, testing, and test deploying solutions to the project goals.

The transition phase includes performing the final integration and testing of the solution and preparing for deployment in the user environment.
# 8

Which scripting language is the preferred method of performing Windows administration tasks?


4.  Powershell

Solution

Powershell is the preferred method of performing Windows administration tasks.

Javascript is the programming language of the web and is one of the most popular programming languages.

Python is a popular language for implementing all kinds of development projects, including automation tools and security tools, as well as malicious scripts.

Ruby is a dynamic, open source programming language with a focus on simplicity and productivity. It has an elegant syntax that is natural to read and easy to write.

# 9
An employee is attempting to install new software they believe will help them perform their duties faster. When the employee tries to install the software, an error message is received, stating they are not authorized to install the software. The employee calls the help desk for assistance. Evaluate the principles of execution control to conclude what has most likely occurred in this scenario.


3.  The company is utilizing allow list control, and the software is not included in the list.


Solution

It is likely that the company is using allow list control, and the software is not on the approved allow list. Any software not listed will be blocked from running.

If the company was using a block list, the software would be able to run as long as it is not on the prohibited list. Block list only blocks software that has been listed.

Allow list will not allow any software to run if it is not on the list. If the software was on the list, it would have been allowed to run.

Execution control only focuses on either the allow list or the block list, and does not scan for viruses or malicious software.
# 10
Examine each of the following statements and determine which most accurately compares an allow and block list control practices.

4.  An allow list operates on a default-deny policy, while a block list is a default-allow policy.

Solution

Execution control is the process of determining what additional software or scripts a host can run or install beyond its baseline. An allow list is a default-deny policy that means only running authorized processes and scripts. An allow list may impede accessibility and increase support time and costs.

A block list is a default-allow policy that prevents the execution of listed processes and scripts. It is vulnerable to software exploits not previously labeled as malicious.

Access control schemes refer to how users receive rights or permissions to access network resources.

Discretionary access control (DAC) depends on a resource owner, who controls the resource’s access control list.
# 11
Analyze the following statements and select the statement which correctly explains the difference between cross-site scripting (XSS) and cross-site request forgery (XSRF).

1.  XSRF spoofs a specific request against the web application, while XSS is a means of running any arbitrary code.


Solution

A client-side or cross-site request forgery (CSRF or XSRF) can exploit applications that use cookies to authenticate users and track sessions. XSS exploits a browser’s trust and can perform an XSRF attack.

XSS inserts a malicious script that appears to be part of a trusted site. XSS can conduct an XSRF attack.

XSRF passes an HTTP request to the victim’s browser that spoofs a target site action, such as changing a password. The attacker can disguise and accomplish this request without the victim necessarily having to click a link.

XSRF is a client-side exploit. An XSS attack may be reflected (nonpersistent) or stored (persistent) and may target back-end systems (server-side) or client-side scripts.
# 12
A hacker compromises a web browser and uses access to harvest credentials users input when logging in to banking websites. What type of attack has occurred?

2.  Man-in-the-Browser


Solution

A man-in-the-browser (MitB) attack compromises the web browser. An attacker may be able to inspect session cookies, certificates, and data, change browser settings, perform redirection, and inject code.

An evil twin is a rogue WAP masquerading as a legitimate one. It can capture user logon attempts, allow man-in-the-middle attacks, and allow access to private information.

Session hijacking involves replaying a web application cookie in some way. Attackers can sniff network traffic to obtain session cookies sent over an unsecured network.

In a clickjacking attack, the user sees and trusts as a web application with a login page or form that contains a malicious layer or invisible iFrame that allows an attacker to intercept or redirect user input.
# 13
Which type of attack disguises the nature of malicious input, preventing normalization from stripping illegal characters?


2.   Canonicalization


Solution

The threat actor might use a canonicalization attack to disguise the nature of the malicious input. Canonicalization refers to the way the server converts between the different methods by which a resource (such as a file path or URL) may be represented and submitted to the simplest (or canonical) method used by the server to process the input.

Fuzzing is a means of testing that an application's input validation routines work well. The test, or vulnerability scanner, generates large amounts of deliberately invalid and random input and records the application's responses.

Code reuse occurs through the use of a block of code from elsewhere in the same application, or from another application, to perform a different function.

Code signing is the principal means of proving the authenticity and integrity of code.
# 14
An attacker compromises a Linux host, installing a web shell as a backdoor. If the attacker gained access to the host through a connection the host established, what type of attack has occurred?


2.  Reverse shell


Solution

A reverse shell is a common attack vector against a Linux host, where a victim host opens a connection to the attacking host through a maliciously spawned remote command shell.

A man-in-the-browser (MitB) attack compromises the web browser. An attacker may be able to inspect session cookies, certificates, and data, change browser settings, perform redirection, and inject code.

Malware running with system or root level privilege is referred to as a rootkit, which gives an attacker unrestricted access to everything from the root of the file system down.

Session hijacking involves replaying a web application cookie in some way. Attackers can sniff network traffic to obtain session cookies sent over an unsecured network.
# 15
A threat analyst is asked about malicious code indicators. Which indicator allows the threat actor's backdoor to restart if the host reboots or the user logs off?

1.  Persistence

Solution

Persistence is when a mechanism allows the threat actor's backdoor to restart if the host reboots or the user logs off. Typical methods are to use AutoRun keys in the registry or adding a scheduled task.

Credential dumping is where the malware might try to access the credentials file or sniff credentials held in memory by the lsass.exe system process.

Shellcode is a minimal program designed to exploit a buffer overflow or similar vulnerability to gain privileges, or to drop a backdoor on the host if run as a Trojan. Having gained a foothold, this type of attack will be followed by some type of network connection to download additional tools.

Lateral movement/insider attack uses the foothold to execute a process remotely. If the attacker has compromised an account, these commands can blend in with ordinary network operations.
# 16
Identify the type of attack that occurs when the outcome from execution process are directly dependent on the order and timing of certain events, and those events fail to execute in the order and timing intended by the developer.


3.  Race conditions


Solution

Race conditions occur when the outcome from executive processes is directly dependent on the order and timing of certain events, and those events fail to execute in the order and timing intended by the developer.

A stack is an area of memory used by a program subroutine. It includes a return address which is the location of the program that called the subroutine. An attacker could use a buffer overflow to change the return address.

Integers are widely used as a data type, where they are commonly defined with fixed lower and upper bounds. An integer overflow attack causes the target software to calculate a value that exceeds these bounds.

A Dynamic Link Library (DLL) injection is not a vulnerability of an application but of the way the operating system allows one process to attach to another and then force it to load a malicious link library.
# 17
Which cookie attribute can a security admin configure to help mitigate a request forgery attack?


3.  SameSite


Solution

Cookies can be a vector for session hijacking and data exposure if not configured correctly. Use the SameSite attribute to control where a cookie may be sent, mitigating request forgery attacks.

Set the Secure attribute to prevent a cookie from being sent over unencrypted HTTP.

Set the HttpOnly attribute to make the cookie inaccessible to document object model/client-side scripting.

A number of security options can be set in the response header returned by the server to the client, including Cache-Control, which sets whether the browser can cache responses. Preventing caching of data protects confidential and personal information where multiple users might share the client device.
# 18
A threat actor programs an attack designed to invalidate memory locations to crash target systems. Which statement best describes the nature of this attack?


3.  The attacker programmed a null pointer dereferencing exception.


Solution

Dereferencing occurs when a pointer variable stores a memory location, which is attempting to read or write that memory address via the pointer. If the memory location is invalid or null, this creates a null pointer dereference type of exception and the process may crash.

Dereferencing does not mean deleting or removing; it means read or resolve.

A null pointer might allow a threat actor to run arbitrary code. Programmers can use logic statements to test that a pointer is not null before trying to use it.

A race condition is one means of engineering a null pointer dereference exception. Race conditions occur when processes depend on timing and order, and those events fail to execute in the order and timing intended.
# 19


Which malicious code indicator is a minimal program designed to exploit a buffer overflow?


4.  Shellcode

Solution

Shellcode is a minimal program designed to exploit a buffer overflow or similar vulnerability to gain privileges, or to drop a backdoor on the host if run as a Trojan.

Credential dumping is when malware might try to access the credentials file (SAM on a local Windows workstation) or sniff credentials held in memory by the lsass.exe system process.

Lateral movement/insider attack is the general procedure that uses the foothold to execute a process remotely, using a tool such as psexec.

Persistence is a mechanism that allows the threat actor's backdoor to restart if the host reboots or the user logs off.
# 20
Which scenario best describes provisioning?


2.  A developer deploys an application to the target environment.

Solution

Provisioning is the process of deploying an application to the target environment. An enterprise provisioning manager might assemble multiple applications in a package. 

Deprovisioning is the process of removing an application from packages or instances. This might be necessary if software has to be completely rewritten or no longer satisfies its purpose. 

Version control is an ID system for each iteration of a software product. Most version control numbers represent both the version and internal build numbers for use in the development process. 

Continuous integration is the principle that developers should commit and test updates often—every day or sometimes even more frequently. This reduces the chances of two developers spending time on code changes that are later found to conflict with one another.
# 21
Analyze types of vulnerabilities and summarize a zero-day exploit.


2.  A vulnerability that is capitalized on before the developer knows about it.


Solution

A zero-day exploit is a vulnerability that is exploited before the developer knows about it or can release a patch to address it. These can be extremely destructive as it can take the vendor a lot of time to develop a patch.

A vulnerability is a design flaw that can cause the application security system to be circumvented, or will cause the application to crash.

An input validation attack passes invalid data to the application. Since the input handling on the routine is inadequate, it causes the application or even the operating system, to behave in an unexpected way.

In a buffer overflow vulnerability, the attacker passes data to deliberately overfill the buffer that the application reserves to store the expected data.

# 22

An attacker uses a sniffer to gain session cookies a client sends over an unsecured network. What type of attack can the malicious actor now use the session cookies to conduct?

1.  Session hijacking


Solution

Session hijacking typically means replaying a cookie in some way. Attackers can sniff network traffic to obtain session cookies sent over unsecured networks.

A cross-site scripting (XSS) attack exploits the fact that the browser is likely to trust scripts that appear to come from a site the user has chosen to visit. XSS inserts a malicious script that appears to be part of the trusted site.

In an SQL injection attack, the attacker modifies basic SQL functions by adding code to some input the app accepts, causing it to execute the attacker's SQL queries or parameters.

A threat actor could exploit either unauthenticated access or a vulnerability in a client app to submit arbitrary Lightweight Directory Access Protocol (LDAP) queries.


# 23
Which of the following is NOT a scripting language?

1.  regex

Solution

Automated or procedural scripting languages take standard arguments as data, so there is less scope for uncertainty over configuration choices leading to errors. A domain-specific language (DSL) performs a particular task, such as regex string parsing.

PowerShell is the preferred method of performing Windows administration tasks, which also makes it a go-to toolkit for hackers. Most PowerShell usage is founded on cmdlets. A cmdlet is a compiled library that exposes some configuration or administrative task.

JavaScript is a general purpose scripting language used to create and control dynamic website content.

Python is a popular language for implementing a variety of development projects, including automation tools and security tools, as well as malicious scripts.

# 24
Code developers de-conflict coding with one another during which phase of the software development life cycle (SDLC)?

1.  Continuous integration


Solution

Continuous integration (CI) is the principle that developers should commit and test updates often. CI aims to detect and resolve coding conflicts early.

Continuous delivery is about testing all of the infrastructures that support an app, including networking, database functionality, client software, and so on.

Verification is a compliance testing process to ensure that the product or system meets its design goals. Validation is the process of determining whether the application is fit-for-purpose. These processes ensure the application conforms to the secure configuration baseline.

An automation solution will have a system of continuous monitoring to detect service failures, security incidents, and failover mechanisms.

# 25
Which of the following is a common solution that protects an application from behaving in an unexpected way when passing invalid data through an attack?

4.  Input Validation

Solution

Input validation is a primary vector for attacking applications. If the application cannot check for valid inputs, a hacker can take advantage of this vulnerability to enter in commands that can query a database, for example, and obtain confidential data.

A buffer overflow occurs when an attacker passes data to deliberately overfill the buffer that the application reserves to store the expected data.

Race conditions occur when events fail to execute in the order and timing intended by the developer. Applications are vulnerable to this when the outcome from an execution process is directly dependent on the order and timing of certain events.

A zero-day exploit is described as a vulnerability that is exploited before the developer knows about it or can release a patch.

# 26
Identify the type of attack that occurs when the outcome from execution process are directly dependent on the order and timing of certain events, and those events fail to execute in the order and timing intended by the developer.


3.  Race conditions


Solution

Race conditions occur when the outcome from executive processes is directly dependent on the order and timing of certain events, and those events fail to execute in the order and timing intended by the developer.

A stack is an area of memory used by a program subroutine. It includes a return address which is the location of the program that called the subroutine. An attacker could use a buffer overflow to change the return address.

Integers are widely used as a data type, where they are commonly defined with fixed lower and upper bounds. An integer overflow attack causes the target software to calculate a value that exceeds these bounds.

A Dynamic Link Library (DLL) injection is not a vulnerability of an application but of the way the operating system allows one process to attach to another and then force it to load a malicious link library.