[[Applied Lab 14#Security policy]]

# APPLIED LAB 14: Configuring Identity and Access Management Controls

## Scenario

You have been asked to provide a general security audit for 515 Support. First, you will review and implement aspects of the written security policy. Next, you will configure both Windows NTFS permissions and Linux standard permissions. You will use a password cracking utility to audit a user password. Finally, you will deploy certificates, including an **SSL certificate for a web site** and certificate management with OpenSSL.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   1.2 Given a scenario, analyze potential indicators to determine the type of attack
    
-   3.7 Given a scenario, implement identity and account management controls
    
-   3.8 Given a scenario, implement authentication and authorization solutions
    
-   3.9 Given a scenario, implement public key infrastructure
    
-   4.1 Given a scenario, use the appropriate tool to assess organizational security

## Security policy

Implement the settings required by the 515 Support written security policy for user account managment and auditing.

1.  Review the following written security requirements. Edit the Default Domain Policy Group Policy Object to enforce the password and account lockout configurations. Edit the 515 Support Domain Policy to enforce the remaining security options.
    )))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))
    -   Passwords will be changed every [[Maximum password age]] 60 days, and may not be changed more frequently than every [[Minimum password age]] one day. Passwords must be at least [[Minimum password length]] 12 characters in length. Passwords must meet complexity requirements. Users may not reuse the last [[Enforce password history]] 20 passwords.
        !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
    -   Accounts will be locked out for 10 minutes if an incorrect password is entered more than three times.
        
    -   Local guest user accounts will be disabled.
        
    -   Servers and workstations will not display the user name of the last user to log on.
        
    -   Servers and workstations will display the following title and message: "Warning" (title) "Authorized use only!" (message)
        
2.  Select the [DC1]
    
3.  Use the **Group Policy Management**  (Under Tools) in the Server Manager. [[domain object and observe the two existing GPOs]]
    
4.  Edit the existing **Default Domain Policy** to match the password and account lockout requirements defined above in the security requirements.
    
    Settings locations
    
    -     Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies Password Policy: See ))))))))))))))))))))))))))))))))

-   Password history
-   Max password age
-   Min password age
-   Min password length
-   Password must meet complexity requirements

Account Lockout Policy: See !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

-   Account lockout duration
-   Account lockout threshold
        
    
5.  Edit the existing **515 Support Domain Policy** to match the guest account, logon message, and last user name requirements defined above in the security requirements.
    
    Settings locations
    
    -     Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options

-   Accounts: Guest account status - disabled
-   Interactive logon: Do not display last user name
-   Interactive logon: Message text for users attempting to log on
-   Interactive logon: Message title for users attempting to log on.
        
    
6.  From **Administrator: Windows PowerShell** run the `gpupdate /force` command twice.
    
7.  From **Administrator: Windows PowerShell** run the `gpresult /H C:\Users\Administrator\Desktop\GPreport.htm` command.
    
8.  Confirm that the .htm file exists on the Desktop
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
9.  Close **Administrator: Windows PowerShell**.



## Manage Windows permissions

You will manage user access to data on Windows Server by using NTFS permissions.

1.  Select the [DC1]
2.  Create the following folders on the C: drive:
    
    -   SalesData
    -   ITData
3.  Confirm that the C:\SalesData folder exists
    
4.  Confirm that the C:\ITData folder exists.
    
    > Don’t forget to use exactly the same names as specified in the instructions.
    
5.  A Help Desk ticket forwarded to you states that **Bobby** should be a member of the **Sales** group, and that the **Sales** group needs the **Modify** permission to the **SalesData** folder.
    
    Use **File Explorer** and **Active Directory Users and Computers** to satisfy the requirements.
    
6.  Confirm that Bobby is a member of the Sales group.
    
7.  Confirm that the Sales group has the Modify permission to the C:\SalesData folder.
    
8.  A Help Desk ticket forwarded to you states that **Sam** should be _explicitly denied_ access to the **ITData** folder. Configure the explicit deny permission.
    
9.  Confirm that Sam has an explicit Deny permission to the C:\ITData folder.


## Configure Linux permissions

You will configure user access to resources in Linux. First, you need to create a user account and a group. Next, you need to create the resources (a directory and a file). Finally, you'll set ownership and permissions. Such configurations demonstrate the relationship between user identities (accounts and group memberships), ownership, and permissions.

1.  Select the [PT1-Kali] virtual machine, sign in as root using Pa$$w0rd as the password.
    
2.  From the top bar, open the **Terminal Emulator** icon.
    
    > You must start in the /root folder. Run cd if you are not sure.
    
3.  Create a user acccount named **floyd**, and then set floyd's password as Pa$$w0rd by using the adduser command.
    
    > You have access to the actual Linux commands below because the focus of this activity is security concepts and not Linux commands.
    
    Create an account.
    
    -   adduser floyd
    -   When prompted, enter and confirm Pa$$w0rd
    -   Select **ENTER** for all other options.
    
4.  Confirm that the floyd user account exists
    
5.  Create a group named **Sales** by using the groupadd command.
    
    Create a group.
    
    -   groupadd Sales
    
6.  Confirm that the Sales group exists.
    
7.  Create a directory named **/SalesInfo** by using the mkdir command, and then create a file in the **/SalesInfo** directory named **SalesPolicies.txt** by using the touch command.
    
    Create a directory and a file.
    
    -   mkdir /SalesInfo
    -   touch /SalesInfo/SalesPolicies.txt
    
8.  Confirm that the /SalesInfo directory exists.
    
9.  Grant **floyd** ownership of the **/SalesInfo** directory and the **Sales** group as the associated group by using the chown -R command.
    
    Configure ownership and group associations.
    
    -   chown -R floyd:Sales /SalesInfo
    
10.  Confirm that floyd owns /SalesInfo.
    
11.  Confirm that the Sales group is associated with /SalesInfo
    
12.  Configure **floyd** with **rwx**, the **Sales** group with **r-x**, and all others with no access to the **/SalesInfo** directory and all of its contents by using the chmod -R command.
    
    Configure Linux permissions.
    
    -   chmod -R u=rwx,g=rx,o-rwx /SalesInfo
    
13.  Confirm that the permissions are configured correctly.


## Audit a user password

You need to audit the password for the Bobby user account. You will add a possible password for his account to the wordlist in order to speed up the decryption process. The focus of this activity is on the tools, not on the likelihood of cracking the password.

1.  Select the [PT1-Kali](https://labclient.labondemand.com/Instructions/a51a582d-9c12-4ae7-9d1c-994d5b84abaa?rc=10#) VM. If necessary, sign in as root using Pa$$w0rd as the password.
    
2.  From the top bar, open the **Terminal Emulator** icon.
    
    > You must start in the /root folder. Run cd if you are not sure.
    
3.  Create an account named **bobby** and set Pa$$w0rd as the password by using the adduser command. .
    
    > You are being provided with step-by-step Linux instructions to keep the focus on CompTIA Security+ concepts.
    
    Create an account.
    
    -   adduser bobby
    -   When prompted, enter Pa$$w0rd
    -   Accept all other defaults by pressing **ENTER**.
    

> Red Hat-derived distributions, such as the CentOS Linux on the LX1 virtual machine, typically use useradd. Debian-based Linux distributions, such as the Kali Linux on the PT1-Kali VM, prefer the adduser command to create users.

6.  Extract the **/usr/share/wordlists/rockyou.txt.gz** word list file by using the gunzip command:
    
    ```bash-notab-nocopy
    gunzip /usr/share/wordlists/rockyou.txt.gz
    ```
    
7.  Open the **rockyou.txt** wordlist file for editing (you may use Vim or nano):
    
    Vim quick reference
    
    vim /usr/share/wordlists/rockyou.txt
    
    Move between modes:  
    To enter Command mode - **ESC**  
    To enter Insert mode - **i**  
    To enter Execute mode - **:**
    
    After editing a file:  
    Save and quit - **:wq**  
    Quit without saving - **:q!**
    
    Use arrow keys to navigate
    
    When in doubt, press **ESC** to enter Command mode.
    
    Editing process:
    
    -   vim filename opens the file
    -   **i** enters Insert mode
    -   Navigate the file with arrow keys
    -   Edit file contents while in Insert mode
    -   **ESC** returns to Command mode
    -   **:wq** saves file and quits Vim  
        
    
8.  Use the **i** key to enter Vim's Insert mode, and then add the password you set for Bobby above at the _top_ of the file.
    
    Recall that you are adding this password to the list because you believe the user has an easily-guessed password.
    
9.  Run the following command to create a text file of usernames and password hashes:
    
    ```bash-notab-nocopy
    unshadow /etc/passwd /etc/shadow > crack-this-file
    ```
    
10.  Run the following command to crack passwords:
    
    ```bash-notab-nocopy
    john --wordlist=/usr/share/wordlists/rockyou.txt crack-this-file
    ```
    
11.  Redirect the results of the john --show crack-this-file to a text file:
    
    ```bash-notab-nocopy
    john --show crack-this-file > password-audit.txt
    ```
    
12.  Display the **password-audit.txt** file contents by using the cat command.
    
13.  Confirm that the password-audit file exits.
    
    The password-audit.txt file.If the password-audit.txt file does not exist, ensure that you have saved the file to the correct location and with the correct name. Rerun the above command.
    

## Request a server certificate

Use Windows Certificate Services to deploy an [[SSL certificate]] to a web server.

1.  Select the [MS1]
2.  Open the aka Server Manager **Internet Information Services (IIS) Manager** console.
    
3.  Select the **Server Certificates** applet.
    
4.  In the Actions pane, select **Create Domain Certificate**. Complete the Create Certificate wizard by entering the following information:
    
    -   Common Name: updates.corp.515support.com
        
    -   Organization: 515 Support
        
    -   Organizational Unit: Web Team
        
    -   Fill in City, State, and other fields with your information or just use Cloud
        
    -   Online Certification Authority: Select **515support-CA**
        
    -   Friendly name: updates.corp.515support.com Domain-issued Certificate
        
    
    After a few seconds, the certificate request will be granted.
    
5.  Right-click **Default Web Site** and select **Edit Bindings**.
    
6.  Add a site binding for **https** that uses a hostname of updates.corp.515support.com and binds the **updates.corp.515support.com Domain-issued certificate** SSL certificate.
    
7.  Remove the **http** entry.
    
8.  Close the dialog box, and return to the main IIS console.
    
9.  In **Internet Explorer** attempt to connect to https://updates.corp.515support.com. If prompted, select **OK** to acknowledge the warning.
    
    It may take up to one minute for the connection to be established.
    
10.  You should see the **515 Support User Portal** web page.
    
11.  Close the browser.



## Manage certificates by using OpenSSL

Use OpenSSL to manage certificates.

1.  Select the [PT1-Kali]
    
2.  From the top bar, open the **Terminal Emulator** icon.
    
    > You must start in the /root folder. Run cd if you are not sure.
    
3.  Create a directory named **keys** in the root user's home directory, and then use the cd command to change to the **keys** directory.
    
4.  Generate a private key and extract public to prepare to create a certificate signing request (which occurs below). Type the following command, then press **ENTER**:
    [[How to confirm key exists]]
    ```bash-notab-nocopy
    openssl genrsa -out corp.515support.com.key 2048
    ```
    
5.  Confirm that the key file exists.
    
6.  Extract the public key.
    **Writes RSA key**
    ```bash-notab-nocopy
    openssl rsa -in corp.515support.com.key -pubout -out corp.515support.com_public.key
    ```
    
7.  Use the ls command to display the public key file.
    
8.  Display the public key file:
    
    ```bash-notab-nocopy
    cat corp.515support.com_public.key
    ```
    
9.  Confirm that the public.key file exists.
    
10.  Generate a certificate signing request. Type the following command, then press **ENTER**:
    
    ```bash-notab-nocopy
    openssl req -new -key corp.515support.com.key -out corp.515support.com.csr
    ```
    
    Provide the following answers to the prompts:
    
    -   Country Code: _your country_
    -   State or Province Name: _your state or province_
    -   Locality Name: _your city_
    -   Organization Name: 515 Support
    -   Organizational Unit Name: WebServices
    -   Common Name: _your name_
    -   Email Address: admin@515support.com
    -   When prompted to enter a challenge password and an optional company name, press **ENTER**.
    
    This OpenSSL command generates a certificate signing request on behalf of the Apache web server service for a web site.
    
11.  Run the ls command to display the .[[csr]] file.