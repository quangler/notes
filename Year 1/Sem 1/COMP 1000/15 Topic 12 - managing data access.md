Share - club door - always open, (just need access)

NTFS - bouncer - only lets SOME in, file level security

  

**Principle of Least Privilege**: (POLP)

- everything (people, programs, etc) should have the minimum amount of privilege to do what they need to do. (ex. read-only)
- this is the reason we have QuinnUser, and use "run as administrator" when needed
- better security
- minimized attack surface
    
    - the less admin mode mess-ups the better
- limit malware propagation
    
    - smaller area, user accounts can be reset, whole systems aren't so easy
- better stability
    
    - someone isn't going to accidentally delete something without realizing and mess stuff up

  

**Share permissions:** determine what type of access others have to a shared folder across a network

- can be used with NTFS, FAT, and FAT32
- **Read**
    
    - Can view file and subfolders, read data and run programs.
- **Change**
    
    - Read perms
    - add files and subfolders, change data in files, and delete files and subfolders
- **Full Control**
    
    - Read perms, Change perms
    - ability to set permissions on the share
- share perms are applied to **folder not content**
- uses a folder hierarchy.
    
    - the share folder is the what users join, and can influence inside (but cant go back a step from share folder)

  

**NTFS Permissions**

- way more specific permissions than Share Level perms
- Apply to local and network access users
- NTFS perms only on NTFS volume
- NTFS perms can apply to folder **AND/OR** **file** (share can only do folder)

  

- NTFS Access Control Entries (ACE)
    
    - Group or users of a folder/file
- NTFS Access Control List (ACL)
    
    - security tab of folder/file properties
- **Read**: user allowed to view contents, permissions, and attributes (cannot execute files)
- **Read and Execute**: can launch files (.exe, .bat, etc.) + Read perms
- **List folder contents**: allows user to view contents of a folder, but not read perms (students folder, can see the student folders but cant open them) - for auditing purposes
- **Write**: can edit the file/folder, add new files/folders **CANNOT delete files in folder**
- **Modify**: Read perms, Read & Execute, Write and **ADDS** ability to delete files and folders
- **Full Control**: all previous perms, **PLUS** ability to change permissions and take ownership of files/folders

  

- **Deny**: takes precedent over allow permissions, leaves a group or user out of ACL
- can add users to allowed groups to give them permission
- **Explicit Deny**: denies **a specific user or group** permission to something, deny perms in ACL
- can be messy in case of people being promoted/transferred & still having deny permissions

  

**Evaluating Effective Permissions:**

- user can belong to numerous groups
- multiple groups can have permissions on a single resource
- a single user can have different permissions based on groups, so it can get messy...

  

**Rules:**

- Address Share and NTFS separately
- evaluate best perms for Share
- evaluate best perms of NTFS
- Combine the lowest common denominator for effective permission.

  

Re-Signing in > generates new security token - refreshes group perms

  

**Inheritance:**

- Parent/Child relationship of permissions in folders
- Child objects of a folder inherit permissions (get the same permissions)
- to **not** do this, disable inheritance
    
    - Convert inherited permissions into explicit permission on this object - keep perms but sever ties to parent folder
    - Remove all inherited permissions from the object - resets all perms and ties to parent folder
    - careful: there could be thousands of (grand) child objects within a child folder when you disable inheritance. (have to then change a ton of perms)

**AGDLP**

Accounts > Global Groups > Domain Local Groups > Permissions

  

**Best Practices:**

- avoid nested shares
    
    - can create conflicting behavior for same network resources if accessed through different shares
- understand inherited permissions
    
    - moving files and folders can mess permissions up
- assign permissions to groups, not users
    
    - AGDLP
- Enforce the principle of least privilege
- Avoid explicitly denying permissions
    
    - makes it messy and :(
- do not set the permissions of everyone group to deny
    
    - you will lock EVERYONE out, including admins and guest accounts.
- Grant Admins group the full control permission to the parent shared folder
    
    - just makes it more work if you don't
- Keep a close eye on the membership of admin group
    
    - don't let anyone sneak in.

  

Security Considerations:

- NTFS only offers security to the volumes when a system is running
    
    - Linux distros like KALI bypasses ACLs :O
- A drive can be "slaved" in another windows system