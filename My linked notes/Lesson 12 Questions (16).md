# 1
Analyze the features of a Full Disk Encryption (FDE) to select the statements that accurately reflect this type of security. **(Select all that apply.)**

3.  A drawback of FDE is the cryptographic operations performed by the OS reduces performance.
4.  FDE requires the secure storage of the key used to encrypt the drive contents.

Solution

FDE means that the entire contents of the drive, including system files and folders, are encrypted. The cryptographic operations performed by the OS reduces performance.

FDE normally utilizes a Trusted Platform Module (TPM) to secure the storage of the key used to encrypt the drive contents.

FDE means that the entire content of the drive (or volume), including system files and folders, are encrypted. This is not limited to only critical files.

FDE requires secure storage of the key used to encrypt the drive contents. Normally, this is in a TPM. It is also possible to use a removable USB drive if USB is a boot device option.
# 2
Compare and evaluate the various levels and types of security found within a Trusted OS (TOS) to deduce which scenario is an example of a hardware Root of Trust (RoT).


2.  The boot metrics and operating system files are checked, and signatures verified at logon.


Solution

A hardware RoT, or trust anchor, is a secure subsystem that can provide attestation. When a computer joins a network, it may submit a report to the NAC declaring valid OS files. The RoT scans the boot metrics and OS files to verify their signatures.

A secure boot is a security system designed to prevent a computer from being hijacked by a malicious OS.

A Trusted Platform Module (TPM) is a specification for hardware-based storage of digital certificates, keys, hashed passwords, and other user and platform identification information.

The Basic Input/Output System (BIOS) provides an industry standard program code that operates the essential components of the PC and ensures that the design of each manufacturer's motherboard is PC compatible.
# 3
Compare and evaluate the various levels and types of platform security to conclude which option applies to a hardware Trusted Platform Module (TPM).


3.  Digital certificates, keys, and hashed passwords are maintained in hardware-based storage.


Solution

A Trusted Platform Module (TPM) is a specification for hardware-based storage of digital certificates, keys, hashed passwords, and other user and platform identification information.

A hardware RoT, or trust anchor, is a secure subsystem that can provide attestation. When a computer joins a network, it may submit a report to the NAC declaring valid OS files. The RoT scans the boot metrics and OS files to verify their signatures.

A secure boot is a security system designed to prevent a computer from being hijacked by a malicious OS.

The Basic Input/Output System (BIOS) provides an industry standard program code that operates the essential components of the PC and ensures that the design of each manufacturer's motherboard is PC compatible.
# 4
Given knowledge of secure firmware implementation, select the statement that describes the difference between secure boot and measured boot.


2.  Secure boot provisions certificates for trusted operating systems (OSes) and blocks unauthorized OSes. Measured boot stores and compares hashes of critical boot files to detect the presence of unauthorized processes.

Solution

Secure boot is about provisioning certificates for trusted operating systems and blocking unauthorized OSes. Measured boot stores and compares hashes of critical boot files to detect unauthorized processes.

Secure boot requires UEFI but does not require a TPM. A trusted or measured boot process uses platform configuration registers (PCRs) in the TPM at each stage in the boot process to check whether hashes of key system state data have changed.

Attestation is the process of sending a signed boot log or report to a remote server.

Secure boot prevents the use of a boot loader or kernel that has been changed by malware (or an OS installed without authorization).
# 5
Contrast vendor support for products and services at the end of their life cycle. Which of the following statements describes the difference between support available during the end of life (EOL) phase and end of service life (EOSL) phase?

1.  During the end of life (EOL) phase, manufacturers provide limited support, updates, and spare parts. In the end of service life (EOSL), developers or vendors no longer support the product and no longer push security updates.

Solution

When a manufacturer discontinues a product’s sales, it enters an end of life (EOL) phase in which support and availability of spares and updates grow limited. An end of service life (EOSL) system is one whose developer or vendor no longer supports.

EOSL products no longer receive security updates and represent a critical vulnerability if companies actively use them.

Microsoft provides Windows versions five years of mainstream support and five years of extended support (during which Microsoft only ships security updates). Most OS and application vendors have similar policies.

Well-maintained open-source software may have long term support (LTS) versions. Developers may also abandon software, and companies who rely on such abandonware must assume any maintenance responsibility.
# 6
A network manager is installing a new switch on the network. Which option does the manager use to harden network security after installation?


4.  The network manager should ensure all patches are applied and it is appropriately configured.

Solution

Network appliances, such as switches, present a special case for hardening. Most of these devices are often only configurable within the parameters allowed by their manufacturers. Hardening is often restricted to ensuring the device is patched and configured correctly.

GPOs are used on Windows networks and are a means of applying security settings across a range of computers. Since the switch is a network appliance, a GPO is not applicable in this situation.

The Server Core option may be utilized when installing a server on the network. It excludes most of the familiar shell tools and only supports a limited number of roles, including Hyper-V and DHCP.

Microsoft Baseline Security Analyzer (MBSA) is used on Windows networks and validates the security configuration.
# 7
Evaluate approaches to applying patch management updates to select the accurate statement.

1.  Operating System major release updates can cause problems with software application compatibility.


Solution

It is well recognized that Operating System major release updates can cause problems with software application compatibility.

The least time-consuming approach is to apply all of the latest patches. A system administrator who applies patches on a case-by-case basis must stay up to date with security bulletins to see if a patch is necessary.

Patches are usually provided at no cost. The cost associated with patches is the time it takes to test, review, and apply them.

It is best practice to trial and update on a test system to try to discover whether it will cause any problems. Applying a patch immediately could do more harm than good to the workstations.
# 8
A system administrator has received new systems to deploy within a work center. Which of the following should the system administrator implement to ensure proper hardening without impacting functionality? **(Select all that apply.)**

3.  Disable any network interfaces that are not required.
4.  Disable all unused services.

Solution

Interfaces provide a connection to the network and some machines may have more than one interface. If any of these interfaces are not required they should be explicitly disabled rather than left unused.

Services provide a library of functions for different types of applications. Unused services should be disabled.

Not all third-party software should be removed. Hardening a system can also restrict the system's capabilities. Additionally, the need for hardening must be balanced against the access requirements and usability in a particular situation.

Application service ports allow client software to connect to applications. These should be closed if access is not required, but be left open if required to conduct business.
# 9
Select the options that can be configured by Group Policy Objects (GPOs). **(Select all that apply.)**

1.  Registry settings

3.  Software deployment


Solution

Group Policy Objects (GPOs) are a means of applying security settings across a range of computers. They can be used to configure software deployment among several other tasks.

GPOs can configure registry settings across a range of computers.

Code signing is the principal means of proving the authenticity and integrity of code (an executable or a script). A GPO can deploy Code Integrity (CI) policies to check for application publisher digital signatures, but not for signing or creating new digital signatures.

Baseline deviation reporting tests the configuration of clients and servers to ensure they are patched, and their configuration settings match the baseline template.
# 10
During a training event, an executive at a large company asks the security manager trainer why pushing automatic updates as a patch management solution is not ideal for their Enterprise network. How will the security manager most likely respond?


2.  Automatic updates can cause performance and availability issues.


Solution

Enterprise networks need to be cautious about automated deployment, as a patch that is incompatible with an application or workflow can cause availability issues. If multiple applications run update clients on the same host, performance issues may also arise.

Scheduling conflicts may influence patch management decisions, but in an enterprise network, a patch management suite, rather than an individual, will handle updates.

Endpoint detection and response (EDR) products analyze system data and logs to provide early threat detection.

Patch management suites identify, test, and deploy operating system (OS) and application updates. Patches are often classified as critical, security-critical, recommended, and optional.
# 11
You are asked to help design a security system. What are some methods that can be used to mitigate risks to embedded systems in such environments? **(Select all that apply.)**


2.  Firmware patching
3.  Network Segmentation
4.  Wrappers

Solution

Firmware patching for embedded systems is just as vital as keeping host OS software up to date on a traditional computer. 

Network segmentation is one of the core principles of network security. This control network should be separated from the corporate network using firewalls and VLANs.

One way of increasing the security of data in transit for embedded systems is through the use of wrappers, such as IPSec. The only thing visible to an attacker or anyone sniffing the wire is the IPSec header, which describes only the tunnel endpoints. 

A faraday cage would help prevent outside interference or leakage of wireless radio frequencies, but may inhibit the use of a security system, such as a keyless door.
# 12
Evaluate the features and vulnerabilities found in medical devices and then select the accurate statements. **(Select all that apply.)**


2.  Attackers may attempt to gain access in order to kill or injure patients, or hold medical units ransom.

4.  Many portable devices, such as cardiac monitors and insulin pumps, run on unsupported operating systems.

Solution

Attackers may have a goal of injuring or killing patients by tampering with dosage levels or device settings.

Many of the control systems for medical devices run on unsupported versions of operating systems, such as Windows XP, because the costs of updating the software to work with newer OS versions is high and disruptive to patient services.

Medical devices can be found in the hospital, clinic, and as portal devices such as cardiac monitors, defibrillators, and insulin pumps.

Medical devices may have unsecure communications protocols. Many devices run on unsupported systems due to the cost and potential disruptions the update would cause.
# 13
Compare the features of static and dynamic computing environments and then select the accurate statements. **(Select all that apply.)**

1.  Embedded systems are typically static computing environments, while most personal computers are dynamic computing environments.
2.  Dynamic computing environments are easier to update than static computing environments.


Solution

An embedded computing environment is a complete computer system that is designed to perform a specific, dedicated function. A PC is a dynamic computing environment where the user can add or remove programs and data files.

A dynamic computing environment provides users more control to perform actions like install or update applications. A static computing environment update will usually only be available through specific management interfaces.

A static computing environment gives less control than a dynamic computing environment. Each embedded system may differ in how each one is handled or maintained, and therefore may require more manual tasks than dynamic systems.

A static computing environment is easier to protect. This is due to the unchanging environment without adding new hardware or software. With fewer changes and additions, the systems are not introduced to as many threats.
# 14
Examine the differences between general purpose personal computer hosts and embedded systems and select the true statements regarding embedded system constraints. **(Select all that apply.)**

1.  Many embedded systems work on battery power, so they cannot require significant processing overhead.

3.  Embedded systems often use the system on chip (SoC) design to save space and increase power efficiency.


Solution

Many embedded devices are battery-powered and may need to run for years without having to replace the cells. Processing must be kept to the minimum possible level.

Embedded systems often use system on chip (SoC), a design where processors, controllers, and devices reside on a single processor die (or chip). This packaging saves space and is usually power efficient.

TPM establishes a root of trust at the hardware level on PC, but most embedded systems do not have embedded TPMs, so they must rely on implicit trust and network perimeter security.

Customers can program a field programmable gate array (FPGA) to run a specific application an embedded system requires, which is more efficient than running a pre-programmed device.
# 15
A company security manager takes steps to increase security on Internet of Things (IoT) devices and embedded systems throughout a company’s network and office spaces. What measures can the security manager use to implement secure configurations for these systems? **(Select all that apply.)**

1.  Isolate hosts that are using legacy versions of operating systems (OSes) from other network devices through network segmentation.
2.  Use wrappers, such as Internet Protocol Security (IPSec) for embedded systems’ data in transit.


Solution

Some embedded systems use legacy OSes, making them difficult to secure. Isolating these hosts from others through network segmentation and using endpoint security can help secure them against exploitation.

One way of increasing the security of data in transit for embedded systems is through the use of wrappers, such as IPSec, which secures data through authentication and encryption.

Only specific security control functions require network access for static environments, which the security manager should keep separate from the corporate network with perimeter security.

When designed for residential use, IoT devices can suffer from weak defaults that customers do not take steps to secure. The security manager can configure them to "work" with a minimum of configuration effort.


# 16
A system administrator is deploying a new web server. Which hardening procedures should the administrator consider? **(Select all that apply.)**

1.  The administrator should use SFTP to transfer files to and from the server remotely.

3.  The administrator should assign a digital certificate and enable the use of TLS 1.3.


Solution

Secure file transfer protocol (SFTP) safely transfers files remotely via SSH.

Transport layer security (TLS) enables secure communication between the client and the web server. This is implemented by assigning a certificate to the web server. TLS 1.3 prevents downgrade attacks.

Most web servers must allow for secure access to guest web access. Guest web access should only be allowed to view content in the website and not from any other web server directory.

Web servers should deploy using configuration templates where possible.