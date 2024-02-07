Thing you always have to remember with OSPF:

- CCNA all routing is done on routers.

  

In an OSPF autonomous system the shared link is: Network Management VLAN

  

**HAVE to make sure that you advertise the NETWORK MANAGEMENT VLAN**

  

4 different ways to do a network statement: (identify the interfaces on that network)

- for us, best practice is explicit address, network address with subnet mask

  

- method 2 - network address for int with wildcard mask - not very common **ON CISCO CCNA**

  

- method 3 - arguably most common - 0.0.0.0 255.255.255.255 - find any interface, all in the case of single area

  

- method 4 - summary method (that doesn't summarize) - 192.168.0.0 0.0.3.255 - this IS NOT a summary, it FINDS interfaces

  

**OSPF single area (area 0) CANNOT be summarized** #important

  

a network statement in OSPF finds interfaces,

  

**COMMANDS**

1. router ospf
2. router id
3. autocross reference bandwidth
4. passive interface **(do not send hello's, you can only do this on routed layer 3 or routers)**

  

default route is an external route

we propagate this through OSPF

  
  

DEMO FOLLOW ALONG:

all IPs are configured

  

**R1**

- going out G0/3/0 (OUTSIDE NAT)

- going inside through G0/0/0 (INSIDE NAT)

  

'router ospf 34' - (this number doesnt matter)

'router-id 1.1.1.254' - need a designated router - ethernet is a multiaccess media (always)

^^^ it is not an IP address. **HIGHEST NUMBER WINS. (this will be second guy)**

**'**auto-cost reference-bandwidth 1000' - in Mbps, so 1000 is gigabit **(you need to change this for every router in the domain)**

'network 192.168.255.254 0.0.0.0 area 0' - this tells you which network to look for interfaces on

'default-information originate' - propagate default route to the rest of the network

  

VLAN 16 is shared logical link - (NetMgmt VLAN, and doesnt have a helper address)

  

**S2**

'int vlan 16'

'ip ospf priority 200' - only for the shared link (vlan 16)

'exit'

'router ospf 56'

'router-id 1.1.1.255' - this makes this the default router for **EVERYTHING**

'auto-cost reference-bandwidth 1000' - setting cost to same as R1

'network 192.168.13.254 0.0.0.0 area 0' - for VLAN 13

'network 192.168.14.254 0.0.0.0 area 0' - for VLAN 14 (these are setup for HSRP, you don't need to do this)

'network 192.168.15.254 0.0.0.0 area 0' - for VLAN 15 (

'network 192.168.16.254 0.0.0.0 area 0' - **for VLAN 16**

'network 192.168.255.253 0.0.0.0 area 0' - this is the command that makes an adjacency with **R1**

  
  

**R1 will now have connections to 192.168.(13-16).0 - they were found through S2 and OSPF**

  
  

**S1**

(dont need ospf priority because the designated router already has one, and there's no point)

'router ospf 1'

'router-id 1.1.1.1'

'auto-cost reference-bandwidth 1000'

'network 192.168.10.254 0.0.0.0 area 0' - for VLAN 10

'network 192.168.11.254 0.0.0.0 area 0' - for VLAN 11

'network 192.168.12.254 0.0.0.0 area 0' - for VLAN 12

'network 192.168.17.254 0.0.0.0 area 0' - for VLAN 17

'network 192.168.16.253 0.0.0.0 area 0' - makes the adjacency with **S2**

  

passive interface command:

'passive-interface vlan X'

'passive-interface vlan 10'

'passive-interface vlan 11'

'passive-interface vlan 12'

'passive-interface vlan 17'

**SETTING PASSIVE-INTERFACE ON VLAN 16 WILL BREAK OSPF, THIS IS THE ONLY FORM OF COMMUNICATION.**

  

**What is the definition of passive interface: DO NOT** **SEND** **HELLO'S** #important