---
tags: [,section]
---
# EXAM OBJECTIVES COVERED

2.7 Explain the importance of physical security controls

4.1 Given a scenario, use the appropriate tool to assess organizational security (Data sanitization only)

As with data networks, perimeter defenses are not sufficient to ensure the security of hosts within a site. As well as the risk that the perimeter could be breached, security systems must also be resilient against insider threats. You need to deploy additional controls to secure areas, such as computer rooms and data centers.

Environmental security ensures that risks to [[My linked notes/Dictionary/Availability]] from hosts overheating are minimized. All sites also need effective procedures for the disposal of equipment and paper records, to ensure that confidential data remnants are not at risk of exposure.
# SECURE AREAS 

A secure area is designed to store critical assets with a higher level of access protection than general office areas. The most vulnerable point of the [[network infrastructure]] will be the communications or server room. This should be subject to the most stringent access and surveillance controls that can be afforded. Similar measures apply to hardening access to data centers.

Installing equipment within secure cabinets/enclosures provides mitigation against insider attack and attacks that have broken through the perimeter security mechanisms. These can be supplied with key-operated or electronic locks.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7546-1599771812981.png)

Rack cabinet with key-operated lock. (Image © 123RF.com.)

Some data centers may contain racks with equipment owned by different companies (colocation). These racks can be installed inside cages so that technicians can only physically access the racks housing their own company's servers and appliances.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7635-1599771813082.jpg)

Colocation cages. (Image © Chris Dag and shared with CC BY 2.0 flickr.com/photos/chrisdag/865711871.)

### Air Gap/Demilitarized Zone

An air gapped host is one that is not physically connected to any network. Such a host would also normally have stringent physical access controls, such as housing it within a secure enclosure, validating any media devices connected to it, and so on.

An air gap within a secure area serves the same function as a demilitarized zone. It is an empty area surrounding a high-value asset that is closely monitored for intrusions. As well as being disconnected from any network, the physical space around the host makes it easier to detect unauthorized attempts to approach the asset. Security policies should prevent any unauthorized computing hosts or storage media from being carried into the DMZ.

### Safes and Vaults

Portable devices and media (backup tapes or USB media storing encryption keys, for instance) may be stored in a safe. Safes can feature key-operated or combination locks but are more likely to come with electronic locking mechanisms. Safes can be rated to a particular cash value for the contents against various international grading schemes. There are also fire safes that give a certain level of protection against exposure to smoke and flame and to water penetration (from fire extinguishing efforts).

A vault is a room that is hardened against unauthorized entry by physical means, such as drilling or explosives. A vault is expensive, but may be considered necessary for mission critical assets that need to be very securely air gapped, such as the root server for a commercial CA.
# PROTECTED DISTRIBUTION AND FARADAY CAGES

A physically secure cabled network is referred to as protected cable distribution or as a protected distribution system ([[PDS]]). There are two principal risks:

-   An intruder could attach eavesdropping equipment to the cable (a tap).
-   An intruder could cut the cable (Denial of Service).

A hardened PDS is one where all cabling is routed through sealed metal conduit and subject to periodic visual inspection. Lower-grade options are to use different materials for the conduit (plastic, for instance). Another option is to install an alarm system within the cable conduit, so that intrusions can be detected automatically.

It is possible to install communications equipment within a shielded enclosure, known as a Faraday Cage. **The cage is a charged conductive mesh that blocks signals from entering or leaving the area**. The risk of eavesdropping from leakage of electromagnetic signals was investigated by the US DoD who defined [[TEMPEST]] (Transient Electromagnetic Pulse Emanation Standard) as a means of shielding the signals
# HEATING, VENTILATION, AIR CONDITIONING 

Environmental controls mitigate the loss of [[My linked notes/Dictionary/Availability]] through mechanical issues with equipment, such as overheating. Building control systems maintain an optimum working environment for different parts of the building. The acronym [[HVAC]] (Heating, Ventilation, Air Conditioning) is often used to describe these services. An HVAC uses temperature sensors and moisture detection sensors (to measure humidity).

Use a portable monitor to verify that the HVAC's temperature and humidity sensors are returning the correct readings.

For computer rooms and data centers, a thermostatically controlled environment is usually kept at a temperature of around 20-22°C (68-70°F) and relative humidity of 50%. The heat generated by equipment per hour is measured in British Thermal Units (BTU) or kilowatts (KW). 1 KW is 3412 BTU. To calculate the cooling requirement for an air conditioning system, multiply the wattage of all equipment in the room (including lighting) by 3.41 to get the BTU/hour. If the server room is occupied (unlikely in most cases), add 400 BTU/person. The air conditioner's BTU-rating must exceed this total value.

Some data centers (notably those operated by Google) are allowing higher temperatures (up to around 26°C/80°F). This can achieve significant energy cost savings and modern electronics is proving reliable at this temperature.

The positive air pressure created by the HVAC system also forces contaminants such as dust out of the facility. Filters on HVAC systems collect the dust and must be changed regularly. When using an air conditioning system, ensure that it is inspected and maintained periodically. Systems may be fitted with alarms to alert staff to problems. Mission-critical systems may require a backup air conditioning system.

The server room should not be used as storage space. Do not leave boxes or unused equipment in it. Also, do not install unnecessary devices that generate a lot of heat and dust, such as printers.
# HOT AND COLD AISLES

A data center or server room should be designed in such a way as to maximize air flow across the server or racks. If multiple racks are used, install equipment so that servers are placed back-to-back not front-to-back, so that the warm exhaust from one bank of servers is not forming the air intake for another bank. This is referred to as a hot aisle/cold [[aisle]] arrangement. In order to prevent air leaks from the hot aisle to the cold aisle, ensure that any gaps in racks are filled by blank panels and use strip curtains or excluders to cover any spaces above or between racks.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9697-1599771813222.png)

Hot aisle containment design—Cold air circulates from the air conditioner under the floor and around the rack, while hot air is drawn from between the racks through the ceiling space (plenum) to a heat exchanger. In this design, it is important that hot air does not leak from the ceiling or from the floor space between the racks. (Image © 123RF.com.)

Make sure that cabling is secured by cable ties or ducting and does not run across walkways. Cable is best run using a raised floor. If running cable through plenum spaces, make sure it is fire-retardant and be conscious of minimizing proximity to electrical sources, such as electrical cable and fluorescent light, which can corrupt data signals (Electromagnetic Interference [[EMI]]). You also need to ensure that there is sufficient space in the plenum for the air conditioning system to work properly—filling the area with cable is not the best idea.

To reduce interference, data/network cabling should not be run parallel to power cabling. If EMI is a problem, shielded cabling can be installed. Alternatively, the copper cabling could be replaced with fiber optic cabling, which is not susceptible to EMI.
# FIRE DETECTION AND SUPPRESSION

Health and safety legislation dictates what mechanisms an organization must put in place to detect and suppress fires. Some basic elements of fire safety include:

-   Well-marked fire exits and an emergency evacuation procedure that is tested and practiced regularly.
-   Building design that does not allow fire to spread quickly, by separating different areas with fire-resistant walls and doors.
-   Automatic smoke or fire detection systems, as well as alarms that can be operated manually.

Fire suppression systems work on the basis of the fire triangle. The fire triangle works on the principle that a fire requires heat, oxygen, and fuel to ignite and burn. Removing any one of those elements provides fire suppression (and prevention). In the US (and most other countries), fires are divided by class under the [[NFPA]] (National Fire Protection Association) system, according to the combustible material that fuels the fire. Portable fire extinguishers come in several different types, with each type being designed for fighting a particular class of fire. Notably, **Class C** extinguishers use gas-based extinguishing and can be used where the risk of electric shock makes other types unsuitable.

Under the European classification system, electrical fires are Class E.

Premises may also be fitted with an overhead sprinkler system. Wet-pipe sprinklers work automatically, are triggered by heat, and discharge water. Wet-pipe systems constantly hold water at high pressure, so there is some risk of burst pipes and accidental triggering, as well as the damage that would be caused in the event of an actual fire. There are several alternatives to wet-pipe systems that can minimize damage that may be caused by water flooding the room.

-   Dry-pipe—these are used in areas where freezing is possible; water only enters this part of the system if sprinklers elsewhere are triggered.
-   Pre-action—a pre-action system only fills with water when an alarm is triggered; it will then spray when the heat rises. This gives protection against accidental discharges and burst pipes and gives some time to contain the fire manually before the sprinkler operates.
-   Halon—gas-based systems have the advantage of not short circuiting electrical systems and leaving no residue. Up until a few years ago, most systems used Halon 1301. The use of Halon has been banned in most countries as it is ozone depleting, though existing installations have not been replaced in many instances and can continue to operate legally.
-   Clean agent—alternatives to Halon are referred to as "clean agent." As well as not being environmentally damaging, these gases are considered nontoxic to humans. Examples include INERGEN (a mixture of CO₂, argon, and nitrogen), FM-200/HFC-227, and FE-13. The gases both deplete the concentration of oxygen in the area (though not to levels dangerous to humans) and have a cooling effect. CO₂ can be used too, but it is not safe for use in occupied areas.
# SECURE DATA DESTRUCTION 

Physical security controls also need to take account of the disposal phase of the data life cycle. Media sanitization and remnant removal refer to erasing data from hard drives, flash drives/SSDs, tape media, CD and DVD ROMs before they are disposed of or put to a different use. Paper documents must also be disposed of securely. Data remnants can be dealt with either by destroying the media or by purging it (removing the confidential information but leaving the media intact for reuse).

One approach to sanitization is to destroy the media, rendering it unusable. There are several physical destruction options:

-   Burning—incineration is an effective method for all media types, so long as it is performed in a furnace designed for media sanitization. Municipal incinerators may leave remnants.
-   Shredding and pulping—most media can be shredded. For paper documents, shredders are rated by the size of the remnants they reduce a sheet to. Level 1 is 12mm strips, while Level 6 is 0.8x4mm particles. Pulping the shredded remains with water or incinerating them provides an extra measure of protection. Some office shredders can destroy optical media too. Industrial shredders can destroy hard drives and flash drives.
-   Pulverizing—hitting a hard drive with a hammer can leave a surprising amount of recoverable data, so this type of destruction should be performed with industrial machinery.
-   [[Degaussing]]— exposing a hard disk to a powerful electromagnet disrupts the magnetic pattern that stores the data on the disk surface. Note that SSDs, flash media, and optical media cannot be degaussed, only hard disk drives.

Due to the cost of facilities, physical destruction is likely to be contracted to a third party. It is important to use a reputable service provider and to obtain a detailed inventory of how each media item was sanitized and certificates of destruction.
# DATA SANITIZATION TOOLS 

Files deleted from a magnetic-type hard disk are not erased. Rather, the sectors are marked as available for writing and the data they contain will only be removed as new files are added. Similarly, using the standard Windows format tool will only remove references to files and mark all sectors as usable.

The standard method of sanitizing an HDD is called overwriting. This can be performed using the drive's firmware tools or a utility program. The most basic type of overwriting is called zero filling, which just sets each bit to zero. Single pass zero filling can leave patterns that can be read with specialist tools. A more secure method is to overwrite the content with one pass of all zeros, then a pass of all ones, and then a third pass in a pseudorandom pattern. Some organizations or governmental agencies require more than three passes. Overwriting can take a considerable amount of time to complete, depending on the number of passes.

![Kill box shows To Erase [Hard Disk 1 (81h) SAMSUNG HD321KJ], Erase Method [One Pass Zeros (1 pass)], Retry Attempts (2), Ignore Errors (checked).](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5698-1599771813326.png)

Active KillDisk data wiping software. (Screenshot used with permission from LSoft Technologies, Inc.)

Examples of tools supporting secure file or disk erasing include Sdelete (part of Sysinternals [https://docs.microsoft.com/sysinternals](https://docs.microsoft.com/sysinternals)) and Darik's Boot and Nuke ([https://dban.org](https://dban.org/)), plus the Active KillDisk suite shown here.

### Secure Erase (SE)

Since 2001, the SATA and Serial Attached [[SCSI]] ([[SAS]]) specifications have included a Secure Erase ([[SE]]) command. This command can be invoked using a drive/array utility or the hdparm [[Linux]] utility. On HDDs, this performs a single pass of zero-filling.

For SSDs and hybrid drives and some USB thumb drives and flash memory cards, overwriting methods are not reliable, because the device uses wear-leveling routines in the drive controller to communicate which locations are available for use to any software process accessing the device.

On SSDs, the SE command marks all blocks as empty. A block is the smallest unit on flash media that can be given an erase command. The drive firmware's automatic garbage collectors then perform the actual erase of each block over time. If this process is not completed (and there is no progress indicator), there is a risk of remnant recovery, though this requires removing the chips from the device to analyze #Ops them in specialist hardware.

### Instant Secure Erase (ISE)

HDDs and SSDs that are self-encrypting drives ([[SEDs]]) support another option, invoking a SANITIZE command set in SATA and SAS standards from 2012 to perform a crypto erase. Drive vendors implement this as Instant Secure Erase ([[ISE]]). With an [[SED]], all data on the drive is encrypted using a media encryption key. When the erase command is issued, the [[MEK]] is erased, rendering the data unrecoverable. FIPS140-2 or FIPS140-3 validation provides assurance that the cryptographic implementation is strong.

If the device firmware does not support encryption, using a software disk encryption product and then destroying the key and using SE should be sufficient for most confidentiality requirements.
