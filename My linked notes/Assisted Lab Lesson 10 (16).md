# Assisted Lab 16: Configuring a Firewall

## Scenario

You will configure a basic firewall rule on a Linux server to block port 80 (HTTP) traffic. Next you will reconfigure the server to accept HTTP connections, and then you will configure iptables logging for all traffic. Finally, you will display log file traffic.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   3.3 Given a scenario, implement secure network designs.

## Configure a Linux iptables firewall for HTTP connections

You are tasked with securing a new web server. You need to verify that connectivity exists, and then insert a rule into the iptables firewall that blocks inbound port 80 traffic.

1.  Sign in to the as the password.
    
2.  Open a terminal using the menu at the top of the screen.
    
3.  Run the following command to start the Apache web service:
    
    ```bash-notab-nocopy
    systemctl start apache2
    ```
    
    > The service is now started, but it is not persistent. If the server reboots, the service will not automatically start. You would enter systemctl enable apache2 to make the service persistent.
    
4.  Run the following command to verify that Apache is running:
    
    ```bash-notab-nocopy
    systemctl status apache2
    ```
    
5.  Confirm that the apache2 service is running on the virtual machine.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
    Apache![Apache status](https://labondemand.blob.core.windows.net/content/lab84048/Screen%20Shot%202020-11-07%20at%204.18.01%20PM.png)
    
6.  Switch to theas the HTTP client for this task.
    
7.  Sign on with the default centos account, usd as the password.
    
8.  From the **Applications** menu, select **Firefox**.
    
9.  In the Firefox address bar, enter http://10.1.0.192 to connect to the **515 support** web site.
    
    The connection attempt succeeds. iptables currently accepts all inbound connection attempts.
    
    The default Apache web page.![515 Support web page](https://labondemand.blob.core.windows.net/content/lab84048/Screen%20Shot%202020-11-07%20at%204.21.05%20PM.png)
    
10.  Close Firefox.
    
11.  Switch to the and then configure the iptables service to DROP inbound HTTP connections by port number 80 by using the following command:
    
    ```bash-notab-nocopy
    iptables -I INPUT 1 -p tcp --destination-port 80 -j DROP
    ```
    
    > The -I option inserts the rule to drop port 80 traffic at the line number specified after "INPUT." In this example, that is line number one. This rule is being processed before all other rules.
    
12.  Display the iptables rules and observe that the HTTP service is specified by port number 80.
    
    ```bash-notab-nocopy
    iptables -S
    ```
    
13.  Run the following command to redirect the output of the iptables -S command to a text file for scoring:
    
    ```bash-notab-nocopy
    iptables -S > ~/iptables.txt    
    ```
    
14.  Confirm that the iptables.txt file exists.
    
    The iptables.txt file.![iptables configurations](https://labondemand.blob.core.windows.net/content/lab84048/Screen%20Shot%202020-11-07%20at%204.23.44%20PM.png)
    
15.  Switch to the [LX1](https://labclient.labondemand.com/Instructions/af89867d-2832-4ad2-b600-dd5568ea8030?rc=10#) virtual machine, launch Firefox, and then attempt to connect to the Kali http://10.1.0.192 test site again.
    
    Firefox spends several minutes attempting to connect. Eventually, the connection attempt fails.
    
16.  Why did the connection attempt succeed the first time, and then fail the second time?
    
    You added a rule to drop outbound packets for port 80.
    
    You added a rule to drop inbound packets for port 80.
    
    You disabled the Apache2 web service after the first attempt.
    
    You enabled the firewall after the first attempt.

# Display iptables log files

You will now reverse the firewall configuration, once again permitting inbound traffic over port 80. You will then configure iptables to log all inbound connections.

1.  Select the [PT1-Kali](https://labclient.labondemand.com/Instructions/af89867d-2832-4ad2-b600-dd5568ea8030?rc=10#) virtual machine.
    
2.  Insert a new iptables rule at line 1 so that connections for port 80 are accepted:
    
    ```bash-notab-nocopy
    iptables -I INPUT 1 -p tcp --destination-port 80 -j ACCEPT
    ```
    
    > The easiest way is to use the up arrow key to recall recent commands, and then backspace over DROP and type in ACCEPT.
    
3.  Enable iptables logging.
    
    ```bash-notab-nocopy
    iptables -I INPUT 1 -j LOG
    ```
    
    > Observe that you are now placing the LOG rule at the top of the list. All traffic will be logged before being processed by the rules that follow after the LOG rule.
    
4.  Display the iptables rules and observe that the destination port 80 ACCEPT and LOG rules are listed above the DROP rule. Firewall rules are processed in order.
    
    ```bash-notab-nocopy
    iptables -S
    ```
    
    iptables Accept![iptables accept and log rules](https://labondemand.blob.core.windows.net/content/lab84048/Screen%20Shot%202020-11-07%20at%204.26.33%20PM.png)
    
5.  Switch back to the [LX1](https://labclient.labondemand.com/Instructions/af89867d-2832-4ad2-b600-dd5568ea8030?rc=10#) VM, and attempt or refresh the http://10.1.0.192 web connection again with Firefox.
    
6.  Switch to the [PT1-Kali](https://labclient.labondemand.com/Instructions/af89867d-2832-4ad2-b600-dd5568ea8030?rc=10#) VM.
    
7.  Display destination port 80 traffic in the **/var/log/kern.log** log file by using the **tail** command.
    
    ```bash-notab-nocopy
    tail /var/log/kern.log | grep "80"
    ```

## Comprehensive questions

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  In what order are iptables firewall rules processed?
    
    In the order listed in iptables.

2. Which of the following actions must you perform to log traffic processed by iptables?

	Add a LOG command in one or more rules.

# Exam Results
1. Why did the connection attempt succeed the first time, and then fail the second time?
	1. You added a rule to drop inbound packets for port 80.
2. In what order are iptables firewall rules processed?
	1. In the order listed in iptables
2. Which of the following actions must you perform to log traffic processed by iptables?

 Add a LOG command in one or more rules.



