Server Message Block (SMB) - standard file sharing protocol for windows

SAMBA - package that allows a linux machine to access and host Server Message Block (SMB) shares

The client is installed by default usually - basically no configuration

'sudo yum install -y samba' #remember-for-later

  

SAMBA Client:

GUI way:

files>other locations "**smb://**192.168.1.1/share"

CLI way:

'==smbclient //192.168.1.1/share -U u1==' - specified logging in user u1

to add a file:

'put Desktop/e3mark e3mark' #remember-for-later

  

SAMBA server:

config location > ==/etc/samba/smb.conf==

comes with default configs that require configuration

to add a basic share: create a new empty file with the same name (you can rename original one)

  

[global] - global settings

map to guest = bad user | if they dont have an account, give them a guest user

server role = standalone server | no domain controllers

usershare allow guests = yes | allow unauthenticated users (fix later)

idmap config * : backend = tdb | dont talk about much, sets id numbers to files (sets an "owner)

hosts allow = 192.168.91.0/24 | ACL that only allows connections to this subnet

  

SAMBA Shares:

between [ ] is the share name

  

[linuxshare]

force group = group1 | all objects created will be owned by the same user

force user = user1 | and group (the user and group must be created)

guest ok = yes | allow anonymous users (no username/password needed)

path = /tmp/sharelinux | **actual location of directory** doesnt need to match, however the directory must exist

read only = no | allows users to make changes (basically writable = yes)

  

SAMBA Services

- two services/daemons with SAMBA
    
    - smb
    - nmb
        
        - testparm - checks config file syntax
- still gotta stop/disable firewalls
- also need to disable SELinux (security policy)
    
    - >==/etc/selinux/conf==
        
        - '==SELINUX=disabled==' (at bottom)