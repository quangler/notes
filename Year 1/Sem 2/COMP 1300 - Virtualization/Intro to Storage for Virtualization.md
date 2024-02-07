Direct Attached Storage (DAS)

- block level internal storage installed within ESXi
- Block level external storage connected to ESXi host by dedicated cable
    
    - SAS (serial attached SCSI)
- local storage does not support sharing between multiple hosts

  
  

Storage Area Networks (NAS)

- block level external storage connected to the ESXi host by network (fibre channel [FC], or fibre channel over ethernet [FCoE])
- block level external storage connected to the ESXi host by IP network (iSCSI)
- Shared storage is necessary for disaster recovery, high availability, and moving VMs between hosts (for us)

  

Network Attached Storage (NAS)

- file level external storage connected to the ESXi host by IP (NFS- Network File System)
  

  

Datastore - logical storage unit that can use disk space on one or more physical devices

- Vmware vSphere VMFS
- NFS
- used to hold VM files, templates, and ISOs

  

VMFS:

- allows concurrent access to shared storage
- dynamically expandable
- on-disk, block-level locking

use VMFS datastores whenever possible:

- optimized for storing and accessing large files
- max volume size of 64TB
- can be created on DAS, FC, FCoE, and iSCSI