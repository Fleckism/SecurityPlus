---
tags: [,section]
---
# ## 

LESSON INTRODUCTION

Risks from intrusion by social engineering, wireless backdoors, and data exfiltration by mobile devices all mean that physical security is a critical consideration for site design and operations. The premises in which networks are installed need to use access control mechanisms and be resilient to person-made and natural disasters, such as fire.

## 

LESSON OBJECTIVES

In this lesson, you will:

-   Explain the importance of physical site security controls.
-   Explain the importance of physical host security controls.
# EXAM OBJECTIVES COVERED

1.2 Given a scenario, analyze potential indicators to determine the type of attack

2.7 Explain the importance of physical security controls

If an attacker can gain [[physical access]] to your premises, there may be lots of opportunities to install rogue devices, vandalize or disrupt systems, or observe confidential information. Consequently, as a security professional, you should be able to explain the importance of installing access and monitoring controls that protect sites against physical intrusion.
# PHYSICAL SECURITY CONTROLS

Physical access controls are security measures that restrict and monitor access to specific physical areas or assets. They can control access to a building, to equipment, or to specific areas, such as server rooms, finance or legal areas, data centers, network cable runs, or any other area that has hardware or information that is considered to have important value and sensitivity. Determining where to use physical access controls requires a cost–benefit analysis and must consider any regulations or other compliance requirements for the specific types of data that are being safeguarded.

Physical access controls depend on the same access control fundamentals as network or operating system security:

-   Authentication—create access lists and identification mechanisms to allow approved persons through the barriers.
-   Authorization—create barriers around a resource so that access can be controlled through defined entry and exit points.
-   Accounting—keep a record of when entry/exit points are used and detect security breaches.

Physical security can be thought of in terms of zones. Each zone should be separated by its own barrier(s). Entry and exit points through the barriers need to be controlled by one or more security mechanisms. Progression through each zone should be progressively more restricted.
# SITE LAYOUT, FENCING, AND LIGHTING

In existing premises, there will not be much scope to influence site layout. However, given constraints of cost and existing infrastructure, try to plan the site using the following principles:

-   Locate secure zones, such as equipment rooms, as deep within the building as possible, avoiding external walls, doors, and windows.
-   Use a demilitarized zone (DMZ) design for the physical space. Position public access areas so that guests do not pass near secure zones. Security mechanisms in public areas should be highly visible, to increase deterrence.
-   Use signage and warnings to enforce the idea that security is tightly controlled. Beyond basic no trespassing signs, some homes and offices also display signs from the security companies whose services they are currently using. These may convince intruders to stay away.
-   Conversely, entry points to secure zones should be discreet. Do not allow an intruder the opportunity to inspect security mechanisms protecting such zones (or even to know where they are). Use industrial camouflage to make buildings and gateways protecting high-value assets unobtrusive, or create high-visibility decoy areas to draw out potential [[threat actor]]s.
-   Try to minimize traffic having to pass between zones. The flow of people should be "in and out" rather than "across and between."
-   Give high-traffic public areas high visibility, so that covert use of gateways, network access ports, and computer equipment is hindered, and surveillance is simplified.
-   In secure zones, do not position display screens or input devices facing toward pathways or windows. Alternatively, use one-way glass so that no one can look in through windows.

### Barricades and Entry/Exit Points

A barricade is something that prevents access. As with any security system, no barricade is completely effective; a wall may be climbed or a lock may be picked, for instance. The purpose of barricades is to channel people through defined entry and exit points. Each entry point should have an authentication mechanism so that only authorized persons are allowed through. Effective surveillance mechanisms ensure that attempts to penetrate a barricade by other means are detected.

Sites where there is a risk of a terrorist attack will use barricades such as bollards and security posts to prevent vehicles from approaching closely to a building at high speed.

### Fencing

The exterior of a building may be protected by fencing. Security fencing needs to be transparent (so that guards can see any attempt to penetrate it), robust (so that it is difficult to cut), and secure against climbing (which is generally achieved by making it tall and possibly by using razor wire). Fencing is generally effective, but the drawback is that it gives a building an intimidating appearance. Buildings that are used by companies to welcome customers or the public may use more discreet security methods.

### Lighting

Security lighting is enormously important in contributing to the perception that a building is safe and secure at night. Well-designed lighting helps to make people feel safe, especially in public areas or enclosed spaces, such as parking garages. Security lighting also acts as a deterrent by making intrusion more difficult and surveillance (whether by camera or guard) easier. The lighting design needs to account for overall light levels, the lighting of particular surfaces or areas (**allowing cameras to perform facial recognition, for instance**), and avoiding areas of shadow and glare.
# GATEWAYS AND LOCKS 

In order to secure a gateway, it must be fitted with a lock. A secure gateway will normally be self-closing and self-locking, rather than depending on the user to close and lock it. Lock types can be categorized as follows:

-   Physical—a conventional lock prevents the door handle from being operated without the use of a key. More expensive types offer greater resistance against lock picking.
-   Electronic—rather than a key, the lock is operated by entering a PIN on an electronic keypad. This type of lock is also referred to as cipher, combination, or keyless. A smart lock may be opened using a magnetic swipe card or feature a proximity reader to detect the presence of a physical token, such as a wireless key fob or smart card.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5820-1599771812716.png)

Generic examples of locks—From left to right, a standard key lock, a deadbolt lock, and an electronic keypad lock. (Images from user macrovector © 123RF.com.)

-   Biometric—a lock may be integrated with a biometric scanner. 

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/6795-1599771812839.png)

Generic examples of a biometric thumbprint scanner lock and a token-based key card lock. (Images from user macrovector © 123RF.com.)

### Mantraps

Apart from being vulnerable to lock picking, the main problem with a simple door or gate as an entry mechanism is that it cannot accurately record who has entered or left an area. Multiple people may pass through the gateway at the same time; a user may hold a door open for the next person; an unauthorized user may "tailgate" behind an authorized user. This risk may be mitigated by installing a turnstile (a type of gateway that only allows one person through at a time). The other option is to add some sort of surveillance on the gateway. Where security is critical and cost is no object, an access control vestibule, or mantrap, could be employed. A mantrap is where one gateway leads to an enclosed space protected by another barrier.

### Cable Locks

Cable locks attach to a secure point on the device chassis. A server chassis might come with both a metal loop and a [[Kensington security slot]]. As well as securing the chassis to a rack or desk, the position of the secure point prevents the chassis from being opened, without removing the cable first.
# PHYSICAL ATTACKS AGAINST SMART CARDS AND USB

Some types of smart cards used as passkeys for electronic locks can be vulnerable to cloning and skimming attacks:

-   Card cloning—this refers to making one or more copies of an existing card. A lost or stolen card with no cryptographic protections can be physically duplicated. Card loss should be reported immediately so that it can be revoked and a new one issued. If there were a successful attack, it might be indicated by use of a card in a suspicious location or time of day.
-   Skimming—this refers to using a counterfeit card reader to capture card details, which are then used to program a duplicate. Some types of proximity cards can quite easily be made to transmit the credential to a portable RFID reader that a [[threat actor]] could conceal on his or her person. Skimmers installed on public readers, such as ATM machines, can be difficult to spot. 

These attacks can generally only target "dumb" smart cards that transfer tokens rather than perform cryptoprocessing. Bank-issued smart cards, referred to as EMV (Europay, MasterCard, Visa), can also be vulnerable through the magnetic strip, which is retained for compatibility.

When evaluating risks from [[card cloning]] and skimming, you need to realize that there are many types of "smart card." For example, old MIFARE Classic cards used as public transit payment cards are easily cloned because they use a weak cryptographic implementation. Building entry systems using contactless cards with no cryptoprocessing are also vulnerable ([youtube.com/watch?v=cxxnuofREcM](https://www.youtube.com/watch?v=cxxnuofREcM)). Cloning of MIFARE EV or EMV smart cards that implement a TPM-like cryptoprocessor is not thought to be possible.

Malicious [[USB charging]] cables and plugs are also a widespread problem. As with card skimming, a device may be placed over a public charging port at airports and other transit locations. A USB data blocker can provide mitigation against these juice-jacking attacks by preventing any sort of data transfer when the smartphone or laptop is connected to a charge point ([zdnet.com/article/this-cheap-gadget-can-stop-your-smartphone-or-tablet-being-hacked-at-an-airport-hotel-or-cafe](https://www.zdnet.com/article/this-cheap-gadget-can-stop-your-smartphone-or-tablet-being-hacked-at-an-airport-hotel-or-cafe/)).
# ALARM SYSTEMS AND SENSORS
[[alarm systems]]
When designing premises security, you must consider the security of entry points that could be misused, such as emergency exits, windows, hatches, grilles, and so on. These may be fitted with bars, locks, or alarms to prevent intrusion. Also consider pathways above and below, such as false ceilings and ducting. There are five main types of alarm:

-   Circuit—a circuit-based alarm sounds when the circuit is opened or closed, depending on the type of alarm. This could be caused by a door or window opening or by a fence being cut. A closed-circuit alarm is more secure because an open circuit alarm can be defeated by cutting the circuit.
-   Motion detection—a motion-based alarm is linked to a detector triggered by any movement within an area (defined by the sensitivity and range of the detector), such as a room. The sensors in these detectors are either microwave radio reflection (similar to radar) or passive infrared ([[PIR]]), which detect moving heat sources.
-   Noise detection—an alarm triggered by sounds picked up by a microphone. Modern AI-backed analysis and identification of specific types of sound can render this type of system much less prone to false positives.
-   Proximity—radio frequency ID ([[RFID]]) tags and readers can be used to track the movement of tagged objects within an area. This can form the basis of an alarm system to detect whether someone is trying to remove equipment.
-   Duress—this type of alarm is triggered manually by staff if they come under threat. There are many ways of implementing this type of alarm, including wireless pendants, concealed sensors or triggers, and DECT handsets or smartphones. Some electronic entry locks can also be programmed with a duress code that is different from the ordinary access code. This will open the gateway but also alert security personnel that the lock has been operated under duress.

Circuit-based alarms are typically suited for use at the perimeter and on windows and doors. These may register when a gateway is opened without using the lock mechanism properly or when a gateway is held open for longer than a defined period. Motion detectors are useful for controlling access to spaces that are not normally used. Duress alarms are useful for exposed staff in public areas. An alarm might simply sound an alert or it may be linked to a monitoring system. Many alarms are linked directly to local law enforcement or to third-party security companies. A silent alarm alerts security personnel rather than sounding an audible alarm.
# SECURITY GUARDS AND CAMERAS

Surveillance is typically a second layer of security designed to improve the resilience of perimeter gateways. Surveillance may be focused on perimeter areas or within security zones themselves. Human security guards, armed or unarmed, can be placed in front of and around a location to protect it. They can monitor critical checkpoints and verify identification, allow or disallow access, and log physical entry events. They also provide a visual deterrent and can apply their own knowledge and intuition to potential security breaches. The visible presence of guards is a very effective intrusion detection and deterrence mechanism, but is correspondingly expensive. It also may not be possible to place security guards within certain zones because they cannot be granted an appropriate security clearance. Training and screening of security guards is imperative.

CCTV (closed circuit television) is a cheaper means of providing surveillance than maintaining separate guards at each gateway or zone, though still not cheap to set up if the infrastructure is not already in place on the premises. It is also quite an effective deterrent. The other big advantage is that movement and access can be recorded. The main drawback compared to the presence of security guards is that response times are longer, and security may be compromised if not enough staff are in place to monitor the camera feeds.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2643-1599771812889.jpg)

CCTV installed to monitor a server room. (Image by Dario Lo Presti © 123rf.com.)

The cameras in a CCTV network are typically connected to a multiplexer using coaxial cabling. The multiplexer can then display images from the cameras on one or more screens, allow the operator to control camera functions, and record the images to tape or hard drive. Newer camera systems may be linked in an IP network, using regular data cabling.

If you consider control types, a security guard is a preventive control, as the guard can both discover and act to prevent an attack. A camera is a detective control only.

[[Camera systems]] and robotics can use AI and machine learning to implement smart physical security ([theverge.com/2018/1/23/16907238/artificial-intelligence-surveillance-cameras-security](https://www.theverge.com/2018/1/23/16907238/artificial-intelligence-surveillance-cameras-security)):

-   Motion recognition—the camera system might be configured with gait identification technology. This means that the system can generate an alert when anyone moves within sight of the camera and the pattern of their movement does not match a known and authorized individual.
-   Object detection—the camera system can detect changes to the environment, such as a missing server, or unknown device connected to a wall port.
-   Robot sentries—surveillance systems (and in some cases weapon systems) can be mounted on a wholly or partially autonomous robot.
-   Drones/UAV—cameras mounted on drones can cover wider areas than ground-based patrols ([zdnet.com/article/best-security-surveillance-drones-for-business](https://www.zdnet.com/article/best-security-surveillance-drones-for-business/)).
# RECEPTION PERSONNEL AND ID BADGES

One of the most important parts of surveillance is the [[challenge policy]]. This sets out what type of response is appropriate in given situations and helps to defeat social engineering attacks. This must be communicated to and understood by the staff. Challenges represent a whole range of different contact situations. For example:

-   Challenging visitors who do not have ID badges or are moving about unaccompanied.
-   Insisting that proper authentication is completed at gateways, even if this means inconveniencing staff members (no matter their seniority).
-   Intruders and/or security guards may be armed. The safety of staff and compliance with local laws has to be balanced against the imperative to protect the company's other resources.

It is much easier for employees to use secure behavior in these situations if they know that their actions are conforming to a standard of behavior that has been [[agreed upon and is expected of them]].

### Reception Personnel and Visitor Logs

An access list held at the reception area for each secure gateway records who is allowed to enter. An electronic lock may be able to log access attempts or a reception staff can manually log movement. At the lowest end, a sign-in and sign-out sheet can be used to record authorized access. Visitor logging requirements will vary depending on the organization, but should include at least the name and company being represented, date, time of entry and departure, reason for visiting, and contact within the organization.

### Two-Person Integrity/Control

Reception areas for high-security zones might be staffed by at least two people at all times, providing integrity for entry control and reducing the risk of insider threat.

### ID Badges

A photographic ID badge showing name and (perhaps) access details is one of the cornerstones of building security. Anyone moving through secure areas of a building should be wearing an ID badge; anyone without an ID badge should be challenged. Color-coding could be used to make it obvious to which zones a badge is granted access.
