Cluster: multiple nodes working together to become a single cluster resource

Node: a host

active node: a host that is on and a part of a cluster

active active node: all nodes are doing something

  

failover: a node goes down and the resource goes to another node

failback: a node goes down and the resources goes back to the way it was

  

why we use clusters: high availability - saves a company money from less down time

  

NAS: network attached storage

- file level access
- commonly used in SOHO
- can do RAID, and use SMB, NFS, CIFS, AFP
  

  

SAN: storage area network

- block level access over fibre or iSCSI
- proprietary, expensive, and REAL fast
- 8/16/128Gbps

  

iSCSI SAN

- hardware raid
- block level access
- not super expensive
- but also not super fast (40-60gbps)
- fault tolerance through RAID
- recommended to segregate storage network physically form your LAN

  

**Network Load Balancing**

- older windows based tech before clustering existed
- essentially duplicating servers
- used mostly for stateless applications (web servers)
- can be used in conjunction with server clustering
- hosts had to be on the same subnet
  

  

**Hyper Converged Infrastructure**

- merging multiple pieces of physical infrastructure into one "converged" solution
- aka trying to fully utilize all the resources you have
- A CLUSTER WITHOUT SHARED STORAGE - THE TWO NODES USE EACHOTHER'S DRIVES FOR HIGH AVAILABILITY

  

**Cloud/Hybrid Hyper Convergence**

- hardware remaining on prem is becoming expensive so they split it between on prem and in the cloud
- maximizing equipment's overall utilization

  

Typical HCI Deployment:

- 3 nodes, without a SAN
- this saves money, and still has failover through failover clustering

  

Hyper-V

- storage spaces direct or a 3rd party software

Storage spaces direct

- Functionality only available in **data center edition**
- storage pools required on both hosts
    
    - SATA or SCSI HDD supported
    - SATA or NVME SSDs are supported
- not SAS :(
- storage spaces direct allows admins to tier their storage

- this means you can have some drives that are faster for the more important stuff, and slower drives for things like logs

  

VMWare

- vSAN or 3rd party software

vSAN

- functionality is built into vSphere
- works as platform that virtual machines will run on
- allows for storage tiering￼

the primary two 3rd parties are:

- storm magic
- starwinds vSAN

both work by accessing storage directly from the hosts