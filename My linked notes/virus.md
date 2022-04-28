#tool A computer virus is a type of malware designed to **replicate and spread** from computer to computer:

- Virus's need a human to activate.
# Classified by the types of file or media they infect
-   **[[Non-resident file infector]]**—the virus is contained within a host executable file and runs with the host process. 
-   [[Memory resident]]  when the host file is **executed**, the virus creates a new process for itself in memory. The malicious process remains in memory, even if the host process is terminated. 
-   **Boot**—the virus code is written to the disk boot sector or the partition table of a fixed disk or USB media, and executes as a memory resident process when the OS starts or the media is attached to the computer.
-   [[Script and macro viruses]]

In addition, the term **[[multipartite]]** is used for viruses that use multiple [[vector|vectors]] and **[[polymorphic]]** for viruses that can dynamically change or obfuscate their code to evade detection.

**What these types of viruses have in common is that they must infect a host file or media.** An infected file can be distributed through any normal means—on a disk, on a network, as an attachment to an email or social media post, or as a download from a website.



# Expanded

A computer [[virus]] is a type of malware designed to replicate and spread from computer to computer, usually by "infecting" executable applications or program code. There are several different types of viruses and they are generally classified by the different types of file or media that they infect:

-   **Non-resident/file infector**—the virus is contained within a host executable file and runs with the host process. The virus will try to infect other process images on persistent storage and perform other payload actions. It then passes control back to the host program.
-   **Memory resident**—when the host file is executed, the virus creates a new process for itself in memory. The malicious process remains in memory, even if the host process is terminated.
-   **Boot**—the virus code is written to the disk boot sector or the partition table of a fixed disk or USB media, and executes as a memory resident process when the OS starts or the media is attached to the computer.
-   **Script and macro viruses**—the malware uses the programming features available in local scripting engines for the OS and/or browser, such as PowerShell, Windows Management Instrumentation (WMI), JavaScript, Microsoft Office documents with Visual Basic for Applications (VBA) code enabled, or PDF documents with JavaScript enabled.

In addition, the term **multipartite** is used for viruses that use multiple vectors and **polymorphic** for viruses that can dynamically change or obfuscate their code to evade detection.

What these types of viruses have in common is that they must infect a host file or media. An infected file can be distributed through any normal means—on a disk, on a network, as an attachment to an email or social media post, or as a download from a website.

![Email shows Outlook blocked access to an attached file with a long, numerical name that begins "Docx" and ends "PDF.jar."](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1823-1599771796477.png)


A virus is executed only when the user performs an action such as downloading and running an infected executable process, attaching an infected USB stick, or opening an infected Word document with macros enabled. 

**Viruses and worms**—these represent some of the first types of malware and spread without any authorization from the user by being concealed within the executable code of another process.

[[4B  Analyze Indicators of Malware-Based Attack]]