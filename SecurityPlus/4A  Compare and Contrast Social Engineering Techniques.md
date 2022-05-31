---
tags: [A4 ]
---
#GRC 
## Introduction
It is not sufficient for [[security assesment]]s to focus solely on software vulnerabilities and configuration errors. As well as these hardware and software systems, the attack surface contains a company's employees and the degree to which they can be exploited to gain unauthorized access or privileges. [[threat actor]]s use [[Social engineering]] techniques to elicit information, obtain access to premises, and to trick users into running malicious code. You must understand these attacks and train your colleagues and customers with the ability to detect and report them. As well as being able to explain these techniques, you must be able to describe the indicators associated with different types of malware and analyze #Ops your systems for possible infections.

LESSON OBJECTIVES

In this lesson, you will:

-   Compare and contrast [[Social engineering]] techniques.
-   analyze #Ops indicators of malware-based attacks.

EXAM OBJECTIVES COVERED

1.1 Compare and contrast different types of [[Social engineering]] techniques

People—employees, contractors, suppliers, and customers—represent part of the attack surface of any organization. A person with permissions on the system is a potential target of [[Social engineering]]. Being able to compare and contrast [[Social engineering]] techniques will help you to lead security awareness training and to develop policies and other security controls to mitigate these risks.

## [[Social engineering]]

Adversaries can use a diverse range of techniques to compromise a security system. A prerequisite of many types of attacks is to obtain information about the network and security system. [[Social engineering]] refers to means of either eliciting information from someone or getting them to perform some action for the [[threat actor]]. It can also be referred to as "hacking the human." [[Social engineering]] might be used to gather intelligence as [[reconnaissance]] in preparation for an intrusion, or it might be used to effect an actual intrusion. Typical [[Social engineering]] intrusion scenarios include:

-   An attacker creates an **executable file** that prompts a network user for their password, and then records whatever the user inputs. The attacker then emails the executable file to the user with the story that the user must double-click the file and log on to the network again to clear up some logon problems the organization has been experiencing that morning. After the user complies, the attacker now has access to their network credentials.
-   An attacker contacts the help desk pretending to be a remote sales representative who needs assistance setting up remote access. Through a series of phone calls, the attacker obtains the name/address of the remote access server and login credentials, in addition to phone numbers for remote access and for accessing the organization's private phone and voice-mail system.
-   An attacker triggers a fire alarm and then slips into the building during the confusion and attaches a monitoring device to a network port.

## [[Social engineering]] PRINCIPLES

[[[[Social engineering]]]] is one of the most common and successful malicious techniques. Because it exploits basic human trust, [[Social engineering]] has proven to be a particularly effective way of manipulating people into performing actions that they might not otherwise perform. To be persuasive, [[Social engineering]] attacks rely on one or more of the following principles.

### [[Familiarity Liking]]

Some people have the sort of natural charisma that allows them to persuade others to do as they request. One of the basic tools of a social engineer is simply to be affable and likable, and to present the requests they make as completely reasonable and unobjectionable. This approach is relatively low-risk as even if the request is refused, it is less likely to cause suspicion and the social engineer may be able to move on to a different target without being detected.

### [[Consensus Social Proof]]

The _principle of consensus_ or _social proof_ refers to the fact that without an explicit instruction to behave in a certain way, many people will act just as they think others would act. A [[Social engineering]] attack can use this instinct either to persuade the target that to refuse a request would be odd ("That's not something anyone else has ever said no to") or to exploit polite behavior to slip into a building while someone holds the door for them. As another example, an attacker may be able to fool a user into believing that a malicious website is actually legitimate by posting numerous fake reviews and testimonials praising the site. The victim, believing many different people have judged the site acceptable, takes this as evidence of the site's legitimacy and places their trust in it.

### Authority and Intimidation

Many people find it difficult to refuse a request by someone they perceive as superior in rank or expertise. Social engineers can try to exploit this behavior to intimidate their target by pretending to be a senior executive. An attack might be launched by impersonating someone who would often be deferred to, such as a police officer, judge, or doctor. Another technique is using spurious technical arguments and jargon. [[Social engineering]] can exploit the fact that few people are willing to admit ignorance. Compared to using a familiarity/liking sort of approach, this sort of adversarial tactic might be riskier to the attacker as there is a greater chance of arousing suspicion and the target reporting the attack attempt.

### Scarcity and Urgency

Often also deployed by salespeople, creating a false sense of scarcity or urgency can disturb people's ordinary decision-making process. The social engineer can try to pressure his or her target by demanding a quick response. For example, the social engineer might try to get the target to sign up for a "limited time" or "invitation-only" trial and request a username and password for the service (hoping that the target will offer a password he or she has used for other accounts). Fake antivirus products generate a sense of urgency by trying to trick users into thinking that their computer is already infected with malware.
 
 
 
## ## IMPERSONATION AND TRUST

Impersonation simply means pretending to be someone else. It is one of the basic [[Social engineering]] techniques. Impersonation can use either a consensus/liking or intimidating approach. Impersonation is possible where the target cannot verify the attacker's identity easily, such as over the phone or via an email message.

The classic impersonation attack is for the social engineer to phone into a department, claim they have to adjust something on the user's system remotely, and get the user to reveal their password. This specific attack is also referred to as _pretexting._

![Man holding phone to ear and smiling with a black rectangle superimposed over his eyes.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/6066-1599771796063.png)

Do you really know who's on the other end of the line?

Making a convincing impersonation and establishing a trust with the target usually depends on the attacker obtaining privileged information about the organization. For example, where the attacker impersonates a member of the organization's IT support team, the attack will be more effective with identity details of the person being impersonated and the target.

Some [[Social engineering]] techniques are dedicated to obtaining this type of intelligence as a [[reconnaissance]] activity. As most companies are set up toward customer service rather than security, this information is typically quite easy to come by. Information that might seem innocuous—such as department employee lists, job titles, phone numbers, diaries, invoices, or purchase orders—can help an attacker penetrate an organization through impersonation.

DUMPSTER DIVING AND TAILGATING

[[Social engineering]] includes physical attacks to steal information or gain access.

### Dumpster Diving

Dumpster diving refers to combing through an organization's (or individual's) garbage to try to find useful documents (or even files stored on discarded removable media).

Remember that attacks may be staged over a long period. Initial attacks may only aim at compromising low-level information and user accounts, but this low-level information can be used to attack more sensitive and confidential data and better protected management and administrative accounts.

### Tailgating and Piggy Backing

Tailgating is a means of entering a secure area without authorization by following close behind the person that has been allowed to open the door or checkpoint. _Piggy backing_ is a similar situation, but means that the attacker enters a secure area with an employee's permission. For instance, an attacker might impersonate a member of the cleaning crew and request that an employee hold the door open while they bring in a cleaning cart or mop bucket. Alternatively, piggy backing may be a means of an insider [[threat actor]] to allow access to someone without recording it in the building's entry log. Another technique is to persuade someone to hold a door open, using an excuse, such as "I've forgotten my badge/key."

## IDENTITY FRAUD AND INVOICE SCAMS

Identity fraud is a specific type of impersonation where the attacker uses specific details of someone's identity. A typical consumer identity fraud is using someone else's name and address to make a loan application or using stolen credit card details to start a mobile phone contract. Invoice scams are another common type of identity fraud. The fraudster will usually spoof the invoice details of a genuine supplier, but change the bank account number. This might rely on the target not double-checking the account, or it might be combined with a [[Social engineering]] contact call to convince the target that the account change is genuine.

_Sometimes the terms identity fraud and identity theft are used to distinguish between making up an identity versus stealing someone else's identity._

In terms of attacks on corporate networks, identity fraud is likely to involve compromising a computer account. Various [[Social engineering]] techniques can be used to obtain account credentials without having to rely on malware.  Apart from eliciting credential information from a user directly, some of these techniques include:

-   Credential databases—account details from previous attacks are widely available ([haveibeenpwned.com](https://haveibeenpwned.com/)). An attacker can try to match a target in one of these databases and hope that they have reused a password. The attacker could also leverage third-party sites for impersonation. For example, rather than using a work account, they could gain control of a social media account.
-   [[Shoulder surfing]]—a [[threat actor]] can learn a password or PIN (or other secure information) by watching the user type it. Despite the name, the attacker may not have to be in close proximity to the target—they could use high-powered binoculars or CCTV to directly observe the target remotely.
-   Lunchtime attacks—most authentication methods are dependent on the physical security of the workstation. If a user leaves a workstation unattended while logged on, an attacker can physically gain access to the system. This is often described as a _lunchtime attack._ Most operating systems are set to activate a password-protected screen saver after a defined period of no keyboard or mouse activity. Users should also be trained to lock or log off the workstation whenever they leave it unattended.

## PHISHING, WHALING, AND VISHING

[[Phishing]] is a combination of [[[[Social engineering]]]] and [[spoofing]]. It persuades or tricks the target into interacting with a malicious resource disguised as a trusted one, traditionally using email as the vector. A phishing message might try to convince the user to perform some action, such as installing disguised malware or allowing a remote access connection by the attacker. Other types of phishing campaign use a spoof website set up to imitate a bank or e‑commerce site or some other web resource that should be trusted by the target. The attacker then emails users of the genuine website informing them that their account must be updated or with some sort of hoax alert or alarm, supplying a disguised link that actually leads to the spoofed site. When the user authenticates with the spoofed site, their logon credentials are captured. 

![Clickable images and text in the original email shown in the background have been replaced by the actual links in the email shown in the foreground.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/1515-1599771796223.jpg)

Example phishing email—On the right, you can see the message in its true form as the mail client has stripped out the formatting (shown on the left) designed to disguise the nature of the links.

There are several phishing variants to be aware of:

-   [[Spear phishing]]—a phishing scam where the attacker has some information that makes an individual target more likely to be fooled by the attack. Each phishing message is tailored to address a specific target user. The attacker might know the name of a document that the target is editing, for instance, and send a malicious copy, or the phishing email might show that the attacker knows the recipient's full name, job title, telephone number, or other details that help convince the target that the communication is genuine.
-   [[Whaling]]—a spear phishing attack directed specifically against upper levels of management in the organization (CEOs and other "big fish"). Upper management may also be more vulnerable to ordinary phishing attacks because of their reluctance to learn basic security procedures.
-   [[Vishing]]—a phishing attack conducted through a voice channel (telephone or VoIP, for instance). For example, targets could be called by someone purporting to represent their bank asking them to verify a recent credit card transaction and requesting their security details. It can be much more difficult for someone to refuse a request made in a phone call compared to one made in an email. 

Rapid improvements in deep fake technology ([forbes.com/sites/jessedamiani/2019/09/03/a-voice-deepfake-was-used-to-scam-a-ceo-out-of-243000](https://www.forbes.com/sites/jessedamiani/2019/09/03/a-voice-deepfake-was-used-to-scam-a-ceo-out-of-243000/)) are likely to make phishing attempts via voice and even video messaging more prevalent in the future.

-   [[SMiShing]]—this refers to using short message service (SMS) text communications as the vector.

## SPAM, HOAXES, AND PREPENDING

Unsolicited email, or [[spam]], is used as the vector for many attacks. [[threat actor]]s harvest email addresses from marketing lists or databases of historic privacy breaches, or might try to target every email address at a certain company. Mass mail attacks could also be perpetrated over any type of instant messaging or Internet messaging service ([[SPIM]]).

Hoaxes, such as security alerts or chain emails, are another common [[Social engineering]] technique, often combined with phishing attacks. An email alert or web pop-up will claim to have identified some sort of security problem, such as virus infection, and offer a tool to fix the problem. The tool of course will be some sort of Trojan application. Malvertising exploits the use of space on legitimate websites set aside for advertising served from content delivery networks (CDNs) without much oversight ([blog.talosintelligence.com/2019/07/malvertising-deepdive.html](https://blog.talosintelligence.com/2019/07/malvertising-deepdive.html)). Criminals will also use sophisticated phone call scams to try to trick users into revealing login credentials or financial account details.

A phishing or hoax email can be made more convincing by prepending. In an offensive sense, _prepending_ means adding text that appears to have been generated by the mail system. For example, an attacker may add "RE:" to the subject line to make it appear as though the message is a reply or may add something like "MAILSAFE: PASSED" to make it appear as though a message has been scanned and accepted by some security software. Conversely, some mail systems may perform prepending legitimately, such as tagging external messages or messages with a warning if they have not been definitively identified as spam but that do have suspicious elements.

## PHARMING AND CREDENTIAL HARVESTING

Direct messages to a single contact have quite a high chance of failure. Other [[Social engineering]] techniques still use spoofed resources, such as fake sites and login pages, but rely on redirection or passive methods to entrap victims.

### Pharming

[[Pharming]] is a passive means of redirecting users from a legitimate website to a malicious one. Rather than using [[Social engineering]] techniques to trick the user, pharming relies on corrupting the way the victim's computer performs Internet name resolution, so that they are redirected from the genuine site to the malicious one. For example, if mybank.foo should point to the IP address 2.2.2.2, a pharming attack would corrupt the name resolution process to make it point to IP address 6.6.6.6. 

### Typosquatting

Rather than redirection, a [[threat actor]] might use typosquatting. This means that the [[threat actor]] registers a domain name that is very similar to a real one, such as connptia.org, hoping that users will not notice the difference. These are also referred to as _cousin, lookalike,_ or _doppelganger_ domains. Typosquatting might be used for pharming and phishing attacks. Another technique is to register a hijacked subdomain using the primary domain of a trusted cloud provider, such as onmicrosoft.com. If a phishing message appears to come from comptia.onmicrosoft.com, many users will be inclined to trust it. 

### Watering Hole Attack

A watering hole attack is another passive technique where the [[threat actor]] does not have to risk communicating directly with the target. It relies on the circumstance that a group of targets may use an unsecure third-party website. For example, staff running an international e-commerce site might use a local pizza delivery firm. If an attacker can compromise the pizza delivery firm's website or deploy a type of malvertising, they may be able to infect the computers of the e-commerce company's employees and penetrate the e-commerce company systems.

### Credential Harvesting

Within the general realm of phishing and pharming, credential harvesting is a campaign specifically designed to steal account credentials. The attacker may have more interest in selling the database of captured logins than trying to exploit them directly. Such attacks will use an alarming message such as "Your account is being used to host child pornography" or "There is a problem with your account storage" and a link to a pharming site embroidered with the logos of a legitimate service provider, such as Google, Microsoft, Facebook, or Twitter. Attacks using malvertising or scripts injected into shopping cart code are also popular ([csoonline.com/article/3400381/what-is-magecart-how-this-hacker-group-steals-payment-card-data.html](https://www.csoonline.com/article/3400381/what-is-magecart-how-this-hacker-group-steals-payment-card-data.html)). Targeted credential harvesting might be directed against a single company's password reset or account management portal.

## INFLUENCE CAMPAIGNS

An _influence campaign_ is a major program launched by an adversary with a high level of capability, such as a nation-state actor, terrorist group, or hacktivist group. The goal of an influence campaign is to shift public opinion on some topic. Most high-profile influence campaigns that have been detected target election activity, but actors may use such campaigns to pursue a number of goals. With state actors, the concept of _soft power_ refers to using diplomatic and cultural assets to achieve an objective. When deployed along with espionage, disinformation/fake news, and hacking, a hostile campaign can be characterized as hybrid warfare ([assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/840513/20190401-MCDC_CHW_Information_note_-_Conceptual_Foundations.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/20190401-MCDC_CHW_Information_note_-_Conceptual_Foundations.pdf)).

Diplomatic activity and election meddling by foreign security services has a very long history and well-established tactics. Modern campaigns can use social media to ensure wide distribution of hoaxes and invented stories. Actors can use AI-assisted bots and armies of people to open or hack accounts and repeat or reinforce messages that support the campaign's aims.

Apart from destabilizing the host country generally, influence campaigns might affect private companies because they become caught up within a fake story. It is important for companies to closely monitor references to them on social media and take steps to correct or remove false or misleading posts. When an influence campaign is detected, companies operating in critical industries—utilities, election management, transportation—should enter a heightened state of alert.

