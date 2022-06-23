(**CH**ange **MOD**e) A Unix command that changes the permissions (attributes) of a file or directory. Chmod requires an understanding of how the read-write-execute permissions are expressed. The "list long" command (**ls -l**) displays the attributes of a file or directory, and the first part of the line looks like this: **-rwxrwxrwx**. A dash or "d" as the first character means file or directory. The three sets of **rwx** are permissions for owner-group-other. For example, **-rwxrw-r--** gives all permissions to the file on the line to the owner, read/write permissions to the group and read only for the rest.

The command uses =, + and - to set, add and subtract changes to owner (u), group (g), other (o) or all (a). The following examples show the permissions of an **abc.sh** shell script after each command is executed. See [ls](https://www.pcmag.com/encyclopedia/term/ls), [shell script](https://www.pcmag.com/encyclopedia/term/shell-script), [chown](https://www.pcmag.com/encyclopedia/term/chown) and [chgrp](https://www.pcmag.com/encyclopedia/term/chgrp).

 **-rwxrwxrwx**          ALL PERMISSIONS

 chmod o= abc.sh     SET OTHER TO NONE

 **-rwxrwx---**

 chmod o+r abc.sh    ADD R TO OTHER

 **-rwxrwxr--**

 chmod a-x abc.sh    REMOVE ALL EXECUTE

 **-rw-rw-r--**

 chmod a=rwx abc.sh  SET ALL TO RWX

 **-rwxrwxrwx**

 chmod a= abc.sh     SET ALL TO NON

 **----------**

 chmod u=r abc.sh    SET OWNER TO READ

 **-r--------**

![_CHMOD.GIF](https://i.pcmag.com/imagery/encyclopedia-terms/chmod-_chmod.fit_lim.size_640x.gif)

**List Long Shows Permissions**

The list long (ls -l) command shows the permissions of files and directories (folders). The arrow points to the permissions in this macOS example.