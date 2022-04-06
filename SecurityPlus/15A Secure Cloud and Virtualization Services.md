---
tags: [Implementation, A_D,section]
---
# LESSON INTRODUCTION

The main idea behind cloud computing is that you can access and manage your data and applications from any host, anywhere in the world, while the storage method and location are hidden or abstracted through virtualization. Cloud applications—whether accessed as public services or provisioned over private virtualization infrastructure—are rapidly overtaking on-premises service delivery models. Cloud security considerations will form an increasingly important part of your career as a security professional. 

Lesson Objectives

In this lesson, you will:

-   Summarize secure cloud and virtualization services.
-   Apply cloud security solutions.
-   Summarize infrastructure as code concepts.
# EXAM OBJECTIVES COVERED

2.2 Summarize virtualization and cloud computing concepts

In a traditional infrastructure, an attacker may find intrusions to be difficult as the network can be isolated from the outside world. In a cloud environment, the attacker may simply need to have an Internet connection and a **dictionary of stolen password hashes or SSH** keys to cause a breach. A lack of oversight in the security procedures of cloud providers can dramatically increase the risk an organization takes. As a security professional, you must be able to assess the threats and vulnerabilities associated with cloud service and delivery models, plus the virtualization technologies that underpin them.
# CLOUD DEPLOYMENT MODELS

A cloud deployment model classifies how the service is owned and provisioned. It is important to recognize the different impacts deployment models have on threats and vulnerabilities. **Cloud deployment models** can be broadly categorized as follows:

-   **Public (or multi-tenant)**—a service offered over the Internet by cloud service providers ([[CSPs]]) to cloud consumers. With this model, businesses can offer subscriptions or pay-as-you-go financing, while at the same time providing lower-tier services free of charge. As a shared resource, there are risks regarding performance and security. Multi-cloud architectures are where an organization uses services from multiple CSPs.
-   **Hosted Private**—hosted by a third-party for the exclusive use of the organization. This is more secure and can guarantee a better level of performance but is correspondingly more expensive.
-   **Private**—cloud infrastructure that is completely private to and owned by the organization. In this case, there is likely to be one business unit dedicated to managing the cloud while other business units make use of it. With private cloud computing, organizations can exercise greater control over the privacy and security of their services. This type of delivery method is geared more toward **banking and governmental services** that require strict access control in their operations.

This type of cloud could be on-premise or offsite relative to the other business units. An onsite link can obviously deliver better performance and is less likely to be subject to outages (loss of an Internet link, for instance). On the other hand, a dedicated offsite facility may provide better shared access for multiple users in different locations.

-   **Community**—this is where several organizations share the costs of either a hosted private or fully private cloud. This is usually done in order to pool resources for a common concern, like standardization and security policies.

There will also be cloud computing solutions that implement some sort of hybrid public/private/community/hosted/onsite/offsite solution. For example, a travel organization may run a sales website for most of the year using a private cloud but break out the solution to a public cloud at times when much higher utilization is forecast.

**Flexibility is a key advantage** of cloud computing, but the implications for data risk must be well understood when moving data between private and public storage environments.
# CLOUD SERVICE MODELS

As well as the **ownership model (public, private, hybrid, or community)**, cloud services are often differentiated on the level of **complexity** and pre-configuration provided. These models are referred to as something or anything as a service (XaaS). The three most common implementations are infrastructure, software, and platform.

### Infrastructure as a Service

**Infrastructure as a service (IaaS) is a means of provisioning IT resources such as servers, load balancers, and storage area network (SAN) components quickly. Rather than purchase these components and the Internet links they require,** you rent them on an as-needed basis from the service provider's data center. Examples include Amazon Elastic Compute Cloud ([aws.amazon.com/ec2](https://aws.amazon.com/ec2/)), Microsoft Azure Virtual Machines ([azure.microsoft.com/services/virtual-machines](https://azure.microsoft.com/services/virtual-machines)), Oracle Cloud ([oracle.com/cloud](https://www.oracle.com/cloud/)), and OpenStack ([openstack.org](https://www.openstack.org/)).

### Software as a Service

**Software as a service (SaaS) is a different model of provisioning software applications. Rather than purchasing software licenses for a given number of seats, a business would access software hosted on a supplier's servers on a pay-as-you-go or lease arrangement (on-demand). Virtual infrastructure allows developers to provision on-demand applications much more quickly than previously. The applications can be developed and tested in the cloud without the need to test and deploy on client computers.** Examples include Microsoft Office 365 ([microsoft.com/en-us/microsoft-365/enterprise](https://www.microsoft.com/en-us/microsoft-365/enterprise)), Salesforce ([salesforce.com](https://www.salesforce.com/)), and Google G Suite ([gsuite.google.com](https://gsuite.google.com/)).

### Platform as a Service

**Platform as a service (PaaS) provides resources somewhere between SaaS and IaaS. A typical PaaS solution would provide servers and storage network infrastructure (as per IaaS) but also provide a multi-tier web application/database platform on top. This platform could be based on Oracle or MS SQL or PHP and MySQL.** Examples include Oracle Database ([oracle.com/database](https://www.oracle.com/database/)), Microsoft Azure SQL Database ([azure.microsoft.com/services/sql-database](https://azure.microsoft.com/services/sql-database)), and Google App Engine ([cloud.google.com/appengine](https://cloud.google.com/appengine)).

As distinct from SaaS though, th**is platform would not be configured to actually do anything. Your own developers would have to create the software (the [[CRM]] or e‑commerce application) that runs using the platform**. The service provider would be responsible for the integrity and availability of the platform components, but you would be responsible for the security of the application you created on the platform.

![Screenshot of Amazon Web Services EC2 dashboard, showing Resources used, Scheduled Events, Account Attributes, and Additional Information.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/3838-1599771810001.png)

Dashboard for Amazon Web Services Elastic Compute Cloud (EC2) IaaS/PaaS. (Screenshot used with permission from [Amazon.com](https://www.amazon.com/).)
# ANYTHING AS A SERVICE

There are many other examples of [[XaaS]], reflecting the idea that anything can be provisioned as a cloud service. For example, database as a service and network as a service can be distinguished as more specific types of platform as a service. The key security consideration with all these models is identifying where responsibilities lie. This is often referred to as security in the cloud versus security of the cloud. **Security in the cloud is the things you must take responsibility for**;;;;; **security of the cloud is the things the CSP manages**. These responsibilities vary according to the service type:
{Insert actual table}
Responsibility

IaaS

PaaS

SaaS

IAM

You

You

You (using CSP toolset)

Data security (CIA attributes/backup)

You

You

You/CSP/Both

Data privacy

You/CSP/Both

You/CSP/Both

You/CSP/Both

Application code/configuration

You

You

CSP

Virtual network/firewall

You

You/CSP

CSP

Middleware (database) code/configuration

You

CSP

CSP

Virtual Guest OS

You

CSP

CSP

Virtualization layer

CSP

CSP

CSP

Hardware layer (compute, storage, networking)

CSP

CSP

CSP

Note that this matrix identifies generic responsibilities only. Specific terms must be set out in a contract and service level agreement (SLA) with the [[CSP]].
# SECURITY AS A SERVICE

The breadth of technologies requiring specialist security knowledge and configuration makes it likely that companies will need to depend on third-party support at some point. You can classify such support in three general "tiers":

-   **Consultants**—the experience and perspective of a third-party professional can be hugely useful in improving security awareness and capabilities in any type of organization (small to large). Consultants could be used for "big picture" framework analysis and alignment or for more specific or product-focused projects (pen testing, SIEM rollout, and so on). It is also fairly simple to control costs when using consultants if they are used to **develop capabilities rather than implement them**. Where consultants come to "own" the security function, it can be difficult to change or sever the relationship.
-   **Managed Security Services Provider** ([[MSSP]])—a means of fully outsourcing responsibility for[[ information assurance]] to a third party. This type of solution is expensive but can be a good fit for a [[SMB]] that has experienced rapid growth and has no in-house security capability. Of course, this type of outsourcing places a huge amount of trust in the MSSP. Maintaining effective oversight of the MSSP requires a good degree of internal security awareness and expertise. There could also be significant challenges in industries exposed to high degrees of regulation in terms of information processing.
-   **Security as a Service** (SECaaS)—can mean lots of different things, but is typically distinguished from an MSSP as being a means of implementing a particular security control, such as virus scanning or SIEM-like functionality, in the cloud. Typically, there would be a connector to the cloud service installed locally. For example, an antivirus agent would scan files locally but be managed and updated from the cloud provider; similarly a log collector would submit events to the cloud service for aggregation and correlation. Examples include Cloudflare ([cloudflare.com/saas](https://www.cloudflare.com/saas)), Mandiant/FireEye ([fireeye.com/mandiant/managed-detection-and-response.html](https://www.fireeye.com/mandiant/managed-detection-and-response.html)), and SonicWall ([sonicwall.com/solutions/service-provider/security-as-a-service](https://www.sonicwall.com/solutions/service-provider/security-as-a-service/)).
# VIRTUALIZATION TECHNOLOGIES AND HYPERVISOR TYPES

Virtualization means that **multiple operating** systems can be installed and run simultaneously on a single computer. A **virtual platform** requires at least **three components**:

-   **Host hardware**—the platform that will host the virtual environment. Optionally, there may be multiple hosts networked together.
-   **Hypervisor/Virtual Machine Monitor (VMM)**—manages the virtual machine environment and facilitates interaction with the computer hardware and network.
-   **Guest operating systems, Virtual Machines (VM), or instances**—operating systems installed under the virtual environment.

One basic distinction that can be made between virtual platforms is between host and bare metal methods of interacting with the host hardware. **In a guest OS (or host-based) system, the hypervisor application (known as a Type II hypervisor) is itself installed onto a host operating system. Examples of host-based hypervisors include VMware Workstation, Oracle Virtual Box, and Parallels Workstation**. The hypervisor software must support the host OS.

![A large box labeled “Operating System” (that contains a Hypervisor box with 6 smaller GUEST OS boxes inside) sits above a box labeled “Hardware”.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7487-1599771810121.png)

Guest OS virtualization ([[Type II hypervisor]])—The hypervisor is an application running within a native OS, and guest OSes are installed within the hypervisor.

A bare metal virtual platform means that the hypervisor ([[Type I hypervisor]]) is installed directly onto the computer and manages access to the host hardware without going through a host OS. Examples include VMware ESXi Server, Microsoft's Hyper-V, and Citrix's XEN Server. The hardware needs only support the base system requirements for the hypervisor plus resources for the type and number of guest OSes that will be installed.

![A large box labeled “Hypervisor” (that contains a Virtual Machine Manager box and 6 smaller GUEST OS boxes) sits above a box labeled “Hardware”.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/5750-1599771810221.png)

Type I "bare metal" hypervisor—The hypervisor is installed directly on the host hardware along with a management application, then VMs are installed within the hypervisor.
# VIRTUAL DESKTOP INFRASTRUCTURE AND THIN CLIENTS

Virtual desktop infrastructure ([[VDI]]) refers to using a VM as a means of provisioning corporate desktops. In a typical VDI, desktop computers are replaced by low-spec, low-power thin client computers. When the [[thin client starts]], it boots a minimal OS, allowing the user to log on to a VM stored on the company server infrastructure. The user makes a connection to the VM using some sort of remote desktop protocol (Microsoft Remote Desktop or Citrix ICA, for instance). The thin client has to find the correct image and use an appropriate authentication mechanism. There may be a 1:1 mapping based on machine name or IP address or the process of finding an image may be handled by a connection broker.

All application processing and data storage in the virtual desktop environment ([[VDE]]) or workspace is performed by the server. The thin client computer must only be powerful enough to **display the screen image, play audio, and transfer mouse, key commands and video, and audio information over the network**. All data is stored on the server, so it is easier to back up and the desktop VMs are easier to support and troubleshoot. They are better "locked" against unsecure user practices because any changes to the VM can easily be overwritten from the template image. With VDI, it is also easier for a company to completely offload their IT infrastructure to a third-party services company.

The main disadvantage is that in the event of a failure in the server and network infrastructure, users have no local processing ability, so downtime events may be more costly in terms of lost productivity.
# APPLICATION VIRTUALIZATION AND CONTAINER VIRTUALIZATION

Application virtualization is a more limited type of [[VDI]]. Rather than run the whole client desktop as a virtual platform, the client either accesses an application hosted on a server or streams the application from the server to the client for local processing. Most application virtualization solutions are based on Citrix XenApp (formerly MetaFrame/Presentation Server), though Microsoft has developed an App-V product with its Windows Server range and VMware has the ThinApp product. These solution types are now often used with HTML5 remote desktop apps, referred to as **"clientless" because users can access them through ordinary web browser software.**

Application cell/container virtualization **dispenses with the idea of a hypervisor and instead enforces resource separation at the operating system level.** The OS defines isolated "cells" for each user instance to run in. Each cell or container is allocated CPU and memory resources, but the processes all run through the **native OS kernel.** These containers may run slightly different OS distributions but cannot run guest OSes of different types (you could not run Windows or Ubuntu in a RedHat Linux container, for instance). Alternatively, the containers might run separate application processes, in which case the variables and libraries required by the application process are added to the container.

One of the best-known container virtualization products is Docker ([docker.com](https://www.docker.com/)). Containerization underpins many cloud services. In particular it supports microservices and serverless architecture. Containerization is also being widely used to implement corporate workspaces on mobile devices.

![Diagram of VM environment and container environment.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/7141-1599771810285.png)

Comparison of VMs versus containers.
# VM ESCAPE PROTECTION

VM escaping refers to [[malware]] running on a guest OS jumping to another guest or to the host. To do this, the malware must identify that it is running in a virtual environment, which is usually simple to do. One means of doing so is through a timing attack. **The classic timing attack** is to send multiple usernames to an authentication server and measure the server response times. An invalid username will usually be rejected very quickly, but a valid one will take longer **(while the authentication server checks the password). This allows the attacker to harvest valid usernames.** Malware can use a timing attack within a guest OS to detect whether it is running in a VM (certain operations may take a distinct amount of time compared to a "real" environment). There are numerous other "signatures" that an attacker could use to detect the presence of virtualized system hardware. The next step in VM escaping is for the attacker to compromise the hypervisor. Security researchers have been focusing on this type of exploit and several vulnerabilities have been found in popular hypervisors.

One serious implication of VM escaping is where virtualization is used for hosted applications. If you have a hosted web server, apart from trusting the hosting provider with your data, you have no idea what other applications might be running in other customers' VMs. For example, consider a scenario where you have an e-commerce web server installed on a virtual server leased from an ISP. If a third-party installs another guest OS with malware that can subvert the virtual server's hypervisor, they might be able to gain access to your server or to data held in the memory of the physical server. Having compromised the hypervisor, they could make a copy of your server image and download it to any location. This would allow the attacker to steal any unencrypted data held on the e-commerce server. Even worse, it could conceivably allow them to steal encrypted data, by obtaining the private encryption keys stored on the server or by sniffing unencrypted data or a data encryption key from the physical server's memory.

It is **imperative to monitor security bulletins for the hypervisor software that you operate and to install patches and updates promptly.** You should also design the VM architecture carefully so that the placement of VMs running different types of applications with different security requirements does not raise unnecessary risks.

Preventing VM escaping is dependent on the virtualization vendor identifying security vulnerabilities in the hypervisor and on these being patched. The impact of VM escaping can be reduced by using effective service design and network placement when deploying VMs.

![Diagram of VM configuration susceptible to VM escaping. Web Services, LAN, and Middleware/back-end Services run through the same vSwitch.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/VM%20escape%20protection%20-%20collapsing%20zones%20to%20virtualized%20device.png)

Collapsing zones to virtualized devices—This configuration is highly vulnerable to a VM escaping attack. (Images © 123RF.com.)

For example, when considering security zones such as a [[DMZ]], VMs providing front-end and middleware/back-end services should be separated to different physical hosts. This reduces the security implications of a VM escaping attack on a host in the DMZ (which will generally be more vulnerable to such attacks).

![Diagram of VM configuration that is less susceptible to VM escaping. There are 2 hosts and 2 firewalls](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/VM%20escape%20proteciton%20-%20Isolating%20VMs%20in%20different%20zones%20on%20separate%20hardware.png)

Isolating VMs in different zones on separate hardware—This should reduce the impact of a VM escaping attack. (Images © 123RF.com.)
# VM SPRAWL AVOIDANCE

As well as securing the hypervisor, you must also treat each VM as you would any other network host. This means using security policies and controls to ensure the confidentiality, integrity, and availability of all data and services relying on host virtualization.

Each VM needs to be installed with its own security software suite to protect against malware and intrusion attempts. Each guest must also have a patch management process. This might mean installing updates locally or replacing the guest instance from an updated VM template image.

Ordinary antivirus software installed on the host will **NOT detect viruses infecting the guest OS.** Scanning the virtual disks of guest OSes from the host will cause serious performance problems.

Although one of the primary benefits of virtualization is the ease of deploying new systems, this type of system sprawl and deployment of undocumented assets can also be the root of security issues. It will often be the case that a system will be brought up for "just a minute" to test something, but languish for months or years, undocumented, unsecured, and unpatched. Each of these undocumented systems could represent an exploitable vulnerability. They increase the potential attack surface of the network. Policies and procedures for tracking, securing, and, when no longer used, destroying virtualized assets should be put in place and carefully enforced.

Virtual machine life cycle management ([[VMLM]]) software can be deployed to enforce VM sprawl avoidance. VMLM solutions provide you with a centralized dashboard for maintaining and monitoring all the virtual environments in your organization. More generally, the management procedures for developing and deploying machine images need to be tightly drafted and monitored. VMs should conform to an application-specific template with the minimum configuration needed to run that application (that is, not running unnecessary services). Images should not be run in any sort of environment where they could be infected by malware or have any sort of malicious code inserted. One of the biggest concerns here is of rogue developers or contractors installing backdoors or "logic bombs" within a machine image. The problem of criminal or disgruntled staff is obviously one that affects any sort of security environment, but concealing code within VM machine images is a bit easier to accomplish and has the potential to be much more destructive.
