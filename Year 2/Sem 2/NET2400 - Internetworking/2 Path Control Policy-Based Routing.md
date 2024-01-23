#### Best Path Decisions
A router uses it **routing table** to determine the best path to forward the packet.
- router receives a packet - examines the destination IP and searches for best network address match in **routing table**
- routing table entries also include the **interface to be used to forward the packet**
- once a match is found the router **encapsulates the IP packet into the data link frame of the outgoing or exit interface**
- the packet is then **forwarded toward its destination**

it is better to use next hop IP as it will ARP once and add it to the table.

**Path Control** - any function that influences where a router forwards a packet
- path control tools can be used to **change the default destination forwarding** and optimize the path
- one of the most common tools for this is **policy based routing (PBR)**
- **PBR** adds flexibility in a difficult-to-manage environment by providing the ability to route traffic that i based on network needs
#### Intro to Path Control
two path control methods:
###### **Policy-Based Routing (PBR)**
the router makes a forwarding decision before changing the IP Routing Table
###### IP Service-Level Agreement (SLA)
monitors network health and reachability, the router can choose when to use or ignore routes, based on the status determined by the IP SLA.
#### Policy-Based Routing
used when you need to define specific criteria, other than destination network for routing traffic.
- PBR can route traffic based on:
	- source address
	- source port
	- destination address
	- destination port
	- protocol
	- or a combination of these
- PBR overrides the router's natural destination based forwarding logic. (PBR acts **before** the router performs its IP routing table lookup/matching)
PBR can be configured to provide **equal-access** load-sharing based on source subnets.
```PBR-R1
ip access-list extended ISP-1 permit 1.1.1.0 0.0.0.255 any !!! traffic from the 1.1.1.0 network
ip access-list extended ISP-2 permit 1.2.2.0 0.0.0.255 any

route-map EQUAL-ACCESS-RM permit 10
match ip address ISP-1
set ip next-hop 172.16.1.1

route-map EQAUL-ACCESS-RM permit 20
match ip address ISP-2
set ip next-hop 172.20.5.1

interface f0/0 !!! put it on both vlans in case of 2 vlans
ip policy route-map EQUAL-ACCESS-RM
```
^^^ this will allow one router to split the load to 2 ISPs.
any packets that do not match the route-map policy are routed normally.

PBR chooses to forward the packet by using the matching logic defined through a **Route-Map**
- allows you to check for certain matching conditions and set a value
	- it typically refers to a defined IP ACL
- it defines the forwarding instructions for the packets matched
	- next-hop IP address
	- outgoing interface
###### On Cisco Devices:
the `match` command is needed with a **route-map** on **PBR**
`match ip address <address>` - references a standard or extended ACL
`match length <min> <max>` - allows specifying a range of lengths, in bytes
the `set` command defines the **action** to take regarding **how to forward the packet** (outgoing interface or next-hop IP)
`set interface <int>` - specifies the outgoing interface
`set ip next-hop <address>` - specifies the next-hop IP (must be in a connected subnet)
- if the next hope does **NOT** exist in the routing table, the command uses the normal routing table to forward the packet

`set ip default next-hop <address>` - checks to see if the destination IP address exists in the routing table:
- if it does, it routes it through the normal routing table
- if it does **NOT**, the command policy routes the packet and sends it to the specified next hop

Policy routes are nothing more than sophisticated static routes
- static routes forward a packet to a specified next hop based on **destination address** of the packet
policy routes - can forward a packet to a specified next hop based on the source of the packet
- policy routes can also be linked to extended IP access lists so that routing may be based on **protocol types and port numbers**
- like a static route, policy route influences the routing only on the router on which it is configured.