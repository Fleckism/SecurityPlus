# EXAM OBJECTIVES COVERED

5.4 Summarize ( #GRC) risk management processes and concepts

Business impact analysis informs [[risk assesment]] by documenting the workflows that run the organization and the critical assets and systems that support them. Key metrics quantify how much downtime those systems can withstand. As a security professional, you will often be asked to produce this type of analysis.
# BUSINESS IMPACT ANALYSIS

Business impact analysis ([[BIA]]) is the process of assessing what losses might occur for a range of threat scenarios. For instance, if a DDoS attack suspends an e-commerce portal for five hours, the business impact analysis will be able to quantify the losses from orders not made and customers moving permanently to other suppliers based on historic data. The likelihood of a DoS attack can be assessed on an annualized basis to determine annualized impact, in terms of costs. You then have the information required to assess whether a security control, such as load balancing or managed DDoS mitigation, is worth the investment.

Where BIA identifies risks, business continuity planning ([[BCP]]) identifies controls and processes that enable an organization to maintain critical workflows in the face of some adverse event.

The term continuity of operations planning ([[COOP]]) refers to the same sorts of activities when undertaken by a government agency, rather than a business.
# MISSION ESSENTIAL FUNCTIONS

A mission essential function ([[MEF]]) is one that cannot be deferred. This means that the organization must be able to perform the function as close to continually as possible, and if there is any service disruption, the mission essential functions must be restored first.

Functions that act as support for the business or an MEF but are not critical in themselves are referred to as primary business functions ([[PBF]]).

Analysis of mission essential functions is generally governed by four main metrics:

-   Maximum tolerable downtime ([[MTD]]) is the longest period of time that a business function outage may occur for without causing irrecoverable business failure. Each business process can have its own MTD, such as a range of minutes to hours for critical functions, 24 hours for urgent functions, seven days for normal functions, and so on. MTDs vary by company and event. Each function may be supported by multiple systems and assets. The MTD sets the upper limit on the amount of recovery time that system and asset owners have to resume operations. For example, an organization specializing in medical equipment may be able to exist without incoming manufacturing supplies for three months because it has stockpiled a sizable inventory. After three months, the organization will not have sufficient supplies and may not be able to manufacture additional products, therefore leading to failure. In this case, the MTD is three months.
-   Recovery time objective ([[RTO]]) is the period following a disaster that an individual IT system may remain offline. This represents the amount of time it takes to identify that there is a problem and then perform recovery (restore from backup or switch in an alternative system, for instance).
-   Work Recovery Time ([[WRT]]). Following systems recovery, there may be additional work to reintegrate different systems, test overall functionality, and brief system users on any changes or different working practices so that the business function is again fully supported. 

**RTO+WRT must not exceed MTD**!

-   Recovery Point Objective ([[RPO]]) is the amount of data loss that a system can sustain, measured in time. That is, if a database is destroyed by a virus, an RPO of 24 hours means that the data can be recovered (from a backup copy) to a point not more than 24 hours before the database was infected.

Metrics governing mission essential functions. (Images © 123RF.com.)

For example, a customer leads database might be able to sustain the loss of a few hours' or days' worth of data (the salespeople will generally be able to remember who they have contacted and rekey the data manually). Conversely, order processing may be considered more critical, as any loss will represent lost orders and it may be impossible to recapture web orders or other processes initiated only through the computer system, such as linked records to accounting and fulfillment.

MTD and RPO help to determine which business functions are critical and also to specify appropriate risk countermeasures. For example, if your RPO is measured in days, then a simple tape backup system should suffice; if RPO is zero or measured in minutes or seconds, a more expensive server cluster backup and redundancy solution will be required.
# IDENTIFICATION OF CRITICAL SYSTEMS

To support the resiliency of mission essential and primary business functions, it is crucial to perform an identification of critical systems. This means compiling an inventory of business processes and the assets that support them. [[Asset types]] include:

-   People (employees, visitors, and suppliers).
-   Tangible assets (buildings, furniture, equipment and machinery (plant), ICT equipment, electronic data files, and paper documents).
-   Intangible assets (ideas, commercial reputation, brand, and so on).
-   Procedures (supply chains, critical procedures, standard operating procedures).

For mission essential functions, it is important to **reduce the number of dependencies between components**. Dependencies are identified by performing a business process analysis ([[BPA]]) for each function. The BPA should identify the following factors:

-   Inputs—the sources of information for performing the function (including the impact if these are delayed or out of sequence).
-   Hardware—the particular server or data center that performs the processing.
-   Staff and other resources supporting the function.
-   Outputs—the data or resources produced by the function.
-   Process flow—a step-by-step description of how the function is performed.
# SINGLE POINTS OF FAILURE

Each IT system will be supported by hardware assets, such as servers, disk arrays, switches, routers, and so on. Reducing dependencies means the system design can more easily eliminate the sort of weakness that comes from these devices becoming single points of failure ([[SPoF]]). A SPoF is an asset that causes the entire workflow to fail if it is damaged or otherwise not available. SPoFs can be mitigated by provisioning redundant components. Metrics for asset reliability can help to determine when and how much redundancy is required. Some of the main KPIs relating to service [[My linked notes/Dictionary/Availability]] are as follows:

-   Mean time to failure ([[MTTF]]) and mean time between failures (MTBF) represent the expected lifetime of a product. MTTF should be used for non-repairable assets. For example, a hard drive may be described with an MTTF, while a server (which could be repaired by replacing the hard drive) would be described with an MTBF. You will often see MTBF used indiscriminately, however. For most devices, failure is more likely early or late in life, producing the so-called "bathtub curve."  
      
    MTTF/MTBF can be used to determine the amount of asset redundancy a system should have. A redundant system can failover to another asset if there is a fault and continue to operate normally. It can also be used to work out how likely failures are to occur.
-   The calculation for MTBF is the total time divided by the number of failures. For example, if you have 10 devices that run for 50 hours and two of them fail, the MTBF is 250 hours (10*50)/2.
-   The calculation for MTTF for the same test is the total time divided by the number of devices, so (10*50)/10, with the result being 50 hours.
-   Mean time to repair (MTTR) is a measure of the time taken to correct a fault so that the system is restored to full operation. This can also be described as mean time to "replace" or "recover." This metric is important in determining the overall recovery time objective (RTO).

NIST has published a guide to resiliency and IT contingency planning (SP800-34), available at [nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-34r1.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/nistspecialpublication800-34r1.pdf).
# DISASTERS

In terms of business continuity, a disaster is an event that could threaten mission essential functions. For example, a privacy breach is a critical incident, but it is probably not a direct threat to business functions. An earthquake that destroys a data center is a disaster-level event. Disaster response involves many of the same principles and procedures as incident response, but at a larger scale.

### Internal versus External

An internal disaster is one that is caused by malicious activity or by accident by an employee or contractor—anyone or anything whose presence within the company or organization has been authorized. Internal disaster also encompasses system faults, such as wiring causing a fire. Conversely, external disaster events are caused by [[threat actor]]s who have no privileged access. External disaster includes disasters that have an impact on the organization through wider environmental or social impacts, such as disruption of public services or impacts to the supply chain.

### Person-Made

A person-made disaster event is one where human agency is the primary cause. Typical examples other than devastating cybersecurity incidents include terrorism, war, vandalism, pollution, and arson. There can also be accidental person-made disasters, such as cutting through power or telecoms cabling.

### Environmental

An environmental disaster, or natural disaster, is one that could not be prevented through human agency. Environmental disasters include river or sea floods, earthquakes, storms, disease, and so on. Natural disasters may be quite predictable (as is the case with areas prone to flooding or storm damage) or unexpected, and therefore difficult to plan for.

Most natural or environmental disasters can also have a human or artificial source. For example, flooding might be more likely because dams are not adequately maintained; a wildfire could be the result of arson or poorly maintained power infrastructure.

### Site [[risk assesment]]

Where cybersecurity generally has financial impacts, site safety can have impacts to life and property. A site [[risk assesment]] evaluates exposure to the following types of factor:

-   Risk from disaster events, such as earthquake, flood, and fire. These events can occur naturally or from person-made causes.
-   Risk from disruption to utilities, such as electricity, water, and transportation. These risks are higher in geographically isolated sites.
-   Risk to health and safety from on-premises electromechanical systems or chemicals.
# DISASTER RECOVERY PLANS

Disaster recovery plans ([[DRPs]]) describe the specific procedures to follow to recover a system or site to a working state following a disaster-level event. The DRP should accomplish the following:

1.  Identify scenarios for natural and non-natural disaster and options for protecting systems. Plans need to account for risk (a combination of the likelihood the disaster will occur and the possible impact on the organization) and cost.  
      
    There is no point implementing disaster recovery plans that financially damage the organization. The business case is made by comparing the cost of recovery measures against the cost of downtime. The recovery plan should not generally exceed the downtime cost.
2.  Identify tasks, resources, and responsibilities for responding to a disaster.

-   Who is responsible for doing what? How can they be contacted? What happens if they are not available?
-   Which functions are most critical? Where should effort first be concentrated?
-   What resources are available? Should they be pre-purchased and held in stock? Will the disaster affect [[My linked notes/Dictionary/Availability]] of supplies?
-   What are the timescales for resumption of normal operations?

3.  Train staff in the disaster planning procedures and how to react well to change.

As well as restoring systems, the disaster recovery plan should identify stakeholders who need to be informed about incidents with impacts to life and safety. There may be a legal requirement to inform the police, fire service, or building inspectors about any safety-related or criminal incidents. If third-party or personal data is lost or stolen, the data subjects may need to be informed. If the disaster affects services, customers need to be informed about the time-to-fix and any alternative arrangements that can be made.
# FUNCTIONAL RECOVERY PLANS

Because disasters are extreme and (hopefully) rare events, it is very difficult to evaluate how effective or functional a recovery plan is. There are four principal methods for assessing the functionality of recovery plans:

-   Walk-throughs, workshops, and orientation seminars—often used to provide basic awareness and training for disaster recovery team members, these exercises describe the contents of DRPs, and other plans, and the roles and responsibilities outlined in those plans.
-   Tabletop exercises—staff "ghost" the same procedures as they would in a disaster, without actually creating disaster conditions or applying or changing anything. These are simple to set up but do not provide any sort of practical evidence of things that could go wrong, time to complete, and so on.
-   Functional exercises—action-based sessions where employees can validate DRPs by performing scenario-based activities in a simulated environment.
-   Full-scale exercises— action-based sessions that reflect real situations, these exercises are held onsite and use real equipment and real personnel as much as possible. Full-scale exercises are often conducted by public agencies, but local organizations might be asked to participate.
