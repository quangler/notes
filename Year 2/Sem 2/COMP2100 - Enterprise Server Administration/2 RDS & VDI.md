#### Remote Desktop Services
- platform that allows end users to access individual virtualized applications
- provides secure mobile and remote desktop access
- allows users to run their desktops from the cloud
	- replaced terminal services in server 2008 R2
	- handled through Citrix XenApp for a few years
##### Use Case:
- centralized application deployment to smaller number of machines
- controlled variables - no more hardware compatibility worries
- controlled applicated updates and testing
- lower cost of ownership - thin client / BYOD (basically a monitor and keyboard)
#### Deployment Methods:
##### Session-based virtualization
Traditional form of RDS
- users are given full desktop experience (individual profiles and settings)
- ideal for users that rely on RDS as their primary workstation
- used for backend infrastructure for thin client computing
	- thin clients allow for diskless computing for end user workstations
		- used in medical field, hazardous area, point of sale
		- easy to swap a thin client out if they die
		- lets your server hold all the heat and sound, not your desk
		- cons: doesn't help if you need more power
	- used typically in general use computing; office settings
- BYOD environments
- incompatible computing platforms for line of business applications - lets you run it on any OS
- ease of application deployment - only have to set it up once for infinite (?) users
###### Remote Apps
Still session-based virtualization
- full desktop experience is removed - only applications are hosted and ran in virtualized instances
- remote apps for end users appear normally as locally installed applications
	- apps have taskbar entry's, can be resized, moved across multiple monitor
	- proper configuration and certificates make the experience seamless for end users
basically lets you have icons that link to specific RDS apps (like being able to have any user reset a password by clicking on the button > brings to AD reset password guy)

###### RDWeb Overview
- remote apps now become available over the internet
- can also be used to publish the full desktop experience "remotely"
- very useful for work from home scenarios where hardware standardization cannot be guaranteed
- can be used with normal standalone VPN connection or with an RDGateway
###### RDGateway
- alternative to a stand-alone VPN client to provide users access to their RDS environment
- all traffic is encrypted back to the host site
- RDGateway makes it more seamless for end users
- needs to be patched regularly or it could be insecure
##### VDI vs RDS
|  | VDI | Remote Desktop |
| ---- | ---- | ---- |
| base OS | windows client based | windows server based |
| shared resources | no | infrastructure resource sharing |
| dedicated to end user | yes | no - shared amongst multiple users |
| admin control end user | yes | no - shared resource locks admin control from non administrative accounts |
##### VDI - Virtual Desktop Infrastructure
Alternate to RDS where more computing power is required - can share GPUs
- dedicated VMs are required for setting up VDI's
- VDI's are only limited by the hosts they are running on
- VDI's can be standalone (not as efficient) or managed by an RDS broker (more efficient)
###### Virtual Desktop Collection (deployment)
- Pooled virtual desktop collection
	- shared amongst a group of users
	- used for infrequent high computing needs
- Personal virtual desktop collection
	- dedicated to the user assigned
	- user for frequent high computing needs