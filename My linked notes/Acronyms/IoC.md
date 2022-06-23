**indicator of compromise (IoC)** aka indicator of risk
-   Unauthorized software and files
-   Suspicious emails
-   Suspicious registry and file system changes
-   Unknown port and protocol usage
-   Excessive bandwidth usage
-   Rogue hardware
-   Service disruption and defacement
-   Suspicious or unauthorized account usage

An IoC can be definite and objectively identifiable, like a malware signature, but often IoCs can only be described with confidence via the correlation of many data points. Because these IoCs are often identified through patterns of anomalous activity rather than single events, they can be open to interpretation and therefore slow to diagnose. Consequently, threat intelligence platforms use AI-backed analysis to speed up detection without overwhelming analysts' time with false positives.

Strictly speaking, an [[IoC]] is evidence of an attack that was successful. The term **indicator of attack ([[IoA]])** is sometimes also used for evidence of an intrusion **attempt in progress**.

Put another way, an IoC is evidence of a [[TTPs]].
IoA:  Indicator of an attack that is currently happening.
IoC:  are “pieces of forensic data, such as data found in system log entries or files, that identify potentially malicious activity on a system or network.” Indicators of compromise aid information security and IT professionals in detecting data breaches, malware infections, or other threat activity. By monitoring for indicators of compromise, organizations can detect attacks and act quickly to prevent breaches from occurring or limit damages by stopping attacks in earlier stages.

There are several indicators of compromise that organizations should monitor. In an [article for DarkReading](http://www.darkreading.com/attacks-breaches/top-15-indicators-of-compromise/d/d-id/1140647?), Ericka Chickowski highlights 15 key indicators of compromise:

Indicators 
-   Unusual Outbound Network Traffic
-   Anomalies in Privileged User Account Activity
-   Geographical Irregularities
-   Log-In Red Flags
-   Increases in Database Read Volume
-   HTML Response Sizes
-   Large Numbers of Requests for the Same File
-   Mismatched Port-Application Traffic
-   Suspicious Registry or System File Changes
-   Unusual DNS Requests
-   Unexpected Patching of Systems
-   Mobile Device Profile Changes
-   Bundles of Data in the Wrong Place
-   Web Traffic with Unhuman Behavior
-   Signs of DDoS Activity