### Characteristics and functionality of the First Hop Redundancy Protocols work (VRRP, HSRP, GLBP) 
#### VRRP - Virtual Router Redundancy Protocol - multiple vendors
- virtual router is known as a `VRRP Group`
- comprised of a master virtual router and backup virtual routers
- VRRP Group can use either the IP address of one of the routers, or a different unique address - this is what is set as the default gateway address
- when master router fails, it swaps to router with next highest priority, or highest IP address if priority is equal
- when the original router becomes available again, it automatically swaps over
- VRRP virtual MAC - `0000.5e00.01xx`
- VRRP multicast address - `224.0.0.18`
- can also use authentication
```VRRP-Commands
(R1)
interface f0/0.1
ip address 10.1.1.9 255.255.255.0
vrrp 1 ip 10.1.1.1
vrrp 1 priority 110
vrrp 1 authentication md5 key-string VRRP
------------------
(R2)
interface f0/0.1
ip address 10.1.1.10 255.255.255.0
vrrp 1 ip 10.1.1.1
vrrp 1 priority 90
vrrp 1 authentication md5 key-string VRRP
```

#### HSRP - Hot Standby Routing Protocol - cisco proprietary
- active / standby model - only one active at a time
- shared **virtual router MAC address**
- active router sends hello messages to standby - when those stop the standby becomes the active router
- when HSRP failover happens, the original router doesn't become active again unless the `preempt` command is used
- can use both routers to load balance between two VLANs - use different priorities on each sub interface
- works with IPv4 and IPv6
```HSRP-Commands
(R1)
interface f0/0.10
ip address 10.1.10.9 255.255.255.0
standby 1 ip 10.1.10.1
standby 1 priority 110
standby 1 preempt
-------------------
(R2)
interface f0/0.10
ip address 10.1.10.10 255.255.255.0
standby 1 ip 10.1.10.1
standby 1 priority 90
-------------------
(extra commands)
show standby
show standby <int>
debug standby errors
debug standby events
```

#### GLBP - Gateway Load Balancing Protocol - cisco proprietary
- uses a **single virtual IP address** and **multiple MAC addresses**
- uses **Active Virtual Gateway (AVG)** and **Active Virtual Forwarders (AVF)**
- hosts will have the same virtual IP address, but different MAC addresses associated with the gateway
- the AVG assigns the virtual MAC addresses to the AVFs - each client will send packets to their respective router, if it goes down, another router will assume the role of the original router.
- uses **round-robin load-balancing algorithm** by default - each AVF MAC address takes turns being in the ARP reply for the virtual IP
- when an AVF fails, the AVG will respond for 10 minutes until the redirect timer expires, then it will stop responding to the host with the failed AFV MAC address
- after 4 hours of being down (timeout timer) the AFV gets removed from the group and the clients will have to refresh their ARP table
```GLBP-Commands
(R1)
interface f0/0
ip address 192.168.15.9 255.255.255.0
glbp 1 ip 192.168.15.1
glbp 1 priority 120
glbp 1 preempt
------------------
(R2)
interface f0/0
ip address 192.168.15.10 255.255.255.0
glbp 1 ip 192.168.15.1
glbp 1 priority 110
glbp 1 preempt
------------------
(R3)
interface f0/0
ip address 192.168.15.11 255.255.255.0
glvp 1 ip 192.168.15.1
```
GLBP Interface Tracking:
lower threshold applies when a router loses weight (priority)
- if a router falls below the threshold it loses its active state as a forwarder
upper threshold applies when the router regains weight (priority)
- if a router exceeds this threshold it regains its active role as a forwarder
```GLBP-InterfaceTracking
track 15 interface f0/1 line-protocol

interface f0/0
ip address 192.168.15.9 255.255.255.0
glbp 1 ip 192.168.15.1
glbp 1 priority 120
glbp 1 preempt

glbp 1 weighting 110 lower 85 upper 105
glbp 1 weighting track 15 decrement 30
```
^ this loses forwarding state if the interface goes down

### Understanding how to read OSPF neighbor tables, routing tables.
`show ip ospf neighbor`

| Neighbor ID | Pri | State  | Dead Time | Address      | Interface   |
| ----------- | --- | ------ | --------- | ------------ | ----------- |
| 10.3.3.3    | 1   | FULL/- | 00:00:30  | 192.168.10.6 | Serial0/0/1 |

**Neighbor ID:** the **router ID** of the neighboring router
**Pri:** OSPF priority of the interface - default 1, routers with a priority of 0 will never be a DR or BDR, they will be a DROTHER
**State:** FULL - means router's interface is fully adjacent with neighbor, have identical OSPF link-state databases | can also be DR/BDR
**Dead Time:** amount of time remaining that the router will wait to receive an OSPF hello packet from neighbor before deciding the neighbor is down - resets upon hello packet
**Address:** IP address of **neighbor's interface** that the router is connected to
**Interface:** interface that this router has formed adjacency with neighbor

`show ip route`
O - means OSPF
IA - means OSPF inter area
D - means EIGRP
EX - mean EIGRP external
**E1/E2** - extended routes
**N1/N2** - type 5 learned by Type 7 LSAs (NSSA)
`[110/XX]` - 110 means it is using OSPF, `XX` is the cost of the link (can be changed)
### Multiarea OSPF / Understand characteristics of OSPF type areas (stub, totally stub, NSSA, standard, backbone) and router types. 
we use multiarea OSPF because having one giant area makes a huge link-state database which is harder for the router's CPU - too many LSAs, SPF calculations
- also adds scalability
Routers:

| Internal                                     | router that has all interfaces in the same area                              |
| -------------------------------------------- | ---------------------------------------------------------------------------- |
| **Backbone**                                 | router with at least one interface connected to **area 0**                   |
| **ASBR** (Autonomous System Boundary Router) | routers that have at leas one interface connected to an **external network** |
| **ABR** (Area Border Router)                 | routers with interfaces attached to **multiple areas**                       |

| LSA 1     | ROUTER LSA - every router creates one, has router's links, interfaces, link states, costs - flooded in a single area                                           |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **LSA 2** | NETWORK LSA - every DR creates one on every broadcast / NBMA network, lists all routers in multiaccess network - contained in a single area                    |
| **LSA 3** | SUMMARY LSA FOR ABRs - created by ABRs, sent into an area to advertise destinations outside the area - interarea                                               |
| **LSA 4** | SUMMYARY LSA FOR ASBRs - created by ABRs, sends into an area to advertise the IP address of the ASBR - interarea                                               |
| **LSA 5** | AUTONOMOUS SYSTEM EXTERNAL LSA - originates by ASBR -> converted by ABRs, advertises external destinations to whole OSPF system - sent out by ABRs - interarea |
| **LSA 7** | NSSA EXTERNAL LSA - created by ASBRs in NSSA, only flooded inside of an NSSA - NSSA area                                                                       |

| Normal Area               | LSA 1-5 are allowed                                                                                                                                                                                                                                                                        |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Stub Area                 | LSA 1-3 are allowed - default route is substituted for external routes<br>`area 51 stub` - all routers need this                                                                                                                                                                           |
| Totally Stubby Area       | LSA 1-2 are allowed - default route is injected as a SINGLE LSA 3 to reach ABR<br>`area 52 stub` - all routers<br>`area 52 stub no-summary` - all ABRs                                                                                                                                     |
| Not-So-Stubby Area (NSSA) | LSA 1-3, 7 are allowed - doesn't allow type 5 external LSAs<br>`area 53 nssa` - all routers in area<br>`area 53 nssa default-information-originate` - adds a default route into NSSA to route to external destination - on ABR<br>`are 53 nssa no-summary` - no LSA 3 - all ABRs need this |

### IPv6 characteristics (fragmentation, broadcast/multicast, purpose of extension headers) 
- 128 bit address length
- 8 groups of 4 hexadecimal digits separated by colons (0-9, A-F)
- does **not** support broadcast - replaced by **link-local all nodes multicast group (FF02::1)**
- **IPSec** is built into IPv6
- packet size of **1208 bytes** required without fragmentation
- fragmentation is done by **sending host only** (not the router)
extension headers add flexibility and allow for future enhancements:
- follow the main IPv6 header - presence indicated by the "next header" field, ex.
  43 - routing - allows source of packet to specify path to destination
  0 - hop by hop options - carries information that must be examined by every router along the path of the packet
### IPv6 Router Advertisements/Solicitation and Neighbor Advertisement messages 
| Router Advertisement   | Type 134 | sends message to all devices on the network to inform that it is a router and it is alive - adds some basic routing information      |
| ---------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Router Solicitation    | Type 133 | host can send this message to request for router advertisements from all active routers                                              |
| Neighbor Solicitation  | Type 135 | network members send when joining a network - do this to discover neighbors, update every 30 seconds to make sure info is up to date |
| Neighbor Advertisement | Type 136 | sent in response to neighbor solicitation, or unsolicited by routers to ensure neighbor info is up to date                           |
### IPv6 types 
#### Unicast:
- **Global Unicast** - can be assigned internally, can be accessed externally - 2000::/3 - follow 3-1-4 rule: 3 hextets for **global routing prefix** (ISP assigned), next 1 hextet is **subnet**, last 4 hextets are **interface ID** (unique to host)
- **Link-Local** - for internal routing - communications to routers is through link-local addresses (FE80::/10)
- **Unspecified** - when you have no address and its looking for an IPv6 address (::128)
- **Unique Local** - functions like an IPv4 private address - not advertised on internet (FC00::/7)
- **Embedded IPv4** - IPv4 address embedded inside of an IPv6 address
#### Multicast:
used as a group - identifies a set of devices
- FF00::/8
- source: **unicast**, destination: **multicast**
	- FF02::1 - all nodes (link-local)
	- FF02::2 - all routers (link-local)
	- FF05::101 - all NTP server (site-local)
#### Anycast:
represents a service that might appear on multiple devices
used in content delivery networks or DNS

- Default Route - ::/0
- Unspecified address - ::/128
- Loopback - ::1/128
### IPv6 addresses abbreviation
**Rule 1**: Leading 0's
- 0100 can be 100
- 0000 can be 0
**Rule 2**: double colon
- :: can replace any continual string of 0s
ex. 2001:0d02:0000:0000:0014:0000:0000:0095 can be
2001:d02==::==14:0:0:95 **OR** 2001:d02:0:0:14==::==95
### How Autoconfiguration is done on the IPv6 hosts 
using **SLAAC (stateless address auto-configuration)**
- first sends out router solicitations and listens to router advertisements to find the global unicast prefix
- uses EUI64 which splits the mac address in half, adds `FF:FE` into the middle, then swaps the 7th bit of the new address.
- it could also just randomize it as some OSes are doing this now
uses the `A` flag set to `1`
### DHCP and DNS for IPv6 (SLAAC, stateless and stateful) 
**SLAAC (stateless address auto-configuration)** - uses router solicitations to ask for IPv6 address info (FF02::2) - gets global unicast prefix then uses EUI64 / random number - **client:** UDP/546. **server:** UDP/547
**Stateless DHCPv6** - DHCPv6 server gives host information **other than IP address** - the host makes its own IPv6 address using its MAC address or a randomized number through the use of EUI64. (using SLAAC)
**Stateful DHCPv6** - DHCPv6 server gives host IP address, DNS servers, domain name, etc. (similar to how DHCPv4 works)
DNSv6 - uses AAAA records, reverse lookup zones: `ip6.arpa` - reverse nibble sequence (DEPLOY INCREMENTALLY)
### Routing IPv6 (understand both dual stack methods)
Two methods:
1. **Address Families**: using OSPFv3 you can put both IPv4 and IPv6 on the same OSPFv3 instance - SHARE NEIGHBOR TABLE AND LINK STATE DATABASE
2. **No address families**: using OSPFv2 and OSPFv3 separately you can use IPv4 and IPv6 on the same router in different OSPF instances