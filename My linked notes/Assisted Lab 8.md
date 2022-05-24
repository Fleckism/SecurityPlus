# Assisted Lab 13: Managing Access Controls in Linux

## Scenario

In this activity, you will manage access controls on a Linux server. First, you will configure local users and groups on the system. Next, you will create directories and files to represent resources that need to be controlled. Next, you will configure the ownership of these directories and files. Finally, you'll configure standard Linux permissions to manage for the users and groups to access the directories and files.

## Objectives

This activity is designed to test your understanding of and ability to apply content examples in the following CompTIA Security+ objectives:

-   3.8 Given a scenario, implement authentication and authorization solutions.
    
-   4.1 Given a scenario, use the appropriate tool to assess organizational security.


## Create users and groups

You need to create two test users and two groups on the Linux virtual machine. You'll configure passwords for the two users, too.

1.  Sign in to the [PT1-Kali](https://labclient.labondemand.com/Instructions/b6758386-77f1-4243-87de-9f95fc703536?rc=10#) VM as root using Pa$/$w0rd as the password.
    
2.  From the toolbar at the top of the Desktop, open the Terminal.
    
    > You should get used to managing Linux servers from the command line.
    
3.  Run the following command to create a new user named user01:
    
    ```bash-notab-nocopy
    useradd user01
    ```
    
4.  Run the following command to set a password for user01:
    
    ```bash-notab-nocopy
    passwd user01
    ```
    
5.  When prompted, enter and confirm the password Pa$$w0rd
    
    > Creating a user in Linux is two steps: 1) create the user by using the useradd command, and 2) set the password by using the passwd command.
    
    Create a user.![Screen Shot 2020-11-07 at 3.31.45 PM.png](https://labondemand.blob.core.windows.net/content/lab84047/Screen%20Shot%202020-11-07%20at%203.31.45%20PM.png)
    
6.  Repeat the above steps to create user02, and then set Pa$$w0rd as password.
    
7.  Confirm that user01 and user02 exist.
    
    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
    
    Confirm user accounts
    
8.  Run the following command to create a new group named admins:
    
    ```bash-notab-nocopy
    groupadd admins
    ```
    
9.  Confirm that the admins group exists.
    
    Confirm admins group
    
10.  Create a second group named devs.
    
    Confirm that the devs group exists.
    
    Confirm the devs group exists.
    
11.  Add **user01** to the **admins** group:
    
    ```bash-notab-nocopy
    usermod -aG admins user01
    ```
    
    > Adding a user to a group is a modification of the user object, hence the use of usermod.
    
12.  Run these commands to verify the group memberships:
    
    ```bash-notab-nocopy
    id user01
    ```
    
    Manage groups.![Manage groups](https://labondemand.blob.core.windows.net/content/lab84047/Screen%20Shot%202020-11-07%20at%203.34.09%20PM.png)
    
    ```bash-notab-nocopy
    tail /etc/group
    ```
    
    > The tail command in Linux displays the last 10 lines of a file. In this case, it displays the most recently-created groups.
    
13.  Add **user02** to the **devs** group.
    
14.  Confirm that user02 is a member of the devs group.
    
    Confirm user02 is in the devs group.
    

0% Tasks Complete

PreviousNext: Create directories and files

## Create directories and files

Use the mkdir and touch commands to create directories and files to simulate resources that need to have permissions applied to them.

1.  Run the following commands to create three directories:
    
    ```bash-notab-nocopy
    mkdir /projects
    ```
    
    ```bash-notab-nocopy
    mkdir /projects/ITprojects
    ```
    
    ```bash-notab-nocopy
    mkdir /projects/devprojects
    ```
    
    > You could create all three directories (/projects, /projects/ITprojects, /projects/devprojects) by issuing one command: mkdir /projects /projects/ITprojects /projects/devprojects
    
    > Don’t forget to use exactly the same names as specified in the instructions.
    
2.  Confirm that the /projects/ITprojects directory exists.
    
3.  Confirm that the /projects/devprojects directory exists.
    
    Confirm the directories
    
4.  Run the following commands to create two files:
    
    ```bash-notab-nocopy
    touch /projects/ITprojects/servers.txt
    ```
    
    ```bash-notab-nocopy
    touch /projects/devprojects/programming.txt
    ```
    
    > The touch command updates the timestamp on an existing file. If the specified file does not exist, touch creates it.
    
5.  Confirm that the servers.txt file exists.
    
6.  Confirm that the /projects/devprojects/programming.txt file exists.
    
    Confirm the files![Confirm the files](https://labondemand.blob.core.windows.net/content/lab84047/Screen%20Shot%202020-11-07%20at%203.37.00%20PM.png)
    

41% Tasks Complete

PreviousNext: Configure ownership

## Configure ownership

By default, the creator of a resource owns the resource. Because you used to the root user account to create the directories and files in the previous activity, the root user controls access. You need to permit users and groups to own the directories and files so that they can configure permissions..

1.  Run the following commands to display the current default permissions on the contents of the /labs directory:
    
    ```bash-notab-nocopy
    ls -ld /projects
    ```
    
    > Whoever creates the object, owns the object. Hence, root owns these objects.
    
    Owner and group for /projects![Owner and group](https://labondemand.blob.core.windows.net/content/lab84047/Screen%20Shot%202020-11-07%20at%203.38.06%20PM.png)
    
2.  Run the following commands to change ownership from root to the specified users and groups:
    
    ```bash-notab-nocopy
    chown -R user01:admins /projects/ITprojects
    ```
    
    ```bash-notab-nocopy
    chown -R user02:devs /projects/devprojects
    ```
    
    > The -R option makes the chown recursive. This applies the ownership and groups settings to the directory and everything in it.
    
3.  Run the following command to display the user and group associations for the **/projects/ITprojects** directory itself:
    
    ```bash-notab-nocopy
    ls -ld /projects/ITprojects
    ```
    
4.  Run the following command to display the user and group associations for the _contents_ of the **/projects/ITprojects** directory:
    
    ```bash-notab-nocopy
    ls -l /projects/ITprojects
    ```
    
5.  Who is the owner and what group is associated with the /projects/ITprojects directory?
    
    The user01 account and the devs group.
    
    The user02 account and the admins group.
    
    The user01 account and the admins group.
    
    The user02 account and the devs group.
    
    > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
    
    Confirm ownership
    
6.  Optionally, use ls to view the same information for the **devprojects** directory.

## Configure permissions

You will use the chmod command in symbolic mode to configure permissions for the resource owner, the associated group, and all others.

1.  Run the following command to display the current permissions for the **/projects/ITprojects** directory:
    
    ```bash-notab-nocopy
    ls -ld /projects/ITprojects
    ```
    
2.  Configure the permissions according to the table below. You may select the _Set the permissions_ section below if you need a reminder on how to configure permissions:
    
    Resource:
    
    User/Group:
    
    Access Level:
    
    /projects/ITprojects
    
    user01/admins
    
    rwxrwxr-x
    
    /projects/devprojects
    
    user02/devs
    
    rwxrwxr-x
    
    Set the permissions
    
3.  Confirm dthat permissions are set correctly for the /projects/ITprojects directory.
    
    Confirm permissions
    
4.  Confirm that permissions are set correctly for the /projects/devprojects directory.
    
    Confirm permissions
    

76% Tasks Complete

PreviousNext: Comprehensive questions



Exam Results

Score

13 / 15

Passed

Yes

Activities (15)

user01 and user02 exist

Confirm that user01 and user02 exist.

Correct

Score: 1

Score: 1

admins grp exists

Confirm that the admins group exists.

Correct

Score: 1

Score: 1

dev grp exists

Confirm that the devs group exists.

Correct

Score: 1

Score: 1

user02 in devs grp

Confirm that user02 is a member of the devs group.

Correct

Score: 1

Score: 1

/projects/ITprojects dir exists

Confirm that the /projects/ITprojects directory exists.

Correct

Score: 1

Score: 1

/projects/devprojects exists

Confirm that the /projects/devprojects directory exists.

Correct

Score: 1

Score: 1

servers.txt file exists

Confirm that the servers.txt file exists.

Correct

Score: 1

Score: 1

programming.txt exists

Confirm that the /projects/devprojects/programming.txt file exists.

Correct

Score: 1

Score: 1

Who is the owner and what group is associated with the /projects/ITprojects directory?

 The user01 account and the admins group.

 The user02 account and the admins group.

 The user01 account and the devs group.

 The user02 account and the devs group.

```
        Correct
```

Score: 1

ITprojects perms

Confirm dthat permissions are set correctly for the /projects/ITprojects directory.

Correct

Score: 1

Score: 1

perms devprojects

Confirm that permissions are set correctly for the /projects/devprojects directory.

Correct

Score: 1

Score: 1

Which command below adds userA to groupZ?

 useradd userA

 useradd userA groupz

 groupmod -aG userA groupZ

 usermod -aG groupZ userA

```
        Correct
```

Score: 1

Enter the command to create a file named "fileA" in a directory named "/test".

```
        Correct
```

Score: 1

Enter the command to set "admin" as the user and "IT" as the group for a directory named /infrastructure and all of its contents.

```
        Try again
```

Score: 0

Which of the following best describes the steps you took in this activity?

 Created users and groups, added users to groups, created directories and files, configured ownership, configured permissions.

 Created users and groups and set permissions on files and directories.

 Configured file and directory ownership.

 Configured users and passwords, removed unnecessary users, created computer accounts, managed permissions.

```
        Try again
```

Score: 0