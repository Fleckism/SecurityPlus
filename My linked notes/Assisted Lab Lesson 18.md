# Assisted Lab 30: Acquiring Digital Forensics Evidence

## Scenario

As a digital forensics analyst, you should never work directly on the suspect hard disk drive. In this activity, you will use a built-in Linux command to duplicate the suspect disk. You will also use hashing to ensure data integrity. Next, on a Windows computer, you will use the file carving tools provided with the open source forensics suite Autopsy ([sleuthkit.org](https://www.sleuthkit.org/)) to investigate a disk image. You will open a pre-built case file and probe the information extracted to identify a malware installation event.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objective:

-   4.1 Given a scenario, use the appropriate tool to assess organizational security
    
-   4.5 Explain the key aspects of digital forensics





## Use Linux to create a disk image

A virtual hard disk drive containing possible evidence has already been attached to the PT1-Kali Linux virtual machine. You need to create a disk image, and then prove whether there have been unexpected changes to the file during the investigation. Linux contains a built-in tool named dd that can easily create copies of disks for forensics professionals. You will use dd to create an image. Next, you will use MD5 hashes to discover whether a file has changed unexpectedly.

1.  Log in to the [PT1-Kali](https://labclient.labondemand.com/Instructions/0fc54871-aff4-472c-ade8-8d99a465bacd?rc=10#) VM with root and Paw0rd
    
    > The suspect 1 GB disk is already attached to the PT1-Kali VM.
    
2.  From the top bar, select **Terminal Emulator**.
    
3.  Run lsblk and use the output to record the name of the 1G disk:
    
4.  Run the following commands to display disk information. Make sure you have input the name of the drive (such as sdb) in the text box:
    
    ```bash-notab-nocopy
    cat /proc/partitions
    ```
    
    ```bash-notab-nocopy
    df -h /dev/sdb
    ```
    
5.  Use the following command to create a copy of the suspect disk. Make sure you have input the name of the drive (such as sdb) in the text box:
    
    ```bash-notab-nocopy
    dd if=/dev/sdb of=/root/suspect.img
    ```
    
    > The image creation process will take several seconds. If the /dev/sdb drive were larger, the process would take much longer.
    
6.  Confirm that that /root/suspect.img disk image file exists.
    
    Correct
    
    Use the dd command to create the suspect.img file.![The dd command](https://labondemand.blob.core.windows.net/content/lab84061/Screen%20Shot%202020-11-08%20at%202.30.08%20PM.png)
    
    If the file does not exist, re-run the dd command. Ensure that you use the correct file name.
    
7.  Run the md5sum command to generate a checksum and redirect it into a file named suspect.img-hash.
    
    ```bash-notab-nocopy
    md5sum suspect.img > suspect.img-hash
    ```
    
    ```bash-notab-nocopy
    cat suspect.img-hash
    ```
    
8.  Confirm that the /root/suspect.img-hash file exists.
    
    Correct
    
    Create the suspect.img-hash file.![Screen Shot 2020-11-08 at 2.32.11 PM.png](https://labondemand.blob.core.windows.net/content/lab84061/Screen%20Shot%202020-11-08%20at%202.32.11%20PM.png) If the file does not exist, re-run the md5sum command. Ensure that you use the correct file name.
    
9.  To mark the image with today's date, run the following command:
    
    ```bash-notab-nocopy
    echo "Today is $(date)" > suspect.img
    ```
    
    > This command might not seem like a good idea, but run it anyway!
    
10.  Use the md5sum command from the previous steps to hash the suspect.img file again, but this time, _append_ the hash results to the existing suspect.img-hash file.
    
    > You must enter the following command carefully, or you will destroy the hash generated for the original suspect.img file. Note the use of **>>** instead of **>**. The double greater-than signs append data to the file without over-writing existing data.
    
    ```bash-notab-nocopy
    md5sum suspect.img >> suspect.img-hash
    ```
    
11.  Use the cat command from earlier steps to display the contents of the suspect.img-hash file.
    
12.  Are the hash values the same?
    
    Yes
    
    No
    
    Correct
    
    Display the contents of suspect.img-hash![Two different hashes](https://labondemand.blob.core.windows.net/content/lab84061/Screen%20Shot%202020-11-08%20at%202.33.31%20PM.png)
    
    The suspect.img-hash file should contain two lines, each with a hash result. If the two results are the same, than the original suspect.img-hash file has not changed. If the two results are different, than there was a change to the file during the time between when the two hashes were generated. In this case, the suspect.img file is evidence, so a change would be bad.
    
13.  Run the following command to display the contents of the suspect.img file:
    
    ```bash-notab-nocopy
    cat suspect.img
    ```
    
    > It appears that you accidentally overwrote the entire file, hence the hashes are different. This is an extreme example of the risks of working directly with evidence. Because you still have the original content, located at /dev/sdb, you could use dd to create another image file. Had you been working directly with the disk content, the evidence would have been destroyed.
    




## Browse forensics case file

Open the "Forensics – Marketing" case in Autopsy, and browse the disk image that has been seized as evidence.

1.  Select the [MS1](https://labclient.labondemand.com/Instructions/0fc54871-aff4-472c-ade8-8d99a465bacd?rc=10#) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/0fc54871-aff4-472c-ade8-8d99a465bacd?rc=10#), and then log in with the username 515support\Administrator and password Paw0rd.
    
2.  Close Server Manager.
    
3.  Use the desktop shortcut to start **Autopsy**. The program takes 1-2 minutes to open.
    
4.  From the Welcome dialog box, select the **Open Case** icon.
    
5.  In the Open dialog box, browse to the **Forensics - Marketing** folder on the Desktop, select **Forensics - Marketing.aut** and select **Open**.
    
6.  Autopsy identifies many critical portions of the storage media for you. You may briefly examine the following components:
    
    -   Expand the **Data Sources** node then select the **marketing.vhd** disk in the main pane. In the lower pane, select the **Hex** tab.
        
        This is the Master Boot Record, residing in the first 512-byte sector on the disk.
        
    -   Expand the **marketing.vhd**, and then select **vol2**. This is the system volume and is normally hidden from view.
        
        Observe that the initial string of hex characters identifies the partition type as NTFS.
        
7.  Select **vol3**. This is the boot volume, hosting the OS files and applications plus user data. Expand the folders to **Users > Viral > Downloads**. Observe what is shown.
    
    You can see the symbolic links for the current directory and parent directory, plus the default view settings configuration file, but there are no download files present.
    
8.  Autopsy also displays drive contents. You may briefly examine the following results:
    
    -   Under the **Results** node, select the **EXIF Metadata** node. Criminal investigations might need to locate images of illegal activity. This search has only located the default Windows backgrounds, though.
        
    -   Under the **Encryption Detected** and the **Encryption Suspected** nodes. The presence of encrypted files in suspect locations could be a red flag.
        
    -   Under the **Installed Programs** node. Sort by the **Date/Time** column to display what has been installed recently.
        
    -   Under the **Operating System Information** and **Operating System User Account** nodes. Select **Viral's** user account for more information on a per-user basis.
        
9.  What are the last four digits of Viral's Security Identifier (SID)?
    
    Viral's SID
    
10.  Continue examining the results from automated analysis of the drive:
    
    -   Under the **Web History** node. You could display information about web browsing habits in this node.
        
    -   Under **E-Mail Messages**. You might find some valuable information here.
        
    -   Under **Interesting Items**. There are numerous references to an "atypical" compression file format (not native to Windows, that is) within the **carved files** area (that is, typically files that have been deleted).


## Browse activity timeline

Viewing the timeline of file activity might also help to reconstruct the pattern of events.

1.  Select the **Timeline** button from the menu at the top of the Autopsy user interface.
    
    Once the database has been repopulated (this will take a few minutes), a high-level chart of file activity will be displayed in a new window.
    
2.  Maximize the window.
    
3.  From the Display times in panel, select **GMT/UTC**.
    
4.  Right-click the long bar for **2017** and select **Zoom into Time Range**. Repeat to zoom into **April** and then the **29th**. Finally, repeat **Zoom into Time Range** again for the **14** hour (2pm).
    
    > There is a **History - Back** button in the upper left of the interface. If you select a setting in error, use that to return to an earlier time setting.
    
5.  From the View Mode panel, select the **List** button. Scroll down to locate the section containing the email message at **14:48:00** (it is near the bottom of the list).
    
6.  You can read the content of the email from Viral and examine the other operating system activities at this time.
    
7.  Which of the following answers best describes what security incident occurred, based on the information from Viral at 14:48:00?
    

    Viral was tricked into installing malware from an untrusted web site.
    

    > The lab interface makes it difficult to adjust column widths in this application. Use the **Full Screen** feature of the lab environment to maximize window space. Also, you can show the full text in a column by pointing to a field to show its tooltip.
    
8.  Select the email message from Viral at 14:48:00 that reads _I've installed the update but it didn't seem to do anything?_. Right-click the message, choose **Extract File(s)**, and then save it to the **Desktop** with the default file name **Sent-1**.
    
9.  Confirm that the Sent-1 file exists on the Administrators desktop.
    
10.  Close the **Timeline** window.
    
11.  Close **Autopsy**.

## Comprehensive questions

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following best describes why you must create an image of the hard disk drive instead of working with it directly?
    
    To avoid an unintended change to the evidence.

2. Which of the following answers best describes the purpose of hashes, such as the md5sum hash command you used in the lab?

	Hashing proves there have been no changes to data.

3.   

Which of the following answers best describes why the Timeline view in Autopsy is useful?

It displays a chain of events, allowing the digital forensics expert to see a broader picture of what happened on the system.