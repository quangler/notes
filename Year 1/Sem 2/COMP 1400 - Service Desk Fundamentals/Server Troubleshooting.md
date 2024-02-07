GPO Review

- GPOs are applied at different places to have effects on users or computers.

- GPOs apply from the bottom up, so a domain GPO does not overwrite Local.

- GPOs only affect OUs, **not** containers

- Computer Policies - only affect user PCs

- User Policies - only affect User

  

GPO best practices:

- make OUs for computers and for users separately

- GPOs on these OUs for more granularity, and easier to see what's happening

- also keeps it cleaner

  

GPO Modeling

- doesn't act as the GPO, but lets you see if it would have worked or not

- good for testing changes before you apply them

  

GPOZaurr

- builds an HTML summary of existing GPOs

- great for when you take over an environment you are not familiar with

- use with caution, but it is cool and powerful

  

Install-Module -Name GPOZaurr

Import-Module GPOZaurr

Invoke-GPOZaurr

  

DNS - (it's always DNS)

- critical infrastructure

- needed for domain to work, as well as connection to internet

- systems have a HOSTS file (this overwrites any normal DNS resolution)

- installed on a server

  

DNS - Things to check:

- adapter settings (ipconfig /all)

- confirm servers are up

- check hosts file

- check DNS is running

- check records on server

- DNS forwarders

  

DHCP

- provides network connection info automatically

- "technically" not required but like. come on.

- will provide IP and DNS

  

DHCP - Common Problems

- network issues stopping initial DHCP lease

- server not on / DHCP not started

- IP exhaustion

  

Shadows Copies - VSS

- act like snapshots (point-in-time backups)

- good option on file server

- IS NOT A REPLACEMENT FOR A REAL BACKUP

  

right click volume > configure shadow copies

then settings - location of backups, schedule of backups, storage limits (configure these)

  

right click on a file - restore previous versions

  

iDRAC - out of band management

- a dedicated card that has a network connection and can be connected to via web.

- acts like you are in front of the server with a keyboard monitor and mouse.

- iDRAC is the dell brand name