**active directory sites and services**

dc1:

- rename site to calgary or whatever
- make a new custom link with first and new site in

new site

- use custom link to make a new site

subnets folder:

- new subnet
- site subnet ip - select which site its for
- do for old and new site (2 subnets)
  

  

dc2:

- set to static ip, set dns server as DC1 (need router powered on)
- install AD DS
- make it a standalone server, _then_ join it to your domain
- add domain to existing domain
- looking for site name to automatically select **NEW site**
- replicate from any domain controller - fine for now, however now that we are doing more with it, use the closest DC
  

  

can now use admin workstation to manage both DCs

  

users and computers:

wont show up on dc2 yet

  

FORCE REPLICATION:

DC1 -> SITES AND SERVICES -> NTDS SETTINGS -> REPLICATE

- this can either pull updates from another DC, or push updates from that DC

command prompt:

'nltest /dsgetsite' - tells you what site you're connected to

  

for joining client:

new client either needs DHCP or static IP with correct subnet

DNS - closest DC server

  

make sure DNS works or you're idiot