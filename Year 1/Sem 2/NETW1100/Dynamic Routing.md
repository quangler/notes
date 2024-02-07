> [!caution] This page contained a drawing which was not converted.   

**Interior Gateway Protocols**

  

road sign, or **distance vector** - only sees the next hop

  

**RIP** - Routing Information Protocol

**EIGRP** - Enhanced Interior Gateway Routing Protocol

  

road map, or **link state** - sees the whole network

  

**OSPF** - Open Shortest Path First

**IS-IS** - Intermediate System to Intermediate System

  

**Exterior Gateway Protocols**

  

Path Vector

  

**BGP** - Border Gateway Protocol

  

**Dynamic Routing Terms**

  

**Autonomous System**

- a group of routers under the same IP network prefix (/?) and under administrative control of one entity. (they can all communicate to each other)

- the connection out of the network is called a **border router**

  

**Neighbors**

- routers connecting to each other form an adjacency and become neighbors.

  

  
  
  
  
  
  
  
  
  

  
  
  
  
  

  

- only neighbors can communicate with each other

  

**Administrative Distance**

- the first thing a router looks at to determine which route source to use if the router communicates with more than one other.

- the lower the administrative distance, the more trusted, and it will by default use this link.

  

- connected interface 0

- Static Route - 1

- EIGRP - 90

- OSPF - 110

- IS-IS - 115

- RIP - 120

- **DEFAULT STATIC ROUTE - 254(terry says 255)** > only ever used if NOTHING else is connected > question on test will look for 255

- unknown - 255?

  

**Routing Algorithms**

- RIP - Bellman-Ford

- OSPF - Dijkstra

- IS-IS - Dijkstra

EIGRP - Diffusing Update (DUAL) - Cisco Proprietary

  

**Dynamic Routing Components**

- Data Structures

> neighbor table

> topology table

> routing table

  

**Dynamic Routing Operation Fundamentals**

1. Directly connected routes added to routing table
2. static routes (if configured) added to routing table
3. neighbour discovery & establishment
4. network discovery - exchange of connected routes with neighbours
5. exchange of complete routing table entries with neighbours
6. achieve convergence !

  

**Device Vector Protocols: know thy neighbor**

- RIPv1 - 1st gen, legacy

- RIPv2 - simple, not scalable

- IGRP - obsolete, cisco proprietary

- EIGRP - cisco developed, proprietary, RFC as of 2014 (the one)

  

**Link State Protocols: know thy whole neighborhood**

- OSPF - Dijkstra algorithm - it is an open standard!

> metric - "cost" or "shortest path"

  

**Classful vs Classless**

  

**Classful**

- does not send subnet mask info in routing updates

- does not support subnetting or VLSM

- RIPv2 - classful by default

  

**Classless**

- Includes subnet mask information in routing updates

- supports VLSM and subnetting

  

**Routing Table**

R 172.16.4.0/28 [120/2] via 209.165.200.226, 00:00:12, Serial0/0/0 #important

  

**R** - route source

**172.16.4.0/28** - destination network

**[120** - administrative distance

**2]** - metric (for ospf it is cost)

**209.165.200.226** - next-hop IP

**00:00:12** - route timestamp

**Serial0/0/0** - outgoing interface

  

**Levels of Routes**:

  

**Ultimate Route - in the routing table**

  

**/ Level 1 Route**

- the subnet address (192.168.1.**0**/24)

  

**Level 1 Parent Route**

- only a parent route if it is a **supernetted** address

  

**Level 2 Child Route**

- the actual subnet itself (192.168.2.0/24, 192.168.3.0/24, 192.168.4.0/28)