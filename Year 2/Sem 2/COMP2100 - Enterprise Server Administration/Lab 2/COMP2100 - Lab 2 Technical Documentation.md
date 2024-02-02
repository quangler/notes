### RDS1
`RDS1` is the internal name for `SRV5`, it has remote desktop services installed with the following configurations:  
**Remote Desktop Services:**  
- `Remote Desktop Connection Broker`  
- `Remote Desktop Gateway` - `RDS.BRUNSCO.SF` using AD authentication  
- `Remote Desktop Licensing`  
- `Remote Desktop Session Host`  
- `Remote Desktop Web Access` - `https://SRV5.BRUNSCO.SF/RDWeb` or `https://RDS.BRUNSCO.SF/RDWeb`  
- Certificates are handled by a local self-signed certificate that is to be installed on all user's workstations through GPOs.  
`RDS1` is in the `RDS Pool` server group that provide published remote apps for users.  
***For user access guide to the RemoteApp programs: [[RDWeb User Guide]].***  
### RDS2  
`RDS2` is the internal name for `SRV6`, it has remote desktop services installed with the following configuration:   
**Remote Desktop Services:**  
- `Remote Desktop Session Host`  
`RDS2` is in the `RDS Pool` server group that provide published remote apps for users.  
#### RDS Session Host  
Both `RDS1` and `RDS2` are RD Session Hosts for the RDS deployment in the current infrastructure.  
The two servers both have identical installations of the RemoteApp programs installed so that users can authenticate to either one and have access to the published applications.  
##### RDS Published Applications  
Published Applications can be accessed by users in the `Published App Users` group.  
A list of the published applications that are on both RDS Session Host servers is as follows:  
- `Discord`  
- `MS Paint`  
- `Thunderbird`  
- `WinRAR`  
### RDS3  
`RDS3` is the internal name for `SRV7`, it is configured with `Hyper V`, `Data Deduplication`, and `Remote Desktop Services`.  
**Remote Desktop Services**:  
- `Remote Desktop Connection Broker`  
- `Remote Desktop Gateway` - `VDI.BRUNSCO.SF` using AD authentication  
- `Remote Desktop Licensing`  
- `Remote Desktop Session Host`  
- `Remote Desktop Virtualization Host`  
- `Remote Desktop Web Access` - `https://SRV7.BRUNSCO.SF/RDWeb` or `https://VDI.BRUNSCO.SF/RDWeb`  
- Certificates are handled by a local self-signed certificate that is to be installed on all user's workstations through GPOs.  
#### VDI Pool  
`VDI Pool` is a pool on `RDS3` of two shared VMs that are distributed to any amount of authorized users for use.  
The current configuration for `VDI Pool` has the following settings:  
**Collection ID:** `VDI_Pool`  
**Total Virtual Desktops:** `2`  
**Active Directory domain name:** `brunsco.sf`  
**Storage:** `Local` at `E:\VDI`  
**Virtual desktop template export location:** `\\SRV7\RDVirtualDesktopTemplate\VDI_Pool\IMGS\__1`  
**Virtual desktop name format:**   
	**- Prefix: `VDI-POOL-`   
	- Suffix: `0`  
Allowed User Groups:** `Pooled VDI Users`  
**User Profile Disks:** `DISABLED`  
#### VDI Private  
`VDI Private` is a pool on `RDS3` of two shared VMs that are designed to be 1-to-1 for authorized users.  
**Collection ID:** `VDI_Private`  
**Total Virtual Desktops:** `2`  
**Active Directory domain name:** `brunsco.sf`  
**Storage:** `Local` at `E:\VDI`  
**Virtual desktop template export location:** `\\SRV7\RDVirtualDesktopTemplate\VDI_Private\IMGS\__1`  
**Virtual desktop name format:**   
	**- Prefix: `VDI-PRIV-`   
	- Suffix: `0`  
Allowed User Groups:** `Private VDI Users`  
**Administrative Access:** `GRANTED`  
### RDS Web  
Both the `RDS` and `VDI` setups have web hosts that point to the respective servers.  
For `RDS`, the web server is located at `https://SRV5.BRUNSCO.SF/RDWeb`, or `https://RDS.BRUNSCO.SF/RDWeb` via the CNAME in the DNS server (`RDS` -> `SRV5`).  
For `VDI`, the web server is located at `https://SRV7.BRUNSCO.SF/RDWeb`, or `https://VDI.BRUNSCO.SF/RDWeb` via the CNAME in the DNS server (`VDI` -> `SRV7`).  
Web access allows an authorized user to access either remote apps, or remote sessions to initiate a private VDI / pooled VDI session.  

### RD Gateway  
RD Gateway is the method of authenticating the users to the Active Directory users and computers.   
This is what allows the user to access the RD Web page to have the correct information based on the group they are in.   
`RDS1` and `RDS3` act as RD Gateways.    