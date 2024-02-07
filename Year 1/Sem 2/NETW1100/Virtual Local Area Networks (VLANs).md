physical segment - connection from device to device - cable

logical segment - subnet

  

ARP & DHCP - biggest broadcast traffic

  

VLAN - purpose was to manage size of broadcast domains

- aka make it so you dont have to arp every single god damn thing at once

  

**IEEE 802.1Q - (encapsulation) VLANs**

VLAN Tag 4 bytes - AKA shim

VLAN frame - 1522 bytes

  

- **trunk** carries **ALL VLANs**

  

VLAN benefits:

- Network Administration / Organization -
    
    - can group people by departments easily
- Improved Security
    
    - set a "blackhole" VLAN to VLAN 1 - any unused port goes to that VLAN (doesn't have a subnet to it)
    - locks down phones - can only call emergency and inside building
- Easier Fault Management - smaller chunks that makes it easier to tell where the issue is
- Improved Quality of Service -
  

  

VLAN 1 is the default native VLAN, all switch ports are member by default

- its the easiest one to figure out, so don't use it
- vlan 1 has no VLAN tag - meaning it is legacy / has backwards compatibility
- cisco uses VLAN 1 for identifying neighboring switches so you cant change name or anything

  

switchport mode access - accessing specified VLANs

switchport mode trunk - every VLAN

  

IEEE 802.1Q Tag - 4 bytes

- Tag Protocol Identifier (TPID) - always 0x8100 (ethernet) : 16 bits
- Tag Control Information (TCI) : 16 bits
    
    - PCP - Priority Code Point - used for priority and QOS, gets some packets through before others : 12 bits
    - DEI - Discard Eligible Indicator - used with IP/TCP to get rid of congestion : 1 bit
    - VID - VLAN Identifier - 4094 possible VLANs (cant use 0 or 4095) : 12 bits

**VLAN Interfaces**

Untagged Port - **Access**

- any int connected to end device (edge port)
- carries data associated with THAT VLAN

Tagged Port - **Trunk**

- any link between switches or between switch and router
- carries data associated with all VLANs
  

  

(802.1Q term - untagged / tagged | cisco term - access / trunk)

  

**VLAN membership:**

- port-based VLANs or static VLANs - assigned VLANs
- "show vlan brief"
  
- MAC-based VLANs or dynamic VLANs - outsources the switch checking VLANs to a RADIUS server
- not used as much now

  
  

**VLAN TYPES:**

- default (1) - everything auto assigned to this, dont use it
- native - used for backwards compatibility, not used much
- management - used for network management, **ONLY** **layer 2** **SWITCHES** are members of **VLAN**
- data - every **user** is a member of a data VLAN, just dont use VLAN 1 please god
- voice - "switchport voice vlan 100" - can be paired up with another VLAN for data
  

  

every access port can be connected to two VLANs - one can be anything, the other **HAS** to be voice

  

**VLAN Design Guidelines**

- biggest subnet size of /22
- **document everything**
- separate management and user data traffic
- **DONT USE VLAN 1**
- ensure only trusted users can access the management VLAN
- set native VLAN to an unused VLAN
- clear native VLAN from all trunks > 'switchport trunk allow [allowed vlans here]'
- unused ports into 'blackhole VLAN'
- configure user ports as static access
- shutdown unused ports
  

  

**VLAN Design REQUIREMENTS:**

trunk must have the following as same on both sides

- link speed & duplex setting
- encapsulation
- allowed VLANs - only uses ID # not name
- native VLAN
  

  

**VLAN 1**:

- cannot be renamed or deleted
- native VLAN on trunk port (cant be removed)

  

VTP (VLAN trunking protocol) - terry hates it - too complex for the same thing as notepad

- needs a vtp domain and password, but then it figures out VLAN tables for you
- vtp mode transparent - doesn't need any of that shit ^ | this is basically off mode, this shit dumb as hell