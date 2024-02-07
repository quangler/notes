HSRP NOTES:

  

interface vlan 10 || doing in this in vlan 10

  

ip address <a.b.c.d> <subnet> || a.b.c.d is replaced by the second or third highest address || (.253 or .252)

  

standby version 2 || this sets the HSRP version to 2

  

standby 10 ip <a.b.c.d> || a.b.c.d is replaced by the virtual default gateway (.254)

  

standby 10 priority <#> || 100 is default, the higher the better

  

standby 10 preempt || forces the highest priority to become the active router

  

standby 10 track <int> || allows you to monitor the interface for HSRP

  

show standby brief || to show the HSRP info you need

  

======================================================================================================================================================================================================================================================================================================

  

HSRP TEMPLATE

  

L3 ROUTING:

  

ACTIVE L3 ROUTER (HIGHEST PRIORITY):

!

int vlan 10 (vlan id for gateway)

ip address 172.20.127.253 255.255.255.0 (vlan ip/mask)

standby version 2

standby 10 ip 172.20.127.254 (Ghost router)

standby 10 priority 105 (Higher than other router)

standby 10 preempt

standby track G1/0/1 (Int to virtual router)

standby track G1/0/2 (Int to network)

!

  

NON-ACTIVE L3 ROUTER:

!

int vlan 10 (vlan id for gateway)

ip address 172.20.127.252 255.255.255.0 (vlan ip/mask)

standby version 2

standby group# ip 172.20.127.254 (Ghost router)

standby group# priority 100 (Lower than other router)

standby group# preempt

standby track G1/0/1 (Int to virtual router)

standby track G1/0/2 (Int to network)

!

  

ROUTER:

  

ACTIVE L3 ROUTER (HIGHEST PRIORITY):

!

int G0/0 (int for gateway)

ip address 172.20.127.253 255.255.255.0 (gateway ip/mask)

standby version 2

standby G0/0 ip 172.20.127.254 (Ghost router)

standby G0/0 priority 105 (Higher than other router)

standby G0/0 preempt

standby track G1/0/1 (Int to virtual router)

standby track G1/0/2 (Int to network)

!

  

NON-ACTIVE ROUTER (LOWER PRIORITY):

!

int G0/0 (int for gateway)

ip address 172.20.127.252 255.255.255.0 (gateway ip/mask)

standby version 2

standby group# ip 172.20.127.254 (Ghost router)

standby group# priority 100 (Lower than other router)

standby group# preempt

standby track G1/0/1 (Int to virtual router)

standby track G1/0/2 (Int to network)

!