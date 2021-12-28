#Threats 
Definitions used in section
tactics, techniques, and procedures (TTPs)
 TTPs and their indicators
 honeynets to try to observe how hackers interact with vulnerable systems.
 
 ## Threat Research Sources
 -  Dark net—a network established as an overlay to Internet infrastructure by software, such as The Onion Router (TOR), Freenet, or I2P, that acts to anonymize usage and prevent a third party from knowing about the existence of the network or analyzing any activity taking place over the network. Onion routing, for instance, uses multiple layers of encryption and relays between nodes to achieve this anonymity.
 -  Dark web—sites, content, and services accessible only over a dark net. While there are dark web search engines, many sites are hidden from them. Access to a dark web site via its URL is often only available via "word of mouth" bulletin boards.
 -  Investigating these dark web sites and message boards is a valuable source of counterintelligence.

## Threat Intelligence Providers
- Threat data can be packaged as feeds that integrate with a security information and event management (SIEM) platform. These feeds are usually described as cyber threat intelligence (CTI) data. The data on its own is not a complete security solution however. To produce actionable intelligence, the threat data must be correlated with observed data from customer networks. This type of analysis is often powered by artificial intelligence (AI) features of the SIEM.
- Threat intelligence platforms
	
    - IBM X-Force Exchange ([exchange.xforce.ibmcloud.com](https://exchange.xforce.ibmcloud.com/))
	-   FireEye ([fireeye.com/solutions/cyber-threat-intelligence/threat-intelligence-subscriptions.html](https://www.fireeye.com/mandiant/threat-intelligence/threat-intelligence-subscriptions.html))
	-   Recorded Future ([recordedfuture.com/solutions/threat-intelligence-feeds](https://www.recordedfuture.com/solutions/threat-intelligence-feeds/))
 ## Tactics, techniques, and procedures and indicators of comprise.
 
 A tactic, technique, or procedure (TTP) is a generalized statement of adversary behavior. The term is derived from US military doctrine ([mwi.usma.edu/what-is-army-doctrine](https://mwi.usma.edu/what-is-army-doctrine/)). TTPs categorize behaviors in terms of campaign strategy and approach (tactics), generalized attack vectors (techniques), and specific intrusion tools and methods (procedures).
 
indicator of compromise (IoC) is a residual sign that an asset or network has been successfully attacked or is continuing to be attacked. Put another way, an IoC is evidence of a TTP.

> TTPs describe what and how an adversary acts and Indicators describe how to recognize what those actions might look like. ([stixproject.github.io/documentation/concepts/ttp-vs-indicator](https://stixproject.github.io/documentation/concepts/ttp-vs-indicator/))

As there are many different targets and vectors of an attack, so too are there many different potential IoCs. The following is a list of some IoCs that you may encounter:

-   Unauthorized software and files
-   Suspicious emails
-   Suspicious registry and file system changes
-   Unknown port and protocol usage
-   Excessive bandwidth usage
-   Rogue hardware
-   Service disruption and defacement
-   Suspicious or unauthorized account usage

## Threat data feeds
### Structured Threat Information eXpression (STIX)

The OASIS CTI framework ([oasis-open.github.io/cti-documentation](https://oasis-open.github.io/cti-documentation/)) is designed to provide a format for this type of automated feed so that organizations can share CTI. The Structured Threat Information eXpression (STIX) part of the framework describes standard terminology for IoCs and ways of indicating relationships between them.

![[Pasted image 20211227222848.png]]

- STIX provides a industry standard for the CTI