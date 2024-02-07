moodle quiz

need to know:
- how to configure enterprise storage services for clustering - theory behind it **???**
	- look at the slide deck
		**use DFS - this allows centralized shared folders to exist for replication, syncs to other server - can use dedupe**

- know best practices for ADFS
	- as per slide decks
		standalone ADFS deployments not supported
		need CA with certs
		DNS must exist
		database

- differences between two storage types
	- block, file, NAS, SAN ????
		**NAS - uses file level access - meaning it runs on top of an OS - slower, usually smaller (SOHO), hardware or software RAID**
		**SAN - uses block level access - runs on hardware - very fast, very expensive, larger and much higher throughput, medium/large business, hardware RAID**

- when to use session based hosting vs VDI
	- why, MORE THAN ONE SENTENCE WHY
		**session based virtualization** - used as backend for thin clients - gives full desktop experience (individual profiles/settings) - windows server based
		- used in general computing, BYOD environments, incompatible computing platforms (for line of business)
		remote apps (still session based) - apps are hosted in virtualized instances - remote apps appear normal
		RDWeb - remote apps over the internet, can be published to desktop - needs RD gateway (used for WORK FROM HOME)

		**Virtual desktop infrastructure** - no shared infrastructure, each user gets a specific VM or a pool of VMs - windows client
		- used when computing power is required, dedicated VMs are required
		- Pooled - infrequent high computing needs - shared amongst a group of users
		- Personal (private) - frequent high computing needs - dedicated to single user, 

- best practices when it comes to administering storage within environments
- know how data dedupe works - concept
	- read the slide on it
		**data is scanned based on params during dedupe config**
		**broken down into chunks**
		**chunks are identified**
		**chunks are placed into a chunk store and compressed (if it can)**
		**original files are replaced by reparse point that points to a chunk store (think symbolic links)**
	
- where can you use data dedupe - scenarios
		**team shares**
		**user home folders**
		**work folders**
		**VDI-VHDs**
		**backup targets**
		
- match the iSCSI component to its meaning

- we will be given scenarios - what remote desktop services should be used here

- the roles of a certificate authority - know these
	- in the slides
		cert - key information, owner identity, digital signature verifying contents (issuer)
		cert authority - root (main one) and sub (secondary, issues also), issues certs - manages cert validity | enterprise - alive and domain joined  | standalone - non-domain joined, offline (if root), MANUAL
	
		web enrollment - allows users to connect to a CA via browser to request certs and CRLs
		online responder - gives cert status info (valid, expired, etc.) when requested
		network device enrollment service - allows network devices to get certs
		certificate enrollment policy web service - lets users get cert enrollment policy info
		certificate enrollment web service - allows users to enroll via HTTPS - when used with certificate enrollment policy web service - allows enrollment for computers that aren't in the domain

- **ADFS mysterious bonus question**

- where would you deploy certain functions - behind RDS

- know the RDS roles - what do they do - purpose
 **`Remote Desktop Connection Broker` - load distribution across RD session hosts - allows users to reconnect to their VM**
- **`Remote Desktop Gateway` - authentication to remote apps / VMs / etc.**  
- **`Remote Desktop Licensing`  - allows managing client access licenses - required for connecting to a remote desktop session host server**
- **`Remote Desktop Session Host`  - allows a server to host remote apps, or by virtual desktops**
- **`Remote Desktop Web Access` - allows users to access remote apps through the start menu or through browser** 

- limitations of specific RDS deployments

- **biggest one** - know which roles can coexist 


- know what OS can be used for which functionality ???? - RDS - what operating systems can be used for what functionality
	- **APPLY TO STORAGE AND ADFS AS WELL ???**
	**session based - windows server**
	 **vdi - windows client (vm)**
	 **data dedupe - can be on anything**
	 **ADFS - 2008+ needs database (WID, MS SQL)**


![[Pasted image 20240206140335.png]]
**ALLEGEDLY NOT IN THE EXAM!?!?**