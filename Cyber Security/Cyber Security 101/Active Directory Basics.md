**Windows domain** is a group of users and computers under the administration of a given business. The main idea behind a domain is to centralise the administration of common components of a Windows computer network in a single repository called **Active Directory (AD)**. The server that runs the Active Directory services is known as a **Domain Controller (DC)**.

The main advantages of having a configured Windows domain are:

- **Centralised identity management:** All users across the network can be configured from Active Directory with minimum effort.
- **Managing security policies:** You can configure security policies directly from Active Directory and apply them to users and computers across the network as needed.


#### Active Directory

The core of any Windows Domain is the **Active Directory Domain Service (AD DS)**. This service acts as a catalogue that holds the information of all of the "objects" that exist on your network. Amongst the many objects supported by AD, we have users, groups, machines, printers, shares and many others.

**_Users_**

Users are one of the most common object types in Active Directory. Users are one of the objects known as **security principals**, meaning that they can be authenticated by the domain and can be assigned privileges over **resources** like files or printers. You could say that a security principal is an object that can act upon resources in the network.

Users can be used to represent two types of entities:

- **People:** users will generally represent persons in your organisation that need to access the network, like employees.
- **Services:** you can also define users to be used by services like IIS or MSSQL. Every single service requires a user to run, but service users are different from regular users as they will only have the privileges needed to run their specific service.


**_Machines_**

Machines are another type of object within Active Directory; for every computer that joins the Active Directory domain, a machine object will be created. Machines are also considered "security principals" and are assigned an account just as any regular user. This account has somewhat limited rights within the domain itself.

The machine accounts themselves are local administrators on the assigned computer, they are generally not supposed to be accessed by anyone except the computer itself, but as with any other account, if you have the password, you can use it to log in.


**_Security Groups_**

If you are familiar with Windows, you probably know that you can define user groups to assign access rights to files or other resources to entire groups instead of single users. This allows for better manageability as you can add users to an existing group, and they will automatically inherit all of the group's privileges. Security groups are also considered security principals and, therefore, can have privileges over resources on the network.

| **Security Group** | **Description**                                                                                                                                           |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Domain Admins      | Users of this group have administrative privileges over the entire domain. By default, they can administer any computer on the domain, including the DCs. |
| Server Operators   | Users in this group can administer Domain Controllers. They cannot change any administrative group memberships.                                           |
| Backup Operators   | Users in this group are allowed to access any file, ignoring their permissions. They are used to perform backups of data on computers.                    |
| Account Operators  | Users in this group can create or modify other accounts in the domain.                                                                                    |
| Domain Users       | Includes all existing user accounts in the domain.                                                                                                        |
| Domain Computers   | Includes all existing computers in the domain.                                                                                                            |
| Domain Controllers | Includes all existing DCs on the domain.                                                                                                                  |

 **Organizational Units (OUs)** are container objects that allow you to classify users and machines. OUs are mainly used to define sets of users with similar policing requirements.

**Containers automatically created by windows**
- **Builtin:** Contains default groups available to any Windows host.
- **Computers:** Any machine joining the network will be put here by default. You can move them if needed.
- **Domain Controllers:** Default OU that contains the DCs in your network.
- **Users:** Default users and groups that apply to a domain-wide context.
- **Managed Service Accounts:** Holds accounts used by services in your Windows domain.

#### Security Groups vs OUs

- **OUs** are handy for **applying policies** to users and computers, which include specific configurations that pertain to sets of users depending on their particular role in the enterprise. Remember, a user can only be a member of a single OU at a time, as it wouldn't make sense to try to apply two different sets of policies to a single user.
- **Security Groups**, on the other hand, are used to **grant permissions over resources**. For example, you will use groups if you want to allow some users to access a shared folder or network printer. A user can be a part of many groups, which is needed to grant access to multiple resources.

#### Type of devices in AD

**1. Workstations**

Workstations are one of the most common devices within an Active Directory domain. Each user in the domain will likely be logging into a workstation. This is the device they will use to do their work or normal browsing activities. These devices should never have a privileged user signed into them.  

**2. Servers**

Servers are the second most common device within an Active Directory domain. Servers are generally used to provide services to users or other servers.

**3. Domain Controllers**

Domain Controllers are the third most common device within an Active Directory domain. Domain Controllers allow you to manage the Active Directory Domain. These devices are often deemed the most sensitive devices within the network as they contain hashed passwords for all user accounts within the environment.

#### Group Policy Objects
**Group Policy Objects (GPO)**. GPOs are simply a collection of settings that can be applied to OUs. GPOs can contain policies aimed at either users or computers, allowing you to set a baseline on specific machines and identities.

**GPO distribution**
GPOs are distributed to the network via a network share called `SYSVOL`, which is stored in the DC. All users in a domain should typically have access to this share over the network to sync their GPOs periodically. The SYSVOL share points by default to the `C:\Windows\SYSVOL\sysvol\` directory on each of the DCs in our network.

Once a change has been made to any GPOs, it might take up to 2 hours for computers to catch up.

#### Authentication Method in AD

###### 1. Kerberos Authentication

 **Definition**

Kerberos is the **default and secure authentication protocol** used in modern Windows domains. It relies on **tickets** to prove identity without repeatedly sending credentials over the network.

 **Process**

1. **Initial Authentication (AS Request)**
    
    - User sends **username + timestamp**, encrypted with a key derived from their password, to the **Key Distribution Center (KDC)**.
        
    - KDC returns a **Ticket Granting Ticket (TGT)** and a **Session Key**.
        
    - TGT is encrypted with the **krbtgt account hash**.
        
2. **Service Ticket Request (TGS Request)**
    
    - User sends the **TGT**, an encrypted timestamp (using the Session Key), and the **Service Principal Name (SPN)** to the KDC.
        
    - KDC returns a **Ticket Granting Service (TGS)** and a **Service Session Key**.
        
    - TGS is encrypted using the **service account’s password hash**.
        
3. **Service Authentication**
    
    - User presents the **TGS** to the target service.
        
    - Service decrypts the TGS, validates the session key, and grants access.
        

---

###### 2. NetNTLM Authentication

**Definition**

NetNTLM is a **legacy challenge–response authentication protocol** retained mainly for backward compatibility. It does not use tickets.

**Process**

1. Client requests authentication to a server.
2. Server sends a **random challenge** to the client.
3. Client encrypts the challenge using their **NTLM password hash** and sends the response back.
4. Server forwards the challenge and response to the **Domain Controller**.
5. Domain Controller recalculates and verifies the response.
6. Authentication result is returned to the server and then to the client.

**Note:**

- Passwords or hashes are **never sent directly over the network**.
- For **local accounts**, the server validates authentication using its local SAM without contacting the Domain Controller.


#### Active Directory Domain Structures

**Single Domain**

**Definition**  
A single domain is the most basic Active Directory setup where all users, computers, and policies are managed within one administrative boundary.

**Key Points**

- One Domain Controller manages authentication and authorization
- Centralized users, computers, and Group Policies
- Suitable for small organizations
- Can become difficult to manage as the organization grows

---

**Trees**

**Definition**  
A tree is a collection of multiple domains that share the same namespace and are arranged in a hierarchical structure under a root domain.

**Structure / Process**

- Root domain (e.g., `thm.local`)
- Child domains (e.g., `uk.thm.local`, `us.thm.local`)
- Each domain has its own Domain Controllers
- Two-way trust relationships are automatically created

**Administration**

- Domain Admins control only their own domain
- Enterprise Admins control all domains in the tree

---

**Forests**

**Definition**  
A forest is a collection of one or more domain trees that use different namespaces but share a common Active Directory infrastructure.

**Key Points**

- Multiple trees with different namespaces (e.g., `thm.local`, `mht.local`) 
- Used during mergers or acquisitions
- Allows administrative separation with controlled sharing
- Highest-level Active Directory structure

---

**Trust Relationships**

**Definition**  
Trust relationships allow users from one domain to be authenticated and authorized to access resources in another domain.

**Types of Trusts**

**One-Way Trust**

- Domain A trusts Domain B
- Users from Domain B can access resources in Domain A
- Trust direction is opposite to access direction

**Two-Way Trust**

- Both domains trust each other
- Users can be authorized in both domains
- Created by default within trees and forests

**Important Notes**

- Trusts do not automatically grant access
- Access must be explicitly authorized
- Used to enable secure cross-domain resource sharing