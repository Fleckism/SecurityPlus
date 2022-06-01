# Assisted Lab 17: Configuring an Intrusion Detection System

## Scenario

In this activity, you will use an IDS sensor to monitor packets on a LAN router's interface with the outside internetwork. You will use the Security Onion Linux distribution ([securityonion.net](https://securityonion.net/)) and its bundled Snort IDS as the sensor. Security Onion is installed to the SIEM1 VM.

As you cannot access the relevant configuration settings in this lab environment, the IDS sensor has already been configured for you. The eth1 interface on RT1-LOCAL is configured as a source port for mirroring. The eth1 interface on SIEM1, also connected to the vISP switch, is the destination port. This interface has no IP address. It is used as a monitoring sensor only. SIEM1's eth0 interface is connected to the vLOCAL switch. This interface does have an IP address. It can be used to manage the appliance from the local network.

![Lab topology showing SIEM1 monitoring RT1-LOCAL](https://labondemand.blob.core.windows.net/content/lab84049/IDS%20Lab.png) Diagram showing lab topology.

The PT1-Kali VM is located on a remote network, representing the internet. Packets directed at the VMs on the vLOCAL "LAN" are routed via RT3-ISP, RT2-ISP, and RT1-LOCAL.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   3.3 Given a scenario, implement secure network designs.


## Browse IDS tool

Sign on to the SIEM1 VM and run the SGUIL tool, which is used to monitor incidents in real-time.

> Remember that the type text feature will not work with the Linux VMs. You will need to enter the marked text manually.

1.  Select the [SIEM1]
    
2.  Open the **Sguil** icon on the desktop and log on with the credentials siem for the username and Pa$$w0rd for the password.
    
    Security Onion![SGUIL sign in](https://labondemand.blob.core.windows.net/content/lab84049/Screen%20Shot%202020-11-07%20at%204.33.17%20PM.png)
    
3.  Check the **siem1-eth1** interface check box (make sure that _only_ siem1-eth1 is checked) then select **Start SGUIL**.
    
    Observe that a number of alerts are already present in the console. These show samples of malicious traffic. We will not be analyzing these as part of this lab, but if you have time at the end, you may want to review them to identify the types of traffic that can be detected using signatures.
    
4.  Select the [PT1-Kali](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) VM and log on with the credentials username root and password Pa$$w0rd
    
5.  Open a terminal and run ping 10.1.0.1 -c10
    
6.  Switch to the [SIEM1](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) VM.
    
7.  The probes will be shown as a new "GPL ICMP_INFO" record in the console. Note the CNT field. This shows that the rule was matched 10 times. Select the record.
    
8.  In the panel in the bottom-right, check the **Show Packet Data** and **Show Rule** check boxes to show the packet contents and the rule that produced a signature match for this event. Record the rule SID (it appears in blue).
    
    SID:  
    
    > To resize the panes, you need to click-and-drag on the little boxes, rather than the frame borders.
    

## Configure IDS rules

When rules generate events that you decide you do not need to inspect manually, you have several choices:

-   You can configure SGUIL to autocategorize the event.
    
-   You can tune the ruleset to remove the rule.
    
-   You can apply a threshold to only alert if the rule is matched a certain number of times.
    
-   You can add conditions to trigger (or not trigger) the rule.
    

To continue this activity, you will disable the rule that alerts on ICMP matches. To do this, you will modify one of the configuration files for the Pulled Pork script, which updates Snort rulesets.

1.  In the [SIEM1](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) VM, minimize SGUIL, and then right-click the desktop and select **Open Terminal**.
    
2.  Run sudo vim /etc/nsm/pulledpork/disablesid.conf. Enter 
    
    > You may use the nano text editor if you are more comfortable with it than vim.
    
    Vim quick reference  
      
      
    
      
      
    
    -     
        
    
3.  Type Go to move the cursor to the end of the file in insert mode.
    
4.  Type 1:2100366, using the value for the SID you recorded earlier.
    
5.  Press **ESC** to exit Vim's Insert Mode.
    
6.  Type **:wq** to save and close the file.
    
    Configuration file![SGUIL configuration file](https://labondemand.blob.core.windows.net/content/lab84049/Screen%20Shot%202020-11-07%20at%204.42.31%20PM.png)
    
7.  Run sudo rule-update to apply the change.
    
    Wait for the update to complete before moving to the next step.
    
8.  Switch to [PT1-Kali](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) and run ping 10.1.0.1 -c4
    
9.  On [SIEM1](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#), check the SGUIL console. Examine the CNT field—no alerts should be generated and this should remain at 10.
    
10.  Which of the following best describes the purpose of editing the /etc/nsm/pulledpork/disablesid.conf configuration file?
    
    To disable a rule that identifies ping packets based on the specified SID.
    
    





## Test IDS

Run some intrusive pen tests from PT1-Kali and identify the events they generate in the IDS.

1.  Select the [PT1-Kali](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) VM.
    
2.  In the terminal window, run nmap 10.1.0.2 to begin a basic Nmap scan.
    
3.  Switch to [SIEM1](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) and view the alerts in **Sguil**.
    
    It may take several moments for the scan to appear in the IDS. The scan triggers several alerts, both for probing sensitive ports (such as the ports for various SQL application servers).
    
4.  On the [PT1-Kali](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) VM, run the following command in the terminal:
    
    ```bash-notab-nocopy
    hping3 -c 1000 -d 120 -S -w 64 -p 80 --flood --rand-source 10.1.0.2
    ```
    
5.  What kind of attack is hping3 perpetrating in this activity?
    

    Denial of Service (DoS).
    
    
6.  Let the attack attack proceed for a few seconds, then press **CTRL+C** to stop it.
    
7.  Switch back to [SIEM1](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) and observe the rules that the attack has triggered.
    
8.  Which of the following best describes the Event Messages displayed by SGUIL?

    
    ET DROP Spamhaus DROP messages.
    

    

## Attack the MS1 Windows Server

In this activity, you will experience the DDoS attack on the MS1 virtual machine.

1.  Switch to [MS1](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) and send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) to sign on to the system.
    
2.  Sign on using
    
3.  Right-click the **Taskbar**, and select **Task Manager**.
    
4.  Select the **Performance** tab, and then select **Ethernet** to display network traffic (there should be little to no traffic at the moment).
    
    Leave Task Manager open.
    
5.  Select **Start**, right-click **Windows PowerShell**, and select **Run as Administrator**. Select **Yes** when prompted.
    
6.  Run the `netstat` command. You should see very few connections.
    
7.  Organize the windows so that Task Manager is on top, with the network performance information displayed.
    
8.  Switch to the [PT1-Kali](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) VM, and re-run the hping3 DDoS attack.
    
    > Use the **UP ARROW** key at a Linux command prompt to cycle through recent commands rather than retyping them.
    
9.  While the attack is running, switch to [MS1](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#), and view the network traffic in Task Manager.
    
    The network throughput should remain at approximately 100%. However, it is possible that the attack is effective enough to stop Task Manager from displaying updated information. The MS1 system may appear locked or extremely sluggish.
    
    > You are overwhelming the Windows server with the DDoS attack. The server may be extremely slow or completely non-responsive.
    
10.  Select the PowerShell window, and attempt to re-run the `netstat` command - it may not execute during the attack.
    
11.  Switch back to the [PT1-Kali](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) VM, and select **Ctrl+C** to halt the attack.
    
12.  Switch to the [MS1](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#) VM.
    
    Task Manager and netstat should function as expected.
    
13.  Switch to [SIEM1](https://labclient.labondemand.com/Instructions/d3854466-572b-4fd6-b13d-bfbe445b7825?rc=10#), and then observe that the attack times correspond with the time you ran the above commands.
    
14.  Why are the Src IP addresses all different in the SGUI if the attack originates from PT1-Kali at 192.168.2.192?
    
    
    The hping3 utility randomizes and spoofs the source IP address, based on the --random-source parameter.
    
     

1. Why was the Nmap scan identified as a threat by SGUIL?
- Nmap followed a pattern for a well-known scan.
2. Why might it be useful to set a rule that ignores ICMP (ping) network traffic?
- ICMP and ping are essential network troubleshooting utilities.