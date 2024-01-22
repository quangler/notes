## COMP2100 Lab 1 - Cutsheet
Completed by Quinn Parent for Barett Olsen in COMP2100.

| Hostname | Roles / Services | Internal IP | VMNET / VLAN | External IP | Default Gateway | External Ports | Notes |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Admin1.brunsco.sf | Admin workstation | 172.30.0.101/24<br>(DHCP) | VMNET15 | N/A | 172.30.0.1 | N/A | Used for administrative tasks |
| SRV1.brunsco.sf | DC, DNS, DHCP, File Server | 172.30.0.5/24 | VMNET15 | N/A | 172.30.0.1 | N/A | DC1, Used as main DNS server for network. |
| SRV2.brunsco.sf | DC, DNS, File Server, Print Server | 172.30.0.6/24 | VMNET15 | N/A | 172.30.0.1 | N/A | DC2 |
| SRV3.brunsco.sf | File Server, DFS Namespace, DFS Replica, Data DeDupe | 172.30.0.7/24 | VMNET15 | N/A | 172.30.0.1 | N/A | FS1 - namespace server, primary member for replication |
| SRV4.brunsco.sf | File Server 2, DFS Replica | 172.30.0.8/24 | VMNET15 | N/A | 172.30.0.1 | N/A | FS2 - DFS replication between FS1 & FS2 |
| SRV5.brunsco.sf | iSCSI Target, Data DeDupe | 172.30.0.9/24 | VMNET15 | N/A | 172.30.0.1 | N/A | STOR1 |
| OPNsense.localdomain | Firewall | 172.30.0.1/24 | WAN > VMNET1<br>LAN > VMNET15 | 10.10.64.10/20<br>(DHCP from ISP) | 10.10.79.254 | 80, 443 > LAN | Firewall - used for internet access |
