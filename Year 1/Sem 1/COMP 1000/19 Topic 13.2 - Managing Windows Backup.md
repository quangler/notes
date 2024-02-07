Why backup?

- data integrity
    
    - corrupt files
    - deleted files
- archival data
    
    - not using but need
        
        - historical reasons - (health records | 11, 20, 30 years)
        - legal reasons - (taxes | 6 years)
        - to cover your butt

  

Creating backup drive:

-add a new drive

-bring it online

-initialize

-convert to dynamic

  

-install windows backup feature (server manager - DC2)

- full server should make a backup enough to fully restore the server -> once a month
- data only -> daily/hourly

  

you need to leave system group in stuff for backups

  

select drive you want for backup

-will format the drive so it doesn't accept normal data (only backups)

- this will not assign a drive letter

  

You can do a backup whenever, or setup a backup schedule

-important to test backups

- move a folder to a different volume
- then go to data recovery
- look for specific date - when did they last have it
- can restore just files/folders or a whole volume (ex. C:)

folders are better to do than volume, since volume includes windows settings (no merge, just an overwrite)

- after the folder has been recovered, check permissions/share

  

Full backups

- advantages:
    
    - fast data recovery in case of disaster
    - better storage management (whole data set is stored in single backup file)
- disadvantages:
    
    - backup routine takes a long time
    - need a large capacity storage to store full backups
      
    

  

Incremental Backup

  

- advantages:
    
    - backup jobs run at high speed; only increments are backed up
    - less storage is needed
    - can be run as often as you want
- disadvantages
    
    - slow restore; have to restore full backup, then the incremental backups
    - if one part of incremental data is corrupt, can't recover successfully

Storage Media

- magnetic tape - linear tape-open (LTO) (current version is LTO8)
    
    - offline data for hardcore resets (basically a vhs of data)
    - can store up to 30TB compressed data (12TB non compressed)
    - LTO tape drives - single or libraries
        
        - works like a jukebox, pulls a tape out, then reads/writes from/to tapes
- on-prem drives - Network Attached Storage (NAS)
    
    - residential/small office/home office
    - enterprise
        
        - usually high capacity, high speed storage attached directly to the LAN
- off-prem drives (not Cloud) - (can't have student or medical files outside of province)
    
    - co-locates
    - another office in your company
    - basically renting space in an actual data center (locally, like in edmonton for ex)
- cloud
    
    - can be a backup from the onsite NAS,
    -