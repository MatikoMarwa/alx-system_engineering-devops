| Resources |
| ----------- |
| Read |
| [Permissions](http://linuxcommand.org/lc3_lts0090.php) |
| `man` or `help` |
| - [`chmod`](https://www.computerhope.com/unix/uchmod.htm): The command name chmod stands for "change mode." It restricts the way a file can be accessed. |
| - [`sudo`](https://www.computerhope.com/unix/sudo.htm): The sudo command ("superuser do") allows a user with proper permissions to execute a command as another user. |
| - [`su`](https://www.computerhope.com/unix/usu.htm): the su command changes the current user ID to that of the superuser, or another specified user. |
| - [`chown`](https://www.computerhope.com/unix/uchown.htm): The chown command changes ownership of files and directories in a filesystem. |
| - [`chgrp`](https://www.computerhope.com/unix/uchgrp.htm): The chgrp command changes the group ownership of a file or files. |
| - [`id`](https://www.computerhope.com/jargon/u/username.htm): In general, an ID is an abbreviation for identification. Identification is the act of being identified so a system can verify whom you say you are. |
| - [`whoami`](https://www.computerhope.com/unix/whoami.htm): The whoami command prints the effective user ID. |
| - [`groups`](https://www.computerhope.com/jargon/g/group.htm) |
| - [`adduser`](https://www.computerhope.com/unix/adduser.htm): The adduser command creates a new user. |
| - [`useradd`](): The useradd command creates a new user or sets the default information for new users. |
| - [`addgroup`](https://www.computerhope.com/unix/adduser.htm): The adduser command creates a new group. |
|  |

---

### Permissions
#### File Permissions

On a Linux system, each file and directory is assigned access rights for the owner of the file, the members of a group of related users, and everybody else. Rights can be assigned to read a file, to write a file, and to execute a file (i.e., run the file as a program).

To see the permission settings for a file, we can use the ls command.

![File permissions](http://linuxcommand.org/images/file_permissions.png)

| **Value** | **Meaning** |
| ----------- | ----------- |
| **777** | **(rwxrwxrwx)** No restrictions on permissions. Anybody may do anything. Generally not a desirable setting. |
| **755** | **(rwxr-xr-x)** The file's owner may read, write, and execute the file. All others may read and execute the file.|
| **700** | **(rwx------)** The file's owner may read, write, and execute the file. Nobody else has any rights. |
| **666** | **(rw-rw-rw-)** All users may read and write the file. |
| **644** | **(rw-r--r--)** The owner may read and write a file, while all others may only read the file. |
| **600** | **(rw-------)** The owner may read and write a file. All others have no rights. |

###### Representing the sets of permissions as a single number

It is easy to think of the permission settings as a series of bits.
```
rwx rwx rwx = 111 111 111
rw- rw- rw- = 110 110 110
rwx --- --- = 111 000 000

and so on...

rwx = 111 in binary = 7
rw- = 110 in binary = 6
r-x = 101 in binary = 5
r-- = 100 in binary = 4
```
