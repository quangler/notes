> [!caution] This page contained a drawing which was not converted.   

why do we need IPv6? - running out of IP addresses

  

what does IPv6 give us:

- 340 undecillion addresses

it doesnt play well with nat tho :/

  

**theres 128 bits in an IPv6 address** #important

**- broken up into 8 hextets**

**1 hextet = 16 bits**

**each hextet is separated by a COLON ONLY** #important

  

prefix = subnet mask (we use prefix now)

  

we don't subnet in IPv6 because we got so damn networks

- we are given 65000 NETWORKS

  

**the global routing prefix is 48 bits always** #important

**subnet range is 16 bits - we control this one** #important

**interface ID is 64 bits**

  

- know slide 8 #important

  

IPV6 zero elimination/suppression

- you remove any leading 0s in a hextet

- :0001: becomes :1:

IPv6 sets of 0s become either

- :0:1abc:0:0:

or - :0: and ::

**double colons are only for the largest set of 0000s, only ever put :: not more.**

  

**anycast is not used in the LAN, it is only used in the WAN** #important

- multiple different hosts will belong to the same anycast

- used for streaming often

- it sends to the BEST member of the anycast group

  

**multicast**

FF02::6/8 - this is the OSPF designated routers

- exact same way as IPv4

  

**unicast types**

- link-local (**NOT ROUTABLE**) MANDATORY #important

- just like 169 (APIPA)

- FE80::/10 (always /10, don't have to show it)

- EVERY link in a network NEEDS a link-local address

- best practice for DG = FE80::1/10

  

- global unicast

- public topology first 48 bits

- site topology is next 16 bits

- interface identifier last 64 bits

  

- slide 19 #important

  
  

- unique local address (**ROUTABLE**)

- the same as a private address in ipv4

- FC00 - globally assigned addressing

- FD00 - locally assigned addressing

  
  

**any IPv6 client that accesses the internet needs at LEAST 2 IP addresses.** #important

  

loopback address

- ::1: - the same as 127.0.0.1

  

unspecified address

- ::/128 - the same as 0.0.0.0 255.255.255.255

  

default route

- ::/0 - the same as 0.0.0.0 0.0.0.0

  
  

**enabling IPv6 on cisco routers**

- IPv6 routing is not enabled by default

  

'ipv6 unicast-routing' - enables IPv6 routing

int g0/1

'ipv6 address FE80::1 link-local' - creates the link local address (NEEDED)

'ipv6 address 2620::/64 eui-64' - creates a global unicast address on the interface

  

**Extended Unique Identifier (EUI-64) - KNOW SLIDE 30** #important

- it takes the mac address (48 bits)

- puts FFFF in the middle of the two halves

- swaps the second last bit of the first hextet

  

00:21:2F:B5:6E:10 -> 02:21:2F:FF:FF:B5:6E:10

  
  

**Network Discovery Protocol (NDP)** - uses local-link #important

- the ipv6 version of ARP and ICMP (ALL IN ONE)

  

**neighbor side**

- neighbor solicitation (NS) - requests L2 address from neighbor

- neighbor advertisement (NA) - response to NS

  

**router side**

- router advertisement (RA) - the router will send a request to the client when it comes up

- router solicitation (RS) - the client will send a request to the router when it comes up

  

**IPv6 static routing**

- ipv6 route ?

ipv6 route 2002:FC::/64 g0/2 2002:EF::1

  

**CISCO IPv6 needs IOS 15 or greater**

  
  

17 questions:

- no subnetting

- but there will be 0 suppression

  

make sure there is 8 hextets

make sure it's only 0-9&a-f