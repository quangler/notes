### **Terms:**
**AAA** - Authentication, Authorization, and Accounting - common functions performed upon system login - accounting is somewhat less common
**Access Control** - Mechanism used to determine what access permissions subjects have for specific objects
**Access Control List (ACL)** - a list associated with an object that identifies what level of access each subject has - what they can do with the object (read, write, execute)
**Accounting** - collection of billing and other detailed records
**Authentication** - the process where a subject's identity is verified
**Authentication Header (AH)** - a portion of the IPsec security protocol that provides authentication services, and replay-detection ability. Can be used by itself or with Encapsulating Security Payload (ESP)
**Authentication Server (AS)** - A server used to perform authentication tasks
**Authorization** - The function of determining what is permitted for an authorized user
**Content protection** - The protection of the header and data portion of a user datagram
**Context protection** - the protection of the header of a user datagram
**Domain Controller** - a computer that responds to security authentication requests, such as logging into a computer, for a windows domain
**Domain Password Policy** - a password policy for a specific domain
**eXtensible Access Control Markup Language (XACML)** - open standard XML-based language used to describe access control
**Group** - a collection of users with some common criteria, such as a need for access to a particular dataset or group of applications
**Key Distribution Center (KDC)** - a portion of the Kerberos authentication system
**Group Policy Object (GPO)** - Stores the group policy settings in a Microsoft Active Directory environment
**Kerberos** - a network authentication protocol designed by MIT for use in client/server environments
**Single Sign-On (SSO)** - authentication process where a user can use a single user ID and password and then move from application to application without having to supply further authentication info
**Ticket-granting Server (TGS)** - a portion of the Kerberos authentication system
**Token** - a hardware device that can be used in challenge-response authentication process
**User** - any person accessing a computer system - a user is a single individual - generally lowest level addressed by privilege management - most common area for addressing access, rights, and capabilities

**Privileges** - mean you have the ability to "do something" on a computer
**Privilege Management** - is the process of restricting a user's ability to interact with the computer system
**Authentication** is the process of establishing a user's identity to enable the granting of permissions

### User, Group, and Role Management
- need to separate people into distinct entities (**users**) is required
- lumping users into **groups** is convenient and efficient
- useful to be able to grant or restrict access based on a person's job or function within the organization (**role**)
- **rights** define the actions a user can perform on the system itself
- **permissions** control what the user is allowed to do with objects on the system

### Group
a **GROUP** is a collection of users with a common criteria (need for access to a particular dataset or group of applications)
- a new user added to a group will automatically "inherit" the permissions of the group
some operating systems have built in groups
- makes assigning and managing permissions easier

### Password Policies
to help users pick strong passwords, organizations implement and enforce a **password policy**
- **Password Construction** - how many characters a password should have - what characters are allowed or forced, making sure its not a common word or a slight modification to existing password
- **Reuse Restrictions** - whether or not passwords can be reused, if so, what frequency (how many different passwords before you can repeat)
- **Duration** - minimum and maximum amount of time a password can be used before it can / must be changed
- **Protection of Passwords** - not writing down passwords, not saving passwords, not allowing automated logins, not sharing passwords with other users, etc.
- **Consequences** - associated with violation or noncompliance with the policy

### Domain Password Policy
**domain password policy** is a password policy for a specific domain
the domain password policy usually falls under a **GPO** and has several elements

### Single Sign-On
Form of authentication that involves transferring of credentials between systems
- allows user to sign in using one username and password for multiple locations
- harder to implement than vendors will tell you
1. user signs into the Single Sign-On Server
2. Single Sign-On Server then signs into the resources (user doesn't need to sign in again)

### Time of Day Restrictions
- can restrict when a user logs in, when certain resources can be accessed, etc.
- makes your system more secure to people who shouldn't be accessing it
- drawback: user cannot work outside of normal hours

### Tokens
A token is an authentication factor that is typically a physical or logical entity that the user must possess to access their account or resource.
- physical tokens display a series of numbers that changes every 30 to 90 seconds
- software tokens still provide two-factor authentication but do not require the user to have a physical device on hand

### Account and Password Expiration
- an account expiration / password expiration feature allows admins to specify a period of time for which a password or an account will be active
#### Password Expiration 
- when date is reached, the user generally is asked to create a new password
- if password has been compromised, this helps to stop attackers
#### Account Expiration
- specify the length of time an account is valid, when it "expires" the account is disabled.
	- used for temporary accounts
- organizations must define whether accounts are deleted or disabled when no longer needed
	- deleting an account removes the account from the system permanently
	- disabling an account leaves it in place but makes it unusable
- often used for people who leave an organization for more than 30 days so no one can mess around in the account

### Security Controls and Permissions (NFS vs NTFS)
most OS's use permissions and right to control access to resources
Windows uses:
- permissions and rights to control access to files, folders, and information resources (NFS)
- user rights or privileges to determine actions a user or group is allowed to perform
remember concept of least privilege (NTFS)

**NFS** - who can get to an object, **NTFS** - how they can interact with the object
#### NTFS Permissions:
- **Full Control** - can change permissions on the folder/file, take ownership, delete subfolders/files, perform actions permitted by all other NTFS folder permissions
- **Modify** - view and modify files/folders and their properties - can delete and add files/folder and can delete or add properties to a file/folder
- **Read & Execute** - view the file/folder and execute scripts and executables, but cannot make any changes (read only + use executables)
- **List folder contents** - can list only what is inside the folder (applies to folders only)
- **Read** - can view the contents of the file/folder and properties
- **Write** - can write to the file
#### User rights
- **Log on Locally** - can log on to the local system
- **Access this computer from the network** - can access this system through a network connection
- **Manage auditing and security log** - can view, modify, and delete auditing and security log info

### Change Effects of NTFS when moved or copied
by default, an object inherits permissions from its parent object, either at the time of creation or when it is copied or moved to its parent folder.
- the **only exception to this rule** is when you **move** an object to a **different folder** on the **same volume** - in this case, the original permissions are retained.
#### Copy
- copy a folder/file **within a single NTFS partition**, the copy of the folder or file **inherits the permissions of destination folder**
- copy a folder/file **to a different NTFS partition**, the copy of the folder or file **inherits the permissions of destination folder**
- copy a folder/file to a **non-NTFS partition**, copy of the folder or file **loses its NTFS permissions**, because non-NTFS partitions do not support NTFS permissions
#### Move
- ==move a folder/file **within an NTFS partition**, the folder or file **retains its original permissions**==
- move a folder/file **to a different NTFS partition**, the folder or file **inherits the permissions of the destination folder**
- move a folder/file to a **non-NTFS partition**, folder or file **loses NTFS permission**, because non-NTFS partitions do not support NTFS permissions

### Access Control Lists
used in:
- routers and firewalls: set of rules used to control traffic flow in or out of an interface / network
- system resources: an ACL lists permissions attached to an object