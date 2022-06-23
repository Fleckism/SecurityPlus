**access control list**
- A set of **data** associated with a file, directory or other network resource that defines the **permissions** that **users, groups, processes or devices** have for accessing it. See access control and wildcard mask.
- Not all ACLs are the same.
- aka Apply permissions
-  if access to the data is fully mediated through a trusted OS.
- Each record is called an access control entry ([[ACE]])
- File system must support permissions.   (NTFS, ext3/ext4, or ZFS)
	- Linux has Read(r), Write(w), Execute(x)
- Mandatory access control ([[MAC]]) is based on the idea of security clearance levels


<mark style="background: #FFB8EBA6;">Discretionary access control</mark> ([[DAC]])
	- The owner (the original creator) is granted full control over the resource
	- Most flexible model
	- Weakest, makes centralized administration of security policies the most difficult to enforce.

<mark style="background: #FFB8EBA6;">Role-based access control</mark> ([[RBAC]]) adds an extra degree of centralized control to the DAC model. Under RBAC, a set of organizational roles are defined, and subjects allocated to those roles. Under this system, the right to modify roles is reserved to a system owner. Therefore, the system is non-discretionary, as each subject account has no right to modify the [[ACL]] of a resource, even though they may be able to change the resource in other ways. **Users are said to gain rights implicitly (through being assigned to a role) rather than explicitly (being assigned the right directly)**.


A packet filtering firewall is configured by specifying a **group of rules**, called an access control list ([[ACL]]). Each rule defines a specific type of data packet and the **appropriate action** to take when a packet matches the rule. An action can be either to deny (block or drop the packet, and optionally log an event) or to accept (let the packet pass through the firewall). A packet filtering firewall can **inspect the headers of IP packets**. This means that rules can be based on the information found in those headers:

-   IP filtering—accepting or denying traffic on the basis of its source and/or destination IP address.
-   Protocol ID/type (TCP, UDP, ICMP, routing protocols, and so on).
-   Port filtering/security—accepting or denying a packet on the basis of source and destination port numbers (TCP or UDP application type).

There may be additional functionality in some products, such as the ability to block some types of [[ICMP]] (ping) traffic but not others, or the ability to filter by hardware [[MAC address]]. Another distinction that can be made is whether the firewall can control only inbound traffic or both inbound and outbound traffic. This is also often referred to as **ingress and egress traffic or filtering.** Controlling outbound traffic is useful because it can block applications that have not been authorized to run on the network and defeat malware, such as [[backdoor]]s. Ingress and egress traffic is filtered using separate ACLs. 
+++++++++++++++++++++++++++++ Old+++++++++++
- Group of of rules for
- Used by [[firewall]]
	- Configured on the principle of least access