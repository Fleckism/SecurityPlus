---
tags: [zFleck, secondTag]
---
# LESSON INTRODUCTION

If a company operates with one or more vulnerable business processes, it could result in disclosure, modification, loss, destruction, or interruption of critical data or it could lead to loss of service to customers. Quite apart from immediate financial losses arising from such security incidents, either outcome will reduce a company's reputation. If a bank lost its trading floor link to its partners, even for an hour, since the organization's primary function (trading) would be impossible, huge losses may result. Consequently, when planning a network or other IT system, you must perform risk management to assess threats and vulnerabilities.

Analyzing risk plays a major role in ensuring a secure environment for an organization. By assessing and identifying specific risks that can cause damage to network components, hardware, and personnel, you can mitigate possible threats and establish the right corrective measures to avoid losses and liabilities.

Lesson Objectives

In this lesson, you will:

-   Explain risk management processes and concepts.
-   Explain business impact analysis concepts.
# EXAM OBJECTIVES COVERED

5.4 Summarize risk management processes and concepts

Most organizations have formal risk management policies and processes, both to meet compliance requirements and to make the business secure. These policies and processes are usually driven by frameworks and come with some standard terminology to describe factors and procedures within the overall process. It is vital that you be able to summarize the key concepts of risk management, so that you can participate in these important assessments.
# RISK MANAGEMENT PROCESSES

<mark style="background: #FF5582A6;">Risk management is a process for identifying, assessing, and mitigating vulnerabilities and threats to the essential functions that a business must perform to serve its customers.</mark> You can think of this process as being performed over five phases:

1.  **Identify mission-essential functions**—mitigating risk can involve a large amount of expenditure so it is important to focus efforts. Effective risk management must focus on mission essential functions that could cause the whole business to fail if they are not performed. Part of this process involves identifying critical systems and assets that support these functions.
2.  **Identify vulnerabilities**—for each [[function or workflow]] (starting with the most critical), analyze systems and assets to discover and list any vulnerabilities or weaknesses to which they may be susceptible.
3.  **Identify threats**—for each function or workflow, identify the threat sources and actors that may take advantage of or exploit or accidentally trigger vulnerabilities.
4.  **Analyze business impacts**—the likelihood of a vulnerability being activated as a security incident by a threat and the impact of that incident on critical systems are the factors used to assess risk. There are quantitative and qualitative methods of analyzing impacts and likelihood.
5.  **Identify risk response**—for each risk, identify possible countermeasures and assess the cost of deploying additional security controls. Most risks require some sort of mitigation, but other types of response might be more appropriate for certain types and level of risks.

For each business process and each threat, you must assess the degree of risk that exists. Calculating risk is complex, but the two main variables are likelihood and impact:

-   [[Likelihood of occurrence]] is the probability of the threat being realized.
-  [[ Impact is the severity]] of the risk if realized as a security incident. This may be determined by factors such as the value of the asset or the cost of disruption if the asset is compromised.

Risk management is complex and treated very differently in companies and institutions of different sizes, and with different regulatory and compliance requirements. Most companies will institute enterprise risk management ([[ERM]]) policies and procedures, based on frameworks such as NIST's Risk Management Framework ([[RMF]]) or [[ISO 31K]]. These legislative and framework compliance requirements are often formalized as a Risk and Control Self-Assessment ([[RCSA]]). An organization may also contract an external party to lead the process, in which case it is referred to as a Risk and Control Assessment ([[RCA]]).

A RCSA is an internal process undertaken by stakeholders to identify risks and the effectiveness with which controls mitigate those risks. RCSAs are often performed through questionnaires and workshops with department managers. The outcome of an RCSA is a report. Up-to-date RCSA reports are critical to the external audit process.
# RISK TYPES

General types of risks can be identified as arising from specific threat and vulnerability scenarios.

### External

External threat actors are one highly visible source of risk. You must also consider wider threats than those of cyberattack. Natural disasters, such as the COVID-19 pandemic, illustrate the need to have IT systems and workflows that are resilient to widespread dislocation. The most critical type of impact is one that could lead to loss of life or critical injury. The most obvious risks to life and safety come from natural disasters, person-made disasters, and accidents, such as fire.

### Internal

Internal risks come from assets and workflows that are owned and managed by your organization. When reviewing internal risks, it is important to remember that these can be classed as malicious or accidental (non-malicious). Internal threats can include contractors who were granted temporary access.

### Multiparty

Multiparty risk is where an adverse event impacts multiple organizations. Multiparty risk usually arises from supplier relationships. If a critical event disrupts a supplier or customer, then your own organization will suffer. These are often described as ripple impacts. For example, if one of your top five customers goes out of business because of a data breach, your company will lose substantial revenue. Organizations in these supply chain relationships have an interest in promoting cybersecurity awareness and capability throughout the chain.

As an illustration of how risk assessments can change in view of multiparty relationship, consider a company that makes wireless adapters, originally for use with laptops. In the original usage, the security of the firmware upgrade process is important, but it has no impact on life or safety. The company, however, earns a new contract to supply the adapters to provide connectivity for in-vehicle electronics systems. Unknown to the company, a weakness in the design of the in-vehicle system allows an adversary to use compromised wireless adapter firmware to affect the car's control systems. The integrity of the upgrade process now has an impact on safety, and is much higher risk.

### Intellectual Property (IP) Theft

Intellectual property (IP) is data of commercial value that is owned by the organization. This can mean copyrighted material for retail (software, written work, video, and music) and product designs and patents. If IP data is exfiltrated it will lose much of its commercial value. Losses can be very difficult to recover in territories where there are not strong legal protections.

### Software Compliance/Licensing

Breaking the terms of the end user licensing agreement (EULA) that imposes conditions on installation of the software can expose the computer owner to substantial fines. License issues are most likely to arise from [[shadow IT]], where users install software without change control approval. Network inventory management suites can report software installations on each host and correlate those with the number of license seats purchased. Licensing models can also be complex, especially where virtualization and the cloud are concerned. It is important to train the administrative staff on the specific license terms for each product.

### Legacy Systems

Legacy systems are a source of risk because they **no longer receive security updates** and because the expertise to maintain and troubleshoot them is a scarce resource.
# QUANTITATIVE RISK ASSESSMENT

There are quantitative and qualitative methods of performing risk analysis to evaluate likelihood and impact.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/2627-1599771812041.jpg)

Quantitative risk assessment aims to assign concrete values to each risk factor. (Image © 123RF.com.)

**Quantitative risk assessment aims to assign concrete values to each risk factor.**

-   **Single Loss Expectancy** ([[SLE]])—the amount that would be lost in a single occurrence of the risk factor. This is determined by multiplying the value of the asset by an Exposure Factor ([[EF]]). EF is the percentage of the asset value that would be lost.
-   **Annualized Loss Expectancy** ([[ALE]])—the amount that would be lost over the course of a year. This is determined by multiplying the SLE by the Annualized Rate of Occurrence ([[ARO]]).

It is important to realize that the value of an asset does not refer solely to its material value. The two principal additional considerations are direct costs associated with the asset being **compromised (downtime)** and consequent costs to intangible assets, such as the **company's reputation**. For example, a server may have a material cost of a few hundred dollars. If the server were stolen, the costs incurred from not being able to do business until it can be recovered or replaced could run to thousands of dollars. In addition, that period of interruption where orders cannot be taken or go unfulfilled leads customers to look at alternative suppliers, resulting in perhaps more thousands of lost sales and goodwill.

The problem with quantitative risk assessment is that the process of determining and assigning these values is complex and time consuming. The accuracy of the values assigned is also **difficult to determine without historical data** (often, it has to be based on subjective guesswork). However, over time and with experience, this approach can yield a detailed and sophisticated description of assets and risks and provide a sound basis for justifying and prioritizing security expenditure.
# QUALITATIVE RISK ASSESSMENT

Qualitative risk assessment avoids the complexity of the quantitative approach and is focused on identifying significant risk factors. The qualitative approach seeks out people's opinions of which risk factors are significant. Assets and risks may be placed in simple categories. For example, assets could be categorized as Irreplaceable, High Value, Medium Value, and Low Value; risks could be categorized as one-off or recurring and as Critical, High, Medium, and Low probability.

Another simple approach is the heat map or "Traffic Light" impact matrix. For each risk, a simple Red, Yellow, or Green indicator can be put into each column to represent the severity of the risk, its likelihood, cost of controls, and so on. This approach is simplistic but does give an immediate impression of where efforts should be concentrated to improve security.

![A table shows 3 risk factors (Legacy Windows Clients, Untrained Staff, No Antivirus Software) and Impact, ARO, Cost of Controls, Overall Risk columns.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/4123-1599771812142.png)

Traffic light impact grid.

FIPS 199 ([nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.199.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/NIST.FIPS.199.pdf)) discusses how to apply security categorizations ([[SC]]) to information systems based on the impact that a breach of **confidentiality, integrity, or availability** would have on the organization as a whole. Potential impacts can be classified as:

-   **Low**—minor damage or loss to an asset or loss of performance (though essential functions remain operational).
-   **Moderate**—significant damage or loss to assets or performance.
-   **High**—major damage or loss or the inability to perform one or more essential functions.
# RISK MANAGEMENT STRATEGIES

The result of a quantitative or qualitative analysis is a measure of inherent risk. [[Inherent risk]] is the level of risk before any type of mitigation has been attempted.

In theory, [[security controls]] or countermeasures could be introduced to address every risk factor. The difficulty is that security controls can be expensive, so you must balance the cost of the control with the cost associated with the risk. **It is not possible to eliminate risk; rather the aim is to mitigate risk factors to the point where the organization is exposed only to a level of risk that it can afford**. The overall status of risk management is referred to as **risk posture**. [[Risk posture]] shows which risk response options can be identified and prioritized. For example, you might identify the following priorities:

-   Regulatory requirements to deploy security controls and make demonstrable efforts to reduce risk. Examples of legislation and regulation that mandate risk controls include SOX, HIPAA, Gramm-Leach-Bliley, the Homeland Security Act, PCI DSS regulations, and various personal data protection measures.
-   High value asset, regardless of the likelihood of the threat(s).
-   Threats with high likelihood (that is, high ARO).
-   Procedures, equipment, or software that increase the likelihood of threats (for example, legacy applications, lack of user training, old software versions, unpatched software, running unnecessary services, not having auditing procedures in place, and so on). 

In the quantitative approach, the Return on Security Investment ([[ROSI]]) can be determined by calculating a new [[ALE]], based on the reduction in loss that will be created by the security controls introduced. The formula for calculating ROSI is: [(ALE - ALEm) - Cost of Solution] / Cost of Solution, where ALE is the ALE before controls and ALEm is after controls. 

[[Risk mitigation (or remediation)]] is the overall process of reducing exposure to or the effects of risk factors. If you deploy a countermeasure that reduces exposure to a threat or vulnerability that is risk deterrence (or reduction). Risk reduction refers to controls that can either make a risk incident less likely or less costly (or perhaps both). For example, if fire is a threat, a policy strictly controlling the use of flammable materials on site reduces likelihood while a system of alarms and sprinklers reduces impact by (hopefully) containing any incident to a small area. Another example is offsite data backup, which provides a remediation option in the event of servers being destroyed by fire.
# RISK AVOIDANCE AND RISK TRANSFERENCE

Avoidance means that you stop doing the activity that is risk-bearing. For example, a company may develop an in-house application for managing inventory and then try to sell it. If while selling it, the application is discovered to have numerous security vulnerabilities that generate complaints and threats of legal action, the company may make the decision that the cost of maintaining the security of the software is not worth the revenue and withdraw it from sale. Obviously this would generate considerable bad feeling among existing customers. Avoidance is not often a credible option.

Transference (or sharing) means assigning risk to a third party, such as an insurance company or a contract with a supplier that defines liabilities. For example, a company could stop in-house maintenance of an e-commerce site and contract the services to a third party, who would be liable for any fraud or data theft. Specific cybersecurity insurance or cyberliability coverage protects against fines and liabilities arising from data breaches and DoS attacks.

Note that in this sort of case it is relatively simple to transfer the obvious risks, but risks to the company's reputation remain. If a customer's credit card details are stolen because they used your unsecure e-commerce application, the customer won't care if you or a third party were nominally responsible for security. It is also unlikely that legal liabilities could be completely transferred in this way. For example, insurance terms are likely to require that best practice risk controls have been implemented.
# RISK ACCEPTANCE AND RISK APPETITE

It is not possible to reduce risks to zero, so part of risk posture is concerned with managing what risks remain.

### Risk Acceptance

[[Risk acceptance]] (or tolerance) means that no countermeasures are put in place either because the level of risk does not justify the cost or because there will be unavoidable delay before the countermeasures are deployed. In this case, you should continue to monitor the risk (as opposed to ignoring it). 

### Residual Risk and Risk Appetite

Where inherent risk is the risk before mitigation,[[ residual risk]] is the likelihood and impact after specific mitigation, transference, or acceptance measures have been applied. Risk appetite is a strategic assessment of what level of residual risk is tolerable. [[Risk appetite is broad in scope]]. Where risk acceptance has the scope of a single system, risk appetite has a project- or institution-wide scope. Risk appetite is constrained by regulation and compliance.

### Control Risk

[[Control risk]] is a measure of how much less effective a security control has become over time. For example, antivirus became quite capable of detecting malware on the basis of signatures, but then less effective as threat actors started to **obfuscate code**. Control risk can also refer a security control that was never effective in mitigating inherent risk. This illustrates the point that risk management is an ongoing process, requiring continual reassessment and re-prioritization.
# RISK AWARENESS

To ensure that the business stakeholders understand each risk scenario, you should **articulate it such that the cause and effect can clearly be understood by the owner of the asset**. A DoS risk should be put into plain language that describes how the risk would occur and, as a result, what access is being denied to whom, and the effect to the business. For example: "As a result of malicious or hacking activity against the public website, the site may become overloaded, preventing clients from accessing their client order accounts. This will result in a loss of sales for so many hours and a potential loss of revenue of so many dollars."

A [[risk register]] is a document showing the results of risk assessments in a comprehensible format. The register may resemble the heat map risk matrix shown earlier with columns for impact and likelihood ratings, date of identification, description, countermeasures, owner/route for escalation, and status. Risk registers are also commonly depicted as scatterplot graphs, where impact and likelihood are each an axis, and the plot point is associated with a legend that includes more information about the nature of the plotted risk. A risk register should be shared between stakeholders (executives, department managers, and senior technicians) so that they understand the risks associated with the workflows that they manage.
