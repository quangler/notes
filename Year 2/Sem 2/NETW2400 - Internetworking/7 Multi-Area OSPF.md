### Link-State Routing Protocols
Link-state routers originate information about:
- themselves (IP addresses)
- their connected links (number and type of links)
- state of those connected links
Information is flooded to all routers in network as changes in link state occur
- each router makes a copy of info received and forwards it
- each router independently calculates the best path to each destination network
- each router creates a shortest path tree with itself as the root
- each router maintains a map of the network
After the initial exchange of information, link-state updates are only sent if topology changes
- All routers will have convergence - the same topology database
- Routers send hello messages to maintain neighbor relationships
- if no updates have been sent, link-state route database is refreshed after 30 minutes
### Issues with large OSPF area
**Large link-state database (LSDB)**
- LSDB maintain an entry for every network in the area, even if not every route is selected for the routing table
- too many routers would make the LSDB very large and increase the load on the CPU (router gets too many LSAs)
**Frequent SPF algorithm calculations**
- in a large network, changes will happen so the routers spend many CPU cycles recalculating the SPF algorithm and updating the routing table

### OSPF Areas
OSPF uses areas for scalability
- can divide routing domain (autonomous system or AS) into smaller, multiple, distinct areas that can help to control routing update traffic 
- single-area OSPF uses a single area (area 0 - backbone area)
- link-state info is flooded through AS
- each router maintains a database that describes the topology of the AS
	- within an area, OSPF routers have the same topology database

**OSPF is a hierarchical routing protocol**
- when network is defined, the backbone consists of only some devices
- backbone routers service and coordinate the routes and traffic to or from routers not in local network
**Multi-area OSPF** is a **two-layer area hierarchy** using a **backbone area interconnecting regular areas**
- useful in larger network deployments to reduce processing and memory overhead
- reduces complexity and the size of the link-state database
- reduces the time it takes for SPF algorithm to happen as info sent from one area into another is only summarized info of the LSDB

All areas must interconnect to the backbone area (area 0)
- interconnecting routers are called **Area Border Routers (ABR)**

### Routers in Multi-Area OSPF
**Internal** - Routers with all their interfaces within the **same area**
**Backbone** - Routers with at least one interface **connected to area 0**
**ASBR (Autonomous System Boundary Router)** - routers that have at leas one interface connected to an **EXTERNAL NETWORK** (another autonomous system)
**ABR (Area Border Router)** - Routers with interfaces attached to **MULTIPLE AREAS**
**DR (Designated Router)** - whenever another router gets information of an update, it sends to the DR. The DR then updates and sends the information to all other routers.
**BDR (Backup Designated Router)** - The backup for the DR.
**Autonomous System** - the whole entire OSPF (not just a single area, but all OSPF connected things)
### OSPF LSA Messages
**Within an Area** - types 1 and 2
**Between Areas** - types 3 and 4
**Throughout the entire autonomous system** - types 5 & 7

| Type Code | Type                           | Description                                                                                                                                 | quick notes                                                                      |
| --------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| 1         | Router LSA                     | **Produced by every router** - Flooded through a single area - Contains router's links, interfaces, link states, and costs.                 | sent between routers in the same area - don't go past ABR                        |
| 2         | Network LSA                    | **Produced by every DR** - Contained within an area - Lists all routers in a multiaccess network                                            | give other routers info about **multi-access networks (?)** within the same area |
| 3         | Summary LSA for ABRs           | **Produced by ABRs** - sent into an area to advertise destinations outside the area                                                         | used by ABRs for between areas                                                   |
| 4         | Summary LSA for ASBRs          | **Originated by ABRs** - sent into area by ABR to advertise the IP addresses of the ASBRs                                                   | ABRs send summary information when there is an ASBR                              |
| 5         | Autonomous System External LSA | **Originated by ASBRs** - flooded through the whole OSPF autonomous system - advertises destinations external to the OSPF autonomous system | area connected to external network, advertised by ASBR                           |
| 7         | NSSA External LSA              | **Originated by ASBRs in an NSSA** - not flooded through the OSPF AS but only to NSSA - similar to Type 5                                   | ASBR advertising external network - turns into LSA 5 by ABRs                     |

### OSPF LSA Messages and Areas
**Normal Areas**
- default type of area
- standard config rules
- LSA types 1-5 are used

**Stub Area**
- depending on the type of Stub area, LSA 3-5 are blocked and replaced by default routes
- concept is to reduce number of inter-area or external LSAs that get flooded into a stub area
- has a single entry point into the area
- LSAs 1 & 2 are still propagated throughout the area
- LSA 3 are sent into the area by the ABR
- **LSAs 4 & 5 are blocked**
- **Default route is injected to reach the ABR**

**Totally Stubby Area**
- LSAs 1 & 2 are still propagated throughout the area
- **LSAs 3, 4, and 5 are blocked**
	- **default route is injected to reach the ABR**
- all routers must be configured as `stub`
- ABR must be configured as `stub no-summary`

**Not-So-Stubby Area (NSSA)**
- **allow type 1, 2, 3, and 5 LSAs**
- allows an area to remain a stub, but **carry external routing information (type 7 LSAs) from its stubby** end back towards the OSPF backbone
- a stub area that has a second entry point - an ASBR to non-OSPF domain network
- **ASBR in NSSA injects external routing information in the form of LSA type 7s into the backbone and the NSSA area** - ==rejects the external routing information coming from the ABR==
- The **ABR** convers the **TYPE 7** LSAs from **NSSA** into **TYPE 5** LSAs and advertise to the other areas
	- routes learned via Type-7 LSAs are denoted by either a default "N1" or an "N2" in the routing table (Relative to E1 and E2)

### Routing Table information
- **IA** - inter-area
- **E1/E2** - extended routes
- **N1/N2** - type 5 learned by Type 7 LSAs (NSSA)
### Multi-area OSPF Configuration
#### Basic:
```R1
router ospf 1
router-id 1.1.1.1
network 10.1.1.254 0.0.0.0 area 1
network 10.1.2.254 0.0.0.0 area 1
network 192.168.10.1 0.0.0.0 area 0
```
#### Stub Area
`area 51 stub`
#### Totally Stubby Area
`area 51 stub no-summary`
#### Not-So-Stubby Area
`area 13 nssa` (normal / stub)
`area 13 nssa default-information-originate` (lets ABR inject the default route info from NSSA)
`area 13 nssa no-summary` (act as totally stubby area - no LSA 3)

OSPF Route summarization is not done automatically, but it can be helpful:
```route-summarization
area 1 range 192.168.0.0 255.255.252.0 ! this will be a range of 192.168.0.1-192.168.3.254
```
`redistribute connected subnets` - used on ASBR, generates external route into NSSA area

```Helpful-Commands
show ip ospf neighbor
show ip ospf
show ip ospf interface
---
show ip protocols
show ip ospf interface brief
show ip route ospf
show ip ospf database
```
