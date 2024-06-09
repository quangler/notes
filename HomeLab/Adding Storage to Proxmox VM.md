1. Click on selected VM, then `Hardware`  
2. Under `Add` click `Hard Disk`  
  ![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609144418.png)  
3. Set `Storage` to `thinpool`  
4. Set disk size  
5. Click `Add` at bottom right  
  ![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609144558.png)  

## Linux adding the storage to the VM  
1. check to see if the drive was added by using the command:  
	`sudo fdisk -l` - this will display all partitions  
  ![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609162910.png)  
The drive in this case was created at 6TB and is identified as `/dev/sdb`  

### Creating a logical volume  
Using the following commands you can make this drive have a logical volume that can be used to store things on.  
1. `sudo pvcreate <path>` in this case: `sudo pvcreate /dev/sdb`  
This creates the physical volume under `/dev/sdb`  
  ![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609171241.png)  
2. `sudo vgcreate <name> <path>` in this case: `sudo vgcreate storageVG /dev/sdb`  
This creates a volume group called `storageVG` that contains the physical volume, you can add many physical disks to this  
  ![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609171344.png)  
3. `sudo lvcreate -l 100%FREE -n <name> <name of volume group>` in this case: `sudo lvcreate -l 100%FREE -n storageLV storageVG`  
This creates a logical volume called `storageLV` that has 100% of its space allocated so that it can be used for storage.  
  ![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609171400.png)  

### Giving it a file system and mounting it  
Now we have to give the logical volume a filesystem that we can use. To do this we will use the following command:  
`sudo mkfs.ext4 /dev/<VG name>/<LV name>` in this case: `sudo mkfs.ext4 /dev/storageVG/storageLV`.  
  ![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609171550.png)  
Now that there is a file system, we can mount it to a mount point by doing the following commands:  
`sudo mkdir /mnt/data` - this is the mount point we will be using  
  ![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609171621.png)  
`sudo nano /etc/fstab` -> in this file we want to write this out at the bottom of the file:  
`/dev/storageVG/storageLV /mnt/data ext4 defaults 0 1`  
![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609171702.png)  
This will automatically mount our new filesystem to the `/mnt/data` folder every bootup.  
To ensure it worked we can do `sudo mount -a`. If there are any errors, fix them - otherwise we are good to go.  
Restart the system.  
If we do `mount /dev/storageVG/storageLV /mnt/data` it should fail because it is already mounted.  
![](../!%20Images/Post%20Grad/Adding%20Storage%20to%20Linux%20Proxmox%20VM/Pasted%20image%2020240609171738.png)  

**Now we have a usable and mounted drive! The usable storage is located at /mnt/data**