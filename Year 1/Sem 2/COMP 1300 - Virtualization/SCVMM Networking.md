- it is more complex than the Hyper-V V-Switch manager

  

**Logical Network** - like VLANS

- things like: Corporate network, network management, testing, etc.

  

**Network Sites** - like SITES - different physical locations (or subnets)

- these sites allow SCVMM to assign the correct IP addresses (if using DHCP)

- can use IP address pools for DHCP

  

**VM Networks** - like VMNETS

- can have them setup to a network adapter for outside access or just internally.

- need to set which logical network and site in SCVMM #important

  

**Uplink Port Profile** - connectivity of virtual switch to the logical networks

- used for setting up QOS (quality of service - prioritizing some packets rather than others)