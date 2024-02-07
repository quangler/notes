Thin provisioning : not allocating all at once, can use up to allowed amount

Thick provisioning : allocating all at once, WILL use allowed amount

  

Recap:

RAID 1 - mirroring drives

RAID 5 - multiple drives into one (data striping & parity)

- lowest common denominator for parity and striping,
- larger drives have extra left over (can be used as a span or expanded drive)

  
  

When partitioning : GUID partition table, quick format & NTFS

  

Hardware RAID: fast as hell (8 drive volume, 8x fast)

Software RAID: for learning / development of things on raid systems

  

Home Folders: - AD users and computers

- Folders that have sharing permissions and can be backed up and administered remotely
- [\\ServerName\Share\%UserName%](file:///\\ServerName\Share\%UserName%) - target for home folder, %UserName% is a placeholder for username ([\\x](file:///\\x) uses UNC or universal naming convention)
- Can select multiple users to change home folder at a time
  

  

Quotas: File Server Resource Manager Tool

- limit space allocated to a volume or folder, capacity management
- can be more or less restricted for some volumes/folders than others
- **hard quota:** cannot exceed this limit
- **soft quota:** can exceed quota - just for setting up thresholds

  

Quota Threshold:

- can be done on either hard or soft quotas,
- can be set to any percent; can be sent as an email or event log, and can activate a command, or report.

  

Admin accounts don’t have quota limits, (for moving and installing things, as well as managing)