# 1
A large sales organization uses a cloud solution to store large amounts of data. One afternoon, the data becomes inaccessible due to an outage at a data center. Which replication service level is currently in use?

2.  Local

Solution

A local replication solution replicates data within a single data center in the region that created the storage account. If the data center experiences an outage, so do all of the replicated copies.

A regional replication solution (also called zone-redundant storage) replicates data across multiple data centers within one or two regions.

A Geo-redundant storage (GRS) solution replicates data to a secondary region that is distant from the primary region. Cross-country or around the globe are other terms for this type of solution.

A zone is a portion of a region that performs replication.
# 2
A developer considers using an API for service integration and automation. If choosing Representational State Transfer (REST) as the API, which features can the developer expect? **(Select all that apply.)**

1.  The ability to submit a request as an HTTP operation/verb
2.  It is a looser architectural framework


Solution

Requests sent as Simple Object Access Protocol (SOAP) must be in a correctly formatted XML document. However, with Representational State Transfer (REST) requests, they can be submitted as an HTTP operation/verb (GET or POST for example).

Representational State Transfer (REST) is a looser architectural framework, also referred to as RESTful APIs. SOAP is a tightly specified protocol.

Simple Object Access Protocol (SOAP) uses XML format messaging and has a number of extensions in the form of Web Services (WS) standards.

Simple Object Access Protocol (SOAP) also has built-in error handling and supports common features, such as authentication, transport security, and asynchronous messaging.
# 3
An engineer uses an abstract model that represents network functionality. Using infrastructure as code to deploy and manage a network, how does the engineer make control decisions?

2.  By prioritizing and securing traffic

Solution

When using an abstract model, the engineer can divide the network functions into three "planes." The control plane makes decisions about how to prioritize and secure traffic, as well as where to switch it.

A software-defined networking (SDN) application can manage the aspects of all "planes" in the abstract model. SDN can manage compatible physical appliances, but also virtual switches, routers, and firewalls.

The management plane monitors traffic conditions and the overall network status.

The data plane handles the actual switching and routing of traffic and the imposition of security access controls.
# 4
A company has many employees that work from home. The employees obtain data and post data to a shared file they access through a link on the Internet. Consider the types of virtualization and conclude which the company is most likely utilizing.

3.  Cloud computing


Solution

Cloud computing is a service that provides on-demand resources such as server instances, data storage, databases, or applications. The service is typically provided over the Internet.

Resource pooling is described as the hardware making up the cloud provider's data center is not dedicated or reserved to a particular customer account.

Rapid elasticity refers to the cloud being able to scale quickly to meet peak demand.

Measured service is described as a cloud service in which the customer pays for the memory, disk, and the network bandwidth resources they are actually consuming rather than paying a monthly fee for a particular service level. This is known as a pay-per-use service. This service falls under the cloud computing type of virtualization.
# 5
An organization plans a move of systems to the cloud. In order to identify and assign areas of risk, which solution does the organization establish to contractually specify cloud service provider responsibilities?

1.  Service level agreement

Solution

It is imperative to identify precisely which risks are transferring to the cloud, which risks the service provider is undertaking, and which risks remain with the organization. A service level agreement (SLA) outlines those risks and responsibilities.

A trust relationship simply defines the relationship with a cloud service provider. The more important the service is to a business, the more risk the business invests in that trust relationship.

A responsibility matrix is a good way to identify what risks exist, and who is responsible for them. The matrix can be part of an SLA.

High availability is an approach to keeping systems functionality at a constant.
# 6
A company conducts file sharing via a hosted private cloud deployment model. Which scenario accurately depicts this type of file sharing?

1.  A cloud hosted by a third party for the exclusive use of the organization.

Solution

A third party hosts a hosted private cloud deployment model for the exclusive use of the organization. This service is more secure and provides guaranteed performance but is more costly than other options.

A third party hosts a public cloud deployment model and shares it with other subscribers. This is the most known form of cloud computing and is the least secure.

A private cloud is completely private to and owned by the company that uses it. This is geared toward companies and services that require strict control, such as banking or government entities.

Several organizations use a community cloud that shares the costs of either a hosted private or fully private cloud. This is usually done in order to pool resources for a common concern, such as standardization and security policies.
# 7
A security team suspects the unauthorized use of an application programming interface (API) to a private web-based service. Which metrics do the team analyze and compare to a baseline for response times and usage rates, while investigating suspected DDoS attacks? **(Select all that apply.)**

1.  Number of requests
3.  Latency


Solution

The number of requests is a basic load metric that counts the number of requests per second or requests per minute. Depending on the service type, admin can set a baseline for typical usage.

Latency is the time in milliseconds (ms) taken for the service to respond to an API call. This can be measured for specific services or as an aggregate value across all services.

Error rates measure the number of errors as a percentage of total calls, usually classifying error types under category headings.

Admin can manage unauthorized and suspicious endpoint connections to the API in the same sort of way as remote access.
# 8
When provisioning application services in network architecture, an engineer uses a microservices approach as a solution. Which principle best fits the engineer's implementation?

4.  Each program or tool should do one thing well

Solution

Microservice-based development uses a philosophy that each program or tool should do one thing well. Each microservice should be capable of developing, testing, and deploying independently, and said to be highly decoupled, rather than just loosely decoupled.

Service-oriented architecture (SOA) conceives of atomic services closely mapped to business workflows. Each service takes defined inputs and produces defined outputs.

Services integration refers to ways of making these decoupled service or microservice components work together to perform a workflow.

Orchestration performs a sequence of automated tasks. Orchestrated steps run numerous automated scripts or API service calls.
# 9
A startup designs a new online service and uses a serverless approach for some business functions. With this approach, how does the startup accomplish these functions? (Select all that apply.)

2.  Containers
4.  Orchestration

Solution

When an operation needs processing, by using a container, the cloud spins up the container to run the code, performs the processing, and then destroys the container.

A virtual machine is a full-fledged operating system that runs in a virtual environment and considered a server, not serverless. Serverless refers to creating and using containers when needed.

A single service would provide a specific output. Many services require working together in a serverless environment.

Serverless architecture depends heavily on the concept of event-driven orchestration with many services involved to facilitate operations.
# 10
A security professional is looking to harden systems at an industrial facility. In particular, the security specialist needs to secure an HVAC system that is part of an IoT network. Which areas does the specialist look to secure from data exfiltration exploits? **(Select all that apply.)**

3.  Fog node
4.  Edge gateway

Solution

A security specialist can incorporate fog nodes as a data processing layer positioned close to edge gateways, assisting the prioritization of critical data transmission. Fog nodes are high-value targets for both denial of service and data exfiltration attacks.

Edge gateways perform some pre-processing of data to and from edge devices to enable prioritization. They also perform the wired or wireless connectivity to transfer data to and from the storage and processing networks. Edge gateways are high-value targets to exploit.

Edge devices collect and depend upon data for their operation. In this case it would help to harden the HVAC devices or route to HVAC devices.

The cloud or data center provides the main storage and processing resources, plus distribution and aggregation of data. The IOT network is typically segmented from the main data center.
# 11
A company has recently started using a Platform as a Service (PaaS). Compare cloud service types to determine what is being deployed.

4.  The company has leased an instance that runs Microsoft Azure SQL Database.

Solution

Platform as a service (PaaS) provides resources somewhere between SaaS and IaaS. A typical PaaS solution would provide servers and storage network infrastructure (as per IaaS) but also provide a multi-tier web application/database platform on top.

IaaS is a means of provisioning resources such as servers, load balancers, and Storage Area Network (SAN) components quickly.

SaaS is a different model of provisioning software applications. Rather than purchasing software licenses for a given number of seats, a business can access software hosted on a supplier's servers on a pay-as-you-go or lease arrangement.

Managed Security Services Provider (MSSP) is a means of fully outsourcing responsibility for information assurance to a third party.
# 12
What actions are typically recommended when securing virtualized and cloud-based resources? **(Select all that apply.)**

3.  Ensure software and hosts are patched regularly.
4.  Configure devices to support isolated communications.

Solution

Virtual Machine (VM) software, hosts and guest Operating Systems (OS) should be patched on regular intervals. Regular patching provides fixes for identified vulnerabilities.

Virtual networking devices should be configured to support isolated communications wherever necessary. This will allow communications with the necessary clients.

Virtual machines should log all critical events versus all events. Logging all events will be counterproductive as critical events could be missed due to too much data.

The principle of least privilege for access to virtual machines should be utilized for security purposes. Most privilege would not maximize security for virtualized or cloud-based resources.
# 13
A systems administrator configures several subnets within a virtual private cloud (VPC). The VPC has an Internet gateway attached to it, however, the subnets remain private. What does the administrator do to make the subnets accessible by the public?

3.  Configure a default route for each subnet.


Solution

The administrator must configure the Internet gateway as the default route for each public subnet. If the admin does not configure a default route, the subnet remains private, even if the VPC has an Internet gateway attached to it.

Connections to other services such as storage or services running in other VPCs are possible with VPC endpoint configurations.

While VPCs remain private from each other, the admin can create a CSP-managed feature or a VPN, to connect the VPCs and VPNs.

Multiple VPCs are not required. A VPC is an isolated virtual cloud that can contain many subnets.
# 14
Analyze and select the accurate statements about threats associated with virtualization. **(Select all that apply.)**

2.  VM escaping occurs as a result of malware jumping from one guest OS to another.
3.  A timing attack occurs by sending multiple usernames to an authentication server to measure the server response times.


Solution

Virtual Machine (VM) escaping refers to malware running on a guest Operating System (OS) jumping to another guest or to the host.

A timing attack occurs by sending multiple usernames to an authentication server and measuring the server's response times.

Hypervisors are a common target of attacks and become more complex when the network infrastructure, such as switches and routers, is also virtualized. When the network infrastructure is implemented in software, it may not be subject to inspection and troubleshooting by system administrators.

VMs providing front-end, middleware, and back-end services should be separated to different physical hosts. This reduces the security implications of a VM escaping attack on a host in the Demilitarized Zone (DMZ).
# 15
A systems administrator deploys a cloud access security broker (CASB) solution for user access to cloud services. Evaluate the options and determine which solution may be configured at the network edge and without modifying a user's system.

4.  Reverse proxy

Solution

A reverse proxy (positioned at the cloud network edge) directs traffic to cloud services if the contents of that traffic comply with policy. This does not require configuration of users' devices.

Single sign-on authentication and enforcing access controls and authorizations from the enterprise network to the cloud provider is a feature of a CASB.

Rather than placing a CASB appliance or host inline with cloud consumers and the cloud services, an API-based CASB brokers connections between the cloud service and the cloud consumer.

A forward proxy is a security appliance or host, positioned at the client network edge, that forwards user traffic to the cloud network if the contents of that traffic comply with policy. This requires configuration of users' devices.
