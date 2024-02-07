You can install Hyper-V on:

- windows server, add it as a role

- standard edition: two VMs with each windows server OS
- datacenter edition: unlimited VMs with each windows server OS
    
    - Hyper-V Server ("BareMetal" install)
- only Hyper-V role
- command-line management only (if locally managed)
- free, VMs must be licensed separately
    
    - 64-bit client OS since windows 8
- doesn't include server-level features like high availability or live migration
  

- Hyper-V host should have multiple NICs

- dedicated NIC for Hyper-V management
- At least one NIC for virtual machine networks
- Two NICs for shared storage
- dedicated NIC for failover clustering (private network)
- at least one NIC for live migration
- the links speed must support the expected traffic
  
  

- installed as a server role (restart required)
- hypervisor is added and starts automatically
- windows server is moved into "parent partition"
- adds a bunch of new stuff

  

**ctrl+alt+left arrow to release mouse by default**

  

- enables hosts to scale up CPUs and memory
- Partitions CPUs and memory into NUMA nodes
- allocation and latency depends on relative CPU location

  

- physical and virtual NUMA will align by default

  

- meaning that you can connect to a VM without network connectivity
- devices can be redirected,
- copy and paste works
- RDS works :) (just RDP into the name of the VM)

  

- external - connects to a physical adapter
- internal - parent and vm connections only
- private - vm connections only

  

- Virtual Switch manager to create vSwitches
- vm settings to connect a virtual network adapter to switch

  

- VM has virtual hardware devices
- only things that support Hyper-V can be used
- virtual hardware can be:

- emulated - available during boot
- synthetic - available in supported OS
- SR-IOV - available in supported OS
  

- emulated devices are removed
- EUFI firmware instead of BIOS
- can run side by side with Gen 1 (must be used for legacy systems)
- supports windows 2012 or newer
  

on setup there aren't many settings

integration services: literally VMWare tools but for Hyper-V

  

- checkpoints cannot be modified, only viewed, applied, exported, renamed, or deleted.
- have:

- configuration file (.xml)
- saved state file (.vsv)
- memory content (.bin)
- differencing disks (.avhd)
  

  
  
  

**Should haves:**

  
  

How to install Hyper-V

  
  

NUMA:

  

Hyper-V lets NUMA happen at VM level

  

remote desktop over VMBus

  

vSwitches

  

configuration of vSwitches:

  

**Gen 1 VMs**

  

**Gen 2 VMs**

  

after install there are many !

  
  

checkpoints (snapshots):