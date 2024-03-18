#### Information / Troubleshooting Commands
```Troubleshooting
show run int f0/0.2        ! this will show specifically one interface

show vlan brief
show int trunk
show port
show span
show cam
show int portchannel
show ip protocols
show ip ospf
show ip int br
```

#### HSRP - Hot Standby Routing Protocol
##### IPv4
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

##### IPv6
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
```HSRP-Troubleshooting
show standby (view HSRP info)
show standby <int> (view HSRP info for specific int)
show standby brief (show quick HSRP info)
debug standby errors (display HSRP error events)
debug standby events (display info on HSRP events)
debug standby packets (display contents of HSRP packets)
```

#### VRRP - Virtual Router Redundancy Protocol

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

#### GLBP - Gateway Load Balancing Protocol
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
```GLBP-Troubleshooting
show glbp
show glbp brief
```

##### GLBP - Interface Tracking
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

##### PBR - policy based routing
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
#### VLANs
```Creating and Applying VLANs
vlan 10
name Routing

int range g1/1-4
switchport mode trunk
switchport trunk native vlan 999

int g1/0/1-24
switchport mode access
switchport access vlan 10
switchport voice vlan 50
```
```router-on-a-stick
int g0/0
no ip address
no shut

int g0/0.10
encapsulation dot1q 10
ip address 10.10.10.10 255.255.255.0
ip helper-address 10.10.10.200
```
```L3-switch-routing
ip routing
int vlan 1
no ip address
shut
int vlan 10
ip address 10.10.10.10 255.255.255.0
no shut
ip helper-address 10.10.10.200
```

#### Spanning Tree
```spanning-tree
spanning-tree mode rapid-pvst
spanning-tree vlan 10 root primary / or / spanning-tree vlan 10 priority 4096
```
```switch-to-switch
int range g1/1/1-4
spanning-tree link-type point-to-point
```
#### Edge Ports
```edge-ports
int range f0/1-24
switchport mode access
spanning-tree portfast
spanning-tree bpduguard enabled
```
#### Port Security
```port-security don't do it on trunks
int range f0/1-24
switchport port-security
switchport port-security maximum 3
switchport port-security mac-address sticky
switchport port-security violation shutdown
```
#### Link Aggregation
```etherchannel
int range g1/1/1-4
switchport mode trunk
switchport trunk native vlan 999
channel-group 1 mode active

interface port-channel 1
switchport mode trunk
swichport trunk native vlan 999
```
#### ACLs - Access Control Lists
```RemoteACL
ip access-list standard ForRemoteAccess
permit host 172.16.0.1
permit 172.16.0.0 0.0.0.255

line vty 0 15
login local
transport input ssh
access-class ForRemoteAccess in
```
```Reflexive-Lists
ip access-list extended Name1OUT
permit icmp any any reflect STATEMENT

ip access-list extended Name2IN
evaluate STATEMENT

int f0/0
ip access-group Name1OUT out
ip access-group Name2IN in
```
#### SSH
```SSH-Setup
hostname S1
enable secret cisco
username admin password class
ip domain name bubba.local
crypto key generate rsa modulus 1024
ip ssh v 2

line vty 0 15
login local
transport input ssh
```

#### OSPF - Open Shortest Path First
```OSPF
router ospf 1
router-id 1.1.1.255
auto-cost reference-bandwidth 1000
network 10.10.10.10 0.0.0.0 area 0
default-information originate
```
```OSPF-help-commands
show ip ospf int
show ip ospf
show ip ospf neighbor
```

#### EIGRP - Enhanced Interior Gateway Routing Protocol
```EIGRP
router eigrp 100
network 10.10.10.10
no auto-summary
```

#### VPN commands
##### IPsec
```IPSec-commands
crypto isakmp policy 1
authentication pre-share
exit

crypto isakmp key KeyWord address 10.10.10.11
access-list ACLName permit ip 10.10.10.10 10.10.10.11
crypto ipsec transform-set SetName esp-sha-hmac
crypto ipsec transform-set SetName esp-aes

crypto map MapName 1 ipsec-isakmp

set transform-set SetName
set peer 10.10.10.11
match address ACLName
exit

int f0/0
crypto map MapName
```
```IPSec-help-commands
show crypto isakmp sa
show crypto ipsec sa
show crypto ipsec transform
sho crypto isakmp policy
show crypto map
```
