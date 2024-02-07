types of virtual switches:

- standard switches - virtual switches for a single host

  

- distributed switches - centralized management and monitoring of the networking config for all hosts
    
    - they work with live migration too

(not available vsphere standard edition)

  

distributed switching has private vlans and standard switching doesn't

- can set configurations at the port level

  

traffic-shaping policy - setting traffic priority (want gaming > school for example)

- disabled by default
- apply to each NIC in the group or individually
- set for inbound and outbound traffic
  

  

NIC teaming - adds failover for redundancy in an ESXi server

- includes load balancing

  

VLANs - distributed switches allow for private VLANs

- private VLANs allow further segmentation of logical broadcast domain into smaller broadcast subdomains
-