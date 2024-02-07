**router to router - IP address to IP address**

  

R1

interface GigabitEthernet 0/1 to

ip address 192.0.2.1 255.255.255.252

  

**switch to router - IP routing on switch, no switchport, IP address to IP address (this is pretty common)**

  

S1

ip routing

interface GigabitEthernet 1 /0/1

no switchport

ip address 192.0.2.1 255.255.255.252

  
  

**switch to router (vlan) - set switch to vlan, access mode, IP address to IP address**

  

S1

ip routing

interface GigabitEthernet I /0/1

switchport mode access

switchport access vlan 13

spanning-tree portfast

interface vlan 13

ip address 192.0.2.1 255.255.255.252

  
  

**switch to router (router vlans) - trunk with vlan, matches sub interface, IP address to IP address (this is the most common ?)**

  

S1

ip routing

interface GigabitEthernet 1 /O/I

switchport trunk encapsulation dotl q

switchport mode trunk

interface vlan 13

ip address 192.0.2.1 255.255.255.252

  
  

**switch to switch - L3 to L3 - ip routing, trunk to trunk, same vlan, IP address to IP address (ALWAYS using this (VLANs)) #1**

  

S1

ip routing

interface GigabitEthernet I /0/1

switchport trunk encapsulation dotl q

switchport mode trunk

interface vlan 13

ip address 192.0.2.1 255.255.255.252

  
  

**switch to switch - L3 to L3 - ip routing, no switchport on both, IP address to IP address (not very common) #2**

  

S1

ip routing

interface GigabitEthernet I /0/1

no switchport

ip address 192.0.2.1 255.255.255.252

  

R2

interface GigabitEthernet 0/1

ip address 192.0.2.2 255.255.255.252

to

R2

interface GigabitEthernet 0/1

ip address 192.0.2.2 255.255.255.252

to

R2

interface GigabitEthernet 0/1

ip address 192.0.2.2 255.255.255.252

to

R2

interface GigabitEthernet 0/1

no ip address

no shutdown

interface GigabitEthernet 0/1 . 1 3

encapsulation dot Iq 13

ip address 192.0.2.2 255.255.255.252

to

R2

ip routing

interface GigabitEthernet I /0/1

switchport trunk encapsulation dotl q

switchport mode trunk

interface vlan 13

ip address 192.0.2.2 255.255.255.252

to

S2

ip routing

interface GigabitEthernet I /0/1

no switchport

ip address 192.0.2.1 255.255.255.252