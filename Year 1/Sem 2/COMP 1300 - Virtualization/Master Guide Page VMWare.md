**ESXi DCUI**

- hostname

configure network (f2)

DNS configuration > "use the following DNS server addresses and hostname" (space bar)

set IP of DNS server, and FULL hostname (ESXi.ist.com)

  

- setting management NIC

configure network (f2)

Network Adapters > any NIC with and x next to it is enabled for management (space bar)

  

- setting IP address

configure network (f2)

IPv4 Configuration > "set static IPv4 address and network configuration (space bar)

set IP, subnet mask, default gateway

  

- ping test

(f2) > test management network

put IPs you want to try and hostname to check for DNS

  

**ESXi Web Interface**

- getting to it

go into browser of VM that has connectivity to ESXi server

type IP into browser > 10.1.1.10 (ex)

root | P@ssw0rd

  
- changing NTP server

  

under host, manage tab > system > time & date

edit NTP settings > use network time protocol radio button

start and stop with host | add NTP server (time1.srv.ualberta.ca) > save

  

- monitoring & logs

monitoring | click on the monitoring tab > performance

logs | monitor tab > logs > generate support bundle

  

- showing licensing

manage tab > licensing

  

- setting DNS servers

networking tab (left side) > TCP/IP stacks > Default TCP/IP stack

edit settings, configure to liking

  

- making a datastore

storage tab (left side) > new datastore > create new VMFS datastore

select storage device and name of datastore (ESXi01local200GB)

  

- transferring ISOs to datastore

storage tab (left side) > select datastore

datastore browser > (either create directory or just upload)

*this will pull files from your adminWS that you are using to connect to the web client

put ISO in and let it upload

  

- creating a VM

Virtual Machines tab (left side) > Create/Register a VM

- either do this from a new VM (using ISO we uploaded) or deploying a VM (OVF or OVA file)

name of VM | Compatibility | OS > select datastore to put VM on

configure VM settings here (make sure to put the right ISO in at this point)

  

- creating and configuring accounts

**creating a user**

manage tab > security & users > users

add user > username | description | password

  

**assigning permissions**

right click host (top left) > permissions

add user > select created user | select pre-set role (or select the boxes below)

(propagate to children is important to be able to access things inside of ESXi, without it you will be able to only see ESXi monitor / manage)

you should be able to sign in with this account now with proper permissions