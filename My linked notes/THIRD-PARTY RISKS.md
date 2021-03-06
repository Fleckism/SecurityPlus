#vulnerability 
High-profile breaches have led to a greater appreciation of the importance of the supply chain in vulnerability management. A product, or even a service, may have components created and maintained by a long chain of different companies. Each company in the chain depends on its suppliers or vendors performing due diligence on their vendors. A weak link in the chain could cause impacts on service availability and performance, or in the worst cases lead to data breaches.

### Vendor Management

Vendor management is a process for selecting supplier companies and evaluating the risks inherent in relying on a third-party product or service. When it comes to data and cybersecurity, you must understand that risks cannot be wholly transferred to the vendor. If a data storage vendor suffers a data breach, you may be able to claim costs from them, but your company will still be held liable in terms of legal penalties and damage to reputation. If your webstore suffers frequent outages because of failures at a hosting provider, it is your company's reputation that will suffer and your company that will lose orders because customers look elsewhere.

A vendor may supply documentation and certification to prove that it has implemented a security policy robustly. You might be able to see evidence of security capabilities, such as a history of effective vulnerability management and product support. Larger companies will usually ask vendors to complete a detailed audit process to ensure that they meet the required standards.

Within vendor management, _system integration_ refers to the process of using components/services from multiple vendors to implement a business workflow. For example, a workflow allowing customers to make online purchases might involve the storefront product, a web application firewall, [[cloud]] data processing and analytics, plus integration with on-premises accounting and customer relationship management ([[CRM]]) and support ticketing systems. The contracting company may have a list of preferred vendors and ask a third-party systems integrator to build and support the solution. Alternatively, systems integration might be fully outsourced, with the third-party integrator also selecting their preferred vendors for the component parts. The principal risk in both these scenarios is that the contracting company does not have sufficient expertise to oversee the project and places too much trust in the third-party integrator.

When a vendor has become deeply embedded within a workflow, lack of vendor support can have serious impacts, as retooling the workflow to use a different vendor can be a long and complex process. Vendors may become unsupportive for any number of reasons. For example, their company might be growing too quickly and resources are spread too thinly, they may drop support for products that are not profitable, they may have overstated capabilities in terms of security, and so on. The key point for vendor management is to assess these risks when determining whether to outsource all or part of a workflow and to have contingency plans if a vendor does not perform as expected.

### Outsourced Code Development

The problem of effective oversight is particularly pertinent to outsourced code development. Many companies do not have in-house programming expertise, but without such expertise it is hard to ensure that contractors are delivering secure code. A solution is to use one vendor for development and a different vendor for vulnerability and penetration testing.

### Data Storage

There are two main scenarios for risks to data when using third parties. First, you may need to grant vendor access to your data, and second, you may use a vendor to host data or data backups and archives. The following general precautions should be taken:

-   Ensure the same protections for data as though it were stored on-premises, including authorization and access management and encryption.
-   Monitor and audit third-party access to data storage to ensure it is being used only in compliance with data sharing agreements and nondisclosure agreements.
-   Evaluate compliance impacts from storing personal data on a third-party system, such as a cloud provider or backup/archive management service.

### Cloud-Based versus On-Premises Risks

On-premises risks refer to software [[vulnerability|vulnerabilities]], weak configurations, and third-party issues arising from hosts, servers, routers, switches, access points, and firewalls located on a private network installed to private offices or campus buildings. Many companies use cloud services to fully or partly support business workflows. The third-party vendor management, code, and data storage risks discussed previously apply directly to cloud as well as to on-premises. Software and weak configuration risks can also apply, however. They are not the sole responsibility of the cloud service provider (CSP). Clouds operate a shared responsibility model. This means that the cloud service provider is responsible for the security of the cloud, while the cloud consumer is responsible for security in the cloud. The types of software and configuration [[vulnerability|vulnerabilities]] that you must assess and monitor vary according to the nature of the service.

[[vulnerability]]
[[[[vulnerability|vulnerabilities]]]]
