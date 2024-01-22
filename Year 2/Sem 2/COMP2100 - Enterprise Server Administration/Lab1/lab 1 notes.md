- encrypted vm password - P@ssw0rd
- dhcp could be busted - just remake it (on firewall)
- srv4 - second file server (FS2)
- srv5 - second iSCSI server (Store1) - enable dedupe
- srv2 - only needs to run once a week ????

#### DFS
- srv3 - namespace and replica server
- srv4 - replica server
- gotta add DFS to srv3 and srv4
	- (SRV3) DFS management -> create a namespace = srv3 | name would be `brunsco.sf\<name>`
	- change local path > use `K:\` , admin full access & users read and write
	- domain-based namespace, 2008 mode enabled
	- make a folder and point it at the correct data
	- you can add another target from a different server (must be on a share) > yes for replication group

- make file shares - as close to departmental folders as possible
- put the data in there
- use DFS

**do all of the folders

replication settings:
- primary member is nameserver
- full mesh
- create !
force replication:
- if force replicating from the place with smaller amount of data, you will overwrite the more data with the less
	- in short, you can overwrite with nothing

##### Dedupe
- role under file services (do it on SRV3 & iSCSI target server) - saves SSD space
- go to volumes > disks (`K:/`)> configure data deduplication | before doing anything make sure to check how much data is on the volume already
- general purpose file server, 0 days > OK | this starts dedupe
- to test it just copy and paste the whole damn share a bunch > then use the PowerShell script to force dedupe
- check how much dedupe you got
- ^ turn this on in proj2000 - worlds easiest marks.
- CAUTION.
	- when you back up the volume, it could have the full size as a backup