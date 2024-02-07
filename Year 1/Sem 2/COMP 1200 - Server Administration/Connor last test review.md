different types of backups:

- incremental and full

  

full - a backup of the whole thing

incremental - the changes since the last backups

  

several incremental backups - this creates a chain,

if you lose a link in the chain, you lose the chan.

- the whole chain is considered a backup (?)

  

backup media

- tapes

- usb drives

- NAS

- SAN

  

NAS VS SAN

- SAN - set storage array network - usually larger, takes more space and has more storage (server rack) - direct storage, running VMs and stuff

  

- NAS - network attached storage - smaller, space and storage

  

SAN - block level storage - raw data (no file system) | centralized storage

  

NAS - file level storage - own operating system, has its own file system | navigate through [\\NAS\Backup\blah](file:///\\NAS\Backup\blah) (controlled entirely by what is on the NAS)

  

**RAID is not a backup** RAID is redundancy. It protects against drives failing NOT as a backup.

  

- on site backup - part of your local network

- off site backup - a remote location, physically separate (usually geographically diverse)

  

how often should you run backups? and why?

  

- 15 minutes - SQL server with a ton of data traffic

  

- every day -

  

security of backups: physical and virtual

- encrypt everything,

- backups should have its own account

  

3, 2, 1

3 copies of your backups

2 media types - nas, or just not online

1 offsite backup

  

the offsite chain is the same as the onsite chain - but they are physically independent

  

sharepoint

- owner, can change everything including permissions

- visitor - read only

- author - can create and modify

  

sharepoint and onedrive

- sharepoint is usually more permissive than onedrive

-

  

considerations for backups:

- network usage - stagger them and/or run them after hours

  
  

**test info:**

**backup heavy**

**16 questions**

**multiple choice, true and false,**