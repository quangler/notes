> [!caution] This page contained a drawing which was not converted.   
Firewall: firewall (control panel) -8 advanced settings-o windows defender firewall properties -o domain/ private l public (all)

timezone: all matching

Active Directory Domain Services

Lo Server manager

topkick ADDS role

↳DNS is needed too

IDHCP is optional @this point

Promoting Server to a DC

Lo Flag @ top -s "promote to DC"

first setup:

Ly add a new forest

Lo Set domain name

↳P@sswQrd

Lo leave default

Lorestart

subsequent:

* b " add a DC to an existing domain"

to enter domain name

LT credentials: Administrator @domainname . P@sswOrd

(sleave defaults

Lo restart

DNS manager:

Reverse Lookup zone:

Lo DNS MMC

Lo DC 1

↳right click on "reverse lookup Zone"

(s new zone

L] Primary Zone

↳to all DNS servers on this domain

↳first 3 octets of DC N

Lyallow only secure dynamic updates

to after zone creation, PTR (pointer) records

Loright click -anew pointer

Lo browse for DCI & DCZ

Active Directory:

"Active Directory Users & computers"

e Domain Controllers-holds DC accounts

-8 users -o right click-anew info

Ls boom, new user

DNS:

Forward lookup zone

Lo new Alias (creates a second name)

L. Nickname

Lo F Q D N-ex. 'delist naira:

Lo this will create a new FAD N of 'nickname. ist nautical

MX -o Mail server

ping name -4-0 shows Pr 4 response

Ns lookup

Lo shame - tests Forward lookup zone (name to IP)

↳, N address-test reverse lookup zone Cip to name)

LF exit

DNS cache + ipconfig displaying

2 Nameserver

(NAME s canonical

SOA 6 Authority

PTR 12 Pointer

record type desc.

short Forms Law

DNS Forwarding

Lo DNS MC

Lo right click dal

L •Properties

L] Forwarders

Load 8.0-8.8 & 1.11

Lo internet connect ion

DHCPs:

Server Manager

Load role to DCI

LODHI p

flag

Lo "complete DHCP configuration'

Lo accept defaults

DHCPS Mc

-0 r-click Apr 4

Lo new scope

Lo name

Loranger of handed out 1 PS

b exclusionary IPS

to lease length

Locon figure more

L, default gateway (192.168. X. 2)

Lamenter parent domain exist NAIT. CA'

Ls Server name ex' DCi'

bioactivate scope

Loright click scope

Lo properties

↳"Always dynamically Update DNS records'

DHCPs Clients

Logo to client machines

Lo Pr 4 settings

(obtain IP address automatically

Lo test by pinging

DHCP M MC -0 domain-o de-o scope-address leases

Reservations. DHD MC -o domain-ode-o scope -o reservations

Adding Client to Domain:

Lalong into Client with local admin acc.

Lo r-click win, system,

Lo advanced system settings

* Lo member of DOMAIN. name

L] Administrator @Domaininame'

DNS MCs DCi-o FW -1-2-0 domains clients should be here

AD users & computers MC. Computers-o clients Should be here

00structure (AD Vic)

bounder domain (right click)

Lo new Organizational Unit

↳sex 1st Admins

NW USERS:

Lo-right click ou

is new user

is Quinn Admin'

Lo clear "must change password"

l To MARE ADMIN

→AD V}, C -J domain-o users

↳Domain Admins -o members

Lo type in 'Quinn Admin'

Lo Check names

Look.

Powershell & Replication

J Powershell -8 "Rep Admin $SynA:IAdp" A-sync all name contexts hosted on home server

Id -ID servers by distinguished name in message 5  
h - Pause For possible user abort after every message

s syncing Partition' DC = Forest Drs Zones,

↳DC = domain, DCI calo replication of forest DNS info

-01 Syncing Partition' DC = Domain DNS Zones, # C-domain, DC = Ca

Lo replication of your domain DNS info

o Callback message tells you which dc is root (from: root, to : secondary)

(15-8 clear screen

"Rep Admin show Rep!" ,

'Default-First-site-Neame DC # J this is the dc you're on

Default-First-site -Name \ DC # via R PC -0 which partition was replicated ! the replication partner

'Last attempt @Htimel was successful' -o last replication attempt & i fit worked

"RePAdmin lice" e knowledge consistency checker

Lo verifies if replication is UP to date

is

"Rep Admin Rep Summary"

Ly shows last replication is if there were any errors

Replication:

AD sites ; Services MC

to Sites-o default-first-site-name

Lo servers -DC # x NTPCS settings

Lo right click-replicate

Event Viewer

Lo Applications ; services Logs

LepirectoryJervice

PowerShell Qu's & users

Ly" New -AD Organizational Unit -Name "folder name." Path "DC = domain, DC-ear" . -sou

"New -AD Organizational Unit -Name "folder name" -Path iou-folderal, DC = domain, DC-car" Honest ed 00

"New -AD computer -Name "client" -path "m" -8 make anew user
|   |   |   |
|---|---|---|
||||
||||
||||
||||
