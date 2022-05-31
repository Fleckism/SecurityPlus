
security assessment
**Network reconnaissance and discovery is used to identify hosts, network topology, and open services/ports, establishing an overall attack surface**. Various types of security assessments can be used to test these hosts and services for vulnerabilities. There are many models and frameworks for conducting security assessments. A good starting point is NIST's Technical Guide to Information Security Testing and Assessment ([nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-115.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/nistspecialpublication800-115.pdf)). SP 800-115 identifies three principal activities within an assessment:

-   Testing the object under assessment to discover vulnerabilities or to prove the effectiveness of security controls.
-   Examining assessment objects to understand the security system and identify any logical (logic bomb ? ) weaknesses. This might highlight a lack of security controls or a common misconfiguration.
-   Interviewing personnel to gather information and probe attitudes toward and understanding of security.

#concepts The main types of security [[assessment]]  are usually classed as **vulnerability assessment, [[threat hunting]], and penetration testing**. A vulnerability assessment is an evaluation of a system's security and ability to meet compliance requirements based on the configuration state of the system. Essentially, the vulnerability assessment determines if the current configuration matches the ideal configuration (the baseline). Vulnerability assessments might involve manual inspection of security controls, but are more often accomplished through automated vulnerability scanners.
## VULNERABILITY SCAN TYPES

An automated scanner must be configured with signatures and scripts that can correlate known software and configuration vulnerabilities with data gathered from each host. Consequently, there are several types of vulnerability scanners optimized for different tasks.

#flashcard: Before running a vulnerability scan verify that the vulnerability feed/plug-in/test has been updated with the specific CVE (Common Vulnerabilities and exposure) that you need to test for
### Network Vulnerability Scanner

A network vulnerability scanner, such as Tenable Nessus ([tenable.com/products/nessus](https://www.tenable.com/products/nessus)) or OpenVAS ([openvas.org](https://www.openvas.org/)), is designed to test network hosts, including client PCs, mobile devices, servers, routers, and switches. It examines an organization's on-premises systems, applications, and devices and compares the scan results to configuration templates plus lists of known vulnerabilities. Typical results from a vulnerability assessment will identify missing patches, deviations from baseline configuration templates, and other related vulnerabilities. 

![Dashboard shows 5 graphs titled Tasks by Severity Class, Tasks by status, CVEs by creation time, Hosts topology, and NVTs by Severity Class.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/9230-1599771795158.png)

Greenbone OpenVAS vulnerability scanner with Security Assistant web application interface as installed on Kali Linux. (Screenshot used with permission from Greenbone Networks, [http://www.openvas.org](http://www.openvas.org/).)

The first phase of scanning might be to run a detection scan to discover hosts on a particular IP subnet. In the next phase of scanning, a target range of hosts is probed to detect running services, patch level, security configuration and policies, network shares, unused accounts, weak passwords, antivirus configuration, and so on.

Each scanner is configured with a database of known software and configuration vulnerabilities. The tool compiles a report about each vulnerability in its database that was found to be present on each host. Each identified vulnerability is categorized and assigned an impact warning. Most tools also suggest remediation techniques. This information is highly sensitive, so use of these tools and the distribution of the reports produced should be restricted to authorized hosts and user accounts.

Network vulnerability scanners are configured with information about known vulnerabilities and configuration weaknesses for typical network hosts. These scanners will be able to test common operating systems, desktop applications, and some server applications. This is useful for general purpose scanning, but some types of applications might need more rigorous analysis.

### Application and Web Application Scanners

A dedicated application scanner is configured with more detailed and specific scripts to test for known attacks, as well as scanning for missing patches and weak configurations. The best known class of application scanners are web application scanners. Tools such as Nikto ([cirt.net/Nikto2](https://cirt.net/Nikto2)) look for known web exploits, such as SQL injection and cross-site scripting (XSS), and may also analyze source code and database security to detect unsecure programming practices. Other types of application scanners would be optimized for a particular class of software, such as a database server.