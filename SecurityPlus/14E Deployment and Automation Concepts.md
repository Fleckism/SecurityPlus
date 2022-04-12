---
tags: [A_D,section]
---
# EXAM OBJECTIVES COVERED

2.3 Summarize secure application development, deployment, and automation concepts

Most organizations use Agile methodologies, involving a development process of continuous integration, delivery, and deployment. You will need to be able to support the creation and use of secure development and staging environments, plus the use of provisioning and deprovisioning tools.
# APPLICATION DEVELOPMENT, ==DEPLOYMENT, AND AUTOMATION==

A [[DevSecOps]] culture gives project teams a broad base of development, security, and operations expertise and experience. This promotes an environment in which security tasks make increased use of automation. Automation is the completion of an administrative task without human intervention. **Task automation steps may be configurable through a GUI control panel, via a command line, or via an API called by scripts**. Tasks can be automated to provision resources, add accounts, assign permissions, perform incident detection and response, and any number of other network security tasks.

**Manual configuration introduces a lot of scope for making errors.** A technician may be unsure of best practice, or there may be a lack of documentation. Over time, this leads to many small discrepancies in the way instances and services are configured. These small discrepancies can become big problems when it comes to maintaining, updating, and securing IT and cloud infrastructure. **Automation provides better scalability and elasticity:**

-   **Scalability means that the costs involved in supplying the service to more users are linear.** For example, if the number of users doubles in a scalable system, the costs to maintain the same level of service would also double (or less than double). If costs more than double, the system is less scalable.
-   **Elasticity refers to the system's ability to handle changes on demand in real time.** A system with high elasticity will not experience loss of service or performance if demand suddenly doubles (or triples, or quadruples). Conversely, it may be important for the system to be able to reduce costs when demand is low. Elasticity is a common selling point for cloud services. Instead of running a cloud resource for 24 hours a day, 7 days a week, that resource can diminish in power or shut down completely when demand for that resource is low. When demand picks up again, the resource will grow in power to the level required. This results in cost-effective operations.
# SECURE APPLICATION DEVELOPMENT ENVIRONMENTS

Security must be a key component of the application or automation design process. Even a simple form and script combination can make a web server vulnerable if the script is not well written. A software development life cycle ([[SDLC]]) divides the creation and maintenance of software into discrete phases. There are two principal SDLCs: the waterfall model and Agile development. Both these models stress the importance of **requirements analysis** and **quality processes** to the success of development projects.

### Quality Assurance (QA)

**Quality processes are how an organization tests a system to identify whether it complies with a set of requirements and expectations.** These requirements and expectations can be driven by risk-based assessments, or they can be driven by internal and external compliance factors, such as industry regulations and company-defined quality standards. Quality control (QC) is the process of determining whether a system is free from defects or deficiencies. **QC procedures are themselves defined by a quality assurance (QA) process, which analyzes what constitutes "quality" and how it can be measured and checked.**

### Development Environments

To meet the demands of the life cycle model and quality assurance, code is normally passed through several different environments:

-   **Development**—the code will be hosted on a secure server. Each developer will check out a portion of code for editing on his or her local machine. The local machine will normally be configured with a sandbox for local tes ting. This ensures that whatever other processes are being run locally do not interfere with or compromise the application being developed.
-   **Test/integration**—in this environment, code from multiple developers is merged to a single master copy and subjected to basic unit and functional tests (either automated or by human testers). These tests aim to ensure that the code builds correctly and fulfills the functions required by the design.
-   **Staging**—this is a mirror of the production environment but may use test or sample data and will have additional access controls so that it is only accessible to test users. Testing at this stage will focus more on usability and performance.
-   **Production**—the application is released to end users.

Secure development environments. (Images © 123RF.com.)

It is important to be able to validate the integrity of each coding environment. Compromise in any environment could lead to the release of compromised code.

-   **Sandboxing**—each development environment should be segmented from the others. No processes should be able to connect to anything outside the sandbox. Only the minimum tools and services necessary to perform code development and testing should be allowed in each sandbox.
-   **Secure configuration baseline**—each development environment should be built to the same specification, possibly using automated provisioning.
-   Integrity measurement—this process determines whether the development environment varies from the configuration baseline. Perhaps a developer added an unauthorized tool to solve some programming issue. Integrity measurement may be performed by scanning for [[unsigned files]] or files that do not otherwise match the baseline. The Linux diff command can be used to compare file structures ([linux.die.net/man/1/diff](https://linux.die.net/man/1/diff)).
# PROVISIONING, DEPROVISIONING, AND VERSION CONTROL

The use of development life cycle models and QA processes extends past development and testing to the deployment and maintenance of an application or script-based automation task.

### Provisioning

**Provisioning is the process of deploying an application to the target environment,** such as enterprise desktops, mobile devices, or cloud infrastructure. An enterprise provisioning manager might assemble multiple applications in a package. Alternatively, the OS and applications might be defined as a single instance for deployment on a virtualized platform. The provisioning process must account for changes to any of these applications so that packages or instances are updated with the latest version.

### Deprovisioning

Deprovisioning is the process of **removing** an application from packages or instances. This might be necessary if software has to be completely rewritten or no longer satisfies its purpose. As well as removing the application itself, it is also important to make appropriate environment changes to remove any configurations (such as open firewall ports) that were made just to support that application.

### Version Control

Version control is an ID system for each iteration of a software product. Most version control numbers represent both the version, as made known to the customer or end user, and internal build numbers for use in the development process. Version control supports the change management process for software development projects. Most software development environments use a build server to maintain a repository of previous versions of the source code. When a developer commits new or changed code to the repository, the new source code is tagged with an updated version number and the old version archived. This allows changes to be rolled back if a problem is discovered.
# AUTOMATION/SCRIPTING RELEASE PARADIGMS

Coding projects are managed using different life cycle models. The **waterfall** model software development life cycle (SDLC) **is an older paradigm that focuses on the successful completion of monolithic projects that progress from stage to stage**. The more recent **Agile paradigm uses iterative processes to release well-tested code in smaller blocks or units.** In this model, development and provisioning tasks are conceived as continuous.

### Continuous Integration

Continuous integration ([[CI]]) is the principle that developers should commit and test updates often—every day or sometimes even more frequently. This is designed to reduce the chances of two developers spending time on code changes that are later found to conflict with one another. CI aims to detect and resolve these conflicts early, as it is easier to diagnose one or two conflicts or build errors than it is to diagnose the causes of tens of them. For effective CI, it is important to use an automated test suite to validate each build quickly.

### Continuous Delivery

Where **CI is about managing code in development**, continuous delivery is about testing all of the **[[infrastructure]] that supports the app, including networking, database functionality, client software,** and so on.

### Continuous Deployment

Where **continuous delivery tests that an app version and its supporting infrastructure are ready for production**, continuous deployment is the separate process of **actually making changes** to the production environment to support the new app version.

Automation and continuous release paradigms. (Images © 123RF.com.)

### Continuous Monitoring and Automated Courses of Action

An automation solution will have a system of continuous monitoring to detect service failures and security incidents. Continuous monitoring might use a locally installed agent or [[heartbeat protocol]] or may involve checking availability remotely. As well as monitoring the primary site, it is important to observe the failover components to ensure that they are recovery ready. You can also automate the courses of action that a monitoring system takes, like configuring an IPS to automatically block traffic that it deems suspicious. This sort of capability is provided by security orchestration and response ([[SOAR]]) management software.

### Continuous Validation

An application model is a statement of the requirements driving the software development project. The requirements model is tested using processes of verification and validation (V&V):

-   **Verification** is a compliance testing process to ensure that the product or system meets its design goals.
-   **Validation** is the process of determining whether the application is fit-for-purpose (so for instance, its design goals meet the user requirements).

With the continuous paradigm, feedback from delivery and deployment must be monitored and evaluated to ensure that the design goals continue to meet user and security requirements. The monitoring and validation processes must also ensure that there is no drift from the secure configuration baseline.
# SOFTWARE DIVERSITY

An application's runtime environment will use one of two approaches for execution on a host system:

-   **Compiled code** is converted to binary machine language that can run **independently** on the target OS.
-   **Interpreted code** is packaged pretty much as is but is compiled line-by-line by an interpreter, such as PowerShell or JavaScript. This offers a solution that is **platform-independent** because the interpreter resolves the differences between OS types and versions.

Software diversity can refer to obfuscation techniques to make code difficult to detect as malicious. This is widely used by [[threat actor]]s in the form of shellcode compilers to avoid signature detection, such as the venerable Shikata Ga Nai ([fireeye.com/blog/threat-research/2019/10/shikata-ga-nai-encoder-still-going-strong.html](https://www.fireeye.com/blog/threat-research/2019/10/shikata-ga-nai-encoder-still-going-strong.html)). This can be used as a defensive technique. **Obfuscating API methods and automation code makes it harder for a [[[[threat actor]]]] to reverse engineer and analyze the code to discover weaknesses.**

There is also general research interest in [[security by diversity]]. This works on the principle that attacks are harder to develop against nonstandard environments. A monoculture environment, such as a Windows domain network, presents a fairly predictable attack surface with plenty of commodity malware tools available to exploit misconfigurations. Using a wide range of development tools and OS/application vendors and versions can make attack strategies harder to research. As with security by obscurity, this will not defeat a targeted attack, but it can partially mitigate risks from less motivated [[threat actor]]s, who will simply move to the next, easier target. On the other hand, this sort of complexity will tend to lead to greater incidence of configuration errors as technicians and developers struggle to master unfamiliar technologies.
