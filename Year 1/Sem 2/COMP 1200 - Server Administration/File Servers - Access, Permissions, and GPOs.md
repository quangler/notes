File server - main job is to host files, can do other but usually doesn't

- centralizes important data (makes it easier to backup/restore)
- multiple servers can work together using DFS (distributed file services)

  

File Server set up:

- Folders are shared to the company
- usually one per department, and a public share for everyone.
- possibly other shares for utils/apps

  

Best Practices:

- dedicated hard drive on the server for shares (not on C:\ drive)
- top level folders for each use case (E:\Shares\whatever)
- keep names short (256 character limit for share path)

  

Don't do:

- if putting shares on C:\ drive - could lose OS, would lose all data on it (shares)
- make specific top level folders on the drive (E:\Data\whatever is better than just E:\whatever, scalability and what not.)
- DON'T SHARE E:\ - this is a root directory, and bad to share

  

Permissions:

- limit data using share and NTFS permissions
- permissions are inherited
- more restrictive >>>

  

Drive Mapping:

- use a drive map to make a drive that is of [\\Accounting\FolderName\Number1](file:///\\Accounting\FolderName\Number1) for example
- it can be done manually, but is annoying
- use GPOs as best practice - auto maps drives (can do it based on membership)
- location of GPO will determine who gets affected
- affects user accounts
  

  

Drive Map Options:

- action: sets behaviour
- Location - share path of share
- Label
- Specific drive letter - N:\, P:\ (network, public) are common
- Could also set every department drive to be set to E:\ for example, (this is kinda messy, don't do it) - called item level targeting

  

Roaming Profiles:

- for users logging into many PCs (gives settings and files and preferences)
- roaming profile basically follows user between PCs
- usually used today for configuration and settings rather than data
- "Roaming Profiles" are the old way of doing it.

  

new way:

  

Folder Redirection:

- auto copies files/folder from local PC to File Server
- saves data in case of drive failure
- copies of their data are made available at any workstation for a user
- if you redirect %appdata% you can mimic roaming folders (settings and configs)

  

Folder Redirection setup:

- use different top level share on root, which is hidden (E:\Users$ or E:\Folder Redirection$ as example)
- new security group to have permissions for redirection
- GPO to apply redirection for those users
- Setup folder under Folder Redirection Share (E:\UserData$\qparent1 as ex.)
- permissions for the hidden shares are automatically setup for privacy

  

File permissions are on the File Server

GPOs are on the DC