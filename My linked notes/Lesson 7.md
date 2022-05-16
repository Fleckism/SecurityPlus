# 1
# Assisted Lab 09: Auditing Passwords with a Password Cracking Utility

## Scenario

You are auditing password quality to better teach your fellow employees the importance of strong passwords. First, you sent out an employee survey, asking seemingly harmless questions. The results are in the following table. Next, you will add the results to a wordlist to be used as a source for password cracking utilities such as John the Ripper. Finally, you will crack the passwords to demonstrate whether they expose the organization to authentication vulnerabilities.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   1.2 Given a scenario, analyze potential indicators to determine the type of attack.

---

## Survey results

Here is an excerpt from the email message:

```bash-notab-nocopy-nocode
Please fill out the following survey so that we can get to know you better and celebrate significant events!

- What is your birthday?
- What is your spouse's name?
- When is your anniversary?
- What is your pet's name?
```

You have documented the survey result in the table below:

Name

Birthday

Spouse

Anniversary

Pet name

user01

06101988

Mary

05232010

Max

user02

10141976

Tim

06011989

no pet

user03

09081998

Rick

07032018

Duke

user04

02081980

George

06142004

Rover

user05

03121985

Shawna

12132010

Spot

user06

no response

no response

no response

no response
# 2
## Create the necessary accounts and passwords

You will create six user accounts with passwords related to the above survey.

1.  Sign in as root using Pa$$w0rd as the password.
    
2.  Launch the **Terminal** application from the toolbar on the top of the Kali desktop.
    
3.  Run the following command to create the first user:
    
    ```bash-notab-nocopy
    adduser --gecos "" user01
    ```
    
    When prompted, set 06101988 as the password (you'll type it in twice).
    
    > As a Debian-based Linux distribution, Kali Linux prefers the adduser command to create users. Red Hat-derived distributions, such as CentOS, typically use useradd.
    
4.  Create the following additional accounts by using the adduser command, and set the specified passwords when prompted:
    
    Username:
    
    Password:
    
    user02
    
    Password
    
    user03
    
    Duke
    
    user04
    
    george
    
    user05
    
    $p0T
    
    user06
    
    G00dPa$$w0rd
    
    > Don't forget about using Bash's history feature. After creating **user01**, press the **UP ARROW** key one time, backspace over the **1** character and then enter the **2** character. This should allow you to create the accounts quickly.
    
    > Recall that Linux does not display any indication on the screen that the password is being entered. It is accepting your keystrokes, however.
    
5.  Confirm that the six specified users exist.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
    Creating users and setting passwords.
    
    ![adduser](https://labondemand.blob.core.windows.net/content/lab84043/Screen%20Shot%202020-11-07%20at%2011.25.06%20AM.png)
    

0% Tasks Complete

PreviousNext: Add probable passwords to the word...
cat /etc/passwd  the linux command to show how many users are on file

# 1
Authentication proves that a subject is who or what it claims to be when it attempts to access the resource. A CAC and pin login are examples of authentication.

Creating an account or ID that identifies the user, device, or process on the network defines identification.

Authorization determines what rights subjects should have on each resource and enforcing those rights. A company employee may need network access but will likely not need access to every resource, and limiting access limits a company’s risk.

Accounting tracks authorized usage of a resource or use of rights by a subject and alerting when unauthorized use is detected or attempted. Reports and audit logs account for who and what has been accessing network resources.

# 2
Identification controls are set to ensure that customers are legitimate. An example is to ensure that billing and primary delivery addresses are real and valid.

Authentication controls are to ensure that customers have unique accounts, and that only they can manage their orders and billing information. An example is to require each customer create an account prior to allowing them to store billing or shipping information.

Authorization controls are to ensure customers can only place orders when they have valid payment information in place prior to completing an order.

Accounting controls include maintaining a record of each action taken by a customer to ensure that they cannot deny placing an order. Records may include order details, date, time, and IP address information.
# 3
Integrity is the fundamental security goal of keeping organizational information accurate, free of errors, and without unauthorized modifications. However, it is not part of the IAM system. IAM defines the attributes that comprise an entity's identity. The four processes include Authorization, Accounting, Identification, and Authentication.

Accounting is tracking authorized usage of a resource or use of rights by a subject and alerting when unauthorized use is detected or attempted.

Identification is creating an account or ID identifying the user, device, or process on the network.

Authentication is proving that a subject is who or what it claims to be when attempting to access the resource.

# 4
In Two-Factor Authentication (2FA), a user must possess two of the three authentication types of “something you know”, “something you have”, or “something you are”. Using a password and a smart card would be 2FA since it combines “something you know” (password) with “something you have” (smart card).

Using a password and a PIN is not 2FA since they both are “something you know.”

Using a fingerprint and facial recognition is not 2FA since they both are “something you are.”

Using a smart card and a key fob is not 2FA since they both are “something you have.”
# 5
A face scan is also known as biometrics, which is a "something you are" authentication. This is known as behavioral biometric recognition.

Creating a user account based on an official company document is an identification process called identity proofing, or verifying subjects are who they say they are.

By creating and sending the initial password over a Virtual Private Network (VPN), the administrator is implementing secure transmission of credentials identification process.

Identification of a subject on a computer system is done through an account. An account consists of an identifier, credentials, and a profile. Each identifier must be unique, which is accomplished with a Security Identifier (SID) string.
# 6
A brute force attack attempts every possible combination in the key space in order to derive a plaintext password from a hash. The key space is determined by the number of bits used.

A hybrid password attack uses a combination of dictionary and brute force attacks. It is principally targeted against naively strong passwords. The password cracking algorithm tests dictionary words, and names in combination with several numeric prefixes.

A rainbow table attack refines the dictionary approach. The attacker uses a precomputed lookup table of all possible passwords and their matching hashes.

A dictionary attack can be used where there is a good chance of guessing the likely value of the plaintext, such as a non-complex password.
# 7
A typical hybrid password attack uses a combination of dictionary and brute force attacks.

A dictionary attack is a type of password attack that compares encrypted passwords against a predetermined list of possible password values. A brute force attack attempts every possible combination in the key space in order to derive a plaintext password from a hash.

Salt is a random or pseudo-random number or string. The term salt is used specifically in conjunction with hashing password values.

A pass the hash (PTH) attack occurs when an attacker obtains the hash of a user's password and presents the hash (without cracking it) to authenticate to network protocols.
# 8
Restricting logons can become a vulnerability by exposing a user to Denial of Service (DoS) attacks. The attacker keeps trying to authenticate, locking out valid users.

In a replay attack, an intercepted key or password hash is reused to gain access to a resource. This is prevented with once-only tokens or timestamping, not restricting logon attempts.

A brute force attack is where an attacker uses an application to exhaustively try every possible alphanumeric combination to crack encrypted passwords. Restricting logon attempts is a way to mitigate this threat, not be vulnerable to it.

In an offline attack, a password cracker works on a downloaded password database without having to interact with the authentication system. It is unrelated to logon attempts.
# 9
The Authentication Service (AS) is responsible for authenticating user logon requests. The first step within AS is when the client sends the AS a request for a Ticket Granting Ticket (TGT). This is composed by encrypting the date and time on the local computer with the user's password hash as a key.

A User Ticket contains information about the client and includes a timestamp and validity period. The information is encrypted using the KDC's secret key. This occurs after the user is found in the database and the request is valid.

The AS does not respond back with a TGT key but with a Ticket Granting Service (TGS) key that is used in communications between the client and the TGS.

The TGS is the service that responds with a service session key for use between the client and the application server.
# 10
The password does not contain special characters, and also contains words that are found in the dictionary. Both of these attributes make the password vulnerable.

The length of the password may be sufficient based on the rules set forth by the system administrator and company policy. The company policy may or may not require the use of special characters, and this is unknown from the scenario.

The password is insufficiently complex. The inclusion of uppercase letters alone does not make a password complex.

While it is correct that the user may be able to remember this password easily, that also makes it susceptible to attack. Dictionary words make it that much easier for an attacker to crack the password.
# 11
Inputting a correct PIN authorizes the smart card's cryptoprocessor to use its private key to create a Ticket Granting Ticket (TGT) request to an Authentication Server (AS).

The AS can place trust when the user's certificate is issued by a local or third-party root certification authority.

An AS responds with a TGT and Ticket Granting Service (TGS) session key, not the smart card.

An AS would be able to decrypt the request because it has a matching public key and trusts the user's smart-card certificate.
# 12
Tokens can persist unexpired in HOTP, increasing the risk of an attacker obtaining one and decrypting data in the future. TOTP addresses this by adding a value to the shared secret derived from the device’s and server’s local timestamp. TOTP automatically expires each token after a short window of time.

The authentication server and client token are configured with the same shared secret in HOTP.

The HOTP server is configured with a counter, combining with the shared secret to create a one-time password. When the HOTP value is authenticated, it increments by one.

The server and the device both compute the hash and derive a 6-8 digit HOTP value.
# 13
RADIUS uses TCP or UDP by default over ports 1812 and 1813 and TACACS+ uses TCP on port 49.

TACACS+ encrypts the whole packet (except the header, which identifies the packet as TACACS+ data) and RADIUS only encrypts the password portion of the packet using MD5.

RADIUS is primarily used for network access for a remote user and TACACS+ is primarily used for device administration. TACACS+ provides centralized control for administrators to manage routers, switches, and firewall appliances, as well as user privileges.

RADIUS is an open-source protocol, not TACACS+. TACACS+ is a Cisco proprietary protocol.
# 14
Where EAP provides the authentication mechanisms, the IEEE 802.1X Port-based Network Access Control (NAC) protocol provides the means of using an EAP method when a device connects to a VPN gateway.

Kerberos is designed to work over a trusted local network. Several authentication protocols have been developed to work with remote access protocols, where the connection is made over a serial link or virtual private network (VPN).

TACACS+ uses TCP communications. Authentication, authorization, and accounting (AAA) functions within TACACS+ are discrete.

With authentication, authorization, and accounting (AAA), the network access server (NAS) devices (RADIUS or TACACS+) do not have to store any authentication credentials. They forward this data between the AAA server and the supplicant.
# 15
Regarding biometric authentication, a false positive is where an unauthorized person is accepted, leading to possible security breaches. This is the False Acceptance Rate (FAR).

A false negative is where a legitimate user is not recognized, denying the user access and causing the user an inconvenience. This event does not result in a breach. This is the False Rejection Rate (FRR).

The Crossover Error Rate (CER) is the point at which FRR equals FAR. A lower CER indicates more efficient and reliable authentication.

Throughput refers to the time required to create a user template and to authenticate. While this is a major consideration for high-traffic access points (airports), a low rate would be frustrating for users, but not a breach risk.
# 16
A sensor module acquires the biometric sample from the target. Examples of a sensor module can be a fingerprint scanner or retina scanner.

One problem that biometric cryptosystems is the lack of revocability. A legitimate person will almost always have the same template (fingerprint, retina, etc). If a company is using a smart card and it is compromised, the card is revoked and reissued. The same cannot be done for biometric cryptosystems.

A feature extraction module records the significant information from the sample. This record would include the fingerprint that was scanned when authentication was requested.

A sensor module acquires the biometric sample from the target.
# 17
Behavioral technologies are sometimes classified as "something you do." These technologies often have a lower cost to implement than other types of biometric cryptosystems, but they have a higher error rate.

Typing is used as a behavioral technology, and the template is based on the speed and pattern of a user's input of a passphrase.

Signature recognition is not based on the actual signature due to it being easy to replicate. Instead, it is based on the process of applying a signature such as stroke, speed, and pressure of the stylus.

Obtaining a voice recognition template is not a fast process, and can be difficult. Background noise and other environmental factors can also interfere with authentication.
# 18
Biometric authentication based on a retinal scan is the hardest method to fool. Retinal scanning is used to identify the patterns of blood vessels with the eye, whereas an iris scan only uses the surface of the eye.

It is possible to obtain a copy of a user's fingerprint and create a mold of it that will fool a fingerprint scanner.

Facial recognition suffers from relatively high false acceptance and rejection rates, and as a result is vulnerable to spoofing.

Voice recognition is subject to impersonation. It is also sensitive to background noise and other environmental factors which can interfere with authentication.
# 19
The process of fine-tuning a biometric system involves adjusting the crossover error rate, the point at which the false rejection rate and false acceptance rate meet.

The false rejection rate (FRR) is also known as a type I error, which rejects authorized templates.

The false acceptance rate (FAR) is the rate at which the system lets in unauthorized users, which constitutes a security breach.

A type II error is a false positive, measured by the false acceptance rate (FAR). This is the rate at which unauthorized personnel gain access to the secure facility.
# 20