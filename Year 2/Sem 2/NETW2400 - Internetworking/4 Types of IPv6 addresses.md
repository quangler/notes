![[Pasted image 20240206101119.png]]
### Unicast
**Global Unicast** - can be assigned internally, can be accessed externally.
**Link-Local** - allows you to connect to other devices internally. Communications to router is through Link-Local address.
**Unspecified** - when you have no address and it's looking for an IPv6 address
**Unique Local** - only use if you have an IPv6 address that doesn't need to access outside of your network.
**Embedded IPv4** - IPv4 address embedded inside of an IPv6 address
### Multicast
**Solicited Node** - checks to see if anyone is using an IP address (doing this to find an IP address)
**Assigned** - you set this address - usually for servers

## Global Unicast (GUA)
**2000:0000:0000:0000:0000:0000:0000:0000 to 3FFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF**
- unique addresss
- routable
given out by **IANA**
#### Terminology:
**Prefix** - equivalent to network address
**Prefix length** - equivalent to subnet mask in IPv4
**Interface ID** - equivalent to host portion
![[Pasted image 20240206102542.png]]
### 3-1-4 rule
- First **3** hextets are the **global routing prefix** (registry, ISP, site prefix)
- Next **1** hextet is **subnet**
- last **4** hextets are the **interface ID** - this is the unique part
## Link Local Addresses
- scope is defined per link - uniqueness assured only on one link
- **not routable off the link**
- devices can determine their own link local IPv6 address - don't need to communicate with other devices
- range of **FE80::/10** but realistically only **FE80::/64** is used.
- devices that have multiple interfaces, every interface is connected to **FE80::/10**
	- have to specify which interface to ping

when dynamically obtaining their IPv6 addressing - **SLAAC** - Stateless Address Autoconfiguration
- they use ICMPv6 **Neighbor Discovery Protocol**
	- **Router Solicitation** and **Router Advertisement messages** to obtain the **Global Unicast Prefix** and configure a Global IP address
	- The host keeps the **link-local** address and the default gateway is the **router's Link-Local Address**
- SLAAC doesn't provide DNS info

## Unique Local Addresses (ULA)
- have the same function as IPv4 private addresses - not advertised on the internet
- begin with **FC** (**FC00::/7**)
	- **FC00::/8** - Centrally Assigned Addresses
	- reserved for providers 
	- **FD00::/8** - used inside organizations
- not necessary considering the availability of the Global Unicast addresses
### Multicast Addresses (ULA)
- identify a set of devices - multicast group
- equivalent to IPv4 - 224.0.0.0/4
- begins with **FF** (**FF00::/8**)
- a packet being sent to a multicast group is originated by a single device:
	- source address: **unicast address**
	- destination address: **multicast address**

FF02::1 - All noes - scope: link local
FF02::2 - All routers - scope: link local
FF05::101 - All NTP servers - scope: site-local

### Anycast Addresses
- represent a service that might appear on multiple devices - same IP can live on multiple devices providing the same service
- used in services such as Content Delivery Networks or DNS
- also used in 6to4 tunnels

## Required IPv6 addresses
### Devices
The IPv6 standard specifies that each host must assign the following addresses to identify itself:
- link-local address for each interface - **FE80::/10** or **FEBF::/10**
- any assigned unicast addresses
- the loopback address - **::1/128**
- the all-nodes multicast address - **(assigned) FF00::/8**
- solicited-node multicast address for each of its assigned unicast and anycast addresses - **FF02::1:FF00:0/104**
- multicast addresses of all other groups to which the host belongs
### Routers
IPv6 standard specifies that a router needs to recognize the following addresses to identify itself:
- link-local address for each interface
- assigned unicast addresses
- loopback address
- all-nodes multicast addres
- **all-routers** multicast address
- subnet-router anycast address for the interfaces for which it is configured to act as a router on each link
- anycast addresses with which the router had been configured
- multicast addresses of **all other groups** to which the router belongs
