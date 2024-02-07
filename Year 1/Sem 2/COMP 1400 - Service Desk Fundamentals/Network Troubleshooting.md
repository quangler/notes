Definition:

- experience and science
- to the uninitiated it may look like an artform

  

Methodologies:

- process to go through
- helpdesk > enterprise support
- hardware, software, network, storage and security problems

  

1. identify the problem and determine scope
2. see what the problem is, how many users is it affecting | single PC not working, probably not a server issue.

  

1. establish a theory of probable cause
2. what do you think caused the issue

  

1. test theory to determine a cause
2. try to figure out where the issue truly lies

  

1. establish a plan of action to resolve the problem
2. list options in order of probability

  

1. implement the solution or escalate as appropriate
2. try your solutions (1 at a time) because your fix might have broken something else

  

1. verify full system functionality & perform root cause analysis
2. make sure everything is working, if you can, figure out what caused the issues to occur
  
4. Document findings, actions and outcomes
5. what did you try, what worked, what didn't work

  
  

Common problems, causes and tools:

clients: hardware/software issues

storage & disks: storage

server: server stuff

firewalls routers and switches

security

  

Troubleshooting Methodologies (continued):

**Identify the problem and determine scope:**

**what changed?**

- change causes failures
- updates, configuration, movement, hardware/software
- questions users/stakeholders about changes made

**collect additional documentation**

- logs, performance counters
- expected configuration and operation - what do they expect it to do

**if possible, make a backup before performing troubleshooting actions**

- you could potentially mess things up a lot more while trying to fix the issue

**can you replicate the problem?**

- replicating the problem can lead to a cause, if you know when it happens that might help you find the issue

  

**establish a theory of probable cause:**

**gather information - include diagnostic and log**

- updates, configuration, movement, hardware/software
- questions users/stakeholders about changes

**question the obvious**

- is it plugged in
- is it on

**propose a hypothesis**

- educated guess of the problem

**is there a common element causing multiple problems?**

- single failure will appear as multiple problems (dns issue for example)
- do the observed symptoms point to a common cause?

  

**establish a plan of action to resolve the problem:**

- if confirmed, determine steps to resolve problem
- if NOT confirmed, establish new theory or escalate.

  

**test the theory to determine cause:**

- what steps will you take to resolve the problem?
- notify impacted users/stakeholders
- do i need to submit a change request?

  

**implement the solution:**

**make one change at a time**

- multiple changes are hard to track for success, and often add more problems
- document changes and results

**test and confirm the change resolved the problem**

- test one change at a time
- test often involve several use-cases

**if the problem is not resolved - reverse course!**

- reverse the change
- implement and test a new change

**may need to escalate as appropriate**

- the problem may be more complex and involve other teams
- this may impact more users/stakeholders

  

**verify full system functionality**

- confirm successful operation by testing and checking with users/stakeholders
- implement preventative measures if needed

  

**perform root cause analysis**

**perform after problem is resolved**

- root cause analysis takes time (up to company you work for)
- repair the outage first if possible

**attempt to determine reason for failure**

- changes, outside influence, hardware failure, malware

**are there prevention measures or policies that can prevent future problems?**

- enforcing strong password for ex.

  

**documentation findings, actions and outcomes**

**documentation is most important!** (i mean fixing the issue is probably more important)

- documents the troubleshooting process and resolution
- provides information for future similar problems
- often documented in a trouble-ticket system

**document the symptoms of the problem**

**document the troubleshooting actions**

**document the cause of the problem**

**document the systems and users affected**

**document the solution to the problem**

  

**ABC-5 Steps program**

1. Check the political layer - ask if its a good time to fix stuff right now - **ALWAYS** ask if you can remote in
2. Check the Physical Layer first
3. Do a quick ipconfig /all
4. Ping yourself. (ping 127.0.0.1)
5. Ping neighbor. Can I connect to the LAN
6. Ping gateway
7. Ping remote IP address (8.8.8.8/4.2.2.2)
8. Ping remote DNS name ([www.google.ca](http://www.google.ca))
  

  

**Hardware Problems, Causes and Tools**

- all hardware and network hardware can have issues.
- can be very complex

**Environmental Causes**

- can cause many of the problems discussed (shut down, slow down)
- can causes multiple simultaneous failures (if something breaks because it gets flooded for ex.)
- can be gradual failures over time (corrosion, or something)
- will reduce the life span of your hardware
- expensive to replace!

**Failed Post**

common causes

- hardware failure
- memory
- processor/bios
- temperature

tools/actions

- beep codes lookups
- displayed numeric codes lookups

  

**Component Failure**

common causes

- hardware failure

tools/actions

- hardware diagnostic
- remove and re-insert
- replace
- use ESD equipment

  

**Incorrect Boot Sequence**

common causes

- configuration error
- often after adding a new device

Tools/actions

- check BIOS config

  

**Software Problems, causes and tools**

- more than just computers, involves ALL software, drivers, etc.
- can get very complex

  

**Logon Failure**

common causes

- account locked
- unknown password
- password expiration

tools/actions

- account policies
- password policies
- password reset

  

**Resource Access Problems**

common causes

- permissions
- user account control
- network/connectivity problem

tools/actions

- verify permissions
- verify connectivity

  

**BSOD**

common causes

- failed driver software
- failed hardware - disk corruption

tools/actions

- check error codes
- replace/remove driver
- replace/remove hardware

  

**Driver Issues**

common causes

- mismatch driver for hardware
- damaged or corrupt
- unsigned 3rd party driver

tools/actions

- download new and correct driver
- use signed drivers

  

**Slow OS Performance**

common causes

- out of disk space - shit sloooooows down
- excessive paging - cant fit software into ram so it puts it in disk drive
- excessive processing - sometimes a program will eat your performance
- fragmentation - moving everything around on the drive which can cause cell degradation

tools/actions

- monitoring tools performance
- located bottleneck
- defragment disks

  

**Server Problems, Causes and tools**

- involves DHCP, DNS, FILE SERVERs

  

DHCP Review

D - discover

O - offer

R - request

A - acknowledgement

  

General terms #important

- unicast vs broadcast - you know the address you're sending to (MAC)
- multicast - talking to multiple end points at the same time
- Active directory
- LDAP
- Domain Controller
- TCP - connection oriented
- UDP - screams into the void
- IPv4 vs IPv6
- CIDR
- APIPA
- BOOTP/DHCP
- ICMP: Ping, Tracert & pathping
- ARP/RARP
- NSLookup
- FTP/HTTP
- ISP