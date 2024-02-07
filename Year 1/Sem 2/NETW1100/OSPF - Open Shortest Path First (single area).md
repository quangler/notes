- OSPF is old (1989)

  

**OSPF areas**

- the backbone area is **Area 0** always

- they are autonomous systems - meaning a single organization management

  

**OSPF features**

- the outer most router is an "autonomous system boundary router"

- a router that is the interface of two **AREAS** is an "area border router"

- still converges - all routers know all other routers in a network

  

**OSPF Routing Algorithm (Dijkstra)**

- the only method is cost, it looks for lowest cost path

- anything 100 mbps or faster = cost of 1

  

create an LSDB (link state database)

- this contains the link state, the link cost

  
  

**OSPF: The beginning.**

- sends a "hello" packet to all of its neighbors.

- it does this to form an **adjacency**

- a neighbor is a router that shares the same link and is running OSPF protocol

  

**OSPF Neighbor Process**

stage 1 - down state: this is before the router knows about its neighbors (immediately after pressing enter to make it OSPF)

  

stage 2 - init state: R2 and R3 receive the hello packet from R1 - put it in the **OSPF neighbor table**

  

stage 3 - two-way state: R2 and R3 are sending hello packets **back**

- this is where they find out neighbor IDs, and can become adjacent

  

stage 4 - ExStart stage - specifies that DR & BDR (designated and backup designated routers) have been elected.

- initial sequence number for adjacency formation is also selected

  

stage 5 - exchange state - OSPF routers exchange Database Descriptor (DBD) packets

- contain LSA (Link State Advertisement) headers that tells routers the full content of the Link State Database (LSDB)

- they compare the info from their own to see if updates need to be made)

  

stage 6 - loading state - all the info is syncing up

  

stage 7 - full state - all functioning, everything is fully synced, normal operations.

  

**224.0.0.5 - hello packets are sent to THIS multicast address (all OSPF routers)** #important

**224.0.0.6 - all OSPF DR (designated) / BDR (backup designated routers)**

  

**Designated router**: (method one)

- command (OSPF Priority) - based on router ID (ALWAYS HIGHEST)

- no router ID? - highest loopback ID

- no loopback? - highest physical interface IP

  

(method 2 - terry method)

- command - interface priority (decimal value, 0-255) - default is 1 (still looking for highest)

  

setting OSPF metric

- auto-cost reference-bandwidth ?

- the ? is the amount of mbps that will be the reference (so 1000 is gig, 10000 is 10 gig) > this part might be wrong !

  

you can manually change the cost of a single interface (dont do that)

  

R 172.16.4.0/28 [120/2] via 209.165.200.226, 00:00:12, Serial0/0/0 #important

  

**R** - route source

**172.16.4.0/28** - destination network

**[120** - administrative distance

**2]** - metric (for ospf it is cost)

**209.165.200.226** - next-hop IP

**00:00:12** - route timestamp

**Serial0/0/0** - outgoing interface

  

**Passive interface does NOT send hello packets** #important

- passive-interface g0/0

  

not necessary to mark point to point routers, but you can (within OSPF)

  

frame relay (dont worry about)

- protocol that does not support broadcast messages

  

**OSPF Designated Router (DR)**

- the point is to have the designated and backup designated to be the only 2 who "collect" all info and redistribute it out

-they use 244.0.0.6 to communicate (still multicast)

  

**OSPF Router ID**

"show ip protocols"

"show ip ospf"

"show ip ospf interface"

  

'router ospf x' - where x is a number that represents the router ID (doesn't need to be the same as the neighbor, but should be)

  

**Initial Config: Single Area OSPF**

interface loopback0

ip address 172.16.1.1 255.255.255.128

ip ospf network point-to-point

!

interface g0/2

ip address 192.168.0.253 255.255.255.252

ip ospf priority 200

!

router ospf 14

router-id 172.16.255.255 - sets the router ID

passive-interface g0/0 - sets this interface to a passive interface

network 172.16.1.1 0.0.0.0 area 0 - this looks for this router specifically throughout that interface

**^^THIS IS NOT ALL THE COMMANDS**

  

**OSPF does not go through TCP or UDP (it is right in the IP packet)**

- protocol field of 89

  

we don't do authentication in first year,

- **Au Type and authentication field contain all 0's for us** because we dont use it

  

**OSPF Packet Types:**

1 - hello - discovers and builds adjacencies between neighbors

2 - database description (DBD) - checks for database sync between OSPF routers

3 - link-state request (LSR)

4 - link-state update (LSU)

5 - link-state acknowledgement (LSAck)

  

once convergence has happened, **hello packets are sent by default every 10 seconds** #important

- the dead interval timer (40s) starts, after 40 seconds, it flushes that link

  

why would you use multi area OSPF

- you want to be able to summarize large routing tables (does not summarize by default)

  

typical exam network - will have around 10-11 routers