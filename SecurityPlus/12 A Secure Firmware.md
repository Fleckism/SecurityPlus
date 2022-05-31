---
tags: [A_D, Implementation,section]
---
# LESSON INTRODUCTION

Effective network architecture #A_D design, protocol configuration, and the use of appliances such as firewalls and intrusion detection help to provide a secure network environment, but we need to consider the security systems configured on network hosts as well. Security procedures and solutions are complicated by the range of different types of hosts that networks must support, from PCs and laptops to smartphones and embedded controllers.

Lesson Objectives

In this lesson, you will:

-   Implement secure firmware.
-   Implement endpoint security.
-   Explain embedded system security implications.
# EXAM OBJECTIVES COVERED

1.2 Given a scenario, analyze #Ops potential indicators ([[[[IoC]]]]) to determine the type of attack

3.2 Given a scenario, implement host or application security solutions

5.3 Explain the importance of policies to organizational security

The security of the hardware underpinning our network and computing devices is often overlooked. In part, this is because it is difficult for most companies to make their own investigations in this area. They have to rely on the market and security agencies to identify bad actors in supply chains. Nevertheless, it is important that you understand the issues involved in secure systems design so that you can evaluate product offerings and make recommendations for purchasing and device configuration.
# HARDWARE ROOT OF TRUST 

A hardware Root of Trust ([[RoT]]) or trust anchor is a secure subsystem that is able to provide attestation. **Attestation means that a statement made by the system can be trusted by the receiver.** For example, when a computer joins a network, it might submit a report to the network access control ([[NAC]]) server declaring, "My operating system files have not been replaced with malicious versions." The hardware root of trust is used to scan the boot metrics and OS files to verify their signatures, then it signs the report. The NAC server can trust the signature and therefore the report contests if it can trust that the signing entity's private key is secure. 

The RoT is usually established by a type of cryptoprocessor called a trusted platform module ([[TPM]]). TPM is a specification for hardware-based storage of encryption keys, hashed passwords, and other user and platform identification information. The TPM is implemented either as part of the chipset or as an embedded function of the CPU.

Each TPM is hard-coded with a unique, unchangeable asymmetric private key called the endorsement key. This endorsement key is used to create various other types of subkeys used in key storage, signature, and encryption operations. The TPM also supports the concept of an owner, usually identified by a password (though this is not mandatory). Anyone with administrative control over the setup program can take ownership of the [[TPM]], which destroys and then regenerates its subkeys. A TPM can be managed in Windows via the tpm.msc console or through group policy. On an enterprise network, provisioning keys to the TPM might be centrally managed via the Key Management Interoperability Protocol (KMIP).

![Screenshot includes TPM Specification Version (1.2), TPM Device (Available), Clear TPM (No), TPM Activation Policy (Allow user to reject).](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1346-1599771806987.png)

Configuring a Trusted Platform Module using system setup on an HP workstation. (Screenshot used with permission from HP.)

The problem with establishing a hardware root of trust is that devices are used in environments where anyone can get complete control over them. There cannot be complete assurance that the firmware underpinning the hardware root of trust is inviolable, but attacks against trusted modules are sufficiently difficult so as to provide effective security in most cases.
# BOOT INTEGRITY

Most PCs implement the unified extensible firmware interface ([[UEFI]]). UEFI provides code that allows the host to boot to an OS. UEFI can enforce a number of boot integrity checks.

### Secure Boot

Secure boot is designed to prevent a computer from being hijacked by a malicious OS. [[UEFI]] is configured with digital certificates from valid OS vendors. The system firmware checks the operating system boot loader and kernel using the stored certificate to ensure that it has been digitally signed by the OS vendor. This prevents a boot loader or kernel that has been changed by malware (or an OS installed without authorization) from being used. Secure boot is supported on Windows ([docs.microsoft.com/en-us/windows/security/information-protection/secure-the-windows-10-boot-process](https://docs.microsoft.com/en-us/windows/security/information-protection/secure-the-windows-10-boot-process)) and many Linux platforms ([wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)). Secure boot requires UEFI, but does not require a TPM.

### Measured Boot

A trusted or measured boot process uses platform configuration registers ([[PCRs]]) in the [[TPM]] at each stage in the boot process to check whether hashes of key system state data (boot firmware, boot loader, OS kernel, and critical drivers) have changed. This does not usually prevent boot, but it will record the presence of unsigned kernel-level code.

### Boot Attestation

Boot attestation is the capability to transmit a boot log report signed by the TPM via a trusted process to a remote server, such as a network access control server. The boot log can be analyzed for signs of compromise, such as the presence of unsigned drivers. The host can be prevented from accessing the network if it does not meet the required health policy or if no attestation report is received.

![Screenshot shows the configuration option selected: “Legacy Support Disable and Secure Boot Enable.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4559-1599771807065.png)

Configuring secure boot settings via an HP workstation's UEFI firmware setup program. (Screenshot used with permission from HP.)
# DISK ENCRYPTION

Full disk encryption (FDE) means that the entire contents of the drive (or volume), including system files and folders, are encrypted. OS ACL-based security measures are quite simple to circumvent if an adversary can attach the drive to a different host OS. Drive encryption allays this security concern by making the contents of the drive accessible only in combination with the correct encryption key. Disk encryption can be applied to both hard disk drives (HDDs) and solid state drives (SSDs).

FDE requires the secure storage of the key used to encrypt the drive contents. Normally, this is stored in a [[TPM]]. The TPM chip has a secure storage area that a disk encryption program, such as Windows BitLocker, can write its keys to. It is also possible to use a removable USB drive (if USB is a boot device option). As part of the setup process, you create a recovery password or key. This can be used if the disk is moved to another computer or the TPM is damaged.

![Screenshot of BitLocker Drive Encryption window shows Operating system drive as “C: BitLocker off” and a link reads “Turn BitLocker on”.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1023-1599771807178.png)

Activating BitLocker drive encryption. (Screenshot used with permission from Microsoft.)

One of the drawbacks of FDE is that, because the OS performs the cryptographic operations, performance is reduced. This issue is mitigated by self-encrypting drives (SED), where the cryptographic operations are performed by the drive controller. The SED uses a [[symmetric]] data/media encryption key (DEK/MEK) for bulk encryption and stores the [[DEK]] securely by encrypting it with an asymmetric key pair called either the authentication key ([[AK]]) or key encryption key ([[KEK]]). Use of the AK is authenticated by the user password. This means that the user password can be changed without having to decrypt and re-encrypt the drive. Early types of SEDs used proprietary mechanisms, but many vendors now develop to the Opal Storage Specification ([nvmexpress.org/wp-content/uploads/TCGandNVMe_Joint_White_Paper-TCG_Storage_Opal_and_NVMe_FINAL.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/TCGandNVMe_Joint_White_Paper-TCG_Storage_Opal_and_NVMe_FINAL.pdf)), developed by the Trusted Computing Group (TCG).

As configuring passwords on individual drives is a huge challenge when more than a few machines are involved, enterprises may use the Key Management Interoperability Protocol ([[KMIP]]) along with a hardware security module ([[HSM]]) to automate the provisioning of keys ([trustedcomputinggroup.org/wp-content/uploads/SWG_TCG_Enterprise-Introduction_Sept2010.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/SWG_TCG_Enterprise-Introduction_Sept2010.pdf)).
# USB AND FLASH DRIVE SECURITY 

As revealed by researcher Karsten Nohl in his BadUSB paper ([srlabs.de/wp-content/uploads/2014/07/SRLabs-BadUSB-BlackHat-v1.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/SRLabs-BadUSB-BlackHat-v1.pdf)), exploiting the firmware of external storage devices, such as USB flash drives (and potentially any other type of firmware), presents adversaries with an incredible toolkit. The firmware can be reprogrammed to make the device look like another device class, such as a keyboard. In this case it could then be used to inject a series of keystrokes upon an attachment or work as a keylogger. The device could also be programmed to act like a network device and [[corrupt name resolution]], redirecting the user to malicious websites.

Another example is the O.MG cable ([theverge.com/2019/8/15/20807854/apple-mac-lightning-cable-hack-mike-grover-mg-omg-cables-defcon-cybersecurity](https://www.theverge.com/2019/8/15/20807854/apple-mac-lightning-cable-hack-mike-grover-mg-omg-cables-defcon-cybersecurity)), which packs enough processing capability into an ordinary-looking USB-Lightning cable to run an access point and keylogger.

A modified device may have visual clues that distinguish it from a mass manufactured thumb drive or cable, but these may be difficult to spot. You should warn users of the risks and repeat the advice to never attach devices of unknown provenance to their computers and smartphones. If you suspect a device as an [[attack vector]], observe a sandboxed lab system (sometimes referred to as a sheep dip) closely when attaching the device. Look for command prompt windows or processes such as the command interpreter starting and changes to the registry or other system files.

Not all attacks have to be so esoteric. USB sticks infected with ordinary malware are still incredibly prolific infection vectors. Hosts should always be configured to prevent autorun when USB devices are attached. USB ports can be blocked altogether using most types of Host Intrusion Detection Systems (HIDS).
# THIRD-PARTY RISK MANAGEMENT

A root of trust is only trustworthy if the vendor has implemented it properly. Hardware and firmware vulnerabilities and exploits demonstrate the necessity of third-party risk management. A supply chain is the end-to-end process of supplying, manufacturing, distributing, and finally releasing goods and services to a customer. For example, for a Trusted Platform Module (TPM) to be trustworthy, the supply chain of chip manufacturers, firmware authors, OEM resellers, and administrative staff responsible for provisioning the computing device to the end user must all be trustworthy. Anyone with the time and resources to modify the computer's firmware could (in theory) create some sort of backdoor access. The same is true for any kind of computer or network hardware, right down to USB cables.

Establishing a trusted supply chain for computer equipment essentially means denying malicious actors the time or resources to modify the assets being supplied.

For most businesses, use of reputable OEMs will represent the best practical effort at securing the supply chain. Government, military/security services, and large enterprises will exercise greater scrutiny. Particular care should be taken if use is made of second-hand machines.

When assessing suppliers for risk, it is helpful to distinguish two types of relationship:

-   Vendor—this means a supplier of commodity goods and services, possibly with some level of customization and direct support.
-   Business partner—this implies a closer relationship where two companies share quite closely aligned goals and marketing opportunities.

For example, Microsoft is a major software vendor, but it is not feasible for it to establish direct relationships with all its potential customers. To expand its markets, it develops partner relationships with original equipment manufacturers (OEMs) and solution providers. Microsoft operates a program of certification and training for its partners, which improves product support and security awareness.
# END OF LIFE SYSTEMS

When a manufacturer discontinues sales of a product, it enters an end of life (EOL) phase in which support and [[Availability]] of spares and updates become more limited. An end of service life (EOSL) system is one that is no longer supported by its developer or vendor. EOSL products no longer receive security updates and so represent a critical vulnerability if any remain in active use.

For example, in Microsoft's support life cycle policy, Windows versions are generally given five years of mainstream support and five years of extended support (during which only security updates are shipped). You can check the support status for a particular version of Windows at [support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet).

Most OS and application vendors have similar policies. Care also needs to be taken with open source software. If the software is well-maintained, the development group will identify versions that have Long Term Support (LTS). Other builds and version branches might not receive updates.

It is also possible for both open source and commercial projects to be abandoned; if a company continues to rely on such abandonware, it will have to assume development responsibility for it. There are many instances of applications and devices (peripheral devices especially) that remain on sale with serious known vulnerabilities in firmware or drivers and no prospect of vendor support for a fix. The problem is also noticeable in consumer-grade networking appliances and in the Internet of Things. When provisioning a supplier for applications and devices, it is vital to establish that they have effective security management life cycles for their products.
# ORGANIZATIONAL SECURITY [[AGREEMENTS]] 

It is important to remember that although one can outsource virtually any service or activity to a third party, one cannot outsource legal accountability for these services or actions. You are ultimately responsible for the services and actions that these third parties take. If they have any access to your data or systems, any security breach in their organization (for example, unauthorized data sharing) is effectively a breach in yours. Issues of security risk awareness, shared duties, and contractual responsibilities can be set out in a formal legal agreement. The following types of agreements are common:

-   Memorandum of understanding ([[MOU]])—A preliminary or exploratory agreement to express an intent to work together. MOUs are usually intended to be relatively informal and not to act as binding contracts. MOUs almost always have clauses stating that the parties shall respect confidentiality, however.
-   Business partnership agreement (BPA)—While there are many ways of establishing business partnerships, the most common model in IT is the partner agreements that large IT companies (such as Microsoft and Cisco) set up with resellers and solution providers.
-   Nondisclosure agreement (NDA)—Legal basis for protecting information assets. NDAs are used between companies and employees, between companies and contractors, and between two companies. If the employee or contractor breaks this agreement and does share such information, they may face legal consequences. NDAs are useful because they deter employees and contractors from violating the trust that an employer places in them.
-   Service level agreement (SLA)—A contractual agreement setting out the detailed terms under which a service is provided.
-   Measurement systems analysis (MSA)—quality management processes, such as Six Sigma, make use of quantified analysis methods to determine the effectiveness of a system. This can be applied to cybersecurity procedures, such as vulnerability and threat detection and response. A measurement systems analysis (MSA) is a means of evaluating the data collection and statistical methods used by a quality management process to ensure they are robust. This might be an onboarding requirement when partnering with enterprise companies or government agencies.

A legal agreement is all very well, but it is still up to you to make sure that your suppliers, vendors, and contractors can live up to it. If they can't, you may successfully sue them, but if they go out of business, you are still accountable for their actions or failures to act.

Conversely, you need to ensure that you can comply with the requirements and performance standards of any agreements that you enter into as a service provider.
