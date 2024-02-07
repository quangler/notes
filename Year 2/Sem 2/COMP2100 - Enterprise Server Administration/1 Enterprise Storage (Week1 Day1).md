#### Review
**NAS** - network attached storage
- file level access
- commonly used for SOHO
- hardware or software RAID
**SAN** - storage area network
- block level storage
- damn fast, used for bigger businesses
- usually hardware raid
- huge throughput
**iSCSI** SAN - internet small computer system interface
- block level access
- hardware RAID
- not as expensive as normal SAN
- also lower throughput
- iSNS (Internet Storage Name Server) - used as a DNS server for iSCSI (large # of iSCSI targets)
**FibreChannel** - proprietary storage networking
#### Windows Storage Services
Purpose built OS for file servers
in 2019 they abandoned it for having the roles on the standard OS.
now you can use it for iSCSI SAN (on the windows OS!)
#### Data Hoarding
Limited storage space, and lots of copies take a ton of data.
Large organizations see doubling ~ every 3 years
The solution? Data Deduplication:
#### Data Deduplication
- can be handled at a software or hardware level
- recommended usage:
	- team shares
	- user home folders
	- work folders
	- software dev shares
	- VDI - VHD's
	- Backup Targets
##### How does it work? (KNOW ORDER FOR TEST)
1. Data on the system is scanned based on the parameters setup during data dedup config
2. Files are then broken down into variable size chunks
3. unique chunks are then identified
4. chunks are placed into a chunk store and optionally compressed further (if applicable)
5. original file streams are now replaced with a reparse point that points to a chunk store.
#### DFS - Distributed File System
Centralizes shared folders from multiple sources into a logically structured namespace.
- essentially to be able to break up files on multiple file shares (different servers) and have them in the same place for users.
The purpose of DFS is for continuity and to make our lives easier (not security)
- makes it really easy to change-over server)
4 primary elements:
- Namespace Server - contains the namespace
- Namespace root - what hosts the share (?)
- Folder - exist in the namespace
- Folder targets - can be on any server
##### DFS Replication
- DFS provides redundancy by providing replication of data
- data from one target server can be replicated to the other, keeping changes in sync
- if one data point is offline, the replicated data is still available to the namespace