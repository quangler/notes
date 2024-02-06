IPv4 and IPv6 cannot directly communicate

| IPv4 | IPv6 |
| ---- | ---- |
| 32 bit address length | 128 bit address length |
| 4.29x10<sup>9</sup> (4.3 billion) | 3.4x10<sup>38</sup> (340 undecillion) |
| dotted decimal format<br>ex. 10.10.10.10 | groups of 4 hexadecimal digits separated by colons; 0-9 an A-F<br>ex. 2001:0db8:aaaa:1111:0000:0000:0000:0100 |
| supports broadcast | does **not** support broadcast<br>replaced by: **link-local all nodes multicast group (ff02::1)** |
| uses ARP to mac MAC addresses (broadcast ARP) | uses **NDP (neighbor discovery protocol)** to map to MAC addresses (multicast NDP) |
| configured manually or using DHCP | supports **autoconfiguration** capabilities (stateless)<br>enabled by default on all OS |
| no security added to the protocol | **IPsec** is built into IPv6 and can be used with a proper key infrastructure |
| uses NAT to mask non-routable addresses | allows direct addressing due to its vast address space |
| packet size of minimum 576 bytes required; <br>fragmentation optional | packet size of **1208** bytes required without fragmentation<br>**Fragmentation is done by the sending host only** (not the router) |

## Headers
| IPv4 | IPv6 |
| ---- | ---- |
| 20 bytes - 60 bytes | 40 bytes fixed |
| 12 fields | 8 fields |
| IPv4 IP header length | doesn't need it, fixed header size |
| IPv4 Total length field - header plus data | IPv6 Payload Field - only size of data, not header |
| IPv4 Type of Service - how routers should handle packets (QoS) | IPv6 Traffic Class - how routers should handle packets (QoS) |
### IPv6 Headers
- IPv6 Flow Label - new in IPv6 - used to identify all the packets within the same flow
	- value is given by the source to a flow of packets, and that value is the same across that flow
- IPv6 Next Header = **Protocol** field in IPv4
	- indicates data payload type (TCP, UDP, ICMPv6)
- IPv6 Hop Limit = **TTL** field in IPv4
	- number of router hops before packet is discarded
## IPv6 Extension Headers
- add flexibility and allow for future enhancements
- **follow main IPv6 header, presence are indicated in the "next header" field**
	- 0 - hop-by-hop options
	- 6 - TCP segment
	- C2 - jumbo payload
	- 43 - routing
	- 44 - routing
	- 50 - encapsulating security payload (ESP)
	- 51 - authentication header (AH)
	- 60 - destination options
## Why bother with IPv6?
- **Built-In support for mobility** - IPv6 hosts can move around the internetwork and retain their IPv6 address and without losing current application sessions
- **More Efficient Routing** - IPv6's huge address space makes for much easier aggregation of blocks of addresses on the internet, making routing on the internet more efficient
- **No need for NAT/PAT** - huge public IPv6 addresses means we don't need NAT/PAT, which avoids some NAT-induced application problems
- **More efficient packet processing** - IPv6's simplified packet header makes packet processing efficient. Compared with IPv4, IPv6 contains no IP-level checksum, so the checksum does not need to be recalculated at every router hop
- **No Broadcast** - IPv6 does not use layer 3 broadcast addresses, instead relying on multicasts to reach multiple hosts
- **VoIP and QoS** become more robust - IPv6 introduces a couple of fields in its header that are reserved specifically for QoS
- **Simplified Network Configuration** - address auto-configuration (address assignment) is built in to IPv6

## Transitioning to IPv6
- **Dual-stack** - running both IPv4 and IPv6 in parallel
- **Tunneling** - IPv6 packets encapsulated inside IPv4 - (?? how does it do this for packet size)
- **NAT64** - translating between IPv4 and IPv6
- **Native IPv6** - all IPv6 (the goal of every organization)

## Reading and Using IPv6
IPv6 are 128-bit addresses represented in:
- eight 16-bit segments
- hexadecimal between 0000 and FFFF
- separated by colons
one hex bit = 4 bits
### Rule 1: Leading 0's
- 0100 - can be shown as 100
- 0DA1 - can be shown as DA1
- 0000 - can be shown as 0
### Rule 2: Double colon
using a `::` can replace any **single, continuous** string of hextet containing all 0s
- `::` = 0000:0000:0000:0000:0000:0000:0000:0000
## IPv6 network prefixes
same style as IPv4 - just longer 
	3ffe:1944:100:a::/64 - first 64 bits are network 
## IPv6 Addresses
- **Default Route Address** - all zeroes and the prefix length of zero turns into:
	- **::/0**
- **Unspecified Address** - used in some neighbor discover protocol procedures
	- filler address, indicating absence of real IPv6 address
	- different than a default route (by prefix length)
	- **::/128**
	-
- **Loop back address** / **Local host address** - host talking to itself
	- ::1/128
