Collisions were impossible on a switched network, **UNLESS** you are using half-duplex

  

Redundancy is good, loops are bad

  

Loops bad:

- layer 2 can't do anything about the loop so it fully saturates the network with lost packets and slows everything down like hardcore. Broadcast messages basically duplicate and keep sending it to the next guy (even if they have already gotten it)
- layer 3 has TTL and other flags to kill packets

  

STP (spanning tree protocol)

- provides redundant intersegment connections (and prevents loops)
- the yellow light used to be called the "blocking state"

**802.1D - standard** (aka Common Spanning Tree / CST) - takes minimum of 30 seconds, but most commonly used

**802.1w** (Rapid Spanning Tree / RST) - takes like maybe 5 seconds

**802.1s** (Multiple Spanning Tree / MST) - also very quick

- **802.1D** has **w** and **s** in it now.

common spanning tree is the default because it is backwards compatible and you're probably not gonna need it anyways since spanning tree is the least of your worries while setting it up

  
  

**Physical Topology** - How devices are connected

**Logical Topology** - How data flows

  

- By default, all layer 2 switches support and use spanning tree

  

The switch with the lowest **BridgeID** is the **root bridge** (only ever 1)

- **bridgeID** is a combination of (**priority** and **mac address**)
- priority - default to 32768 (cisco goes down in chunks of 4096)
  

  
  

packet tracer vlan 1 mac address is the same as the base mac address (this is not the case in the real world)

  

**root port**

- **best** path from non root bridge TO the root bridge
- where you **recieve** BPDUs from (designated port) root bridge
    
    - lowest cost to root bridge - quickest path (two 1gb jumps vs one 100mb | two 1gb ones win) not least jumps

  

**designated port**

- **sends** BPDUs to root ports (**Bridge Protocol Data Units** - contains all spanning tree data)

  
  

**alternate port**

- port that will become active if the root fails (yellow, always discarding)
- always opposite of a designated port
- (CANNOT SEND ANYTHING OR RECIEVE **DATA)**

  

**disabled port**

- "bpduguard" - goes into errdisabled state, aka shuts down
- not a trunk so it can't make a loop

  

**edge port**

- end devices are plugged into edge ports
- all edge ports are disabled ports, not other way around

  

**backup port**

- used to connect to a hub (lame as hell, wont be asked about)

  

**dont ever disable stp ever**

  

**Discarding**

- a port that would cause a switching loop if it were active
- no data is sent or received, but BPDU data is still received
- Alternate & Backup ports

  

**Forwarding**

- normal operation, receiving and forwarding frames
- monitors BPDUs that would tell it to turn into blocking state
- Root & Designated ports
  

  

**Point-to-point / shared link type**

- used for trunk / tagged links

  

RST Path Cost:

FE (100 mbps) - 200,000

GE (1 gbps) - 20,000

10G (10 gbps) - 2,000

100G (100 gbps) - 200

  

**Bridge Protocol Data Unit (BPDU)**

- contain info that allows a switch to build redundant but loop free topologies
- CST - does listening and learning (2x forward delay 15 seconds) to reach convergence (picking a root bridge)
    
    - CST, every switch just relays it and increases message age by 1
  
- RST - uses flags to figure out who the root bridge is, happens to be way fucking faster
    
    - RST, every switch sends a hello message every 2 seconds
      
    

  
  

**802.1w**

- only ever reply to a proposal from a switch that is better than you (lower priority/mac address)

  

**PVST** - per vLAN spanning tree

- spanning tree works on a single LAN
- vLANs are just virtual LANs

  

- Sw1(config)#spanning-tree mode rapid-pvst | how to change from CST to RST
- Sw1(config)#spanning-tree vlan [id] priority [value] | changes the priority of a switch
- Sw1(config)#spanning tree vlan [id] root [primary/secondary] | changes the value