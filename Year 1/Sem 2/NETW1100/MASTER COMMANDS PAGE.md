**helpful for troubleshooting:**

show vlan brief

show int trunk

show port

show int access (?)

show span

show cam

show int portchannel (#)

show ip protocols

show ip ospf

show ip ospf interface

  
  
  

Switch(config)#spanning-tree mode rapid-pvst <--change the spanning tree version

  
  

**---Change the root bridge---**

Switch(config)#spanning-tree vlan 1 root [primary/secondary]

**--or--**

Switch(config)#spanning-tree vlan 1 priority ? #important

<0-61440> bridge priority in increments of 4096

  
  

**---For edge ports---**

Switch(config)#interface range FastEthernet 0/1-24

Switch(config-if-range)#switchport mode access

Switch(config-if-range)#spanning-tree portfast

  

Switch(config-if-range)#spanning-tree bpduguard enable <--to prevent connections from other switches

  
  

**---For switch to switch connections with RTSP---**

Switch(config)#interface range GigabitEthernet 1/1/1-4

Switch(config-if-range)#spanning-tree link-type point-to-point

  
  

**---VLAN's---**

**---creating vlans---**

Switch(config)#vlan <69> <---vlan id number #important

Switch(config vlan)#name <nice> <---vlan name

  

Sw1(config)#interface range g1/1-4

Sw1(config-if-range)#switchport trunk native vlan 999 <---changing the native vlan

  

Sw1(config)#interface range g1/0/1-24

Sw1(config-if-range)#switchport access vlan 11 <---changing the port vlan

Sw1(config-if-range)#switchport voice vlan 66 <---changing the voice vlan

  
  

**---vlan routing---**

**--router on a stick--**

R1(config)#interface G0/0

R1(config-if)#no ip address

R1(config-if)#no shut

R1(config-if)#interface G0/0.x

(x = subinterface ID – should match the VLAN ID)

R1(config-subif)#encapsulation dot1q x

R1(config-subif)#ip address A.B.C.D A.B.C.D

R1(config)#ip helper-address [dhcp server IP] <--- if there is a dhcp server

  
  

**--layer 3 switch with routing--**

Sw2(config)#ip routing

Sw2(config)#interface vlan 1

Sw2(config-if)#no ip address

Sw2(config-if)#shut

Sw2(config-if)#interface vlan x

Sw2(config-if)#ip address A.B.C.D A.B.C.D

Sw2(config-if)#no shut

Sw1(config)#ip helper-address [dhcp server IP] <--- only if using switch routing and there is a dhcp server

  
  

**---layer 2/3 switch (no routing)---**

enter in vlans #important

Sw1(config)#interface vlan 1

Sw1(config-if)#no ip address

Sw1(config-if)#shut

Sw1(config)#int vlan [# of network management]

Sw1(config-if)#ip address [highest ip of vlan subnet - this is the default gateway] [subnet mask]

  
  

**---Port Security---**

Sw3(config)#interface range f0/1-24 <---Don't put this on a trunk because it will mess up your network

Sw3(config-if-range)#switchport port-security

Sw3(config-if-range)#switchport port-security maximum 3 <---should be set to 3 if you have a voice vlan

Sw3(config-if-range)#switchport port-security mac-address sticky

Sw3(config-if-range)#switchport port-security violation shutdown

Sw3(config-if-range)#do write

  
  

**---Link Aggregation---**

Sw1(config)#interface range g1/1/1-4

Sw1(config-if-range)switchport mode trunk

Sw1(config-if-range)switchport trunk native vlan 777 <---make sure both switches have the same native vlan

Sw1(config-if-range)#channel-group 1 mode active

  

Sw1(config)#interface Port-channel 1

Sw1(config-if)#switchport mode trunk

Sw1(config-if)#switchport trunk native vlan 777 <---just to make sure

  
  

**---ACL---**

ip access-list standard <ForRemoteAccess>

permit host 172.16.0.1 - used for specific hosts

permit 172.16.0.0 0.0.0.255 -- this has a wildcard, it is used for whole subnets

line vty 0 15

login local

transport input ssh

access-class <ForRemoteAccess> in

  
  

**---SSH---**

hostname s1

enable secret cisco

username admin password class

ip domain-name bubba.local

crypto key generate rsa modulus 1024

ip ssh v 2

line vty 0 15

login local

transport input ssh

  
  

**---OSPF--- make sure you advertise your network management VLAN**

router ospf 1 - (this number doesn't matter)

_ip ospf priority 200_ - optional

router-id 1.1.1.254 - need a designated router - ethernet is a multiaccess media (always)

_^^^ it is not an IP address._ **HIGHEST NUMBER WINS. (this will be second guy)**

  

auto-cost reference-bandwidth 1000 - in Mbps, so 1000 is gigabit **(you need to change this for every router in the domain - change so they match)**

network 192.168.255.254 0.0.0.0 area 0 - this tells you which network to look for interfaces on - **through the interface 192.168.255.254** to **0.0.0.0 (everything) * DO THIS ON ALL THE INTERFACES ***

default-information originate - propagate default route to the rest of the network

  

**---EIGRP---**

Router eigrp 100

Network <your networks that you want to broadcast outwards>

No auto-summary