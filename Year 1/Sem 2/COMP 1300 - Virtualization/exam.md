windows 22 server - call it **YOURFIRSTNAMEHV01**

8gb of ram

NIC on NAT

  

C:\ISO directory > put tiny 10 ISO in there

  

C:\Examfiles\VHDs

C:\Examfiles\VMs

C:\Examfiles\Export

  

checkpoints:

- snapshots
- right click vm and click checkpoint
- to go back, right click the checkpoint and click apply

  

creating a vm from an existing VHD:

- when going through creation wizard store on local drive (should only be this one)
- make sure **use an existing hard disk** option is selected and that you point it to the VHD

  

exporting / importing vms:

exporting:

- right click created vm and click export
- send it to C:\Examfiles\Export

  

you can now delete your vm

  

importing:

- click the "import virtual machine..." option on right side
- find the VM
- start it up ! its working!

  

backup and restoring vms:

backup:

- add another drive then bring it up (call it backup)
- install windows server backup feature on the Hyper-V Server
- open up windows backup
- click "backup once" on right side (WHILE VM IS RUNNING)

  

- different options
- custom
- add items
- expand hyper-v and select the VM
- select local drives then click on backup

  

can now delete the VM

  

restoring:

- windows server backup - **recover** on right side
- this server
- pick the date of the backup
- hyper-v
- select the VM
- recover to original location
- recover

  

vm should be working again

  
  

**performance monitoring VMs**

- open up performance monitor on Hyper-V server
- under monitoring tools > performance monitor - **hit the plus sign**
- these are all the different counters to track stuff
- Hyper-V has its own set of network monitoring things