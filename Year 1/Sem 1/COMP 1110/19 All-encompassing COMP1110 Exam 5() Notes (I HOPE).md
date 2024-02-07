"sudo yum install -y samba"

  

![Exported image](Exported%20image%2020240206202443-0.png)

**FIREWALLS:**

**"**sudo firewall-cmd --help" - helps

"sudo firewall-cmd --permanent --add-service=samba"

"firewall-cmd --reload"

  

"sudo nano /etc/samba/smb.conf"

  
  

"sudo systemctl <enable/restart> smb nmb"

  

REGEDIT:

Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Sevices\LianmanWorkstation\

Parameters\AllowInsecureGuestAuth > 1

  

"sudo yum install realmd sssd oddjob oddjob-mkhomedir adcli samba-common-tools krb5-workstation"

  

**REALM:**

  

"realm discover <domain>"

"realm join <domain>"

"realm list"

  

"sudo EDITOR=nano visudo"

  

under wheel:

%domain\ admins@<domain_name> ALL=(ALL) ALL

<"%" for groups, "\ " is for a space, "@" is for domain name

  
  

"sudo getfacl <filename>"

  

"sudo setfacl -m g:<group_name>:<rwx|---> <file-name>" - "g::" is default

  

"chmod" > sets user permissions

or

"sudo setfacl -m m::<rwx|---> <file name>"

  

"sudo setfacl -x <...>" -x for delete

  
  

CREATING PEOPLE:

  

"sudo useradd <name>"

"sudo groupadd <g-name>"

  
  

"chown <user>:<group> <directory/file>"

  

"chmod <user> <0-7(x3)> <file_name>"

  

**GETTING INTO THE SHARES:**

  

LINUX:

smbclient //<full_server_path>/<share_file> -U <user-logging in as>

^ CLI WAY ^ | v file way v

smb://<full_server_path>/<share_file>

  

WINDOWS:

[\\<full_server_path>\<file_path>](file:///\\<full_server_path>\<file_path>)

^ UNC way ^ | v map way v

[\\<full_server_path>\<file_path>](file:///\\<full_server_path>\<file_path>)

  

SELINUX = permissive or disabled

"sudo nano /etc/selinux/config"

  

"smbpasswd <username>"

  

**SMB SHARES**

  

[global]

'map to guest = bad user' - logs in windows as guest

'server role = standalone server'

'usershare allow guests = yes'

'idmap config * : backend = tbd'

  

'hosts allow = x.x.x.x'

'hosts deny = x.x.x.x'

  
  
  

[<share_name>]

'force group = <usergroup>' - forces the incoming person to be in this group

'force user = <user>' - forces the incoming person to be this user

'path = <pathname_to_share>'

'read only = no' - allows changes

' guest ok = yes' - allows guest users

'valid users = <username>'