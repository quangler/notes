**DNS**

to see ip address of a site, "dns.qry.name" in wireshark

  

UDP is used predominantly inside the LAN for small data (screaming into the void)

UDP is good for video and audio which is **real-time**

  

TCP - acknowledges stuff, but takes time (think a solid link)

TCP - does segmentation of DATA (UDP cant)

  

DHCP - always uses UDP (it emulates TCP with the back and forth but it is UDP)

  

port 68 - source port - (for DHCP client port) - only client reserved port

port 67 - destination port - (DHCP server port)

  

after ACK the computer can do stuff

within DHCP, there is a thing called DAD - duplicate address detection

-this means that after DORA, the client sends out ARP probes to the same IP it has, **IT DOES NOT WANT A RESPONSE**

  

**ARP probe (starts from client - IP 192.168.1.8)**

sender MAC address, the device's MAC

sender IP address, 0.0.0.0

target MAC address, 00:00:00:00:00:00

target IP address, 192.168.1.8 ~~-~~ (does not want a response)

  

'dns&&ip.src==192.168.1.1' - shows the dns info for a specific IP address

'(dns&&ip.src==192.168.1.1)||(dns&&ip.dst==192.168.1.1)' - shows the dns info (both send and receive) for a specific IP

  

DNS - max DATA size of 512 bytes

  

**TFTP**

client starts session with TFTP server,

-sends a write request (asks if they can copy the config) | block 0

server - ACK | block 0

-data packet | block 1

server - ACK | block 1

  

TFTP (service of segmentation) | Layer 7 (app layer)

- breaks up the file into readable chunks of 512 bytes (23 ms of data) - 8 bits of silence turns into just 1 bit of silence to save space
- the first chunk is block 0, meaning it doesnt have data
- then it acknowledges it (block 0)
- data packet (block 1)
- acknowledge (block 1)

each block is 2 packets each - data, acknowledge

  
  

SSH needs:

hostname

domain name

secret password

username

  

------------------------------------------

SSH

ex.

hostname s1

enable secret cisco

username admin password class

ip domain-name bubba.local

crypto key generate rsa

1024

ip ssh v 2

line vty 0 15

login local

transport input ssh

------------------------------------------

change key size to min of 768 or you're using ssh v1 (it goes in chunks of 512 (?) )

  

new thing for SSH:

restriction (ACL)

  

NMS - network management spaceship (in modern day, it's a server running a network managing software)

- NMS the only thing with access to remoting in to everything
  

  

**ON EXAM**

  

**nat and default routes**

**house keeping**

**this stuff**

  

ip access-list standard <ForRemoteAccess>

permit host 172.16.0.1 - used for specific hosts

permit host 172.16.0.7

permit 172.16.0.0 0.0.0.255

line vty 0 15

login local

transport input ssh

access-class <ForRemoteAccess> in

  

know how to capture data (the command)

and where the data is captured (between what devices)

  

know layer 2, layer 3, layer 4 and how to distinguish between them

|   |   |   |   |   |
|---|---|---|---|---|
|destination|source|type||layer 2|
|protocol|source|destination||layer 3|

|   |   |   |   |
|---|---|---|---|
|source|destination||layer 4|

Configuring router to forward DHCP broadcast:

R1(config)#=='int g0/1'== > will forward any traffic received by g0/1 v

R1(config-if)#'==ip helper-address 172.0.225==' > the address of the DHCP server

R1(config-if)#'==do write=='

  

Configuring router as a DHCP server

config#'==ip dhcp pool <LAN-X_DHCP>==' - LAN-X_DHCP is the name of the lan

dhcp-config#'==network 192.168.0.0 255.255.255.0=='

dhcp-config#'==default-router 192.168.0.254=='

dhcp-config#'==dns-server 199.185.49.17=='

dhcp-config#'==do write=='

straight up mandatory "house-keeping ACL"