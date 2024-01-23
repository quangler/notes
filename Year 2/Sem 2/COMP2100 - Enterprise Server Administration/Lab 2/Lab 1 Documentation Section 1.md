## Sign-in Info
| For | Username | Password |
| ---- | ---- | ---- |
| AD | Brunsco\administrator<br>`quinnadmin@brunsco.sf` | AtomPow!<br>P@ssw0rd |
| FW | root | React1on |

## Cutsheet
| Hostname | Roles / Services | Internal IP | VMNET / VLAN | External IP | Default Gateway | External Ports | Notes |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Admin1.brunsco.sf | Admin workstation | 172.30.0.101/24 | VMNET15 | N/A | 172.30.0.1 | N/A | Used for administrative tasks |
| SRV1.brunsco.sf | DC, DNS, DHCP, File Server | 172.30.0.5/24 | VMNET15 | N/A | 172.30.0.1 | N/A | DC1, Used as main DNS server for network. |
| SRV2.brunsco.sf | DC, DNS, File Server, Print Server | 172.30.0.6/24 | VMNET15 | N/A | 172.30.0.1 | N/A | DC2 |
| SRV3.brunsco.sf | File Server, DFS Namespace, DFS Replica, Data DeDupe | 172.30.0.7/24 | VMNET15 | N/A | 172.30.0.1 | N/A | FS1 - namespace server, primary member for replication |
| SRV4.brunsco.sf | File Server 2, DFS Replica | 172.30.0.8/24 | VMNET15 | N/A | 172.30.0.1 | N/A | FS2 - DFS replication between FS1 & FS2 |
| SRV5.brunsco.sf | iSCSI Target, Data DeDuplication, Hyper V | 172.30.0.9/24 | VMNET15 | N/A | 172.30.0.1 | N/A | STOR1 |
| SRV6.brunsco.sf |  | 172.30.0.10/24 | VMNET15 | N/A | 172.30.0.1 | N/A | Node1 |
| SRV7.brunsco.sf |  | 172.30.0.11/24 | VMNET15 | N/A | 172.30.0.1 | N/A | Node2 |
| OPNsense.localdomain | Firewall | 172.30.0.1/24 | WAN > VMNET1<br>LAN > VMNET15 | 10.10.64.10/20 | 10.10.79.254 | 80, 443 > LAN | Firewall - used for internet access |

## Documentation information
| AD Structure | AD Usernames + Convention | AD Groups + convention | AD GPOs | DNS | DHCP | Firewall + Ports | File Services (Shares, ETC) | VM Info (VMs, Drives, Storage space, NICS, etc.) |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|  |  |  |  |  |  |  |  |  |
AD structure
AD usernames + convention
AD groups + convention
AD GPOs
DNS
DHCP
Firewall + Ports
File Services (Shares / Etc)
VM Information (VMs, Drives, Storage Space, NICS, ETC)

## Screenshots:
Part 3 step 7:
![[Pasted image 20240114130915.png]]
Part 3 step 10:
![[Pasted image 20240114133023.png]]![[Pasted image 20240114133053.png]]
Part 4 step 2:
![[Pasted image 20240114133240.png]]
Part 4 step 5:
![[Pasted image 20240114133458.png]]
Part 4 Step 9d:
![[Pasted image 20240114134024.png]]
Part 4 Step 11:
![[Pasted image 20240114134953.png]]
![[Pasted image 20240114135251.png]]