```

- to trace the root bridge

'show span'

  

- change STP to RSTP

config# 'spanning-tree mode rapid-pvst'

  

- changing priority of a switch in STP

config# 'spanning-tree vlan [number] root [primary <or> secondary]'

or

config# 'spanning-tree vlan [number] priority [increment of 4096]' (good practice to set 8192 on root)

  

- setting up edge ports

config# 'interface range FastEthernet 0/1-24' (note: 0/1-24 is a range)

config-if-range# 'switchport mode access'

config-if-range# 'spanning-tree portfast'

- enable port guarding (be careful, this can brick your switch)

config-if-range# 'spanning-tree bpduguard enable'

  

- configuring point-to-point link type ports (for legacy/other vendors since RSTP does this by default)

config# 'interface range GigabitEthernet 1/0/2-24'

config-if-range# 'spanning-tree link-type point-to-point'

  
  

DHCP - HELPER ?????

port security

link aggregation

vlan database

spanning tree

  

router on a stick vs vsi ??
```
