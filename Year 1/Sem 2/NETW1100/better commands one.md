**helpful commands:**

do show int trunk

  
  

**how to make vlans (EASY, NOT PATCHED, STILL WORKING)*******

  

'vlan [#]'

'name [name of vlan]'

  

**layer 2 switch commands for spanning tree, vlans, port security:**

  

- for making an ip address for the switch:
- recognize what vlan the ip address is about (management vlan probably)

  

'int vlan [management vlan #]'

'ip address [the ip it wants] [subnet mask for it]'

  
  
  

**Router on a stick commands:**

  

'en'

'conf t'

  

'int g0/0.[vlan # here]'

'encapsulation dot1Q [vlan # here again]'

'ip address [subnet address here, ex. 172.17.5.254] [subnet mask]'

'ip help-address [ip address of DHCP server]' (only if there is a dhcp server)

  

- dont need to do it for voice or for native (unless specified nerd)

  

**layer 3 switch:**

  

'spanning-tree mode rapid-pvst'

- add in vlans (check top section)
- set root bridge v

'spanning-tree vlan [vlan range (10-15 for ex)] priority 4096' (or other if specified)

'spanning-tree vlan [vlan range (10-15 for ex)] root [primary / secondary]'

  

- for making an ip address for the switch:
- recognize what vlan the ip address is about (management vlan probably)

  

'int vlan [management vlan #]'

'ip address [the ip it wants] [subnet mask for it]'

  
  
  
  
  

**LINK AGGREGATION: LAST THING YOU DO BECAUSE EVERYTHING HAS TO WORK RIGHT FIRST**

  

(MAKE SURE THEY HAVE THE SAME SPANNING TREE THANG)

  

'interface range [g1/0/1 - whatever]'

'description Connection to 4-link LAG on Sw2' (for example)

'switchport trunk native vlan [native vlan #]'

~~'switchport trunk encapsulation dot1q'~~

'switchport mode trunk'

'channel-group [LAG # (1 or 2)] mode [active or passive]'

'spanning-tree link-type point-to-point'

'exit'

'interface Port-channel [LAG # (1 or 2)]'

'description LAG between Sw1 and Sw2'

'switchport trunk native vlan [native vlan #]'

~~'switchport trunk encapsulation dot1q'~~

'switchport mode trunk'

'do write'