ospf, then HSRP, explicit IP network statements

PAY ATTENTION TO AUTOCOST

  
  
  
  

OSPF NOTES:

  

router ospf <#> || any number, doesn't really matter

  

router-id <a.b.c.d> || the highest ID number gets to be the master router, in IP format, (ex. 1.1.1.255)

|| you want to set this for any IP that is connecting to an OSPF device

  
  

ip ospf priority (?) || for setting priority (goes above router ID) on an individual interface

  
  

auto-cost reference-bandwidth <1000> || 1000 sets gigabit to the standard. make sure its the same on all

  
  
  

network <a.b.c.d> 0.0.0.0 area 0 || a.b.c.d is the IP OF YOUR OUTGOING NETWORK ON THAT DEVICE. 0.0.0.0 is

|| saying that it is a direct connection (interface, best practice) **

  
  

(network <a.b.c.d> <a'.b'.c'.d'> area 0) || network finder, not best practice (subnet going out, then wildcard of subnet)

  
  

(network 0.0.0.0 255.255.255.255 area 0) || identifies all networks, not best practice, but it works.

  
  

default-information originate || only if you are trying to propagate default route info throughout ospf

|| default route info HAS to be on THAT device if this command is turned on

  
  

show ip route || this is to see the connections of OSPF on that device

  

show ip ospf neighbor || this is to see the OSPF neighbor table (direct connections)

  

show ip protocols || this shows what this will tell you what ospf protocol is being used on a device

  

show ip ospf || this shows the ospf id number

  

show ip ospf database || this shows the ip ospf database

  

show ip int br | e una || show the interfaces (excludes the ones that are unavailable)

  
  

==================================================================================================

==================================================================================================

==================================================================================================

  
  

OSPF TEMPLATE

  

ORIGINATING ROUTER:

  

!

ip route 0.0.0.0 0.0.0.0 A.B.C.D

ip route 0.0.0.0 0.0.0.0 INTERFACE

router ospf # (Any. Keep the same.)

router-id 1.1.1.254 (highest number wins for designated router)

auto-cost reference-bandwidth # (same on every router)

network 192.168.255.254 0.0.0.0 area 0 (router int ip)

default-information originate

do write

!

  

MAIN (MOST CENTRAL) ROUTING DEVICE:

  

show run (for vlans to use)

  

!

router ospf # (Any. Keep the same.)

router-id 1.1.1.255 (Highest ID)

auto-cost reference-bandwidth # (same as above)

network 192.168.13.254 0.0.0.0 area 0 (each configured VLAN)

network 192.168.14.254 0.0.0.0 area 0 ^

network 192.168.15.254 0.0.0.0 area 0 ^

network 192.168.255.253 0.0.0.0 area 0 (int ip connected to router)

!

  

ROUTING DEVICE NOT CONNECTED TO ROUTER:

  

show run (for vlans to use)

  

!

router ospf # (Any. Keep the same.)

router id 1.1.1.1

auto-cost reference-bandwidth # (same as above)

network 192.168.10.254 0.0.0.0 area 0 (each configured VLAN)

network 192.168.11.254 0.0.0.0 area 0 ^

network 192.168.12.254 0.0.0.0 area 0 ^

network 192.168.17.254 0.0.0.0 area 0 ^

network 192.168.16.253 0.0.0.0 area 0 ^

!

  

show ip osfp neighbor