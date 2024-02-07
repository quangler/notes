LAG - Link Aggregation Group (this is also known as EtherChannel)

- 8 links per LAG, 2 LAGs per switch (in packet tracer)

  

all packets need to be on the SAME link for LAG (because it can't make a loop so it won't do that)

- link aggregation algorithm + RSTP = no packets loss even when links are lost
  

  

**Implementation Restrictions:**

- link speed must be same
- duplex settings must be same
- spanning-tree path cost must be same
- allowed VLANs must be same
- native VLAN must be same
- LAG link member cannot be a destination for port-mirroring

  

**Static LAG (manually set) / LACP (link aggregation control protocol) (dynamic):**

no protocol is used, both ends of each link are manually configured to be part of a LAG (not recommended in LAN (static)

  

turning it on

- 'interface range gigabitEthernet 1/0/1-4'
- 'channel-group 1 mode [<active> | <passive> | <on (only for static)>]'

  

**Mode types:**

- Active - exchange LACP frames with neighbour switch regardless of neighbour switch config
- Passive - exchanging LACP frames with neighbour switch only upon receiving LACP frame from neighbour switch
- (this means at LEAST one of them needs to be active to do anything)
  

  

Link Aggregation - runs on top of 802.3 (rather than spanning tree that runs on top of 802.2 which acts as a translating layer for 802.3)

Spanning Tree (802.1D in todays world) - runs on top of 802.2

  

Link Aggregation commands:

  

- config#'interface range gigabitEthernet 1/0/1-4'
- config-if#'switchport trunk native vlan [native vlan number]' #important
- config-if#'switchport trunk encapsulation dot1q'
- config-if#'switchport mode trunk'
- config-if#'channel-group [group #] mode active
- config-if#'spanning-tree link-type point-to-point'

  

(more basic version)

on switch 1

- int range 1/0/3-4
- switchport mode trunk
- channel-group 3 mode active
  

on switch 2

- int range g0/1-2
- switchport mode trunk
- channel-group 3 mode active