==Add all linux commands here==
**Always confirm what you did**
Checks users / Check user
- $ cat /etc/passwd
Check groups
- $ cat /etc/group


## List Users on Linux

**In order to list users on Linux, you have to execute the “cat” command on the “/etc/passwd” file. When executing this command, you will be presented with the list of users currently available on your system.**

Alternatively, you can use the “less” or the “more” command in order to navigate within the username list.

$ cat /etc/passwd

$ less /etc/passwd

$ more /etc/passwd
## List Groups on Linux using the /etc/group file

**In order to list groups on Linux, you have to execute the “cat” command on the “/etc/group” file. When executing this command, you will be presented with the list of groups available on your system.**

Use one of the following commands to list groups on your system.

```
$ cat /etc/group

$ less /etc/group

$ more /etc/group
```

```

```

## How to Change File and Folder Permissions

We will be using the **chmod** command to change file and folder permissions in Linux. But first, you need to be aware that there are three types of users who can interact with a file:

-   **Owner** — the user who creates and owns a file or folder.
-   **Group** — all users who are members of the same group.
-   **Others** — all other users on the system who are neither the owner nor members of a group.

To see permissions and owners of a specific file, you can run this command:

ls -1 [file name]

The result will look like this:

-rwxrw–rw- 1 user user 0 Jan 19 12:59 myfile.txt

Let’s break the output down to see what each field means:

-   **“-rwxrw-rw-“** — this part of the line represents the file permissions. To understand it better, we have to divide it into four groups: (**–**), (**rwx**), (**rw-**), and (**rw-**).
    -   The first group indicates the file type. Our example shows a hyphen, which represents a regular file. If we are inspecting a directory, the hyphen will be replaced by **d**.
    -   The three characters after the file type represent the **owner’s file permissions**. In this example, we can see that the owner can read (**r**), write (**w**), and execute (**x**) the file.
    -   The next three characters are the **group’s file permissions**. We can conclude that the group can read (**r**) and write (**w**), but cannot execute the file. This is because the last character is a hyphen instead of the letter **x**.
    -   The last group is **others’ file permissions**. Based on our example, this type of user cannot execute the file, but they are allowed to read and write.
-   **1** – the number of hard links. A hard link is an additional name for an existing file.
-   **user user** – the owner and group owner of the file.
-   **0** – the size of the file in bytes.
-   **Jan 19 12:59** – the last modification date.
-   **myfile.txt** – the name of the file/folder.

### How to Use chmod Command

Let’s say someone in the group is getting bash: permission denied error and we want to change Linux file permissions from **-rwxrw-rw-** to **-rwx-r–r–**. Simply enter this line:

chmod 744 [file name]

By executing this command, the owner can read, write, and execute the file (**rwx**). However, group and others are only allowed to read (**r–**).

At this point, you might wonder why we are using a three-digit number (744) after the chmod command.

The number determines the file permissions. **R****ead**, **write**, and **execute** are represented by a **numerical value:**

-   **r** (read) – **4**
-   **w** (write) – **2**
-   **x** (execute) – **1**

So if you want to give all permissions (**rwx**) to a user, we need to add **read (4), write (2),** and **execute (1).** Therefore, **rwx** is equal to 7.

Meanwhile, since group and others are only allowed to read the file, we give them **4**.

Remember, the owner’s permissions always come first, then followed by group and others. That’s why we enter **744.** 

#### Pro Tip

If you don’t want to give any permission to a user, enter **0** into the corresponding spot.

Here is a list of the most common file permissions:

**Value**

**Numeric Value**

**Explanation**

`-rw-------`

600

Owner can read and write. Group and others have no permission.

`-rw-r--r--`

644

Owner and read and write. Group and others have read only rights.

`-rw-rw-rw-`

666

Owner, group and others can read and write.

`-rwx------`

700

Owner can read, write and execute. Group and others have no permission.

`-rwx--x--x`

711

Owner can read, write and execute. Group and others can execute.

`-rwxr-xr-x`

755

Owner can read, write and execute. Group and others can read and execute.

`-rwxrwxrwx`

777

Owner, group and others can read, write and execute.

Common permissions for directories:

**Value**

**Numeric Value**

**Explanation**

`drwx------`

700

Only owner can read and write to the directory

`drwxr-xr-x`

755

Owner, group and others can read the directory, but only the owner can write.


[[Windows]]
