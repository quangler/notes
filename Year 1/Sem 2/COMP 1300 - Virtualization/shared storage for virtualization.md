shared storage:

- disaster recovery (required)
- high availability (required)
- moving VMs between hosts
  

  

iSCSI target must be configured with storage that it will provide to iSCSI initiators (ESXi hosts)

  

iSCSI target:

- install disks and configure RAID (optional)
- create block disk based on above
- create iSCSI target (IQN)
- create iSCSI Logical Unit Number (LUN)
- create iSCSI Access Control List (ACL)

  

using the ESXi web interface or vCenter:

- add iSCSI software adapter in storage adapters page
- add iSCSI target dynamically by specifying the IP address
- create a new datastore on the iSCSI target

  

iSCSI server is first to start and last to stop #important

  

in vSphere Client (192.168.91.50)

- click on ESXi server
- ~~datastores~~
- storage adapters (in configure - yes)
- add iSCSI storage adapter
- select > properties > edit > iqn.1998-01.com.vmware:esxi01
- do it for both guys

  

- dynamic discovery
- enter the IP address of your iSCSI server (192.168.91.200) (port 3260)

  

- setup the datastore AFTER you setup iSCSI