## Requirements:

- [ ] Description of LSA Types
	- [ ] LSA 1 - used by point to point routers - discuss who they are
	- [ ] LSA 2 - used by multiaccess setups to discuss who the members are
	- [ ] LSA 3 - sent by ABR, sends info to multiple areas (not to totally stubby)
	- [ ] LSA 4 - only in standard / backbone, ABR sends ASBR IP to the area
	- [ ] LSA 5 - sent by ABRs to declare external routes (NON NSSA)
	- [ ] LSA 7 - sent by ASBR to declare external routes (NSSA ONLY)

- [ ] Description of each area type
	- [ ] backbone (?) - area 0, can have multiple paths out
	- [ ] standard (?) - any area #, can have multiple paths
	- [ ] stub area - only one path in - LSA 1, 2, 3
	- [ ] totally stub area - only one path in - LSA 1, 2
	- [ ] not-so-stubby area - stub plus external route (single path in, + path to non OSPF network)
	- [ ] totally not-so-stubby area - 

- [ ] Description of OSPF Router types
	- [ ] designated router
	- [ ] backup designated router
	- [ ] area border router
	- [ ] autonomous system border router

- [ ] **How-to** section
	- [ ] steps to accomplish full connectivity (screenshots)
	- [ ] show configs of one router in each area
	- [ ] show configs of the border routers

- [ ] Analysis of the OSPF tables
	- [ ] `show ip ospf neighbor`
	- [ ] `show ip route`
	- [ ] LSDB??

## Formatting
### Title Page
- Assignment name - Internetworking Research Project
- graphic (optional)
- student name - Quinn Parent
- course number - NETW2400
- Instructor Name - Monica Ciobanu

## VIDEO:
- [ ] **Max 15 minutes**
- [ ] intro - name, topic title, course title
- [ ] conclusion - summarize main topics
- [ ] references
