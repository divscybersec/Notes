Linux is a free, open-source operating system based on the Linux kernel, used to run computers, servers, and devices, known for its security, stability, and flexibility.

| Command | Description                                                                   |
| ------- | ----------------------------------------------------------------------------- |
| echo    | Output any text that we provide                                               |
| whoami  | Find out what user we're currently logged in as!                              |
| ls      | listing                                                                       |
| cd      | change directory                                                              |
| cat     | concatenate                                                                   |
| pwd     | print working directory                                                       |
| find    | it is used to find specific file                                              |
| grep    | The `grep` command allows us to search the contents of files.                 |
| wget    | Used to download file from internet                                           |
| ssh     | Secure Shell or SSH simply is a protocol between devices in an encrypted form |
| scp     | copy file from remote to source or from source to remote                      |
| ps      | list of running process                                                       |
| kill    | kill a process                                                                |

| Command | Full Name      | Purpose                      |
| ------- | -------------- | ---------------------------- |
| touch   | touch          | Create file                  |
| mkdir   | make directory | Create a folder              |
| cp      | copy           | Copy a file or folder        |
| mv      | move           | Move a file or folder        |
| rm      | remove         | Remove a file or folder      |
| file    | file           | Determine the type of a file |

| Symbol / Operator | Description                                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| &                 | This operator allows you to run commands in the background of your terminal.                                                                     |
| &&                | This operator allows you to combine multiple commands together in one line of your terminal.                                                     |
| >                 | This operator is a redirector - meaning that we can take the output from a command (such as using cat to output a file) and direct it elsewhere. |
| >>                | This operator does the same function of the `>` operator but appends the output rather than replacing (meaning nothing is overwritten).          |

#### Linux file structure

|Directory|Name / Stands For|Purpose / What It Contains|
|---|---|---|
|`/`|Root directory|Top of the directory tree; everything starts here.|
|`/bin`|Binaries|Essential user command binaries (e.g., `ls`, `cp`, `mv`).|
|`/boot`|Boot files|Kernel, initrd, and bootloader files (e.g., GRUB).|
|`/dev`|Devices|Device files for hardware (e.g., `/dev/sda`, `/dev/tty`).|
|`/etc`|Etcetera (config)|System-wide configuration files.|
|`/home`|Home directories|Personal directories for users.|
|`/lib`|Libraries|Essential shared libraries needed by `/bin` and `/sbin` programs.|
|`/lib64`|64-bit libraries|64-bit versions of essential libraries.|
|`/media`|Removable media|Mount points for USB drives, CDs, etc.|
|`/mnt`|Temporary mount|Temporary mount point for filesystems.|
|`/opt`|Optional|Optional or add-on application software packages.|
|`/proc`|Processes|Virtual filesystem with process and kernel info.|
|`/root`|Root user home|Home directory for the root user.|
|`/run`|Runtime data|System boot/runtime variable data (since newer FHS versions).|
|`/sbin`|System binaries|System binaries for administration (e.g., `mount`, `shutdown`).|
|`/srv`|Service data|Data used by system services (e.g., web servers).|
|`/sys`|System info|Virtual filesystem about system devices & kernel.|
|`/tmp`|Temporary files|Temporary files cleared on reboot (usually).|
|`/usr`|User system resources|Secondary hierarchy for user programs and data.|
|`/usr/bin`|User binaries|Non-essential but frequently used command binaries.|
|`/usr/sbin`|User system binaries|Non-essential system admin binaries.|
|`/usr/lib`|User libraries|Libraries for `/usr/bin` and `/usr/sbin` programs.|
|`/usr/local`|Local user programs|Locally compiled or installed software.|
|`/var`|Variable data|Logs, caches, spool files, databases, etc.|
|`/var/log`|Log files|System and application logs.|
|`/var/tmp`|Longer-term temp|Temporary files preserved between reboots.|

#### Linux permission , users and groups

##### **1. Linux Permissions**

Linux uses a permission system to control **who can access or modify files and directories**.

###### **Permission Types**

| Symbol | Numeric | Meaning                                    |
| ------ | ------- | ------------------------------------------ |
| **r**  | 4       | Read file / list directory                 |
| **w**  | 2       | Write file / add-delete files in directory |
| **x**  | 1       | Execute file / enter directory             |

#### **2. Linux Users**

Linux is a multi-user system, meaning multiple users can exist and operate on the system.

##### **Types of Users**

| User             | Description                                        |
| ---------------- | -------------------------------------------------- |
| **Root**         | Superuser with full control of system.             |
| **Normal User**  | Limited permissions; non-admin.                    |
| **System Users** | Created by services or daemons (e.g., `www-data`). |

#### **3. Linux Groups**

Groups allow multiple users to share permissions.

##### **Types of Groups**

| Type                 | Description                                    |
| -------------------- | ---------------------------------------------- |
| **Primary group**    | Assigned when user is created; owns new files. |
| **Secondary groups** | Additional membership for shared access.       |
