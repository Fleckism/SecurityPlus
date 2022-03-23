---
tags: [Implementation]
---
# LESSON INTRODUCTION
#zFleck
Mobile devices are now the preferred client for many common work tasks, and network management and security systems have had to adapt to accommodate them. The shift toward mobile also presages a move toward unified management of endpoints, and the use of virtualized workspaces as a better model for provisioning corporate apps and data processing. 

Lesson Objectives

In this lesson, you will:

-   Implement mobile device management.
-   Implement secure mobile device connections.
# EXAM OBJECTIVES COVERED

3.5 Given a scenario, implement secure mobile solutions

As use of mobiles has permeated every type of organization, network management and security [[suites]] have developed to ensure that they are not exploited as unmanaged attack vectors. As a security professional, you will often have to configure these management suites, and assist users with the device onboarding process.

Play Video
# MOBILE DEVICE DEPLOYMENT MODELS

Mobile devices have replaced computers for many email and daily management tasks and are integral to accessing many other business processes and cloud-based applications. A mobile device deployment model describes the way employees are provided with mobile devices and applications.

-   **Bring your own device (BYOD)**—the mobile device is owned by the employee. The mobile will have to meet whatever profile is required by the company (in terms of OS version and functionality) and the employee will have to agree on the installation of corporate apps and to some level of oversight and auditing. This model is usually the most popular with employees but poses the most difficulties for security and network managers.
-   **Corporate owned, business only (COBO)**—the device is the property of the company and may only be used for company business.
-   **Corporate owned, personally-enabled (COPE)**—the device is chosen and supplied by the company and remains its property. The employee may use it to access personal email and social media accounts and for personal web browsing (subject to whatever acceptable use policies are in force).
-   **Choose your own device (CYOD)**—much the same as COPE but the employee is given a choice of device from a list.

**Virtualization can provide an additional deployment model. Virtual desktop infrastructure (VDI)** means provisioning an OS desktop to interchangeable hardware. The hardware only has to be capable of running a VDI client viewer, or have browser support for a clientless HTML5 solution. The instance is provided "as new" for each session and can be accessed remotely. The same technology can be accessed via a mobile device such as a smartphone or tablet. This removes some of the security concerns about BYOD as the corporate apps and data are segmented from the other apps on the device.
# ENTERPRISE MOBILITY MANAGEMENT

Enterprise mobility management ([[EMM]]) is a class of management [[software]] designed to apply security policies to the use of mobile devices and apps in the enterprise. The challenge of identifying and managing attached devices is often referred to as visibility. EMM software can be used to manage enterprise-owned devices as well as BYOD. There are two main functions of an EMM product suite:

-   **Mobile device management** (MDM)—sets device policies for authentication, feature use (camera and microphone), and connectivity. MDM can also allow device resets and remote wipes.
-   **Mobile application management** (MAM)—sets policies for apps that can process corporate data, and prevents data transfer to personal apps. This type of solution configures an enterprise-managed container or workspace.

**Additionally, distinguishing whether client endpoints are mobile or fixed is not really a critical factor** for many of these management tasks, with the consequence that the latest suites aim for visibility across PC, laptop, smartphone, tablet, and even IoT devices. These suites are called unified **endpoint managemen**t (UEM) ([redmondmag.com/Articles/2017/10/01/Unified-Endpoint-Management.aspx](https://redmondmag.com/Articles/2017/10/01/Unified-Endpoint-Management.aspx)).

**The core functionality of endpoint management suites extends the concept of network access control** ([[NAC]]) solutions. The management software logs the use of a device on the network and determines whether to allow it to connect or not, based on administrator-set parameters. When the device is enrolled with the management software, it can be configured with policies to allow or restrict use of apps, corporate data, and built-in functions, such as a video camera or microphone.

Some EMM/UEM solutions include AirWatch ([air-watch.com](https://www.air-watch.com/)), Microsoft Intune ([microsoft.com/en-us/microsoft-365/enterprise-mobility-security/microsoft-intune](https://www.microsoft.com/en-us/microsoft-365/enterprise-mobility-security/microsoft-intune)), Symantec/Broadcom ([broadcom.com/products/cyber-security/endpoint/end-user/protection-mobile](https://www.broadcom.com/products/cyber-security/endpoint/end-user/protection-mobile)), and Citrix Endpoint Management (formerly XenMobile) ([citrix.com/products/citrix-endpoint-management](https://www.citrix.com/products/citrix-endpoint-management/)).
# IOS IN THE ENTERPRISE 

In Apple's iOS ecosystem, third-party developers can create apps using Apple's Software Development Kit, available only on macOS. Apps have to be submitted to and approved by Apple before they are released to users via the App Store. Corporate control over iOS devices and distribution of corporate and B2B (Business-to-Business) apps is facilitated by participating in the Device Enrollment Program ([support.apple.com/business](https://support.apple.com/business)), the Volume Purchase Program, and the Developer Enterprise Program ([developer.apple.com/programs/enterprise](https://developer.apple.com/programs/enterprise/)). Another option is to use an EMM suite and its development tools to create a "wrapper" for the corporate app.

![Device enrollment screen has 3 sections: Apple Certificates, Enrollment Program for Apple, Manage Apple Configurator Enrollment Settings](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2842-1599771807462.png)

Configuring iOS device enrollment in Microsoft's Intune EMM suite. (Screenshot used with permission from Microsoft.)

Most iOS attacks are the same as with any system; users click malicious links or enter information into phishing sites, for instance. As a closed and proprietary system, **it should not be possible for malware to infect an iOS device as all code is updated from Apple's servers only.** There remains the risk that a vulnerability in either iOS or an app could be discovered and exploited. In this event, users would need to update iOS or the app to a version that mitigates the exploit.
# ANDROID IN THE ENTERPRISE 

Android's open source basis means that there is more scope for vendor-specific versions. The app model is also more relaxed, with apps available from both Google Play and third-party sites, such as Amazon's app store. The [[SDK]] is available on Linux, Windows, and macOS. The Android Enterprise ([android.com/enterprise](https://www.android.com/enterprise/)) program facilitates use of EMM suites and the containerization of corporate workspaces. Additionally, Samsung has a workspace framework called KNOX ([samsung.com/us/business/solutions/samsung-knox](https://www.samsung.com/us/business/solutions/samsung-knox/)) to facilitate EMM control over device functionality.

![Company Access Setup screen has 3 items: Work Profile Setup, Device Enrollment, and Device Compliance with a “Continue” button.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5120-1599771807547.png)

Enrolling an Android smartphone with Intune. (Android is a trademark of Google LLC.)

iOS devices are normally updated very quickly. With Android, the situation is less consistent, as updates often depend on the handset vendor to complete the new version or issue the patch for their flavor of Android. Android OS is more open and there is Android malware, though as with Apple it is difficult for would-be hackers and spammers to get it into any of the major app repositories.

One technique used is called [[Staged Payloads]]. The malware writers release an app that appears innocuous in the store but once installed it attempts to download additional components infected with malware ([zdnet.com/article/android-security-sneaky-three-stage-malware-found-in-google-play-store](https://www.zdnet.com/article/android-security-sneaky-three-stage-malware-found-in-google-play-store/)). Google has implemented a server-side malware scanning product (Play Protect) that will both warn users if an app is potentially damaging and scan apps that have already been purchased, and warn the user if any security issues have been discovered.

Since version 4.3, Android has been based on Security-Enhanced Linux. SEAndroid ([source.android.com/security/selinux](https://source.android.com/security/selinux)) uses mandatory access control ([[MAC]]) policies to run apps in sandboxes. When the app is installed, access is granted (or not) to specific shared features, such as contact details, SMS texting, and email. 

![3 screens show WhatsApp with Install button, dialog box asking “Allow WhatsApp to access photos, media and files on your device?”, and App info screen](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7856-1599771807606.png)

Configuring app permissions in Android OS. (Android is a trademark of Google LLC.)
# MOBILE ACCESS CONTROL SYSTEMS 

If a threat actor is able to gain access to a smartphone or tablet, they can obtain a huge amount of information and the tools with which to launch further attacks. Quite apart from confidential data files that might be stored on the device, it is highly likely that the user has cached passwords for services such as email or remote access VPN and websites. 

### Smartphone Authentication

**The majority of smartphones and tablets are single-user devices.** Access control can be implemented by configuring a screen lock that can only be bypassed using the correct password, PIN, or swipe pattern. Many devices now support biometric authentication, usually as a fingerprint reader but sometimes using facial or voice recognition.

![12 configuration settings for Work profile are available: 3 General Settings and 9 Work Profile Password settings.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/6904-1599771808117.png)

Configuring authentication and profile policies using Intune [[EMM]]—Note that the policy allows the user to have a different type of authentication (or none at all) to the workspace hosting corporate apps and data. (Screenshot used with permission from Microsoft.)

Strong passwords should always be set on mobile devices, as simple 4-digit PIN codes can easily be brute-forced. Swipe patterns are vulnerable to poor user choices ([arstechnica.com/information-technology/2015/08/new-data-uncovers-the-surprising-predictability-of-android-lock-patterns](https://arstechnica.com/information-technology/2015/08/new-data-uncovers-the-surprising-predictability-of-android-lock-patterns/)), such as choosing letter or box patterns, plus the tendency for the grease trail to facilitate a smudge attack.

### Screen Lock

The screen lock can also be configured with a lockout policy. This means that if an incorrect passcode is entered, the device locks for a set period. **This could be configured to escalate** (so the first incorrect attempt locks the device for 30 seconds while the third locks it for 10 minutes, for instance). This deters attempts to guess the passcode.

### Context-Aware Authentication

It is also important to consider newer authentication models, such as context-aware authentication. For example, smartphones now allow users to disable screen locks when the device detects that it is in a trusted location, such as the home. Conversely, an enterprise may seek more stringent access controls to prevent misuse of a device. For example, even if the device has been unlocked, accessing a corporate workspace might require the user to authenticate again. It might also check whether the network connection can be trusted (that it is not an open Wi-Fi hotspot, for instance).
# REMOTE WIPE

A remote wipe or kill switch means that if the handset is stolen it can be **set to the factory defaults or cleared of any personal data (sanitization)**. Some utilities may also be able to wipe any plug-in memory cards too. The remote wipe could be triggered by several incorrect passcode attempts or by enterprise management software. Other features include backing up data from the phone to a server first and displaying a "Lost/stolen phone—return to XX" message on the handset.

![Screen shows Exchange highlighted and a list of ActiveSync devices that can be wiped or deleted including a Moto G (5), XT1032, iPad2C5, and iPhone.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8822-1599771808197.png)

Most corporate messaging systems come with a remote wipe feature (such as this one provided with Intermedia mail hosting), allowing mail, calendar, and contacts information to be deleted from mobile devices. (Screenshot used with permission from Intermedia.)

**In theory, a thief can prevent a remote wipe by ensuring the phone cannot connect to the network, then hacking the phone and disabling the security.**
# FULL DEVICE ENCRYPTION AND EXTERNAL MEDIA

All but the early versions of mobile device OSes for smartphones and tablets provide full device encryption. In iOS, there are various levels of encryption.

-   **All user data on the device is always encrypted but the key is stored on the device. This is primarily used as a means of wiping the device. The OS just needs to delete the key to make the data inaccessible rather than wiping each storage location.**
-   **Email data and any apps using the "Data Protection" option are subject to a second round of encryption using a key derived from and protected by the user's credential**. This provides security for data in the event that the device is stolen. Not all user data is encrypted using the "Data Protection" option; contacts, **SMS messages**, and pictures are not, for example.

In iOS, Data Protection encryption is enabled automatically when you configure a password lock on the device. In Android, there are substantial differences to encryption options between versions ([source.android.com/security/encryption](https://source.android.com/security/encryption)). As of Android 10, there is no full disk encryption as it is considered too detrimental to performance. User data is encrypted at file-level by default.

A mobile device contains a solid state (flash memory) drive for persistent storage of apps and data. Some Android handsets support removable storage using external media, such as a plug-in Micro **SecureDigital** (SD) card slot; some may support the connection of USB-based storage devices. The mobile OS encryption software might allow encryption of the removable storage too but this is not always the case. Care should be taken to apply encryption to storage cards using third-party software if necessary and to limit sensitive data being stored on them.

A MicroSD HSM is a small form factor hardware security module designed to store cryptographic keys securely. This allows the cryptographic material to be used with different devices, such as a laptop and smartphone.
# LOCATION SERVICES 

Geolocation is the use of network attributes to identify (or estimate) the physical position of a device. The device uses location services to determine its current position. Location services can make use of two systems:

-   **Global Positioning System** (GPS)—a means of determining the device's **latitude and longitude** based on information received from satellites via a GPS sensor.
-   **Indoor Positioning System** (IPS)—works out a device's location by triangulating its proximity to other radio sources, such as cell towers, Wi-Fi access points, and Bluetooth/RFID beacons.

Location services is available to any app where the user has granted the app permission to use it.

![Screen identifies device and shows map with a smartphone icon located on it; 2 options are available: Play Sound and Enable Lock &amp; Erase.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4598-1599771808258.png)

Using Find My Device to locate an Android smartphone. (Android is a trademark of Google LLC.)

The primary concern surrounding location services is one of privacy. Although very useful for maps and turn-by-turn navigation, it provides a mechanism to track an individual's movements, and therefore their social and business habits. The problem is further compounded by the plethora of mobile apps that require access to location services and then both send the information to the application developers and store it within the device's file structure. If an attacker can gain access to this data, **then stalking, social engineering,** and even identity theft become real possibilities.

### Geofencing and Camera/Microphone Enforcement

Geofencing is the practice of creating a virtual boundary based on real-world geography. Geofencing can be a useful tool with respect to controlling the use of camera or video functions or applying context-aware authentication. An organization may use geofencing to create a perimeter around its office property, and subsequently, limit the functionality of any devices that exceed this boundary. **An unlocked smartphone could be locked and forced to reauthenticate when entering the premises,** and the camera and microphone could be disabled. The device's position is obtained from location services.

![Screen shows 11 configuration settings for General are available (to set as Block or Not configured) but 9 are labeled “(Samsung KNOX only)”.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1047-1599771808357.png)

Restricting device permissions such as camera and screen capture using Intune. (Screenshot used with permission from Microsoft.)

### GPS Tagging

GPS tagging is the process of adding geographical identification metadata, such as the latitude and longitude where the device was located at the time, to media such as photographs, SMS messages, video, and so on. It allows the app to place the media at specific latitude and longitude coordinates. GPS tagging is highly sensitive personal information and potentially confidential organizational data also. GPS tagged pictures uploaded to social media could be used to track a person's movements and location. For example, a Russian soldier revealed troop positions by uploading GPS tagged selfies to Instagram ([arstechnica.com/tech-policy/2014/08/opposite-of-opsec-russian-soldier-posts-selfies-from-inside-ukraine](https://arstechnica.com/tech-policy/2014/08/opposite-of-opsec-russian-soldier-posts-selfies-from-inside-ukraine/)).
# APPLICATION MANAGEMENT 

When a device is joined to the corporate network through enrollment with management software, it can be configured into an enterprise workspace mode in which only a certain number of authorized applications can run.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9150-1599771808461.png)

Endpoint management software such as Microsoft Intune can be used to approve or prohibit apps. (Screenshot used with permission from Microsoft.)

A trusted app source is one that is managed by a service provider. The service provider authenticates and authorizes valid developers, issuing them with a certificate to use to sign their apps and warrant them as trusted. It may also analyze code submitted to ensure that it does not pose a security or privacy risk to its customers (or remove apps that are discovered to pose such a risk). It may apply other policies that developers must meet, such as not allowing apps with adult content or apps that duplicate the function of core OS apps.

The mobile OS defaults to restricting app installations to the linked store (App Store for iOS and Play for Android). Most consumers are happy with this model but it does not work so well for enterprises. It might not be appropriate to deliver a custom corporate app via a public store, where anyone could download it. Apple operates enterprise developer and distribution programs to solve this problem, allowing private app distribution via Apple Business Manager ([developer.apple.com/business/distribute](https://developer.apple.com/business/distribute/)). Google's Play store has a private channel option, called Managed Google Play. Both these options allow an EMM/UEM suite to **push apps from the private channel to the device.** 

Unlike iOS, Android allows for selection of different stores and installation of untrusted apps from any third party, if this option is enabled by the user. With **unknown sources enabled**, untrusted apps can be downloaded from a website and installed using the .apk file format. This is referred to as **sideloading**. 

Conversely, a management suite might be used to prevent the use of third-party stores or sideloading and block unapproved app sources.
# CONTENT MANAGEMENT 

Containerization allows the employer to manage and maintain the portion of the device that interfaces with the corporate network. An enterprise workspace with a defined selection of apps and a separate container is created. **This container isolates corporate apps from the rest of the device. There may be a requirement for additional authentication to access the workspace.**

The container can also enforce storage segmentation. With storage segmentation the container is associated with a directory on the persistent storage device that is not readable or writable by apps that are not in the container. Conversely, apps cannot write to areas outside the container, such as external media or using copy and paste to a non-container app. App network access might be restricted to a VPN tunneled through the organization's security system.

The enterprise is thereby able to maintain the security it needs, without having to enforce policies that affect personal use, apps, or data. 

**Containerization also assists content management and data loss prevention (DLP) systems.** A content management system tags corporate or confidential data and prevents it from being shared or copied to unauthorized external media or channels, such as non-corporate email systems or cloud storage services.
# ROOTING AND JAILBREAKING 

Like Windows and Linux, the account used to install the OS and run kernel-level processes is not the one used by the device owner. Users who want to avoid the restrictions that some OS vendors, handset OEMs, and telecom providers (carriers) put on the devices must use some type of privilege escalation:

-   **Rooting**—this term is associated with Android devices. Some vendors provide authorized mechanisms for users to access the root account on their device. For some devices it is necessary to exploit a vulnerability or use custom firmware. **Custom firmware** is essentially a new Android OS image applied to the device. This can also be referred to as a custom ROM, after the term for the read only memory chips that used to hold firmware.
-   **Jailbreaking**—iOS is more restrictive than Android so the term "jailbreaking" became popular for exploits that enabled the user to obtain root privileges, sideload apps, change or add carriers, and customize the interface. iOS jailbreaking is accomplished by booting the device with a patched kernel. For most exploits, this can only be done when the device is attached to a computer when it boots (tethered jailbreak).
-   **Carrier unlocking**—for either iOS or Android, this means removing the restrictions that lock a device to a single carrier.

Rooting or jailbreaking mobile devices involves subverting the security measures on the device to gain administrative access to it. This also has the side effect of leaving many security measures permanently disabled. If the user has root permissions, then essentially any management agent software running on the device is compromised. If the user has applied a custom firmware image, they could have removed the protections that enforce segmentation. The device can no longer be assumed to run a trusted OS.

[[EMM]]/[[UEM]] has routines to detect a rooted or jailbroken device or custom firmware with no valid developer code signature and prevent access to an enterprise app, network, or workspace. Containerization and enterprise workspaces can use cryptography to protect the workspace in a way that is much harder to compromise than a local agent, even from a rooted/jailbroken device.
