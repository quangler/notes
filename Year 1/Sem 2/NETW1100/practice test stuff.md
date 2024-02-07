vlan 10

name Pippin

vlan 11

name Boromir

vlan 13

name Elrond

vlan 14

name Galadriel

vlan 15

name Deagol

  

switchport mode trunk

switchport trunk native vlan 15

  

switchport mode access

switchport access vlan 11

switcport voice vlan 14

  

spanning-tree portfast

spanning-tree bpduguard enable

  

switchport port-security

switchport port-security maximum 2

switchport port-security mac-address sticky

switchport port-security violation shutdown

do write

  
  

vlan 10

name Pippin

vlan 11

name Boromir

vlan 12

name Gandalf

vlan 13

name Elrond

vlan 14

name Galadriel

vlan 15

name Deagol

  

ip helper-address 172.16.6.200

  

switchport mode access

switchport access vlan 12

switchport voice vlan 14

spanning-tree portfast

spanning-tree bpduguard enable

  

switchport port-security

switchport port-security maximum 2

switchport port-security mac-address sticky

switchport port-security violation shutdown

do write