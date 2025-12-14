#### Windows

| Command      | Description                                                     |
| ------------ | --------------------------------------------------------------- |
| set          | check your environment variables                                |
| ver          | Operating system version                                        |
| systeminfo   | show systems information                                        |
| ipconfig     | display basic network config                                    |
| ping         | send icmp packets to test connection                            |
| tracert      | trace the route of a packet                                     |
| nslookup     | It looks up a host or domain and returns its IP address.        |
| netstat      | current network connections and listening ports.                |
| dir          | List directory                                                  |
| cd           | change directory                                                |
| mkdir        | make directory                                                  |
| copy         | copy directory                                                  |
| type         | dump the content of the text file                               |
| more         | same as type but for larger text file                           |
| move         | move file to different directory                                |
| del or erase | delete file                                                     |
| tasklist     | list task running in windows                                    |
| chkdsk       | checks the filesystem and disk volumes                          |
| driverquery  | display a list of installed device driver                       |
| sfc /scannow | scans system files for corruption and repairs them if possible. |
| shutdown     | use to do shutdown, restart ... operations                      |

#### Powershell
PowerShell is a powerful tool from Microsoft designed for task automation and configuration management. It combines a command-line interface and a scripting language built on the .NET framework. Unlike older text-based command-line tools, PowerShell is object-oriented, which means it can handle complex data types and interact with system components more effectively. Initially exclusive to Windows, PowerShell has lately expanded to support macOS and Linux, making it a versatile option for IT professionals across different operating systems.

An object in PowerShell can contain file names, usernames or sizes as data (**properties**), and carry functions (**methods**) such as copying a file or stopping a process.
The traditional Command Shell’s basic commands are text-based, meaning they process and output data as plain text. Instead, when a **cmdlet** (pronounced _command-let_) is run in PowerShell, it returns objects that retain their properties and methods. This allows for more powerful and flexible data manipulation since these objects do not require additional parsing of text.

Cmdlets follow a consistent `Verb-Noun` naming convention. This structure makes it easy to understand what each cmdlet does. The `Verb` describes the action, and the `Noun` specifies the object on which action is performed.

| Command                | Description                                                                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Get-Command            | ool for discovering what commands one can use.                                                                                                         |
| Get-Content            | Retrieves (gets) the content of a file and displays it in the console.                                                                                 |
| Set-Location           | Changes (sets) the current working directory.                                                                                                          |
| Get-Help               | Gwt Help of specific command                                                                                                                           |
| Get-Alias              | All shortcut and alternate name (aliases) for cmdlets                                                                                                  |
| Get-ChildItem          | List directory                                                                                                                                         |
| Find-Module            | find the list of modules that can be downloaded                                                                                                        |
| Install-Module         | install a specific powershell module                                                                                                                   |
| Write-Output           | Same as echo                                                                                                                                           |
| New-Item               | It can create new files and directory                                                                                                                  |
| Remove-Item            | remove files and directories                                                                                                                           |
| Copy-Item              | Copy file or directory form one place to another                                                                                                       |
| Move-Item              | Move file from one place to another                                                                                                                    |
| Where-Object           | filter objects based on specific conditions                                                                                                            |
| Select-Object          | Select specific property from object to display                                                                                                        |
| Select-String          | Select Specific string from file                                                                                                                       |
| Get-ComputerInfo       | used to display computer information                                                                                                                   |
| Get-LocalUser          | list all the local user account on the system                                                                                                          |
| Get-NetIPConfiguration | Provides detailed information about the network interfaces on the system, including IP addresses, DNS servers, and gateway configurations.             |
| Get-Processes          | Details of all current and running process                                                                                                             |
| Get-Service            | information about the status of services on the machine                                                                                                |
| Get-NetTCPConnection   | Display current TCP connection                                                                                                                         |
| Get-FileHash           | generate file hash or get the hash of a file                                                                                                           |
| Invoke-Command         | It is essential for executing commands on remote systems, making it fundamental for system administrators, security engineers and penetration testers. |


#### Linux
| Command | Description                                          |
| ------- | ---------------------------------------------------- |
| ls      | Lists files and directories in the current directory |
| cd      | Changes the current directory                        |
| pwd     | Displays the full path of the current directory      |
| mkdir   | Creates a new directory                              |
| rmdir   | Deletes an empty directory                           |
| rm      | Removes files or directories                         |
| cp      | Copies files or directories                          |
| mv      | Moves or renames files or directories                |
| touch   | Creates an empty file or updates a file timestamp    |
| cat     | Displays the contents of a file                      |
| less    | Views file contents one page at a time               |
| head    | Shows the first few lines of a file                  |
| tail    | Shows the last few lines of a file                   |
| echo    | Prints text or variables to the terminal             |
| man     | Displays the manual page for a command               |
| clear   | Clears the terminal screen                           |
| whoami  | Displays the current logged-in user                  |
| uname   | Shows system information                             |
| df      | Displays disk space usage                            |
| du      | Shows file or directory size                         |
| free    | Displays memory usage                                |
| top     | Shows running processes and system usage             |
| ps      | Displays running processes                           |
| kill    | Terminates a running process                         |
| chmod   | Changes file or directory permissions                |
| chown   | Changes file or directory ownership                  |
| find    | Searches for files and directories                   |
| grep    | Searches text for matching patterns                  |
| wget    | Downloads files from the internet                    |
| curl    | Transfers data from or to a server                   |
| tar     | Creates or extracts archive files                    |
| zip     | Compresses files into a ZIP archive                  |
| unzip   | Extracts ZIP archive files                           |
###### **Linux Shells Overview**

Linux provides multiple shell environments, similar to Command Prompt and PowerShell in Windows. Each shell has unique features and usage styles. Different Linux distributions may include different shells by default.

###### **Bourne Again Shell (Bash)**

**Description:**  
Bash is the default shell for most Linux distributions and an enhanced replacement for older shells like `sh`, `ksh`, and `csh`.

**Key Features:**

- Widely used shell with strong scripting support
- Tab completion for commands and file names
- Command history with arrow key navigation    
- Stores command history and supports the `history` command

###### **Friendly Interactive Shell (Fish)**

**Description:**  
Fish focuses on simplicity and user-friendliness, making it ideal for beginners.

**Key Features:**

- Simple and readable syntax
- Auto spell correction for commands
- Built-in syntax highlighting
- Customizable prompt with themes    
- Supports scripting, tab completion, and command history

###### **Z Shell (Zsh)**

**Description:**  
Zsh is a modern shell combining features from multiple shells with advanced customization options.

**Key Features:**

- Advanced and extendable tab completion
- Auto spell correction
- Strong scripting capabilities
- Highly customizable using frameworks like **oh-my-zsh**    
- Supports command history and plugins

###### Shell Scripting

**Comments**  
**Syntax:** `# This is a comment`  

**Example:**
`# This script prints a message echo "Hello, World!"`

**Variables**  
**Syntax (Assign):** `variable_name=value`  
**Syntax (Input):** `read variable_name`  
**Example:**
`echo "Enter your name:" read name echo "Hello, $name"`

**Conditional Statements (if)**  
**Syntax:**
`if [ condition ]; then   commands fi`

**Example:**
`num=10 if [ $num -gt 5 ]; then   echo "Number is greater than 5" fi`

**Loops (for loop)**  
**Syntax:**
`for variable in list; do   commands done`

**Example:**
`for i in 1 2 3; do   echo $i done`

**Loops (while loop)**  
**Syntax:**
`while [ condition ]; do   commands done`

**Example:**
`count=1 while [ $count -le 3 ]; do   echo $count   count=$((count+1)) done`