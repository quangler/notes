don't have to make a client 1 - use the one given
gonna have 4 servers - 2 for session based hosting, 2 for the VDI
**use terminal services/rds install mode** to install the apps

for VDI template - use a full windows 10 pro OS - drop the ram (don't use tiny 10)
- sysprep after domain join

profile disks - saves the VDI disks somewhere else so things don't break - we don't need this
- turn on if you want remote users to have different profiles than their in-person profile

dont need file servers or dfs servers
7 vms on - 

## Demo Notes
some tweaks will be made from here to lab
##### Session Based Hosting
add role to RDS1 (SRV6) > remote desktop services > all remote desktop things (**except virtualization host**) > reboot
add role to RDS2 (SRV7) > remote desktop services > session host
	(SRV6) add roles and features > remote desktop service > standard deployment > session-based deployment > select everything as SRV6 > install RD web access service CHECK > deploy
		(on SRV6) manage > create server group > `RDS Servers` add in SRV5, SRV6, SRV7
		(SRV6) server manager > remote desktop services > collections > add host servers > add SRV7
if you need to do maintenance on a server > (in collections) right click on host sever > disable connections (it will act as a forwarder to other host)



RD Gateway > select SRV6 > (SSL cert needs to be external FQDN typically, using internal for now) > `rds.brunsco.sf` | have to make this DNS record (point it to the broker)
	VERY TEDIOUS PART: > create new certificate > name: `RDS.brunsco.sf` `P@ssw0rd` | save this to desktop > allow into trusted group
		each role service you need to select the certificate and click apply
**once everything is grayed out we are doing good**
add RD session host servers > RD session hosts: set as both SRV6 & SRV7 (allows for load balancing) > disable profile disks > create collection
	(on both session hosts) download thunderbird (don't open) > control panel > search `install mode` > find application > standard thunderbird install > finish

RDS > Collections > Remote apps > thunderbird, edge, calculator, notepad, WordPad, XPS viewer
SRV1 -> Groups > new Group > Published App Users (global group) > move some users into it
	sign into `rds.brunsco.sf` as a user in Published App Users > **install cert to trusted root** 
		since they are just a user on a server OS, should make a GPO to lock things down (server manager, firewalls, etc.), will also clean up user experience.
		(assuming you have selected disallow new connections on SRV6) users will need to **sign out** (not disconnect) if they are going to transfer over
go to `http://rds.brunsco.sf/RDWeb/` > sign in to account > click on a guy > and have 10000000 popups for signing in (probably because he was doing it on SRV1??)
install the cert on Admin1 **THEN** do this ^^ (gotta download and run the thing)
OR
control panel > access remote app and desktops > `https://rds.brunsco.sf/RDWeb/feed/webfeed.aspx` > (win button) > work resources > all the apps 😨



##### Virtual Desktop Infrastructure
SRV6 - roles > Hyper-V, remote desktop services > don't worry about, share virtual switch,
	remote desktop > virtualization host
SRV6 - remote desktop installation > quick start > virtual machine-based desktop deployment > 



2 session hosts - RDS1 & RDS2
- 2 new VMS - 2022 or 2019

1 virtualization host - NODE1
- new VM within - needs to be a full windows 10 vm

Client can be the one provided
- need to import RDS cert