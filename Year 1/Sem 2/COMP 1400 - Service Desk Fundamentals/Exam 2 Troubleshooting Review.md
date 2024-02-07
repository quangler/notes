the one question:

- you will have to know some of the switches for searching he registry - RegQuery : have to interpret some of the switches on it (its common sense) - true false question

  

desktop troubleshooting:

server troubleshooting:

network troubleshooting:

  

**Desktop Troubleshooting**

  

Main windows system stuff:

- install locations (program files / program data / appdata)

admin shares

system 32

registry

  

utilites built in to windows

- regedit, tasklist, taskkill, DISM + SFC, etc.

  

third party tools

- disk checkers, MSRA, remote connectivity analyzer, etc.

  

**Windows 10 reset**

  

windows 10 has a refresh, reset or restore function

  

**Refresh** - refresh windows without deleting any personal files or apps

- third party apps will be deleted

  

**Reset** - will remove everything and reinstall windows

  

**Restore** - goes to a specific point in time as a restore - they are auto created if they are enabled (can create manually)

  

**DISM + SFC**

- deployment imaging servicing and management - compares your windows image to a known good windows repository (default looks at online)

  

System file checker - compare protected system files against a local cache

  

sfc /scannow - runs scan

  

**when do we use them?**

windows wont boot, or its acting weirdo

- run DISM command first, then SFC second #important

both commands take time

  

**App installations**

  

Program Files - 64 bit apps

  

Program Files (x86) - only created on 64 bit windows for backwards compatibility (it is 32 bit apps)

  

**Program Files & Program Files (x86) need administrator rights**

  

ProgramData - less restrictive because it is a hidden folder, can be edited by anyone. usually info for multiple users - shared cache, shared settings, shared databases (**used if a program needs to write something** - so it doesnt have to ask for admin privs)

  

users\<username>\appdata - only installs for a specific user - don't need admin privs. (discord for ex.)

- roaming - follows you between pcs in a domain environment

- local - doesn't follow you between pcs

- LocalLow - for temp files and the like

  

**Desktop troubleshooting 3rd party**

  

IP/port scanner - can scan for IP addresses on the network, sometimes for open ports too (used for security sometimes)

- angry IP scanner

- Advanced IP scanner

- nmap, zmap

  

Disk health checks - checks the health of hard drives - shows drive info like power-on hours, temperature, SMART checks

- tools written at the bit level

- seatools is one of the tools for this

  

Email Header Analyzer

- checks header info to see where the email came from (see if it is legitimate)

- allows you to read the header info in human words

- mx toolbox, appriver - these are tools to read them

  

Storage Scanner - used to assess free storage or find the large files taking up space

- breakdown by location, size, and file type

- with admin perms sometimes you can delete files

- WizTree, TreeSizeFree - tools for this

  

MSRA - microsoft support and recovery assistant - utility that can do diagnostic for office / windows 10 configs

- just for microsoft stuff

  

Remote Connectivity Analyzer - used to check if you can connect to exchange

- useful to check for new imap / pop3 servers

  

ForensIT - migrates profiles over

- keeps everything the same after transferring your profile (keeps all settings and personalization)

  
  

Shadow Copies - VSS - allows you to do system restores for specific files/folders

- comes built in with windows,

- act like snapshots - point-in-time backups of data and files

- can be used by third party applications

- system restore, windows server backup, shadow protect

**DOES NOT REPLACE A ROBUST BACKUP SOLUTION** #important

  

Shadow Copies ext.

- MS recommends a dedicated drive for shadow copies ( it will run out of space )

- if it has been running - "restore to previous version"

  
  

**Server Troubleshooting**

event viewer

file permissions

gpo modeling and testing

ad health / replication

dns and dhcp issues

  
  

File sharing settings: by default they are inherited

- Share permissions

- NTFS permissions

  

**Special NTFS Permissions**

- traverse - pass through a folder to folders below

- list - list the contents of a folder

- read attributes - read the attributes of a file in the folder

- write attributes - change the attributes of a file in a folder

- change permissions - change permissions of the contents of a folder

- take ownership - take ownership of a folder

etc.

  

an administrative share is created by default on each volume ([\\<PCname>\c$](file:///\\<PCname>\c$))

  

**Windows Utilities**

GPResult - shows the result of GPOs on the system for this user

ipconfig - shows network settings

nslookup - for dns query

traceroute - follows a ping

systeminfo - info about a system

tasklist/taskkill - find and kill tasks

event viewer - lets you view event logs - show errors and warnings

  

**Troubleshooting Methodology**

general approach:

- identify problem

- establish theory

- test theory to see if youre right

- establish plan of action to resolve

implement the solution or escalate

verify full system function

document

  

**ABC 5 steps progrm** #important

bottom up, top down, other one

  

1. **check the political layer**
2. **Check the physical layer first**
3. **do a quick ipconfig /all**
4. **ping yourself 127.0.0.1**
5. **ping neighbor > can you connect to lan**
6. **ping gateway**
7. **ping remote IP address (8.8.8.8)**
8. **ping google.ca - dns**
  

  

bottom up:

start at physical layer and work your way up

  

divide-and-conquer:

- you have an idea of where some issue may start - "i think it is network issue"

  

top down:

- from application layer down, (we usually don't use this. only if everything else is working except 1 app)

  
  

**Network Troubleshooting Tools**

- protocol analyzer

- cable analyzer/tester

- SNMP monitoring tools

- centralized log management

- WiFi analyzers

  

**UNICAST** - know the logical and physical address of the target

**BROADCAST** - communication message when you know nothing

**MULTICAST** - sends to multiple addresses (you know just the logical address)

**DEFAULT GATEWAY** - the source out to the greater inter/intranet￼**TCP** - connection-based protocol with more overhead - connects to a specific guy and talks to him￼**UDP** - connectionless protocol with less overhead - screams into the void￼**IPV4** - a 32 bit address for a network interface

**IPV6** - a 128 bit address for a network interface

**CIDR** - the name of the fully qualified guy with subnet (192.168.1.25/24 as ex.)

**APIPA** - 169.254.x.x - used when you don't have an IP address in ipv4 from DHCP

**DHCP -** dynamic host configuration protocol

**DNS** - domain name system, converts IP to name

**ICMP: Ping, Tracert & Pathping** - tool used for network troubleshooting

**ARP/RARP** - procedure for mapping a dynamic IP address to a permanent physical machine address in a lan

**NSLOOKUP** - a command used to send a dns query to the dns server for a specific hostname

**FTP/HTTP/TFTP** - file transfer protocol, hyper text transfer protocol, trivial file transfer protocol

**ISP** - internet service provider

**AUTHENTICATION** - checks to see if you are who you are

**AUTHORIZATION** - do you have the access you need for something?

**PUBLIC IP** - can only be 1 on the internet (private are not public)

**SWITCH** - ￼**ROUTER**