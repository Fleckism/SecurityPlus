---
tags: [firstTag, secondTag]
---

## LESSON INTRODUCTION

To make an effective security ,[[assessment]] you must be able to explain strategies for both defense and attack. Your responsibilities are likely to lie principally in defending assets, but to do this you must be able to explain the tactics, techniques, and procedures of threat actors. You must also be able to differentiate the types and capabilities of threat actors. As the threat landscape is continually evolving, you must also be able to identify reliable sources of threat intelligence and research.

Lesson Objectives

In this lesson, you will:

-   Explain threat actor types and attack vectors.
-   Explain threat intelligence sources.

EXAM OBJECTIVES COVERED

1.5 Explain different threat actors, vectors, and intelligence sources

Classifying and evaluating the capabilities of threat actor types enables you to assess and mitigate risks more effectively. Understanding the methods by which threat actors infiltrate networks and systems is essential for you to assess the attack surface of your networks and deploy controls to block attack vectors.
## #VULNERABILITY,  #THREAT, AND RISK

As part of security [[assessment]] and monitoring, security teams must identify ways in which their systems could be attacked. These assessments involve vulnerabilities, threats, and risk:

-   [[vulnerability]] **is a weakness** that could be triggered accidentally or exploited intentionally to cause a security breach. Examples of vulnerabilities include improperly configured or installed hardware or software, delays in applying and testing software and firmware patches, untested software and firmware patches, the misuse of software or communication protocols, poorly designed network architecture, inadequate physical security, insecure password usage, and design flaws in software or operating systems, such as unchecked user input.
-   [[threat]] **is the potential** for someone or something to exploit a vulnerability and breach security. A threat may be intentional or unintentional. The person or thing that poses the threat is called a _threat actor_ or _threat agent._ The path or tool used by a malicious threat actor can be referred to as the _attack vector._
-   Risk is the likelihood and impact (or consequence) of a threat actor exploiting a vulnerability. To assess risk, you identify a vulnerability and then evaluate the likelihood of it being exploited by a threat and the impact that a successful exploit would have.

Relationship between vulnerability, threat, and risk.

These definitions and more information on risk management are contained in NIST's SP 800-30 ([nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-30r1.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/nistspecialpublication800-30r1.pdf)).
## ATTRIBUTES OF THREAT ACTORS

Historically, cybersecurity techniques were highly dependent on the identification of "static" known [[threat]]s, such as viruses or rootkits, Trojans, botnets, and specific software vulnerabilities. It is relatively straightforward to identify and scan for these types of threats with automated software. Unfortunately, adversaries were able to develop means of circumventing this type of signature-based scanning.

The sophisticated nature of modern cybersecurity threats means that it is important to be able to describe and analyze behaviors. This analysis involves identifying the attributes of threat actors in terms of location, intent, and capability.

### Internal/External

An external threat actor or agent is one that has no account or authorized access to the target system. A malicious external threat must infiltrate the security system using malware and/or social engineering. Note that an external actor may perpetrate an attack remotely or on-premises (by breaking into the company's headquarters, for instance). It is the threat actor that is defined as external, rather than the attack method.

Conversely, an internal (or insider) threat actor is one that has been granted permissions on the system. This typically means an employee, but insider threat can also arise from contractors and business partners.

### Intent/Motivation

_Intent_ describes what an attacker hopes to achieve from the attack, while _motivation_ is the attacker's reason for perpetrating the attack. A malicious threat actor could be motivated by greed, curiosity, or some sort of grievance, for instance. The intent could be to vandalize and disrupt a system or to steal something. threats can be characterized as structured or unstructured (or targeted versus opportunistic) depending on the degree to which your own organization is targeted specifically. For example, a criminal gang attempting to steal customers' financial data is a structured, targeted threat; a script kiddie launching some variant on the "I Love You" email worm is an unstructured, opportunistic threat.

**Malicious intents and motivations can be contrasted with accidental or unintentional threat actors and agents. Unintentional threat actors represents accidents, oversights, and other mistakes.**

### Level of Sophistication/Capability and Resources/Funding

You must also consider the sophistication and level of resources/funding that different adversaries might possess. _Capability_ refers to a threat actor's ability to craft novel exploit techniques and tools. The least capable threat actor relies on commodity attack tools that are widely available on the web or dark web. More capable actors can fashion zero-day exploits in operating systems, applications software, and embedded control systems. At the highest level, a threat actor might make use of non-cyber tools, such as political or military assets. Capability is only funded through a substantial budget. Sophisticated threat actor groups need to be able to acquire resources, such as customized attack tools and skilled strategists, designers, coders, hackers, and social engineers. The most capable threat actor groups receive funding from nation states and criminal syndicates.
## HACKERS, SCRIPT KIDDIES, AND HACKTIVISTS

To fully assess intent and capability, it is helpful to identify different categories of threat actors.

### Hackers

[[Hacker]] describes an individual who has the skills to gain access to computer systems through unauthorized or unapproved means. Originally, _hacker_ was a neutral term for a user who excelled at computer programming and computer system administration. Hacking into a system was a sign of technical skill and creativity that gradually became associated with illegal or malicious system intrusions. The terms **black hat (unauthorized) and white hat (authorized)** are used to distinguish these motivations. Of course, between black and white lie some shades of gray. A gray hat hacker (semi-authorized) might try to find vulnerabilities in a product or network without seeking the approval of the owner; but they might not try to exploit any vulnerabilities they find. A gray hat might seek voluntary compensation of some sort (a bug bounty), but will not use an exploit as extortion. A white hat hacker always seeks authorization to perform penetration testing of private and proprietary systems.

### Script Kiddies

A script kiddie is someone who uses hacker tools without necessarily understanding how they work or having the ability to craft new attacks. Script kiddie attacks might have no specific target or any reasonable goal other than gaining attention or proving technical abilities.

### Hacker Teams and Hacktivists

The historical image of a hacker is that of a loner, acting as an individual with few resources or funding. While any such "lone hacker" remains a threat that must be accounted for, threat actors are now likely to work as part of some sort of team or group. The collaborative team effort means that these types of threat actors are able to develop sophisticated tools and novel strategies.

A _hacktivist group,_ such as Anonymous, WikiLeaks, or LulzSec, uses cyber weapons to promote a political agenda. Hacktivists might attempt to obtain and release confidential information to the public domain, perform denial of service (DoS) attacks, or deface websites. Political, media, and financial groups and companies are probably most at risk, but environmental and animal advocacy groups may target companies in a wide range of industries.
## STATE ACTORS AND ADVANCED PERSISTENT THREATS

Most nation states have developed cybersecurity expertise and will use cyber weapons to achieve both military and commercial goals. The security company Mandiant's APT1 report into Chinese cyber espionage units ([fireeye.com/content/dam/fireeye-www/services/pdfs/mandiant-apt1-report.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/mandiant-apt1-report.pdf)) was hugely influential in shaping the language and understanding of modern cyber-attack life cycles. The term Advanced Persistent Threat (APT) was coined to understand the behavior underpinning modern types of cyber adversaries. Rather than think in terms of systems being infected with a virus or Trojan, an APT refers to the ongoing ability of an adversary to compromise network security—to obtain and maintain access—using a variety of tools and techniques.

State actors have been implicated in many attacks, particularly on energy and health network systems. The goals of state actors are primarily espionage and strategic advantage, but it is not unknown for countries—North Korea being a good example—to target companies purely for commercial gain.

![FireEye Resources page lists and briefly describes items under Threat Intelligence: Attack Groups and Threat Intelligence: Technologies headings.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1893-1599771794254.png)

Researchers such as FireEye report on the activities of organized crime and nation state actors. (Screenshot used with permission from fireeye.com.)

State actors will work at arm's length from the national government, military, or security service that sponsors and protects them, maintaining "plausible deniability." They are likely to pose as independent groups or even as hacktivists. They may wage false flag campaigns that try to implicate other states ([media.kasperskycontenthub.com/wp-content/uploads/sites/43/2019/11/20151759/KSB2019_APT-predictions-2020_web.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/KSB2019_APT-predictions-2020_web.pdf)).
## CRIMINAL SYNDICATES AND COMPETITORS

In many countries, cybercrime has overtaken physical crime both in terms of number of incidents and losses. A criminal syndicate can operate across the Internet from different jurisdictions than its victim, increasing the complexity of prosecution. Syndicates will seek any opportunity for criminal profit, but typical activities are financial fraud (both against individuals and companies) and extortion.

Most competitor-driven espionage is thought to be pursued by state actors, but it is not inconceivable that a rogue business might use cyber espionage against its competitors. Such attacks could aim at theft or at disrupting a competitor's business or damaging their reputation. Competitor attacks might be facilitated by employees who have recently changed companies and bring an element of insider knowledge with them.
## INSIDER THREAT ACTORS

Many threat actors operate externally from the networks they target. An external actor has to break into the system without having been granted any legitimate permissions. An insider threat arises from an actor who has been identified by the organization and granted some sort of access. Within this group of internal threats, you can distinguish insiders with permanent privileges, such as employees, from insiders with temporary privileges, such as contractors and guests. The Computer Emergency Response Team ([[CERT]]) at Carnegie Mellon University's definition of a _malicious insider_ is:

> _A current or former employee, contractor, or business partner who has or had authorized access to an organization’s network, system, or data and intentionally exceeded or misused that access in a manner that negatively affected the confidentiality, integrity, or availability of the organization’s information or information systems._ ([insights.sei.cmu.edu/insider-threat/2017/03/cert-definition-of-insider-threat---updated.html](https://insights.sei.cmu.edu/insider-threat/2017/03/cert-definition-of-insider-threat---updated.html))

There is the blurred case of former insiders, such as ex-employees now working at another company or who have been dismissed and now harbor a grievance. These can be classified as internal threats or treated as external threats with insider knowledge, and possibly some residual permissions, if effective offboarding controls are not in place.

CERT identifies the main motivators for malicious insider threats as sabotage, financial gain, and business advantage. Like external threats, insider threats can be opportunistic or targeted. Again, the key point here is to identify likely motivations, such as employees who might harbor grievances or those likely to perpetrate fraud. An employee who plans and executes a campaign to modify invoices and divert funds is launching a structured attack; an employee who tries to guess the password on the salary database a couple of times, having noticed that the file is available on the network, is perpetrating an opportunistic attack. You must also assess the possibility that an insider threat may be working in collaboration with an external threat actor or group.

Insider threats can be categorized as unintentional. An unintentional or inadvertent insider threat is a vector for an external actor, or a separate—malicious—internal actor to exploit, rather than a threat actor in its own right. Unintentional threats usually arise from lack of awareness or from carelessness, such as users demonstrating poor password management. Another example of unintentional insider threat is the concept of shadow IT, where users purchase or introduce computer hardware or software to the workplace without the sanction of the IT department and without going through a procurement and security analysis process. The problem of shadow IT is exacerbated by the proliferation of cloud services and mobile devices, which are easy for users to obtain. Shadow IT creates a new unmonitored attack surface for malicious adversaries to exploit.
##  #Attack SURFACE AND ATTACK VECTORS

**The [[attack]] surface is all the points at which a malicious threat actor could try to exploit a vulnerability.** To evaluate the attack surface, you need to consider the type of threat actor. The attack surface for an external actor is (or should be) far smaller than that for an insider threat. The attack surface can be considered for a network as a whole, but is also analyzed for individual software applications. Minimizing the attack surface means restricting access so that only a few known endpoints, protocols/ports, and services/methods are permitted. Each of these must be assessed for vulnerabilities.

From the point-of-view of the threat actor, different parts of the attack surface represent potential attack vectors. An attack vector is the path that a threat actor uses to gain access to a secure system. In the majority of cases, gaining access means being able to run malicious code on the target.

-   Direct access—this is a type of physical or local attack. The threat actor could exploit an unlocked workstation, use a boot disk to try to install malicious tools, or steal a device, for example.
-   Removable media—the attacker conceals malware on a USB thumb drive or memory card and tries to trick employees into connecting the media to a PC, laptop, or smartphone. For some exploits, simply connecting the media may be sufficient to run the malware. In many cases, the attacker may need the employee to open a file in a vulnerable application or run a setup program.
-   Email—the attacker sends a malicious file attachment via email, or via any other communications system that allows attachments. The attacker needs to use social engineering techniques to persuade or trick the user into opening the attachment.
-   Remote and wireless—the attacker either obtains credentials for a remote access or wireless connection to the network or cracks the security protocols used for authentication. Alternatively, the attacker spoofs a trusted resource, such as an access point, and uses it to perform credential harvesting and then uses the stolen account details to access the network.
-   Supply chain—rather than attack the target directly, a threat actor may seek ways to infiltrate it via companies in its supply chain. One high-profile example of this is the Target data breach, which was made via the company's HVAC supplier ([krebsonsecurity.com/2014/02/target-hackers-broke-in-via-hvac-company](https://krebsonsecurity.com/2014/02/target-hackers-broke-in-via-hvac-company/)).
-   Web and social media—malware may be concealed in files attached to posts or presented as downloads. An attacker may also be able to compromise a site so that it automatically infects vulnerable browser software (a drive-by download). Social media may also be used more subtly, to reinforce a social engineering campaign and drive the adoption of Trojans.
-   Cloud—many companies now run part or all of their network services via Internet-accessible clouds. The attacker only needs to find one account, service, or host with weak credentials to gain access. The attacker is likely to target the accounts used to develop services in the cloud or manage cloud systems. They may also try to attack the cloud service provider (CSP) as a way of accessing the victim system.

Sophisticated threat actors will make use of multiple vectors. They are likely to plan a multi-stage campaign, rather than a single "smash and grab" type of raid.