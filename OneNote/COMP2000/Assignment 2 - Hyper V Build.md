**Build:**

- virtual to virtual server migration - swapping hypervisor platforms
- data segregation
- VLANs - tagging at VM level - not switch level
- external DNS
- everything is virtualized / highly available
- **nested DCFS inside environment (with DHCP client)**
    
    - **DHCP should be coming from DCFS** **not** **firewall**
- still using a virtual firewall - OPNSense or PFSense
- must have a disk witness present - quorum
- DNS working
- web apps ??
- cutsheet
- **best practices - admin accounts, default admin is disabled, firewalls on**
- DNS forwarders still to 10.11.4.4, and 10.11.8.8

  

rubric

- disk witness in hyper V (quorum drive no more than 10gb, can be as small as 100mb)
- virtual apps imported and running - must work (not database error??)
- SMB client setup / DHCP setup / DNS setup
- failover
- data / network segregation

  
  

**Technical Documentation:**

- basically same as last time
- cutsheet, troubleshooting, what worked, what didn't
- **VM planning: for resources**

  
  

**can reuse a lot of stuff for this build** #important

  

**V2V Migration:**

- doesn't matter which you're converting from and going to
- VCSA - can pull from client to client - cant push ?
- SCVMM - can pull clients into cluster

  

- import OVAs into vmware workstation
- get a VMDK
- use a 3rd party application for v2v conversion

starwinds - bidirectional (vmware to hyper v, hyper v to vmware) - **recommended** #important

disk to VHD - can also be used

  

timeline: we are starting azure on the 28th.

- absolute last day for this assignment is DEC 1.
- 24th is best day to start marking