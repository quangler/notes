## **ICMP** - Internet Control Message Protocol
- provides info on network connectivity and routing behavior
- provides a way to return information to senders
- ICMP messages are specially formatted IP datagrams - 8-byte header, on top of IP
- can report errors or network congestion; the host has to do something about it though

### Types of ICMP messages:
- **Echo Messages**: used by ping and traceroute to test end-to-end connectivity
- **Redirect Messages**: used by routers to let the source know there is a better path to a destination (if this packet is not sent by a router, it should be considered suspect)
- **Destination Unreachable Messages**: used to tell the source that their packet could not be delivered for some reason - reason is stated in the destination unreachable message.

### RFC792
Originally RFC777 - made obsolete by RFC792 in Sept 1981
- provides basic specs for all ICMP messages

### ICMPv4 Header
- ICMPv4 header is **value 1 in IP header protocol field**
ICMP packet contains three required fields after IP header:
- **Type** - type of ICMP message that can be sent (ex. type 0 - echo reply, type 3 - destination unreachable, type 8 - echo, )
- **Code** - message inside of the ICMP message (ex. code 0 - network unreachable, code 3 - port unreachable)
- **Checksum** - provides error detection for the **ICMP header only**

#### Destination Unreachable Packets
**ICMP Type 3** - Destination Unreachable
- returned to source node from router
- when packet that was sent could not be delivered to destination address
- reasons: invalid IP, no route to the destination, destination host down
- destination unreachable message includes the IP header and 8 bytes of the original datagram that triggered this response
- sender can then use this information to decide how to correct the problem
how it works:
1. Client sends a DNS query somewhere (10.2.10.2 to 10.3.71.7)
2. Client receives an ICMP reply (from 10.3.71.7 - destination unreachable/port unreachable) - the port was not available to access

#### Redirect
**ICMP Type 5** - Redirect
- **Redirect datagram for the network**: the ICMP sender (router) is not the best way to get to the desired **network** - reply contains the IP address of best router the destination
- **Redirect Datagram for the host**: the ICMP sender (router) is not the best way to get to the desired **host** - reply contains the IP address of the best router to the destination host
**Codes**:
- 0 - redirect datagram for the network (or subnet)
- 1 - redirect datagram for the host
- 2 - redirect datagram for the Type of Service and Network
- 3 - redirect datagram for the Type of Service and Host

#### Time Exceeded
**ICMP Type 11** - Time Exceeded:
**Codes:**
- 0 - **Time to live exceeded in transit:** ICMP sender (router) indicates that originator's packet came in with a TTL of 1. Router can't decrease TTL value to 0 and forward
- 1 - **fragment reassembly time exceeded**: ICMP sender (destination host) did not receive all fragment parts before the expiration (in seconds of holding time) of the TTL value of the first fragment received

#### Echo Request / Echo Reply
**ICMP Type 8** : Code 0 - ICMP echo request
**ICMP Type 0** : Code 0 - ICMP echo reply

#### Traceroute
**ICMP Type 8, Code 0** - ICMP echo (ping) request and reply
**ICMP Type 11** : Code 0 - time-to-live exceeded
- traces the exact sequence of routers from source to destination
- hop-by-hop basis
	- each router forwarding the message responds to the source host with a traceroute message (its IP address and time in ms)
The traceroute is completed like this:
**EACH PING IS SENT 3 TIMES.**
**Client sends a packet with a TTL of 1 to router 1** - this router can't decrement and forward so it returns, the client knows there is at least a router in between
**Client sends a packet with a TTL of 2 to router 1, this is decremented then forwarded to router 2** - the router can't decrement and forward so it returns.
This keeps going until the packet reaches the destination - it will give the client the number of hops its roundtrip time.
- the number of hops is one less than when it replies

### Security Issues for ICMPv4
- **ICMP** - can be used as an information-gathering tool
- **IP address scanning process** - one method of obtaining a list of the active hosts
- **IP host probe** - performed by sending a ping packet to each host within a range and noting the responses

### Wireshark Filters
`icmp.type == 8` - ICMP echo request
`icmp.type == 8 || icmp.type == 0` - ICMP echo request or response
`(icmp.type == 8) && !(icmp.code == 0x00)` - ping packets where code is not set at 0
`icmp.type == 13 || icmp.type == 15 || icmp.type == 17` - ICMP timestamp request, information request or address mask request (possible OS fingerprinting)
`TCP && icmp.type == 3 && (icmp.code == 1 || icmp.code == 2 || icmp.code == 3 || icmp.code == 9 || icmp.code == 10 || icmp.code == 13)` - ICMP destination unreachable response to a TCP handshake (possible firewalled TCP target) - looks for TCP header embedded after the ICMP header
`icmp.type == 11` - ICMP time to live exceeded (possible traceroute)
`icmp.type == 3 && icmp.type == 4` - fragmentation needed, but don't fragment bit set (path MTU discovery packet (how big of a frame can be sent??) - don't block this packet)
