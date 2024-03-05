IPv6 only forwards through interface (not global like IPv4)

### Basics of IPv6 Routing
routing - sending packets from one network to another
routers - devices responsible for interconnecting networks (determine best path, forward packets)

#### Directly Connected Networks
shows up as `C` for directly connected when using `show ip route`.
In IPv6 - `show ipv6 route` shows both `C` for directly connected _AND_ `L` for local address
- Local routes allow the router to process packets sent to itself more efficiently
#### Static Routes
commonly used when routing from a network to a stub network (only one exit in network)
`ip route` or `ipv6 route`
contain both an outbound interface, and a next hop address:
IPv4 ex. `ip route 172.16.29.0 255.255.255.0 172.16.22.1`
IPv6 ex. `ipv6 route 2001:DB8:CAFE:3::/64 2001:DB8:FEED:77::1`
default routes:
IPv4: `ip route 0.0.0.0 0.0.0.0 172.16.22.1`
IPv6: `ipv6 route ::0/0 2001:DB8:FEED:77::1`
Static routes show up as `S` in `show ip(v6) route`; `<subnet> [administrative distance/cost] via <next hop>`

#### Summarizing IPv6 for static routes
R1 is connected to 5 /64 IPv6 networks, to summarize them:
- find the first hextet where you see a difference
- convert the different hextet to binary
- locate the left-most bit that matches and use that mark for your /xx
- to get subnet, copy matching bits and append the rest with zero bits - then convert back to hexadecimal
`ipv6 route 2001:db8:feed::/61 gigabitethernet0/1 2001:db8:cafe:2::1`

#### Why do we use dynamic routing?
- large networks
- want to have automatic adapting
- less administrative overhead
### Routing using OSPF
**OSPF** - open shortest path first is a **link-state routing protocol** (developed to replace distance-vector routing protocol RIP)
OSPF is:
- Classless - carry the subnet masks
- Link-State routing protocol - most concerned with the sate of the link (up or down) as well as bandwidth (not hop count)

**OSPF** routers exchange a series of **link-state** packets to establish adjacencies and exchange information:
- **Hello** - establish and maintain adjacency
- **DBD (Database Description)** - abbreviated list of sending router's link-state database
- **LSR (Link-State Request)** - used by routers to request more information about any entry in the DBD
- **LSU (Link-State Update)** - link-state information - these are packets used by OSPF for routing updates
- **LSAck (LSA Acknowledgement)** - router sends a link-state (LSAck) to confirm receipt of the LSU

OSPF Router must **discover neighbors** before it can flood its link states:
- includes **OSPF Router ID**
Receipt confirms there is another OSPF router on this link
- **Adjacency** is now established
Routers are not considered fully adjacent - at this point each router is aware of the other OSPF router on the link
- (full adjacency happens after both routers have exchanged any necessary LSUs and have identical link-state databases)
#### Router OSPFv2 configuration:
```
router ospf 1 ! this is the process ID, doesn't have to match for networks, only the area does
router-id <ip address>
network <network address> <wildcard-mask> area <area-id>
```
#### **Router-ID** 
Router-ID is used to uniquely identify an OSPF router
- uses router-id command
- if router-id not present, router chooses highest IP address of any of its loopbacks
- if no loopback interfaces, chooses highest MAC address
**important:** if router-id is off when OSPF is configured, the router will use the other methods.
- to change this manually you have to use `clear ip(v6) ospf process` to allow a new router-id to take hold
#### Area-ID
Area-ID is a group of OSPF routers that share link-state info
all OSPF routers in the same area must have the same link-state information in their link-state databases

### OSPF
OSPF shows up as `O` in `show ip route` command
`show ip protocols` will show the routing protocol, process ID, and router-ID.
`show ip ospf database` - shows OSPF topology
`show ip ospf neighbor` - shows the neighbor relationships and the router IDs of the neighboring routers
the `[110/65]` is `[administrative distance / cost]` 110 is OSPF value, cost is able to be configured (command is: auto-cost ??? i forget)

### OSPFv3 for IPv6
```R1-on-interfaces
int f0/1
ipv6 ospf 2 area 0
ipv6 ospf network point-to-point
int f0/0
ipv6 ospf 2 area 0
ipv6 ospf netowkr point-to-point
int f1/1
ipv6 ospf 2 area 0
ipv6 ospf network point-to-point
```
^ this and v this are ON THE SAME ROUTER
```R1-OSPF-instance
ipv6 router ospf 2
router-id 1.1.1.1
passive-interface f1/1 ! this is for stub networks, not always sending hello messages
default-information originate always ! injects a default route in the routing table of peers - allowing it to advertise to those routers
```
`show ipv6 ospf neighbor` the IPv6 version of the OSPF neighbors command
`show ipv6 ospf database` IPv6 version of OSPF database command
`show ipv6 route ospf` IPv6 command that shows OSPF routes
### OSPFv2 Authentication (IPv4)
**OSPFv2 supports:**
- **Plain-text authentication** - simple password authentication - least secure
- **MD5 Authentication** - easy to implement - should only be used if SHA is not available
- **SHA Authentication** - most secure - uses key chains

MD5
```R1-MD5
int ser0/0/0
ip ospf authentication message-digest
ip ospf message-digest-key 1 md5 <password>
```
```R2-MD5
int ser0/0/0
ip ospf authentication message-digest
ip ospf message-digest-key 1 md5 <password (same password)>
```

SHA
```R1-SHA
key chain <chain-name>
key 1
key-string <password>
cryptographic-algorithm ? ! this will show a list of all the encryptions
cryptographic-algorithm hmac-sha-256
exit

interface s0/0/0
ip ospf authentication key-chain <chain-name>
```
`show key chain` - shows the password ???
`show ip ospf int s0/0/0 | section Crypto` - shows if authentication is on - what SA algorithm

### OSPFv3 Authentication and Encryption (IPv6)
OSPFv3 requires the use of IPsec to enable authentication - requires **IPv6 Authentication Header (AH)** or **IPv6 Encapsulating Security Payload (ESP)** header to ensure:
- integrity, authentication, and confidentiality of routing exchanges
**IPv6 Authentication Header (AH)** - authenticates header
**IPv6 Encapsulating Security Payload (ESP)** - encrypts packets - when used, both encryption and authentication of IP datagram are provided

OSPFv3 with IPSec can be used two ways:
- **Per Interface** - authenticates and/or encrypts packets between the routers connected to the link
- **Per OSPF Area** - provides authentication and/or encryption between ALL the routers in the OSPF area
per interface overrides per area authentication/encryption configs.
#### Per Interface:
##### Authentication only
```R1-Authentication-only
int f0/1
ipv6 ospf authentication ipsec spi 300 sha1 1234567890123456789012345678901234567890
! key argument in ipv6 ospf authentication command must be EXACTLY 40 hexadecimal digits
! SPI - security policy index, Key - creates and validates the hash value
```
```R2-Authentication-only
int f0/1
ipv6 ospf authentication ipsec spi 300 sha1 1234567890123456789012345678901234567890
! key arg still needs to be EXACTLY 40 hexadecimal digits
! SPI - security policy index, Key - creates and validates the hash value
```
##### Authentication and Encryption
```R1-Authentication-and-Encryption
int f0/1
ipv6 ospf encryption ipsec spi 300 esp null sha1 1234567890123456789012345678901234567890
```
```R2-Authentication-and-Encryption
int f0/1
ipv6 ospf encryption ipsec spi 300 esp null sha1 1234567890123456789012345678901234567890
```
#### Per Area:
##### Authentication only
```R1-Authentication-Only
ipv6 router ospf 1
area 0 authentication ipsec spi 500 sha1 1234567890123456789012345678901234567890
```
```R2-Authentication-Only
ipv6 router ospf 1
area 0 authentication ipsec spi 500 sha1 1234567890123456789012345678901234567890
```
##### Authentication and Encryption
```R1-Authentication-and-Encryptions
ipv6 router ospf 1
! area 0 encryption ipsec spi 500 esp <PUT ENCRYPTION HERE> sha1 1234567890123456789012345678901234567890
```
```R2-Authentication-and-Encryptions
ipv6 router ospf 1
! area 0 encryption ipsec spi 500 esp <PUT ENCRYPTION HERE> sha1 1234567890123456789012345678901234567890
```