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
# 3

# 4
# 5
# 6
# 7
# 8
# 9
# 10
# 11
# 12
# 13
# 14
# 15
# 16
# 17
# 18
# 19
# 20