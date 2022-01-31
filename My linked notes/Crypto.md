[[payload]]

[[Ransomware]]


# [[Indicators]]
### Resource Consumption

Abnormal resource consumption can be detected using a performance monitor, Task Manager, or the top Linux utility. Indicators such as excessive and continuous CPU usage, memory leaks, disk read/write activity, and disk space usage can be signs of malware, but can also be caused by many other performance and system stability issues. Also, it is only really poorly written malware or [[malware]] that performs intensive operations (botnet DDoS, cryptojacking, and cryptoransomware, for instance) that displays this behavior. Resource consumption could be a reason to investigate a system rather than definitive proof of infection.

The **crypto-malware** class of ransomware attempts to encrypt data files on any fixed, removable, and network drives. If the attack is successful, the user will be unable to access the files without obtaining the private encryption key, which is held by the attacker. If successful, this sort of attack is extremely difficult to mitigate, unless the user has up to date backups of the encrypted files. One example of this is Cryptolocker, a Trojan that searches for files to encrypt and then prompts the victim to pay a sum of money before a certain countdown time, after which the malware destroys the key that allows the decryption