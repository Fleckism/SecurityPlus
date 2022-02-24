---
tags: [Attack]
---

A rootkit is characterized by its ability to **hide itself** by changing core system files and programming interfaces and to escalate privileges.

A rootkit may also contain tools for **cleaning system logs**, further concealing its presence

Consequently, what a rootkit can do depends largely on adversary capability and level of effort. When dealing with a rootkit, you should be aware that there is the possibility that it can compromise system files and programming interfaces, so that local shell processes, such as Explorer, taskmgr, or tasklist on Windows or ps or top on Linux, plus port listening tools, such as netstat, no longer reveals its presence (at least, if run from the infected machine). 


Critical processes run with a higher level of privilege (SYSTEM)
Alternatively, the malware may be able to use an exploit to escalate privileges after installation. Malware running with this level of privilege is referred to as a [[rootkit]]


