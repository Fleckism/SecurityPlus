# Assisted Lab 25: Implementing PowerShell Security

## Scenario

Windows PowerShell is a very powerful administrative tool. As a security professional, you will need to control what PowerShell scripts run on your Windows servers. There are individual PowerShell cmdlets, and there are settings configured through Group Policy. Group Policy allows Active Directory administrators to centralize configuration control. You will create a Group Policy Object (GPO) to manage PowerShell logging. You will then create a script and explore the available execution policies. You will digitally sign your script to provide an additional layer of security. Next, you'll edit the GPO to centrally manage the execution policy. To match the 515support company security policy, you will disable PS remoting. Finally, you will review the PowerShell log files that you enabled at the start of the activity.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objective:

-   3.2 Given a scenario, implement host or application security features.

## Configure a GPO for PS Logging

Configure a Group Policy Object that enables logging and link it to the corp.515support.com domain.

1.  Send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/501e81d9-f9ac-4d70-8fe0-77c9a6147f16?rc=10#), and then sign on to the [DC1](https://labclient.labondemand.com/Instructions/501e81d9-f9ac-4d70-8fe0-77c9a6147f16?rc=10#) VM as 515support\Administrator using Paw0rd as the password.
    
2.  From Server Manager, select **Tools > Group Policy Management**.
    ![[Pasted image 20220622184851.png]] Rename Group Policy Management Icon
3.  Right-click the **corp.515support.com** domain object and select **Create a GPO in this domain, and Link it here**
    
4.  Name the new GPO PowerShell Security [[GPO]], and then select **OK**.
    
5.  Right-click the PowerShell Security GPO, and then select **Edit**.
    
6.  In the GPO editor, select **Computer Configuration > Policies > Administrative Templates > Windows Components > Windows PowerShell**.
    
7.  Right-click the **Turn on PowerShell Script Block Logging** setting, and then select **Edit**.
    
8.  Select the **Enabled** radio button, and then select **OK**.
    
9.  Close the Group Policy Management Editor.
    
10.  Select the **Group Policy Objects** folder. Right-click the **PowerShell Security GPO**, and select **Save Report**.
    
11.  Select the **Desktop** folder, and then select the **Save** button.
    
12.  Confirm that the PowerShell Security GPO .htm file exists.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
13.  Minimize the Group Policy Management console.
    
14.  Select the **Start** menu, right-click **Windows PowerShell**, and then select **Run as Administrator**. Select **Yes** to confirm the UAC prompt.
    
15.  Run the following cmdlet _twice_:
    
    ```
    gpupdate /force
    ```
    
    > Use the **UP ARROW** key to repeat the most recent command or PowerShell cmdlet. For example, type gpupdate /force the first time you need it, and then select the the **UP ARROW** key to repeat it.
    
16.  Minimize the PowerShell console.

## Manage PowerShell execution control

You will configure PowerShell execution control on the DC1 virtual machine. You would not be likely to create and test scripts on a domain controller. We are just using this VM to simplify the lab environment requirements.

PowerShell execution policy reference table:

![[Pasted image 20220622185600.png]]

---

1.  In Server Manager, select **Tools > Windows PowerShell ISE**.
    
2.  In PowerShell ISE, add the following script to the **Untitled.ps1** script pane (in the text editor, not at the command prompt):
    
    > Remember to use the Type Text feature to auto-type the content into the virtual machine.
    
    PowerShell (Has it's own language)
   powershell files 
    `# display the following text Write-Host “Hello, $env:UserName!”  # display the date $today = get-date Write-Host "Today is $today"  # display version information for PowerShell (Get-Host).Version`
    
    The script.![Screen Shot 2020-11-08 at 10.25.48 AM.png](https://labondemand.blob.core.windows.net/content/lab84057/Screen%20Shot%202020-11-08%20at%2010.25.48%20AM.png)
    
3.  From the PowerShell ISE menu bar, select the green triangle **Run Script (F5)** button to execute the script.
    
    Note that the script runs and displays the script contents and the formatted script data.
    
    Executing the script![Screen Shot 2020-11-08 at 10.26.42 AM.png](https://labondemand.blob.core.windows.net/content/lab84057/Screen%20Shot%202020-11-08%20at%2010.26.42%20AM.png)
    
4.  From the PowerShell ISE menu bar, save the script to the **Desktop** as a file named PSversion.ps1.
    
5.  Close the PowerShell ISE.
    
6.  Confirm that the PSversion.ps1 script exists.
    
    The PSversion.ps1 script.
    
     Don’t forget to use exactly the same names as specified in the instructions.
    
7.  Maximize the PowerShell console, or from Server Manager, select **Tools > Windows PowerShell**.
    
8.  Change to the **Desktop** folder by entering cd C:\Users\Administrator\Desktop`.
    
9.  To take advantage of PowerShell's tab completion feature, call the script by typing `PSver`, and then pressing the **TAB** key, and then press **ENTER**.
    
10.  What PowerShell version is installed on the DC1 virtual machine?
    
    3.6
    
    5.1
    
    5.2
    
    6.3
    
    PSversion.
    
    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    
11.  Run the following PowerShell cmdlet to display the current execution control policy on the system:
    
    PowerShell
    
    `Get-Executionpolicy`
    
12.  What is the current PowerShell Execution Policy?
    
    Unrestricted
    
    AllSigned
    
    Restricted
    
    RemoteSigned
    
13.  Review the following snippet of the organization's written security policy as it pertains to scripts and security:
    
    -   _Scripts created in-house must be digitally signed. Such scripts may be signed with a self-signed certificate. Scripts downloaded from the Internet must be digitally signed by a trusted source. The PowerShell execution policy will be set as **AllSigned**_**.**
14.  Configure the PowerShell Execution Policy to match the requirements:
    
    PowerShell
    
    `Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope LocalMachine`
    
15.  When prompted, enter **y** to respond "yes" to the confirmation message.
    
    > This type of configuration usually enforced through Group Policy. You will configure the Group Policy settings below.
    
16.  Run the `.\PSversion.ps1` test script again.
    
    > Use the **UP ARROW** key to cycle through recent commands. For example, you could easily rerun the Get-ExecutionPolicy cmdlet by cycling upward through the history.
    
    The script should fail this time, because it is not digitally signed. PowerShell errors are displayed in red.
    
17.  Run the `Get-ExecutionPolicy` cmdlet again to confirm the policy is set to **AllSigned**.
    
18.  Run the `Get-AuthenticodeSignature -FilePath C:\Users\Administrator\Desktop\PSversion.ps1` cmdlet
    
19.  What is the status of the PSversion.ps1 script?
    NotSigned
    
    Signed by a trusted root CA
    
    Digitally signed
    
    Signed by an untrusted root CA
    
    Valid
    
    The Status of the PSversion.ps1 script.![Setting the execution policy](https://labondemand.blob.core.windows.net/content/lab84057/Screen%20Shot%202020-11-08%20at%2010.32.51%20AM.png)
    


## Create a code signing certificate

According to the company policy, you need to digitally signed your PowerShell scripts. You will generate a code signing certificate and link it to the test script.

1.  In the PowerShell window, run the following cmdlet to generate a new self-signed certificate.
    
    PowerShell
    
    `New-SelfSignedCertificate -DnsName administrator@corp.515support.com -CertStoreLocation Cert:\CurrentUser\My\ -Type Codesigning`
    
    > The certificate may take up to one minute to be generated.
    
2.  Open the Certificates [[MMC]] by running the `certmgr.msc` command.
    
3.  Expand the **Personal** node, and then select the **Certificates** node.
    
    Two certificates are displayed, including the new Code Signing certificate.
    
4.  Double-click the new Code Signing certificate, select the **Details** tab, and then select **Copy to File**.
    
5.  Complete the Certificate Export Wizard by making the following selections:
    
    -   Select **No, do not export the private key**
    -   Select **DER encode binary X.509 (.CER)** format
    -   Browse to the Desktop and save the file with the name code-cert
6.  A message indicates the export was successful. Select **OK**.
    
7.  Close the certificate properties dialog box.
    
8.  In the certmgr console, right-click **Trusted Root Certification Authorities**, and then select **All Tasks > Import**.
    
9.  In the Certificate Import Wizard, specify the **code-cert.cer** file from the Desktop, accept all other defaults, and then select **Finish**.
    
10.  Select **Yes** and then **OK** when prompted to install the certificate.
    
    > The import process may take approximately 30 seconds.

**A window will pop up when complete**
11.  In the certmgr console, right-click **Trusted Publishers**, and then repeat the process above to import the **code-cert.cer** certificate.
    
12.  Confirm the prompts to install the certificate.
    
13.  Close the cermgr console.
    
14.  From the PowerShell console, run the following cmdlet to digitally sign the **PSversion.ps1** script:
    
    PowerShell
    
    `Set-AuthenticodeSignature -FilePath C:\Users\Administrator\Desktop\PSversion.ps1 -Certificate (Get-ChildItem -Path Cert:\CurrentUser\My\ -CodeSigningCert)`
    
15.  Run the `.\PSversion.ps1` test script again.
    
    You should be successful because the script is now digitally signed.
    
16.  Run the `Get-AuthenticodeSignature -FilePath C:\Users\Administrator\Desktop\PSversion.ps1` cmdlet again to confirm the status of the script.
    
17.  What is the status of the PSversion.ps1 script at this point?
    
    Digitally signed
    
    NotSigned
    
    Signed by an untrusted root CA
    
    Valid
    
    Signed by a trusted root CA
    
    The Status of the PSversion.ps1 script.
    
18.  Close the PowerShell window.

## Configure a GPO that enforces the execution policy

Edit an existing Group Policy Object (GPO) to set the execution policy as AllSigned, and link it to the corp.515support.com domain.

1.  In the Group Policy Management console, expand the **corp.515support.com** domain object.
    
2.  Right-click the **PowerShell Security GPO** GPO, and then select **Edit**.
    
3.  In the GPO editor, select **Computer Configuration > Policies > Administrative Templates > Windows Components > Windows PowerShell**.
    
4.  Right-click **Turn on script execution**, and then select **Edit**.
    
5.  Select the **Enabled** radio button.
    
6.  In the Execution Policy drop-down menu, select **Allow only signed scripts**, and then select **OK**.
    
7.  Close the Group Policy Management Editor.
    
8.  Close the Group Policy Management console.
    
9.  Which of the following is an advantage of using Group Policy to configure the execution policy, rather than a standard PowerShell cmdlet?
    
	    Group Policy provides centralized configuration of many machines, and is easily edited.
	    
## Disable Remote PowerShell

The 515 Support security policy states that PowerShell cmdlets must only be run locally on Domain Controllers. You must disable PowerShell Remoting on DC1 to prevent users from establishing remote PowerShell sessions. Such sessions would permit the remote execute of cmdlets such as Restart-Computer or Get-Service on the DC.

1.  Review the following snippet of the organization's written security policy as it pertains to scripts and security:
    
    -   _The Remote PowerShell functionality will be disabled on all Domain Controllers._
2.  If necessary, launch **Windows PowerShell** from the **Tools** menu in Server Manager.
    
3.  Configure the PowerShell cmdlet that disables PowerShell Remoting:
    
    PowerShell
    
    `Disable-Psremoting -Force`
    
4.  Verify the status of PowerShell Remoting:
    
    PowerShell
    
    `Get-Pssessionconfiguration | Format-Table -Property Name, Permission`
    
5.  Which of the following levels of access is displayed for the NT AUTHORITY\NETWORK identity?
    
    AccessDenied
    
    Full Control
    
    No Access
    
    AccessAllowed
    
    PowerShell Remoting.![Disable PowerShell Remoting](https://labondemand.blob.core.windows.net/content/lab84057/Screen%20Shot%202020-11-08%20at%2010.43.04%20AM.png)
    
6.  Close the PowerShell console.

  
## Comprehensive questions
Which of the following best describes why Group Policy is a better tool for managing PowerShell then individual cmdlets if you have many servers?
	Group Policy provided centralized configuration to Windows computers.

  

Which of the following best describes why unsigned local scripts might be more trustworthy than unsigned remote scripts?
	Unsigned local scripts were probably written by your fellow employees.
