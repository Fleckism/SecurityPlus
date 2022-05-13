# OpenSSL
Commands
- ~openssl version
- ~openssl genrsa -out corp.515support.com.key 2048



# 1
1.  ```bash-notab-nocopy
    openssl version
    ```
    
2.  What version of OpenSSL is installed?
    
    1.1
    
    2.3
    
    3.1
    
    6.0
    
    Correct
    
    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    
    OpenSSL version.![Output from openssl version command](https://labondemand.blob.core.windows.net/content/lab84042/Screen%20Shot%202020-11-06%20at%2011.17.41%20AM.png)
    
3.  Run the following command to create a directory named **keys** in the root user's home directory:
    
    ```bash-notab-nocopy
    mkdir keys
    ```
    
4.  Use the cd command to change to the **keys** directory.
    
5.  Generate an asymmetric encryption RSA key pair and extract the public portion to prepare to create a certificate signing request (which occurs below). Type the following command, then press **ENTER**:
    
    ```bash-notab-nocopy
    openssl genrsa -out corp.515support.com.key 2048
    ```
    
6.  Run the following command to display the private key:
    
    ```bash-notab-nocopy
    cat corp.515support.com.key
    ```
    
7.  Extract the public key file to a file for export with a CSR.
    
    ```bash-notab-nocopy
    openssl rsa -in corp.515support.com.key -pubout -out corp.515support.com_public.key
    ```
    
    > You can resize the panes by clicking and dragging the border between the Instructions pane and the VM pane. This can make it much easier to see the long commands contained in this activity.
    
8.  Use the ls command to display the two key files that you have created so far.
    
    The two key files.![Output of the ls command displaying the two key files](https://labondemand.blob.core.windows.net/content/lab84042/Screen%20Shot%202020-11-06%20at%2011.21.13%20AM.png)
    
9.  Display the public key file:
    
    ```bash-notab-nocopy
    cat corp.515support.com_public.key
    ```
    
10.  Confirm that the corp.515support.com_public.key file exists.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
    The .key file
    
    If the file is not found, ensure that you have saved it to the correct location and with the specified file name.
    

23% Tasks Complete

Next: Generate a certificate signing request

## Generate a certificate signing request

Generate a web site certificate signing request that could be sent to a certificate authority (CA).

1.  Generate a certificate signing request. Type the following command, then press **ENTER**:
    
    ```bash-notab-nocopy
    openssl req -new -key corp.515support.com.key -out corp.515support.com.csr
    ```
    
2.  Provide the following answers to the prompts:
    
    -   Country Code: _your country_
    -   State or Province Name: _your state or province_
    -   Locality Name: _your city_
    -   Organization Name: 515 Support
    -   Organizational Unit Name: WebServices
    -   Common Name: webserver.corp.515support.com
    -   Email Address: admin@515support.com
3.  When prompted to enter a challenge password and an optional company name, press **ENTER**.
    
    This OpenSSL command generates a certificate signing request on behalf of the Apache web server service for a web site.
    
4.  Run the ls command to display the .csr file.
    
5.  Confirm that the corp.515support.com.csr file exists.
    
    The .csr file
    
6.  Verify the certificate request. Type the following command, then press **ENTER**:
    
    ```bash-notab-nocopy
    openssl req -text -in corp.515support.com.csr -noout -verify
    ```
    
    This OpenSSL command verifies the certificate request.
    
7.  The certificate signing request must be sent to the certificate authority using the PEM format. Run the following command to display the CSR file in this format:
    
    ```bash-notab-nocopy
    cat corp.515support.com.csr
    ```
    
    > The entire contents of the output must be copied into the certificate request interface (this interface varies by CA vendor). The header **-----BEGIN CERTIFICATE REQUEST-----** and trailer **-----END CERTIFICATE REQUEST-----** must be included.
    

## Convert certificate format

As we don't have a CA available to sign the request, for the next part of the exercise we'll generate a self-signed certificate with a new key, overwriting the old one.

1.  Run the ls command and observe that there are three files in the directory.
    
2.  Generate a self-signed certificate:
    
    ```bash-notab-nocopy
    openssl req -newkey rsa:2048 -nodes -keyout corp.515support.com.key -x509 -days 365 -out corp.515support.com.crt
    ```
    
3.  Provide the following answers to the prompts:
    
    -   Country Code: _your country_
    -   State or Province Name: _your state or province_
    -   Locality Name: _your city_
    -   Organization Name: 515 Support
    -   Organizational Unit Name: WebServices
    -   Common Name: webserver.corp.515support.com
    -   Email Address: admin@515support.com
4.  Confirm that the corp.515support.com.crt file exists.
    
    > Don’t forget to use exactly the same names as specified in the instructions.
    
    The .crt file
    
5.  Run the ls command again and observe that there are now four files in the directory. A new .crt file has been created.

## Merge the .key and .crt files (the non-Windows PEM format) into a .pfx file (the Windows PKCS#12 format)

Convert the certificate you generated to a format accepted by the Windows.

Certificates are often issued by CAs in the PEM format. Windows servers often use the PKCS#12 format, where keys are merged into a single file. The PKCS#12 format is an archival file that stores both the certificate and the private key. This format is useful for migrating certificates and keys from one system to another as it contains all the necessary files. PKCS#12 files use either the .pfx or .p12 file extension.

Use the following command to convert your PEM key and certificate into the PKCS#12 format (i.e., a single .pfx file):

1.  Type the following command to convert the files, then press **ENTER**:
    
    ```bash-notab-nocopy
    openssl pkcs12 -export -name "corp.515support.com" -out corp.515support.com.pfx -inkey corp.515support.com.key -in corp.515support.com.crt
    ```
    
2.  When prompted select **ENTER** to skip defining an **Export Password**.
    
3.  Run the ls command and observe that there are now five files in the directory. A new .pfx file has been created.
    
4.  Confirm that the corp.515support.com.pfx file exists.
    
    The .pfx file
    

77% Tasks Complete

PreviousNext: Comprehensive questions



# Answers
Exam Results

Score

8 / 8

Passed

Yes

Activities (8)

What version of OpenSSL is installed?

 1.1

 2.3

 3.1

 6.0

```
        Correct
```

Score: 1

public.key exists

Confirm that the corp.515support.com_public.key file exists.

Correct

Score: 1

Score: 1

csr exists

Confirm that the corp.515support.com.csr file exists.

Correct

Score: 1

Score: 1

crt exists.

Confirm that the corp.515support.com.crt file exists.

Correct

Score: 1

Score: 1

pfx exists

Confirm that the corp.515support.com.pfx file exists.

Correct

Score: 1

Score: 1

Which of the following is the file extension for certificate request files?

 .crt

 .pfx

 .key

 .csr

```
        Correct
```

Score: 1

Why is it necessary to merge or convert certificate file types?

 CAs issue certificates in a different format than Windows servers use the certificates.

 The merge process encrypts the certificates more securely.

 Merging the certificates makes the file sizes smaller and more efficient to download.

```
        Correct
```

Score: 1

What is the certificate file extension commonly used by Windows servers?

 .crt

 .csr

 .key

 .pfx

```
        Correct
```

Score: 1