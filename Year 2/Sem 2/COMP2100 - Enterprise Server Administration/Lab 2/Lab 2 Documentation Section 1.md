## Sign-in Info
| For | Username | Password |
| ---- | ---- | ---- |
| AD | Brunsco\administrator<br>`quinnadmin@brunsco.sf` | AtomPow!<br>P@ssw0rd |
| FW | root | React1on |
| VDI Pool | `SimpsonLisa@brunsco.sf` | P@ssw0rd |
| VDI Priv | `FrinkJohn2@brunsco.sf` | P@ssw0rd |
| RDS | `BRUNSCO\JoeQuim` | P@ssw0rd |


## Cutsheet
| Hostname | Roles / Services | Internal IP | VMNET / VLAN | External IP | Default Gateway | External Ports | Notes |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Admin1.brunsco.sf | Admin workstation | 172.30.0.100/24 | VMNET15 | N/A | 172.30.0.1 | N/A | Used for administrative tasks |
| Client1.brunsco.sf | Client Workstation | 172.30.0.101/24 | VMNET15 | N/A | 172.30.0.1 | N/A | Used for testing client access |
| SRV1.brunsco.sf | DC, DNS, DHCP, File Server | 172.30.0.5/24 | VMNET15 | N/A | 172.30.0.1 | N/A | DC1, Used as main DNS server for network. |
| SRV2.brunsco.sf | DC, DNS, File Server, Print Server | 172.30.0.6/24 | VMNET15 | N/A | 172.30.0.1 | N/A | DC2 - used for replication |
| SRV3.brunsco.sf | File Server, DFS Namespace, DFS Replica, Data Dedupliation | 172.30.0.7/24 | VMNET15 | N/A | 172.30.0.1 | N/A | FS1 - namespace server, primary member for replication |
| SRV4.brunsco.sf | File Server 2, DFS Replica | 172.30.0.8/24 | VMNET15 | N/A | 172.30.0.1 | N/A | FS2 - DFS replication between FS1 & FS2 |
| SRV5.brunsco.sf<br>RDS.brunsco.sf | Remote Desktop Services: (Broker, Gateway, Licensing, Session Host, Web Access)  | 172.30.0.9/24 | VMNET15 | N/A | 172.30.0.1 | N/A | RDS1 - Session-based deployment<br>`https://rds.brunsco.sf/RDWeb` |
| SRV6.brunsco.sf | RDS: (Session Host) | 172.30.0.10/24 | VMNET15 | N/A | 172.30.0.1 | N/A | RDS2 - used for a secondary session host (Load Balancing) |
| SRV7.brunsco.sf<br>VDI.brunsco.sf | Hyper V, Data Deduplication, RDS: (Broker, Gateway, Licensing, Session Host, Virtualization Host, Web Access) | 172.30.0.11/24 | VMNET15 | N/A | 172.30.0.1 | N/A | RDS3 - VDI Deployment - <br>VDI Pool and VDI Private<br>`https://vdi.brunsco.sf/RDWeb` |
| OPNsense.localdomain | Firewall | 172.30.0.1/24 | WAN > VMNET1<br>LAN > VMNET15 | 10.10.72.104/20 | 10.10.79.254 | 80, 443 > LAN,<br>443 > RDS1 | Firewall - used for internet access |

**1.**       **A test user can access a published application directly from client1 (2)**
![](file:///C:/Users/qparent1/AppData/Local/Temp/msohtmlclip1/01/clip_image002.png)
**2.**       **A test user can login to a session host and interact with the desktop – EG open thunderbird (2)****
![](file:///C:/Users/qparent1/AppData/Local/Temp/msohtmlclip1/01/clip_image004.png)**
**3.**       **A test user can login to a published application without interacting with the desktop – EG open thunderbird from the webpage (2)**
**![](file:///C:/Users/qparent1/AppData/Local/Temp/msohtmlclip1/01/clip_image006.png)
**4.      A test user can login to a Pooled VDI through RDweb (2)**
![](file:///C:/Users/qparent1/AppData/Local/Temp/msohtmlclip1/01/clip_image008.png)
**5.       **A test user can login to a Private VDI through RDweb (2)**
**![](file:///C:/Users/qparent1/AppData/Local/Temp/msohtmlclip1/01/clip_image010.png)
6.**       A test user can install an application on the private VDI (2)
![](file:///C:/Users/qparent1/AppData/Local/Temp/msohtmlclip1/01/clip_image012.png)
**7.       A classmate can browse to your RDweb portal and access a published application – Get them to give you screen capture showing this and some of their identifying information (2)
![](file:///C:/Users/qparent1/AppData/Local/Temp/msohtmlclip1/01/clip_image014.png)
