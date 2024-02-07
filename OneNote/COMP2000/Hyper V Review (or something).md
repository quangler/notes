Virtual Switch - allow VM communication

external network - maps to a NIC (can be a shared NIC) *** this is what we are using for network and data segregation**

internal network - allows VM communication with other VMs and host

private network - allows VM communication with other VMs

- resource tracking
- resource tracking
- port acl
- network traffic monitoring
- isolated private VLANS *** tag at VM level, not switch** - nic team - switch independent lan groups (or just tag at client level)
  

  

two versions - Hyper V core - dont use (doesn't exist in server 2022)

Feature/Role - use this

Type 1 hypervisor

  

Virtual Disks

VHD - backwards compatibility / 2TB limit *** use this one - better for nested**

VHDX - live resizing / corruption protection / 64TB limit

differencing disks - equivalent to linked clones

  

VM generation:

**GEN1 - use if you are taking it home**

GEN2 - will only work the place you create the VMs | more issues than it's worth | fine in industry tho

  

Management built into OS - Hyper V Manager / Failover Cluster Manager

- manage engine - might be good for project (replicates SCVMM - doesn't really replace it)
- SCVMM - would normally be using but we out of time

  

Hyper V Clustering

- Hyper Converged Infrastructure Model **- don't do this. this is insane (for this assignment)**

storage onboard the hosts shared to all nodes using storage space

- Shared Storage Model

SAN / ISCSi SAN

  

**Separate networks for:** #important

**cluster heartbeat**

**storage**

**LAN**

**VM connections**

  

Cloud:

Private - dedicated cloud services used exclusively by individual subscribers

Public -

Hybrid - pretty much the only one you see

  

Cloud provider - one providing cloud services

Cloud subscriber - one using cloud services