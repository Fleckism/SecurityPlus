Assisted Lab:
- First thing I did was disable windows defender
- Then I installed a malicous program.
	- Searched for malicious program.
		- netcat(32) showed up in background process list Common trojan (taskmanager)
	- Ran what I think was a ini.vbs Visual basic script to open port 4450?  There is a snippet of it
		- Used the Service Port firewall rule with the trojan
	- I also created myself a user account so I could log back in later.
		- Then made myself an admin
	- I then deleted the script
	- Stopped the process netcat
	- And I found the Inbound rule for port 4450 and blocked it.
	- To block access to the malware
		- I Stopped the ncat process
		- Deleted the ini.vbs file
		- Closed port 4450
	-
	
	Why is it useful to know the common port numbers?

 Easier to identify protocols that are not standard to your network.