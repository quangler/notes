DHCP is Dynamic Host Configuration Protocol, it allows clients to dynamically get IP addresses and configuration.
#### Ports (UDP)
**Client: 68**
**Server: 67**

#### Parts of DHCP:
**DHCP Scope** - a range/pool of addresses that can be assigned to clients by the DHCP server
**Leases** - the period of time that the IP is given to the client
**Options** - other network parameters that are handed out by the DHCP server
**Exclusions** - individual or ranges of IPs that are not included in the DHCP scope
**Reservations** - used for permanently leasing an address to a client that is handled by the DHCP server (uses MAC)

### DORA Process
Discover, Offer, Request, Acknowledgement
**D** Client > broadcasts (src: 0.0.0.0, dst: 255.255.255.255, **UDP 67**) a DHCPDISCOVER message to any and all DHCP Servers
**O** Server > responds (dst: 255.255.255.255, **UDP 68**) with a DHCPOFFER message that lets them know that they exist and what the scope is
**R** Client > responds (src: 0.0.0.0, dst: 255.255.255.255, **UDP 67**) with a DHCPREQUEST message that asks the DHCP server for an IP address (and other info)
**A** Server > confirms (dst: 255.255.255.255, **UDP 68**) with the DHCPACK that assigns the client with the IP address.

### IP Lease Renewal
- client is assigned an address via DORA
- at **50%** of it's lease (day 4 by default) - client will attempt to renew its lease
	- sends a renewal request and expects an answer only from the original DHCP server (max 3 times - 4, 8, 16 seconds)
- if DHCP server was unavailable:
- at **87.5%** of lease time (day 7 by default) - client tries again, but this time sends a broadcast to find any DHCP server that can renew its IP
	- it will continually retry this every 2 minutes until it gets a DHCP ACK or the lease expires
- lease expires: DORA starts again

### DHCP Header
**Operation Code** - 1 = a request message, 2 = a reply message.
**HType** - hardware type - type of hardware for the local network - Ethernet, IEEE 802, Fiber Channel 
**HLen** - Hardware address length - the size of the hardware address (6 bytes)
**Hops** - set to 0 by a client transmitting the request and used by relay agents to control DHCP forwarding
**XID** - transaction ID - has to be the same on the reply
**Flags** - indicate if the message is a broadcast (bit is turned on) or a unicast (bit is turned off)
**ClAddr** - Client address in renewal - client knows it's IP so it fills this field with its IP (in initial request, is 0)
**YlAddr** - server fills this field with the IP it offers to the client
**SlAddr** - Server IP address of the next server the client should use in the next request
**GlAddr** - Gateway address - filled by relay agent with its IP (if server on same network, stays 0) 
**CHAddr** - Client Hardware address - Client MAC
**SName** - Server Name
**File** - File name - a path to a boot file (optional)
**Options** - DHCP Options - subnet mask, router IP, domain name, DNS server IP
### Wireshark Filters
`dhcp`
`udp.port == 67` server listens on port 67
`udp.port == 68` client listens on port 68
`dhcp.type == 1` DHCP requests
`dhcp.type == 2`  DHCP replies
`dhcp.ip.your == x.x.x.x` displays packets where the IP `x.x.x.x` is offered