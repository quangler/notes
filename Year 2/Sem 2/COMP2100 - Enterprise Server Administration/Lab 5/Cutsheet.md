
| Hostname | Roles / Services | Internal IP | VMNET / VLAN | External IP | Default Gateway | External Ports | Notes |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Admin1.brunsco.sf | Admin workstation | 172.30.0.100/24 (DHCP) | VMNET15 | N/A | 172.30.0.1 | N/A | Used for administering the servers remotely. |
| Client1.brunsco.sf | Client Workstation | 172.30.0.101/24<br>(DHCP) | VMNET15 | N/A | 172.30.0.1 | N/A | Used for testing client access to services. |
| SRV1.brunsco.sf | DC, DNS, DHCP, File Server | 172.30.0.5/24 | VMNET15 | N/A | 172.30.0.1 | N/A | DC1, Used as main DNS server for network. |
| SRV2.brunsco.sf<br> | DC, DNS, File Server, Print Server, Azure AD Connect  | 172.30.0.6/24 | VMNET15 | N/A | 172.30.0.1 | N/A | DC2 - Used for replicating on-prem to Azure environment. Command for forcing replication:<br>`Start-ADSyncSyncCycle -PolicyType Delta` |
| SRV3.brunsco.sf | File Server, DFS Namespace, DFS Replica, Data Dedupliation | 172.30.0.7/24 | VMNET15 | N/A | 172.30.0.1 | N/A | FS1 - namespace server, primary member for replication. |
| SRV4.brunsco.sf<br>**DECOMMISSIONED** | File Server 2, DFS Replica | 172.30.0.8/24 | VMNET15 | N/A | 172.30.0.1 | N/A | FS2 - DFS replication between FS1 & FS2. |
| SRV5.brunsco.sf<br>RDS.brunsco.sf<br>**DECOMMISSIONED** | Remote Desktop Services: (Broker, Gateway, Licensing, Session Host, Web Access)  | 172.30.0.9/24 | VMNET15 | N/A | 172.30.0.1 | N/A | RDS1 - Session-based deployment<br>`https://rds.brunsco.sf/RDWeb`. |
| SRV6.brunsco.sf<br>**DECOMMISSIONED** | RDS: (Session Host) | 172.30.0.10/24 | VMNET15 | N/A | 172.30.0.1 | N/A | RDS2 - used as a secondary session host (Load Balancing). |
| SRV7.brunsco.sf<br>VDI.brunsco.sf<br>**DECOMMISSIONED** | Hyper V, Data Deduplication, RDS: (Broker, Gateway, Licensing, Session Host, Virtualization Host, Web Access) | 172.30.0.11/24 | VMNET15 | N/A | 172.30.0.1 | N/A | RDS3 - VDI Deployment - <br>VDI Pool and VDI Private<br>`https://vdi.brunsco.sf/RDWeb`. |
| OPNsense.localdomain | Firewall | 172.30.0.1/24 | WAN > VMNET1<br>LAN > VMNET15 | 10.10.72.104/20<br>(DHCP) | 10.10.79.254 | 80, 443 > LAN,<br>443 > RDS1 | Firewall - used for internet access from LAN. Port forward setup through HTTPS. |
