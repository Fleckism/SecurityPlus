---
tags: [implementation,section]
---
# EXAM OBJECTIVES COVERED

2.6 Explain the security implications of embedded and specialized systems

As well as the obvious computing hosts within your networks, you must also account for the security of embedded systems. Embedded computing functionality can be found in consumer electronics devices and in specialist monitoring and control systems, so it is important that you know how to identify and secure these devices.
# EMBEDDED SYSTEMS

**An embedded system is a complete computer system that is designed to perform a specific, dedicated function.** These systems can be as contained as a microcontroller in an intravenous drip-rate meter or as large and complex as the network of control devices managing a water treatment plant. **Embedded systems can be characterized as static environments**. A **PC is a dynamic environment**. The user can add or remove programs and data files, install new hardware components, and upgrade the operating system. **A static environment does not allow or require such frequent changes.**

In terms of security this can be ideal, because unchanging environments are typically easier to protect and defend. Static computing environments pose their own risks, however. A static environment is often a black box to security administrators. Unlike an OS environment such as Windows, there may be little support for identifying and correcting security issues.

### Cost, Power, and Compute Constraints

Embedded systems are usually constrained in terms of processor capability (cores and speed), system memory, and persistent storage. Cost is an important factor. As devices may be used in large numbers and are designed for fairly predictable processing workloads, there is no obvious reason to over-provision compute resources and the price per unit can be driven as low as possible.

The other factor determining compute resources is power. Many embedded devices are battery-powered, and may need to run for years without having to replace the cells. This means that processing must be kept to the minimum possible level.

### Crypto, Authentication, and Implied Trust Constraints

The lack of computer resources means that embedded systems are not well-matched to the cryptographic identification and authentication technologies that are widely used on computer networks. As embedded systems become more accessible via those networks, however, they need to use **cryptoprocessors to ensure confidentiality, integrity, and [[My linked notes/Dictionary/Availability]].** This is prompting the development of ciphers that do not require such large processing resources.

On PC hardware, a [[root of trust]] is established at the hardware level by a [[TPM]]. Without this explicit trust anchor, a network has to use an implied trust model. Implied trust means that every device that has been added to the network is trusted, on the assumption that it was added and continues to be operated by a legitimate administrator. Until there is widespread adoption of embedded TPM, **embedded networks have to rely on the perimeter security model.**

### Network and Range Constraints

Minimizing compute functions also has an impact on choices for network connectivity. The Wi-Fi and 4G/5G standards developed for use with computer and smartphone networking use power-hungry antennas to maximize data rates and range, plus processing to encrypt the communications. **Networks for embedded systems emphasize power-efficient transfer of small amounts of data with a high degree of reliability and low latency.**
# LOGIC CONTROLLERS FOR EMBEDDED SYSTEMS

Embedded systems are normally based on firmware running on a programmable logic controller (PLC). These PLCs are built from different hardware and OS components than some desktop PCs. 

### System on Chip (SoC)

Desktop computer system architecture #A_D uses a generalized CPU plus various other processors and controllers and system memory, linked via the motherboard. System on chip (SoC) is a design where all these processors, controllers, and devices are provided on a single processor die (or chip). This type of packaging saves space and is usually power efficient, and so is very commonly used with embedded systems.

**Raspberry Pi** ([raspberrypi.org](https://www.raspberrypi.org/)) and **Arduino** ([arduino.cc](https://www.arduino.cc/)) are examples of SoC boards, initially devised as educational tools, but now widely used for industrial applications, and hacking.

### Field Programmable Gate Array (FPGA)

A microcontroller is a processing unit that can perform sequential operations from a dedicated instruction set. The instruction set is determined by the vendor at the time of manufacture. Software running on the microcontroller has to be converted to these instructions (assembly language). As many embedded systems perform relatively simple but repetitive operations, it can be more efficient to design the hardware controller to perform only the instructions needed. One example of this is the application-specific integrated circuits (ASICs) used in Ethernet switches. ASICs are expensive to design, however, and work only for a single application, such as Ethernet switching.

A **field programmable gate array (FPGA) is a type of controller that solves this problem. The structure of the controller is not fully set at the time of manufacture. The end customer can configure the programming logic of the device to run a specific application.**

### Real-Time Operating Systems (RTOS)

Many embedded systems operate devices that perform acutely time-sensitive tasks, such as drip meters or flow valves. **The kernels or operating systems that run these devices must be much more stable and reliable than the OS that runs a desktop computer or server**. Embedded systems typically cannot tolerate reboots or crashes and must have response times that are predictable to within microsecond tolerances. Consequently, these systems often use differently engineered platforms called real-time operating systems (RTOS). An RTOS should be designed to have as small an attack surface as possible. An RTOS is still susceptible to [[CVE|CVEs]] and exploits, however.
# EMBEDDED SYSTEMS COMMUNICATIONS CONSIDERATIONS 

Historically, embedded systems used proprietary vendor communications technologies. As technologies improve and closer integration with IT networks becomes more important, greater use of standardized communication technologies is becoming more prevalent.

### Operational Technology (OT) Networks

**A cabled network for industrial applications is referred to as an operational technology (OT) network**. These typically use either serial data protocols or industrial Ethernet. Industrial Ethernet is optimized for real-time, deterministic transfers. Such networks might use vendor-developed data link and networking protocols, as well as specialist application protocols.

### Cellular Networks

A cellular network enables long-distance communication over the same system that supports mobile and smartphones. This is also called **baseband radio**, after the baseband processor that performs the function of a cellular modem. There are several baseband radio technologies:

-   **Narrowband-IoT (NB-IoT)**—this refers to a low-power version of the Long Term Evolution (LTE) or 4G cellular standard. The signal occupies less bandwidth than regular cellular. This means that data rates are limited (**20-100 kbps**), but most sensors need to send small packets with low latency, rather than making large data transfers. Narrowband also has greater penetrating power, making it more suitable for use in inaccessible locations, such as tunnels or deep within buildings, where ordinary cellular connectivity would be impossible.
-   **LTE Machine Type Communication (LTE-M)**—this is another low-power system, but supports higher bandwidth (up to about 1 Mbps).

While not yet completely standardized, both NB-IoT and LTE-M are designed to be compatible with 5G networks. This means they do not interfere with 5G signaling and can use tower relays developed for 5G. They may support higher data rates, though latency and reliability tend to be more important considerations.

Any LTE-based cellular radio uses a subscriber identity module (SIM) card as an identifier. The SIM is issued by a cellular provider, with roaming to allow use of other suppliers' tower relays. As a removable card is not really a suitable form factor for embedded, an eSIM incorporates the same function as a chip on the system board or SoC design.

Encryption of frames between the endpoint and the cell tower and within the backhaul to Internet routers is the responsibility of the network operator. Over-the-air encryption is performed by encryption schemes devised by the cellular standards body 3GPP. Backhaul security is usually enforced using IPSec. The embedded system can use application layer encryption for additional security.

### Z-Wave and Zigbee

Z-Wave and Zigbee are wireless communications protocols used primarily for home automation. Both create a mesh network topology, using low-energy radio waves to communicate from one appliance to another. In Z-Wave, devices can be configured to work as repeaters to extend the network but there is a limit of four "hops" between a controller device and an endpoint. Z-Wave uses ~900 Mhz frequencies.

Zigbee has similar uses to Z-Wave and is an open source competitor technology to it. The Zigbee Alliance operates certification programs for its various technologies and standards. Zigbee uses the 2.4 GHz frequency band. This higher frequency allows more data bandwidth at the expense of range compared to Z-Wave and the greater risk of interference from other 2.4 GHz radio communications. Zigbee supports more overall devices within a single network and there is no hop limit for communication between devices.

Both Z-Wave and Zigbee have communications encryption. The main threats are from re-pairing attacks and from rogue devices. A re-pairing attack allows a [[threat actor]] to discover the network key by forcing a device off the network, causing it to try to re-connect ([checkpoint.com/press/2020/the-dark-side-of-smart-lighting-check-point-research-shows-how-business-and-home-networks-can-be-hacked-from-a-lightbulb](https://www.checkpoint.com/press/2020/the-dark-side-of-smart-lighting-check-point-research-shows-how-business-and-home-networks-can-be-hacked-from-a-lightbulb/)). **If the user connects a rogue device to the network, the system depends on application-level security to prevent the device from compromising higher value targets, such as a smart hub, alarm, or door entry mechanism.**
# INDUSTRIAL CONTROL SYSTEMS

Industrial systems have different priorities to IT systems. Often, hazardous electromechanical components are involved, so safety is the overriding priority. **Industrial processes also prioritize [[My linked notes/Dictionary/Availability]] and integrity over confidentiality—reversing the [[CIA]] triad as the AIC triad.**

### Workflow and Process Automation Systems

Industrial control systems ([[ICS]]s) provide mechanisms for workflow and process automation. These systems control machinery used in critical infrastructure, like power suppliers, water suppliers, health services, telecommunications, and national security services. An ICS that manages process automation within a single site is usually referred to as a distributed control system ([[DCS]]).

An ICS comprises plant devices and equipment with embedded PLCs. The PLCs are linked either by an OT fieldbus serial network or by industrial Ethernet to actuators that operate valves, motors, circuit breakers, and other mechanical components, plus sensors that monitor some local state, such as temperature. Output and configuration of a PLC is performed by one or more human-machine interfaces (HMIs). An HMI might be a local control panel or software running on a computing host. PLCs are connected within a control loop, and the whole process automation system can be governed by a control server. Another important concept is the data historian, which is a database of all the information generated by the control loop.

### Supervisory Control and Data Acquisition (SCADA)

A supervisory control and data acquisition (SCADA) system takes the place of a control server in large-scale, multiple-site ICSs. SCADA typically run as software on ordinary computers, gathering data from and managing plant devices and equipment with embedded PLCs, referred to as field devices. SCADA typically use WAN communications, such as cellular or satellite, to link the SCADA server to field devices.

### ICS/SCADA Applications

These types of systems are used within many sectors of industry:

-   **Energy** refers to power generation and distribution. More widely, utilities includes water/sewage and transportation networks.
-   **Industrial** can refer specifically to the process of mining and refining raw materials, involving hazardous high heat and pressure furnaces, presses, centrifuges, pumps, and so on.
-   **Fabrication and manufacturing** refer to creating components and assembling them into products. Embedded systems are used to control automated production systems, such as forges, mills, and assembly lines. These systems must work to extremely high precisions.
-   **Logistics** refers to moving things from where they were made or assembled to where they need to be, either within a factory or for distribution to customers. Embedded technology is used in control of automated transport and lift systems plus sensors for component tracking.
-   **Facilities** refers to site and building management systems, typically operating automated heating, ventilation, and air conditioning (HVAC), lighting, and security systems.

ICS/SCADA was historically built without regard to IT security, though there is now high awareness of the necessity of enforcing security controls to protect them, especially when they operate in a networked environment. 

One infamous example of an attack on an embedded system is the Stuxnet worm ([wired.com/2014/11/countdown-to-zero-day-stuxnet](https://www.wired.com/2014/11/countdown-to-zero-day-stuxnet/)). This was designed to attack the SCADA management software running on Windows PCs to damage the centrifuges used by Iran's nuclear fuels program. NIST Special Publication 800-82 covers some recommendations for implementing security controls for ICS and SCADA ([nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-82r2.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/NIST.SP.800-82r2.pdf)).
# INTERNET OF THINGS

The term Internet of Things (**IoT**) is used to describe a global network of appliances and personal devices that have been equipped with sensors, software, and network connectivity. This compute functionality allows these objects to communicate and pass data between themselves and other traditional systems like computer servers. This is often referred to as Machine to Machine (M2M) communication. Each “thing” is identified with some form of unique serial number or code embedded within its own operating or control system and is able to inter-operate within the existing Internet infrastructure either directly or via an intermediary. An IoT network will generally use the following types of components:

-   **Hub/control system**—IoT devices usually require a communications hub to facilitate Z-Wave or Zigbee networking. There must also be a control system, as most IoT devices are headless, meaning they have no user control interface. This could be a smart hub, with voice control, or a smartphone/PC app.
-   **Smart devices**—IoT endpoints implement the function, such as a smart lightbulb or a video entryphone that you can operate remotely. These devices implement compute, storage, and network functions that are all potentially vulnerable to exploits. Most smart devices use a Linux or Android kernel. Because they're effectively running mini-computers, smart devices are vulnerable to some of the standard attacks associated with web applications and network functions. Integrated peripherals such as cameras or microphones could be compromised to facilitate surveillance.
-   **Wearables**—some IoT devices are designed as personal accessories, such as smart watches, bracelets and pendant fitness monitors, and eyeglasses. Current competing technologies are based on FitBit, Android Wear OS, Samsung's Tizen OS, and Apple iOS, each with their own separate app ecosystems.
-   **Sensors**—IoT devices need to measure all kinds of things, including temperature, light levels, humidity, pressure, proximity, motion, gas/chemicals/smoke, heart/breathing rates, and so on. These are implemented as thermocouples/thermistors, infrared detectors, inductive, photoelectric, and capacitative cells, accelerometers, gyroscopes, and more.

Home automation products often use vendor-specific software and networking protocols. As with embedded devices, security features can be poorly documented, and patch management/security response processes of vendors can be inadequate. When they are designed for residential use, IoT devices can suffer from weak defaults. They may be configured to "work" with a minimum of configuration effort. There may be recommended steps to secure the device that the customer never takes.
# SPECIALIZED SYSTEMS FOR FACILITY AUTOMATION

A specialized system refers to the use of embedded systems and/or IoT devices for a specific purpose or application.

### Building Automation System (BAS) 

A building automation system (BAS) for offices and data centers ("smart buildings") can include physical access control systems, but also heating, ventilation, and air conditioning (HVAC), fire control, power and lighting, and elevators and escalators. These subsystems are implemented by PLCs and various types of sensors that measure temperature, air pressure, humidity, room occupancy, and so on. Some typical vulnerabilities that affect these systems include:

-   **Process and memory vulnerabilities**, such as buffer overflow, in the PLCs. These may arise from processing maliciously crafted packets in the automation management protocol. Building automation uses dedicated network protocols, such as BACnet or Dynet.
-   Use of plaintext credentials or cryptographic keys within application code.
-   **Code injection** via the graphical web application interfaces used to configure and monitor systems. This can be used to perform JavaScript-based attacks, such as clickjacking and cross-site scripting (XSS).

It is possible that control of these systems could be used to perform some sort of [[DoS]] or ransom demand (consider disrupting HVAC controls within a data center, for instance). However, as with the Target data breach, the aim is likely to access the corporate data network from the automation and monitoring system, which may be accessible via a supplier company ([krebsonsecurity.com/tag/fazio-mechanical](https://krebsonsecurity.com/tag/fazio-mechanical/)).

### Smart Meters

A smart meter provides continually updating reports of electricity, gas, or water usage to the supplier, reducing the need for manual inspections. Most meters use cellular data for communication back to the supplier, and an IoT protocol, such as ZigBee, for integration with smart appliances.  

### Surveillance Systems

A physical access control system ([[PACS]]) is a network of monitored locks, intruder alarms, and video surveillance. A PACS can either be implemented as part of a building automation system or a separate system in its own right. Gaining physical access to premises, or even just access to video monitoring systems, gives an adversary many opportunities to develop additional attacks. As with building automation, a PACS is likely to be installed and maintained by an external supplier. This can lead to it being omitted from risk and vulnerability assessments, as highlighted by the US Government Accountability Office's 2014 report into PACS at federal offices ([gao.gov/assets/670/667512.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/667512.pdf)).

Physical security systems use networked camera systems (CCTV) for surveillance. Unfortunately, some makes of camera systems have been found to have numerous serious vulnerabilities that allow attackers either to prevent intrusions from being recorded or to hijack the cameras to perform their own surveillance. These issues tend to affect cheap consumer-grade systems rather than enterprise models, but in both cases it is necessary to evaluate the supplier to demonstrate that their security monitoring and remediation support services are effective.
# SPECIALIZED SYSTEMS IN IT

There are also specialized systems installed within office networks, such as printer and Voice over IP (VoIP) equipment. These systems must not be overlooked by security monitoring procedures.

### Multifunction Printers (MFPs)

Most modern print devices, scanners, and fax machines have hard drives and sophisticated firmware, allowing their use without attachment to a computer and over a network. Often these print/scan/fax functions are performed by single devices, referred to as multifunction printers (MFPs). Unless they have been securely deleted, images and documents are frequently recoverable from all of these machines. Some of the more feature-rich, networked printers and MFPs can also be used as a [[pivot point]] to attack the rest of the network. These machines also have their own firmware that must be kept patched and updated.

### Voice over IP (VoIP)

Types of embedded systems are used to implement both Voice over IP (VoIP) endpoints and media gateways. Endpoints can be individual handsets or conferencing units. A media gateway might use a separate firmware/OS to implement integration with telephone and cellular networks.

Where these devices connect directly to the Internet, a fingerprinting app or website ([https://www.shodan.io/](https://www.shodan.io/), for instance) can be used to probe for unpatched vulnerabilities. There are Shodan queries for any number of IoT and [[ICS]] devices.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/647-1599771807357.png)

Shodan search results for sites responding to probes over port 9100 (TCP port for raw print data).
# SPECIALIZED SYSTEMS FOR VEHICLES AND DRONES

Automobiles and unmanned aerial vehicles (UAV), or drones, contain sophisticated electronics to control engine and power systems, braking and landing, and suspension/stability. Modern vehicles are increasingly likely to have navigation and entertainment systems, plus driver-assist or even driverless features, where the vehicle's automated systems can take control of steering and braking. The locking, alarm, and engine immobilizer mechanisms are also likely to be part of the same system. Each of these subsystems is implemented as an electronic control unit ([[ECU]]), connected via one or more controller area network ([[CAN]]) serial communications buses. The principal external interface is an Onboard Diagnostics ([[OBD-II]]) module. The OBD-II also acts as a gateway for multiple CAN buses.

The CAN bus operates in a somewhat similar manner to shared Ethernet and was designed with just as little security. ECUs transmit messages as broadcast so they are received by all other ECUs on the same bus. There is no concept of source addressing or message authentication. An attacker able to attach a malicious device to the OBD-II port is able to perform DoS attacks against the CAN bus, threatening the safety of the vehicle. There are also remote means of accessing the CAN bus, such as via the cellular features of the automobile's navigation and entertainment system ([wired.com/2015/07/hackers-remotely-kill-jeep-highway](https://www.wired.com/2015/07/hackers-remotely-kill-jeep-highway/)). Some vehicles also implement on-board Wi-Fi, further broadening the
# SPECIALIZED SYSTEMS FOR MEDICAL DEVICES

Medical devices represent an array of systems potentially vulnerable to a wide range of attacks. It is important to recognize that use of these devices is not confined to hospitals and clinics but includes portable devices such as cardiac monitors/defibrillators and insulin pumps. As well as unsecure communication protocols, many of the control systems for these devices run on unsupported versions of operating systems (such as Windows XP) because the costs of updating the software to work with newer OS versions is high and disruptive to patient services. Some of the goals of attacks on medical devices and services are as follows:

-   Use compromised devices to pivot to networks storing medical data with the aim of stealing protected health information (PHI).
-   Hold medical units ransom by threatening to disrupt services.
-   Kill or injure patients (or threaten to do so) by tampering with dosage levels or device settings.
# [[SECURITY FOR EMBEDDED SYSTEMS]] 

Embedded systems must not be overlooked when designing the security system. The following methods can be used to mitigate risk in such environments. 

### Network Segmentation

Network segmentation is one of the core principles of network security. Network access for static environments should only be required for applying firmware updates and management controls from the host software to the devices and for reporting status and diagnostic information from the devices back to the host software. This control network should be separated from the corporate network using firewalls and VLANs.

With environments such as SCADA, the management software may require legacy versions of operating systems, making the hosts particularly difficult to secure. Isolating these hosts from others through network segmentation and using endpoint security (preventing the attachment of USB devices) can help to ensure they do not become infected with malware or exposed to network exploits. 

### Wrappers

One way of increasing the security of data in transit for embedded systems is through the use of wrappers, such as IPSec. The only thing visible to an attacker or anyone sniffing the wire is the IPSec header, which describes only the tunnel endpoints. This is useful for protecting traffic between trusted networks when the traffic has to go through an untrusted network to go between them, or between trusted nodes on the same network. 

### Firmware Code Control and Inability to Patch

Embedded systems demonstrate one of the reasons that supply chain risks must be carefully managed. Programming logic implemented in FPGA and firmware code must not contain backdoors. Firmware patching is just as vital as keeping host OS software up to date, but for many embedded systems, it is far more of a challenge:

-   Many embedded systems and IoT devices use low-cost firmware chips and the vendor never produces updates to fix security problems or only produces updates for a relatively short product cycle (while the device could remain in operational use for much longer).
-   Many embedded systems require manual updates, which are perceived as too time-consuming for a security department with other priorities to perform.
-   [[My linked notes/Dictionary/Availability]] is a key attribute for most embedded deployments. Patching without service interruption may not be possible, and opportunities for downtime servicing extremely limited.

Cisco Live presents a useful overview of embedded system security requirements ([ciscolive.com/c/dam/r/ciscolive/us/docs/2018/pdf/BRKIOT-2115.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/BRKIOT-2115.pdf)).
