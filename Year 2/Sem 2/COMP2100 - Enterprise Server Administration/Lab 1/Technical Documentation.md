# COMP2100 Lab 1 - Technical Documentation
Completed by Quinn Parent for Barett Olsen in COMP2100.
## **Table of Contents:**
- [[#Project Overview|Project Overview]]
	- [[#Project Overview#AD Structure|AD Structure]]
		- [[#AD Structure#AD Usernames and Convention|AD Usernames and Convention]]
		- [[#AD Structure#AD Groups and Convention|AD Groups and Convention]]
		- [[#AD Structure#AD GPOs|AD GPOs]]
	- [[#Project Overview#DNS|DNS]]
	- [[#Project Overview#DHCP|DHCP]]
	- [[#Project Overview#Firewall and Ports|Firewall and Ports]]
	- [[#Project Overview#File Services|File Services]]
		- [[#File Services#Shares|Shares]]
		- [[#File Services#Distributed Files System|Distributed Files System]]
		- [[#File Services#Data Deduplication|Data Deduplication]]
	- [[#Project Overview#VM Information|VM Information]]
## Project Overview
The goal of this project was to reclaim and redocument Burnsco Industries technical infrastructure. 
This was done by entering the environment with an observational perspective to record all basic infrastructure information, then with a continuation of making the environment more functional by utilizing file shares and data deduplication.  
<div style="page-break-after: always; visibility: hidden"> \pagebreak </div>

### AD Structure
The active directory structure is split into multiple OUs that contain the business' departments.
Some OUs contain teams within the department.
Each OU contains users pertaining to that department or team.

![[Pasted image 20240114152437.png|center]]

<div style="page-break-after: always; visibility: hidden"> \pagebreak </div>


#### AD Usernames and Convention
The username convention for modern Burnsco Industries logon is as follows:
`<Last Name><First Name>@brunsco.sf`, an example of which would be: `SimpsonBart@brunsco.sf`.
The user logon for pre-Windows 2000 is as follows:
`BRUNSCO\<First Name><First 4 letters of Last Name>`, an example of which would be: `BRUNSCO\BartSimp`.
#### AD Groups and Convention
Active Directory groups are setup with a name scheme as follows:
For domain local groups: `DL_<Permissions>_<Department>`, an example of such would be: `DL_R_Accounting` which is a domain local read only group for the accounting department.
For global groups: `GG_<Department>`, an example of which would be: `GG_Operations` which is a global group for the operations department.

![[Pasted image 20240114154340.png]]


#### AD GPOs
The Group Policy Management window shows no signs of change from the two default policies created upon the domain being created.
The two default policies being the `Default Domain Controllers` policy which is only applied to the Domain Controllers OU, and the `Default Domain Policy` which is applied to all OUs.

![[Pasted image 20240114155517.png]]
### DNS
The DNS roles is setup on both SRV1 and SRV2, the two DCs for this domain.
SRV1 is set as the primary DNS server for all other servers on the network, SRV2 uses itself as its secondary.
The DNS forwarders are set to `10.11.8.8` and `10.11.4.4`, the Ultracloud ISP network DNS servers, on both SRV1 and SRV2.

![[Pasted image 20240114160215.png]]
### DHCP
SRV1 is the only DHCP server on the network, with a single IPv4 scope setup.
The scope is on the `172.30.0.0/24` network with a range from `172.30.0.100` - `172.30.0.254`.
The scope options are configured to give `172.30.0.1` for default gateway, and `172.30.0.5` for DNS server, as well as `brunsco.sf` as domain name.

![[Pasted image 20240114160652.png]]

![[Pasted image 20240114160633.png]]
### Firewall and Ports
The firewall is an OPNsense firewall that has a LAN and a WAN port.
The WAN port is getting a DHCP address from the ISP network, and is set to `10.10.64.10/20` currently with the default gateway being `10.10.79.254`.
The LAN port is configured as the default gateway for the network at `172.30.0.1`.
The only port forwarding that has been setup on the firewall is the default `Anti-Lockout Rule` that allows any traffic in to the `172.30.0.1` address through port `80 (HTTP)` and `443 (HTTPS)`.

![[Pasted image 20240114161102.png]]
### File Services
SRV1 through SRV4 are all configured to have the file server role enabled.
SRV3 and SRV4 are the two main file servers, being noted as FS1 and FS2 respectively internally.
Both SRV3 and SRV4 have the DFS replica role enabled, and SRV3 acts as the DFS Namespace.
#### Distributed Files System
SRV3 is the DFS Namespace and one of two DFS Replica servers, SRV4 is the other.
`Accounting`, `Executive`, `HR`, `Marketing`, and `Sales` are departments that have DFS enabled for redundancy of files.
They can be accessed by going to: `\\SRV3\Data\<department>`, or going directly to `M:\<department>` on either SRV3 or SRV4.
SRV3 is the primary member for replication in a full mesh topology.

![[Pasted image 20240114162709.png]]
#### Data Deduplication
Data deduplication was configured on SRV3 on the `M:` volume to maximize utilization.
The deduplication settings are as follows:
`General purpose file server`, deduplication of files older than `0 days`, there are two throughput optimization schedules: `weekdays, 5 hours after 5:00pm` and `weekends, 8 hours after 1:00pm`.

![[Pasted image 20240114163336.png]]
### VM Information
There are seven virtual machines. Five servers, `SRV1`-`SRV5`, one admin workstation, `Admin1`, and one firewall, `FW`.
All the servers are running on Windows Server 2022, version 21H2.
The admin workstation is running on Windows 10, version 22H2.
The firewall is running on OPNsense 23.7-amd64.
All VMs are running with `4GB of RAM`, `1 processor`, and `80GB virtual disks`.
Each VM has a NIC assigned to `VMNET15`. The firewall has an additional NIC of `VMNET1` where it is directly patched into the ISP network.
SRV3 and SRV4 have two extra disks that are `30GB`, SRV3 has an additional `500GB` drive for data. 
SRV5 has been given an additional `10GB` and `100GB` drive for a future lab.