- add a redundant gateway to servers & clients in case one goes down.

- devices today very rarely fail, not the case a ton of years ago.

  

router redundancy

- introduces the **virtual router (192.168.1.254)**

  

- **active gateway** - the gateway that currently owns the virtual router address (192.168.1.253 **& 192.168.1.254)**

- standby router - the backup for the active router, will automatically switch to own virtual router address upon old active gateway failure. (192.168.1.252)

  

the default priority is - 100 | higher is better.

- you will see 105, and 110 often.

  

- pre empt command - allows one to come up after another fails.

  

**HSRP Groups**

- Group Number - terry likes group number as VLAN ID (good practice)

(ex. Active 10/11 & Standby 10/11)

  

HSRP Priority and Preemption commands

  

interface vlan 10

ip address 172.20.127.253 255.255.255.0

standby version 2

standby 10 ip 127.20.127.254

standby 10 priority 105 - sets priority to 105

standby 10 preempt - sets highest priority router to active router RIGHT NOW

standby 10 track g1/0/1 - lets you monitor the interface

  

HSRP default mac address: -

version 1 - 0000.0c07.acXX

version 2 - 0000.0c97.fXXX

  
  

TEST:

a combo of OSPF and HSRP **IN THE SAME FILE**

**theory test - 42 questions**

- vast majority about routing

- 1 or 2 are static routing (based on default route)

- generic dynamic routing

- a bunch of ospf questions

- a few subnetting

- a few HSRP

  

**Practical -**

no more than 6 infrastructure devices

  

- ospf

- hsrp

  

out of 60 marks, mostly repetitve

  

router ospf

router id

autocost

network statement

originate

  

version

standby version

standby ip

standby priority

standby preempt

  

ip route