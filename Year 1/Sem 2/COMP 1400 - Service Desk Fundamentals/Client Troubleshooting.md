Important locations:

C:\

- main install drive for windows
- default subdivided into folders
- Admin shares created on all volumes
    
    - [\\<systemname>\c$](file:///\\<systemname>\c$) - c drive
    - [\\<systemname>\e$](file:///\\<systemname>\e$) - e drive

  

C:\Windows\System32

- critical windows utilities that are built in to windows
- ex. task manager, file explorer
- **drivers and registry files are stored here**
- **common for malware to try and install itself here**
  

  

**Windows Registry**

- database that stores low-level settings for windows OS (info, settings, options, values for both hardware and software)
- keys can be exported to back them up as a .REG file
- edited via Reg Edit or command line
- can also be modified by group policy
- corruptions usually mean gg to something

made up of keys, subkeys, and values

HKEY_LOCAL_MACHINE or HKLM

HKEY_CURRENT_USER or HKCU

^ those are the two main ones

values are stored inside a key

- usually a string or DWORD (1 or 0 usually)

  

cant really know all of reg edit > just google that shit bro :)

  

REG cmd prompts

reg delete

reg query

reg save

  

**Windows 10 Reset**

**Refresh** - refresh windows without deleting any personal files or apps - third party apps will be deleted

**Reset** - will remove everything and reinstall windows

**Restore** - can roll your PC back to an earlier point

- good if its a recent install that has broken something
- restore points are made automatically with software/update installs if the most recent restore point is more than 7 days
- also can be made manually

Settings > change PC settings > update recovery > recovery

  

**Built in repair utility that provides a ton of functionality:**

- automatic repair
- reset to factory
- system image recovery
- boot to safe mode - boots with minimal amount of drivers just to start the machine
- cmd and other command line tools
  

  

desktop and server

creates recovery partition on setup

fail boot 3 times > recovery mode

  

**Safe Mode**

- the most basic state of windows - limited files and drivers
- can optionally be launched with networking
- can reboot as safemode

  

**DISM** - Deployment Imaging Servicing and Management (run first)

- service and management for running windows files, images and VHDs
- connects to windows update source to reference and fix system files

**SFC** - System File Checker (run second)

- compares protected system files against local cache
- may run this if safe mode is required
  

  

**App Installation**

- C:\Program Files -
- C:\Program Files (x86) - both need admin rights
- C:\ProgramData
- C:\Users\<USERNAME>\Appdata - installs only for single user, doesn't need admin rights
  

  

Program Files - default install location for 64bit applications

Program Files (x86) - only created on 64bit systems, used for backwards compatibility for 32bit applications

- only admins can make changes to these folders

  

ProgramData - hidden by default

- less restrictive permissions than Program Files - can be edited by **any** user

  

Appdata - folders created for each user, contain user-specific settings or data

- user can see only their own appdata folders (%appdata%)
- 3 subfolders:

roaming - holds settings for different computers￼local - wont follow user between pcs

LocalLow - low level data - temp files, web cache etc.

  

  

**Preventative Maintenance**

- stopping issues before they happen, can apply to any system
  
- antivirus, patching, firewall settings
- password policy
- regular backups
  

  
  

**Best Practices:**

- keep OS up to date
- install anti-virus software
- install and configure personal firewall (windows firewall)
- install and configure anti-spyware programs (included with most anti-virus software)
- keep apps and software up to date
- dont open virus and shit
- follow secure password policies (complex good !)
- follow best practices for user account security (user, escalate if needed)
- configure system restore points
- perform regular backups
- turn off / restart pc regularly

  

**Vendor Drivers**

- most large vendors (Dell, Lenovo, HP, etc.) provide a utility that can automatically check for updates and drivers.
- allows auto bios and driver updates for system
- can and will restart your shit whenever because they can >:)