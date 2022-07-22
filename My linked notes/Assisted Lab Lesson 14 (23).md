# Assisted Lab 23: Identifying Application Attack Indicators

## Scenario

You are concerned about discovering application layer attacks against your Windows servers. You have decided to simulate some attacks that might consume processor or memory resources, making the server sluggish or unresponsive. First, you will use CPU Stress to simulate a heavy processor load on the server. Second, you will use testlimit to simulate a similar heavy memory load. In both cases, you will monitor the output by using CPU Explorer, Task Manager, and Performance Monitor.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   1.3 Given a scenario, analyze potential indicators associated with application attacks.

## Display Process Explorer and Performance Monitor

To prepare for application attack detection, you will use Process Explorer and Performance Monitor to display current resource utilization information. You will create a custom Data Collector Set in Performance Monitor to observe a simulated deviation from the baseline.

1.  On the [DC1](https://labclient.labondemand.com/Instructions/6ced9b8e-274e-47ee-b057-503d229aee29?rc=10#) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/6ced9b8e-274e-47ee-b057-503d229aee29?rc=10#), and then sign on as 515support\Administrator using Paw0rd as the password.
    
2.  In Server Manager, select **Tools > Performance Monitor**.
    
3.  Expand the **Data Collector Sets > User Defined** node. Right-click the **User Defined** node and then select **New > Data Collector Set**.
    
4.  Use CPU baseline as the Name, select the radio button for **Create manually (advanced)**, and then select **Next**.
    

    
5.  With **Create data logs** selected, check the box for **Performance Counter**, and then select **Next**.
    
6.  On the Which performance counters would you like to log? page, select **Add**.
    
7.  On the Available counters page, expand the **Processor** node (it is already highlighted for you). Select the following three counters, and **Add** them to the **Added Counters** column:
    
    -   % Processor Time (this counter is a good general indicator of the processor's overall activity level)
    -   % User Time (this counter provides data on time spent by the processor managing user applications)
    -   Interrupts/sec (this counter measures interrupts that the processor must handle immediately) (All the way at the bottom of the node)
    
    Performance Monitor CPU counters.![PerfMon CPU counters](https://labondemand.blob.core.windows.net/content/lab84055/Screen%20Shot%202020-11-08%20at%209.01.47%20AM.png)
    
8.  Select **OK** to complete the **Available counters** dialog box.
    
9.  Select **Next**.
    
10.  Which of the following is the path displayed for the Root directory, where the Performance Monitor Data Collector Set logs will be stored?
    
%systemdrivePerfLogsAdminCPU baseline
    


	The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    
11.  Select **Finish** to complete the Data Collector Set configuration.
    
    You will start the Data Collector Set in a later step.
    
12.  Minimize Performance Monitor. You will use it in later tasks.
    
13.  From the desktop, open the **LABFILES** folder, browse to the **Sysinternals** folder, and then launch **procexp**.
    
14.  Observe some of the key information reported by Process Explorer, including:
    -  CPU Usage in the lower left corner - a percentage of processor utilization
    -   The tree format of the processes and their relationships to each other
    -   Reorganize data by selecting the column headers. The CPU column can be organized to display processes that are consuming the most resources, for example.(No idea?)
15.  Leave Process Explorer open. You will use it in later tasks.
    
16.  Right-click the **Taskbar**, and then select **Task Manager**.
    
17.  Select the **Performance** tab.
    
18.  Select each of the following three categories to observe the relevant performance information:
    
    -   CPU
    -   Memory
    -   Ethernet
19.  Leave **CPU** selected.
    
20.  Leave Task Manager open. You will use it in later tasks.



## Create stress on the CPU

You will use CPU Stress to place a false load on the VM's processors. You'll use Performance Monitor, Task Manager, and Process Explorer to monitor the workload.

1.  Select [[Performance Monitor]]. Under **Data Collector Sets > User Defined**, right-click the **CPU baseline** set, and then select **Start**.
    
    You will leave the Data Collector Set running through the next several tasks. It gathers information as you accomplish activity steps.
    
2.  From the C:\LABFILES\Sysinternals folder, open **cpustres64**.
    
    You will see a dashboard with four pre-created threads available. The menu allows you to start and stop threads, as well as to create new threads. Right-click threads to manage their priority level. You will create and execute threads in a later step.
    
    > [CPUStres](https://docs.microsoft.com/en-us/sysinternals/downloads/cpustres) is a performance management utility that applies a workload to the processor by creating one or more threads. Each thread can be given a priority level (low, medium, high, maximum). This tool is part of the Windows Sysinternals suite.
    
3.  Resize and reposition the Task Manager, Process Explorer, and CPU Stress windows so that you can observe them simultaneously.
    
    The goal is to view the effect of starting CPU Stress in Task Manager and Process Explorer.
    
    Display all three tools![Task Manager, CPU Stress, Process Explorer](https://labondemand.blob.core.windows.net/content/lab84055/Screen%20Shot%202020-11-08%20at%209.06.45%20AM.png)
    
4.  In the CPU Stress console, select the **Create Threads** button. A thread is generated in the window.
    
    The new thread is currently inactive. You can select additional values, such as workload, affinity, and priority.
    
    There should now be five threads created. Four were created by default, and you created the fifth.
    
5.  Select all five threads, right-click them, and then select **Activity Level** > **Medium (50%)**.
    
    Setting the Activity level.![Activity levels](https://labondemand.blob.core.windows.net/content/lab84055/screens/xbvey4ne.jpg)
    
6.  In CPU Stress, select the five threads, right-click the selection, and then select **Activate**.
    
    > The system will become very slow!
    
7.  Switch to Task Manager. CPU Utilization should be nearly 100%.
    
8.  Switch to Process Explorer. In the lower left corner, CPU Usage should also be nearly 100%.
    
    CPU Utilization![CPU utilization](https://labondemand.blob.core.windows.net/content/lab84055/Screen%20Shot%202020-11-08%20at%209.10.30%20AM.png)
    
9.  In Process Explorer, open the **CPUSTRES64.exe** process to display detailed data. Select **Cancel** when you have browsed each tab.

## End the CPU Stress threads

You have now completed the stress test, so you will end the threads.

1.  In the CPU Stress console, right-click each thread, and then select **Deactivate**.
    
    You can select several or all of the threads by holding down the **SHIFT** or **CTRL** keys.
    
2.  Display Process Explorer and Task Manager. CPU utlization should be well below 100%.
    
3.  Close Process Explorer and CPU Stress.
    
4.  Switch to Performance Monitor, right-click the **CPU baseline** data collector set, and select **Stop**.
    
5.  Right-click **CPU baseline** and select **Latest Report**. Use this log to answer the following question:
    
6.  Which of the following answers best describes the results of the CPU baseline data?

    
    Processor utilization is normal, then high, then normal again.
    

    
7.  Confirm that the CPU baseline report directory exists.
    
    Correct
    
    CPU utilization informationPerformance Monitor should record normal processor utilization until the CPU Stress utility is run. Processor utilization should be very high until you end the CPU Stress task. At that point, it should return to normal. If the report does not exist, you will need to repeat the entire Create stress on the CPU activity.
    

## Create stress on the Memory

You will use the testlimit utility to create a false workload that stresses the system's memory, simulating an application attack that attempts to consume RAM. You'll use Peformance Monitor and Task Manager to observe the results.

1.  Select Performance Monitor, and then create a new Data Collector Set named Memory baseline with the following counters from the **Memory** category:
    
    -   % Committed Bytes In Use (this counter compares committed memory bytes to the byte commit level, indicating paging utilization that may be due to memory leaks or too many open applications)
    -   Available MBytes (this counter reports the quantity of memory available for new applications to startup)
    -   Pages/sec (this counter reports the rate at which memory pages are written to or from the pagefile on the hard disk drive)
    
    How to create a new Data Collector Set
    
    ![Memory counters](https://labondemand.blob.core.windows.net/content/lab84055/Screen%20Shot%202020-11-08%20at%209.16.27%20AM.png)
    

> Don’t forget to use exactly the same names as specified in the instructions.

3.  Right-click the **Memory baseline** data collector set, and then select **Start**.
    
    You will leave the Data Collector Set running through the next several tasks. It gathers information as you accomplish activity steps.
    
4.  From the desktop, select the Windows **Start** menu, right-click **Windows PowerShell**, and then select **Run as Administrator**. Select **Yes** to confirm the UAC prompt.
    
5.  In the Windows PowerShell console, enter cd C:\LABFILES\Sysinternals
    
6.  In the Task Manager console, select the **Memory** node.
    
7.  Resize the Windows PowerShell console and the Task Manager console so that you can observe them simultaneously.
    
    The goal is to view the effect of starting the testlimit utility in Task Manager.
    
8.  Run the following command in Windows PowerShell to simulate the consumption of memory, selecting **Agree** when prompted to accept the license agreement:
    
    ```
    .\testlimit -d 1024 -c 1
    ```
    
9.  Which of the following answers best describes the purpose of the .\ characters in this command?
    
    The .\ characters inform Windows PowerShell to look in the current folder for the executable.
    
 
10.  Switch to Task Manager, and then view the **Memory** category.
    
    Memory utilization should be very high.
    
11.  In Task Manager, select the **Processes** tab.
    
12.  Scroll down to the **Background Processes** section, right-click **Test Windows Limits**, and then select **End Task**.
    
13.  Select Performance Monitor, and then _stop_ the **Memory baseline** Data Collector Set.
    
14.  Right-click **Memory baseline** and then select **Latest Report**. Use this log to answer the following question:
    
15.  Which of the following answers best describes the results of the Memory baseline data?
    
    Memory utilization is normal, then high, and then normal again through the activity.
    
    Memory utilization is unchanged through the activity.
    
    Memory utilization is high through the activity.
    
    Memory utilization is high, then normal, and then high again through the activity.
    
16.  Confirm that the Memory baseline report directory exists.
    
    Memory utilization information
    

What is the purpose behind baselining a server's performance?
 - Baselining documents the server's current performance so that the results can be compared against future performance data.
Which of the following answers best describes the benefits of stress-testing a server's performance? (Choose three)
-  To confirm the server's resources are sufficient for the workload.
- To understand what potential application attacks look like.
-  To check for application failure.