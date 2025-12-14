On NTFS ( New Technology File System ) volumes, you can set permissions that grant or deny access to files and folders.

The permissions are:

- **Full control**
- **Modify**
- **Read & Execute**
- **List folder contents**
- **Read**
- **Write**

#### ADS
Alternate Data Streams  (ADS) is a file attribute specific to Windows  NTFS  (New Technology File System).

Every file has at least one data stream ( `$DATA` ), and ADS allows files to contain more than one stream of data. Natively [Window Explorer](https://support.microsoft.com/en-us/windows/what-s-changed-in-file-explorer-ef370130-1cca-9dc5-e0df-2f7416fe1cb1) doesn't display ADS to the user. There are 3rd party executables that can be used to view this data, [PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.1) also gives you the ability to view ADS for files.

#### Environment Variables
" _Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders_ ".

#### Account
User accounts can be one of two types on a typical local Windows system: **Administrator** & **Standard User**. 

The user account type will determine what actions the user can perform on that specific Windows system. 

- An Administrator can make changes to the system: add users, delete users, modify groups, modify settings on the system, etc. 
- A Standard User can only make changes to folders/files attributed to the user & can't perform system-level changes, such as install programs.

Use Local User and Group Management (lusrmgr.msc) to find users and group info  

#### System Configuration
The **System Configuration** utility (`MSConfig`) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues.

The utility has five tabs across the top.
1. General
2. Boot
3. Services
4. Startup
5. Tools

#### Computer Management.

 **Task Scheduler**
A task can run an application, a script, etc., and tasks can be configured to run at any point. A task can run at log in or at log off. Tasks can also be configured to run on a specific schedule.

**Event Viewer**
Event Viewer allows us to view events that have occurred on the computer. These records of events can be seen as an audit trail that can be used to understand the activity of the computer system. This information is often used to diagnose problems and investigate actions executed on the system.

Event Viewer has three panes.

1. The pane on the left provides a hierarchical tree listing of the event log providers. (as shown in the image above)
2. The pane in the middle will display a general overview and summary of the events specific to a selected provider.
3. The pane on the right is the actions pane.

**Shared Folders** is where you will see a complete list of shares and folders shared that others can connect to.

Under **Sessions**, you will see a list of users who are currently connected to the shares. In this VM, you won't see anybody connected to the shares.

In **Performance**, you'll see a utility called **Performance Monitor**. is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote.

The **Local Users and Groups** use to view user and groups details.

**Storage**
Under Storage is **Windows Server Backup** and **Disk Management**. We'll only look at Disk Management in this room.

Disk Management is a system utility in Windows that enables you to perform advanced storage tasks.  Some tasks are:

- Set up a new drive
- Extend a partition
- Shrink a partition
- Assign or change a drive letter (ex. E:)

**Services and Applications**
A service is a special type of application that runs in the background. You can see all the services and their statuses by clicking the Services button given under the Services and Applications section.

WMI Control configures and controls the **Windows Management Instrumentation** (WMI) service.
"_WMI allows scripting languages (such as VBScript or Windows PowerShell) to manage Microsoft Windows personal computers and servers, both locally and remotely. Microsoft also provides a command-line interface to WMI called Windows Management Instrumentation Command-line (WMIC)._"

#### System Information
Windows includes a tool called Microsoft System Information (Msinfo32.exe).  This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues.

The  information in **System Summary** is divided into three sections:

- **Hardware Resources**
- **Components**
- **Software Environment**


#### Windows Registry
The **Windows Registry** (per Microsoft) is a central hierarchical database used to store information necessary to configure the system for one or more users, applications, and hardware devices.

The registry contains information that Windows continually references during operation, such as:

- Profiles for each user
- Applications installed on the computer and the types of documents that each can create
- Property sheet settings for folders and application icons
- What hardware exists on the system
- The ports that are being used.

#### Resource Monitor
Resource Monitor displays per-process and aggregate CPU, memory, disk, and network usage information, in addition to providing details about which processes are using individual file handles and modules. Advanced filtering allows users to isolate the data related to one or more processes (either applications or services), start, stop, pause, and resume services, and close unresponsive applications from the user interface. It also includes a process analysis feature that can help identify deadlocked processes and file locking conflicts so that the user can attempt to resolve the conflict instead of closing an application and potentially losing data.

In the Overview tab, Resmon has four sections:

- **CPU**
- **Disk**
- **Network**
- **Memory**

#### Command Prompt
**CMD Prompt** (often called **Command Prompt**) is a built-in command-line interface in **Windows** that lets you type text commands to control the computer instead of using the graphical interface.

Basic cmd list :
1. `dir`: Lists files and directories in the current directory.  
2. `cd`: Changes the current directory.  
3. `md`: Creates a new directory.  
4. `rd`: Removes (deletes) a directory.  
5. `copy`: Copies files.  
6. `del`: Deletes files.  
7. `ren`: Renames files.  
8. `type`: Displays the content of a text file.  
9. `edit`: Opens a simple text editor.  
10. `format`: Formats a disk or a diskette.  
11. `chkdsk`: Checks a disk for errors.  
12. `tree`: Displays a graphical representation of the directory structure.  
13. `attrib`: Displays or changes file attributes.  
14. `ping`: Sends ICMP Echo Request packets to test network connectivity.  
15. `ipconfig`: Displays IP configuration information.  
16. `net`: Manages network resources.  
17. `mode`: Configures system devices.  
18. `date`: Displays or sets the system date.  
19. `time`: Displays or sets the system time.  
20. `set`: Displays, sets, or removes environment variables.  
21. `tasklist`: Displays a list of currently running tasks.  
22. `taskkill`: Terminates one or more running tasks.  
23. `fc`: Compares two files or sets of files.  
24. `help`: Displays help information for commands.  
25. `exit`: Exits the Command Prompt.


#### Firewall
Traffic flows into and out of devices via what we call ports. A firewall is what controls what is - and more importantly isn't - allowed to pass through those ports. You can think of it like a security guard standing at the door, checking the ID of everything that tries to enter or exit.

Windows Firewall offers three firewall profiles: domain, private and public.

- **Domain** - The domain profile applies to networks where the host system can authenticate to a domain controller. 
- **Private** - The private profile is a user-assigned profile and is used to designate private or home networks.
- **Public** - The default profile is the public profile, used to designate public networks such as Wi-Fi hotspots at coffee shops, airports, and other locations.

#### TMP

Trusted Platform Module (TPM) technology is designed to provide hardware-based, security-related functions. A TPM chip is a secure crypto-processor that is designed to carry out cryptographic operations. The chip includes multiple physical security mechanisms to make it tamper-resistant, and malicious software is unable to tamper with the security functions of the TPM

#### Bitlocker

BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers

BitLocker provides the most protection when used with a Trusted Platform Module (TPM) version 1.2 or later. The TPM is a hardware component installed in many newer computers by the computer manufacturers. It works with BitLocker to help protect user data and to ensure that a computer has not been tampered with while the system was offline

#### VSS
Volume Shadow Copy Service (VSS) coordinates the required actions to create a consistent shadow copy (also known as a snapshot or a point-in-time copy) of the data that is to be backed up. 

Volume Shadow Copies are stored on the System Volume Information folder on each drive that has protection enabled.  

If VSS is enabled (**System Protection** turned on), you can perform the following tasks from within **advanced system settings**. 

- **Create a restore point**
- **Perform system restore**
- **Configure restore settings**
- **Delete restore points**

