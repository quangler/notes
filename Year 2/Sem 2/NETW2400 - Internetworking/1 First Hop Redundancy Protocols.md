##### The need for First Hop Redundancy
- each host in a network needs a default gateway
- if the default gateway goes down, the connection is now cut off
- first hop redundancy aims to solve this by having multiple points of failure rather than just one
how it works:
- a set of routers/L3 switches work together to present the illusion of a single router to the hosts in the LAN
- it uses a virtual router (hosted on both routers, forwarding and standby router) to ensure that the MAC address and config stays the same if the physical gateway goes down. (the clients connect to the virtual router)
when it fails over:
- standby router stops seeing hello messages from forwarding router
- standby router takes role of forwarding router
##### First Hop Redundancy Protocols
Some examples of FHRP (available with both IPv4 and IPv6):
**HSRP** - Hot Standby Routing Protocol - Cisco Proprietary
**VRRP** - Virtual Router Redundancy Protocol - supported by multiple vendors (Cisco, Juniper)
**GLBP** - Gateway Load Balancing Protocol - Cisco Proprietary
##### Hot Standby Routing Protocol (HSRP)
- uses an active/standby model
- only 1 router at a time can be the active router, the other is the standby
Active Router
- responds to default gateway ARP requests with the **virtual router MAC address**
- actively forwards packets for virtual router
- sends hello messages to standby
- knows the Virtual Router IP
Standby Router
- listens for hello messages
- becomes the active forwarder if it doesn't hear from active router
Virtual router
- not a real router
- represents the HSRP group acting as one virtual router
###### HSRP Failover:
HSRP fails over and has the standby router become the active router, if the original active router comes back on, it doesn't swap back.
Using the `preempt` addition to the command, you can make the original router become the active router upon coming back online.
###### HSRP Load Balancing:
the active and standby routers connect to all VLANs - HSRP can be configured to have some VLANs and the active and some VLANs on the passive.
to achieve this, a single router can be members of multiple HSRP groups on a VLAN.
IPv4 commands:
```R1
interface f0/0.10
ip address 10.1.10.9 255.255.255.0
standby 1 ip 10.1.10.1
standby 1 priority 110
standby 1 preempt
```
```R2
interface f0/0.10
ip address 10.1.10.10 255.255.255.0
standby 1 ip 10.1.10.1
standby 1 priority 90
```
^commands for R1 and R2 for VLAN10
```R1
interface f0/0.20
ip address 10.1.20.9 255.255.255.0
standby 2 ip 10.1.20.1
standby 2 priority 90
```
```R2
interface f0/0.20
ip address 10.1.20.10 255.255.255.0
standby 2 ip 10.1.20.1
standby 2 priority 110
standby 2 preempt
```
^commands for R1 and R2 for VLAN20
all of those commands make a load balancing between R1 and R2 for VLAN10 and VLAN20 in IPv4

IPv6
```R1
interface f0/0.10
ipv6 address 2001:DB8:CAFE:1::2/64
standby version 2
standby 1 priority 110
standby 1 ipv6 fe80::1
standby 1 preempt
ipv6 enable
```
```R2
interface f0/0.10
ipv6 address 2001:DB8:CAFE:1::3/64
standby version 2
standby 1 priority 90
standby 1 ipv6 fe80::1
ipv6 enable
```
^commands for R1 and R2 for VLAN10
```R1
interface f0/0.20
ipv6 address 2001:DB8:CAFE:2::2/64
standby version 2
standby 2 ipv6 fe80::1
ipv6 enable
standby 2 priority 90
```
```R2
interface f0/0.20
ipv6 address 2001:DB8:CAFE:2::3/64
standby version 2
standby 2 priority 110
standby 2 preempt
ipv6 enable
```
^commands for R1 and R2 for VLAN20
all of those commands make load balancing between R1 and R2 for VLAN10 and VLAN20 in IPV4 work

Knowledge commands:
```commands
show standby (view HSRP info)
show standby <int> (view HSRP info for specific int)
show standby brief (show quick HSRP info)
debug standby errors (display HSRP error events)
debug standby events (display info on HSRP events)
debug standby packets (display contents of HSRP packets)
```



#### VRRP - Virtual Router Redundancy Protocol
- open standard, allows for vendor interoperability
- in VRRP the `virtual router` is known as a `VRRP Group`
	- master virtual router and backup virtual routers
The VRRP group can use a physical address of one of the routers, or a virtual IP address.
Physical address makes that address the default gateway, virtual makes a different IP address the default gateway (a unique address that none of the routers have)
- if the master router fails it takes the next highest priority router.
- when the router becomes available again, it becomes the master virtual router again. (preempt is enabled by default)
- if the priority is all the same, it goes by highest IP address
VRRP virtual MAC address: `0000.5e00.01xx`
VRRP Multicast address: `224.0.0.18`
##### Load Balancing
- has to be done with multiple groups like HSRP
- each becomes the master for specific clients, then failover to each other.

```R1
interface f0/0.1
ip address 10.1.1.9 255.255.255.0
vrrp 1 ip 10.1.1.1
vrrp 1 priority 110
vrrp 1 authentication md5 key-string VRRP
```
```R2
interface f0/0.1
ip address 10.1.1.10 255.255.255.0
vrrp 1 ip 10.1.1.1
vrrp 1 priority 90
vrrp 1 authentication md5 key-string VRRP
```
^ commands for R1 & R2 (first set for load balancing), includes authentication (will ignore any routers that don't have authentication)
```R1
interface f0/0.2
ip address 10.1.2.9 255.255.255.0
vrrp 2 ip 10.1.2.1
vrrp 2 priority 90
vrrp 2 authentication md5 key-string VRRP
```
```R2
interface f0/0.2
ip address 10.1.2.10 255.255.255.0
vrrp 2 ip 10.1.2.1
vrrp 2 priority 110
vrrp 2 authentication md5 key-string VRRP
```
^ commands for R1 & R2 (second set for load balancing)
#### Gateway Load Balancing Protocol (GLBP)
cisco proprietary protocol
- provides **a single virtual IP address** and **multiple MAC addresses**
- provides redundancy and load balancing
GLBP uses a router as an **Active Virtual Gateway (AVG)**
- responds to ARP from hosts with a **Virtual MAC Address** of one of the **Active Virtual Forwarder (AVF)** routers
- each host has the same gateway IP, but has a different MAC address in the ARP table.
**AVG** responds and assigns **AVFs** in a round-robin fashion by default
GLBP can have **up to four** member routers acting as IP default gateways (these are the **active virtual forwarders AVFs**)

members of the GLBP group elect one gateway to be the **AVG** for that group.
AVG assigns a virtual MAC address to each member of the group

**GLBP multicast address:** `224.0.0.102`

##### if router A becomes unavailable:
- client 1 will not lose access to the WAN
- Router B will assume responsibility for forwarding packets sent to the virtual MAC address of router A & still have its own MAC address
there are two timers:
- redirect timer (default 10 minutes)
- timeout timer (default 4 hours)
when the timer expires the AVG will stop responding to the hosts with the failed AVF MAC address
instead, the failed AVF will be completely removed from the group - any hosts using the failed AVF have to refresh their ARP tables

##### Load Balancing
- weighted load-balancing algorithm - amount of load directed to an AVF depends on the weighting value advertised by the gateway containing that AVF
- host-dependent load-balancing algorithm - a host is guaranteed to use the same virtual MAC address as long as that virtual MAC address is participating in the GLBP group
- round-robin load balancing algorithm (default) - each AVF MAC address takes turns being included in address resolution replies for the virtual IP address.
```R1
interface f0/0
ip address 192.168.15.9 255.255.255.0
glbp 1 ip 192.168.15.1
glbp 1 priority 120
glbp 1 preempt
```
```R2
interface f0/0
ip address 192.168.15.10 255.255.255.0
glbp 1 ip 192.168.15.1
glbp 1 priority 110
glbp 1 preempt
```
```R3
interface f0/0
ip address 192.168.15.11 255.255.255.0
glvp 1 ip 192.168.15.1
```
^ R1 will always be AVG if possible, if R1 goes down, R2 will become the next AVG
for multiple VLANs use multiple GLBP groups.

knowledge commands:
```
show glbp
show glbp brief
```
##### Interface Tracking
GLBP interface tracking uses weighting mechanism:
- lower threshold - applies when the router loses weight (priority)
	- if a router weight falls below this threshold it loses its active state as a forwarder
- upper threshold - applies when the router regains weight (priority)
	- if the router weight exceeds this threshold, regains its active role as a forwarder

```R1-load-balancing
track 15 interface f0/1 line-protocol

interface f0/0
ip address 192.168.15.9 255.255.255.0
glbp 1 ip 192.168.15.1
glbp 1 priority 120
glbp 1 preempt

glbp 1 weighting 110 lower 85 upper 105
glbp 1 weighting track 15 decrement 30
```
```R2-load-balancing
track 15 interface f0/1 line-protocol

interface f0/0
ip address 192.168.15.11 255.255.255.0
glbp 1 ip 192.168.15.1

glbp 1 weighting 110 lower 85 upper 105
glbp 1 weighting track 15 decrement 30
```
