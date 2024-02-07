LAN - defined by who owns / administers it - usually the whole thing

  

Network - part of a LAN

  

(historically it was the 5-4-3 rule, 5 switches, 4 links between them, 3 can be populated)

  

**Bridge:**

segment = collision domain

interconnects segments via software @ L2

2-4 segments

  

**Switch:** hardware

link = segment = collision domain

connects devices or segments

8-24 devices/segments

  

**Main functions of L2 Switch:**

- address learning
    
    - MAC address table is called a "CAM table" - content accessible memory
- data frame forwarding/filtering
    
    - flooding, check for frame size
- loop avoidance
  

  

when destination mac address is not in table, floods the mac address (copies it then sends it out every active interface)

**flood = behavior, broadcast = address**