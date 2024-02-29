## IPv4 Address Allocation
In IPv4 DHCP, there is a DORA process.
- discover
- offer
- request
- acknowledgement

## IPv6 Address Allocation
IPv6 address and related info can be assigned:
- statically (manual configuration)
- dynamically
	- SLAAC (Stateless Address Auto-Configuration) - IPv6 addressing without DHCPv6
	- Stateless DHCPv6 - i have my address but i need other info
	- Stateful DHCPv6 - just like DHCPv4

### SLAAC - Stateless Address Auto-Configuration
IPv6 addressing without DHCPv6
- nodes configure addresses themselves with info from the routers (if available)
- uses:
	- **Router Solicitation** - client sends message to all IPv6 routers asking for IPv6 address info (FF02::2)
	- **Router Advertisement** - to all IPv6 devices - tells the hosts how they will receive IPv6 address information
		```
		A Flag = 1
		O Flag = 0
		M Flag = 0 (default on cisco routers, "i am everything you need | prefix, prefix-length, default gateway)
		```
		- client will get an address via random number or EUI64
suppress the router advertisements on the WAN ports.

Router must have IPv6 routing enabled:
```R1
ipv6 unicast-routing #enables IPv6 routing
```

**DHCPv6** uses UDP
- client port: UDP/546
- server port: UDP/547
client uses link-local address or address determined using other methods to transmit and receive DHCP messages

### Stateless DHCPv6 Server
- doesn't provide the global unicast address
- gives generic info to all clients - DNS server address, domain name
- client has to send an **information request** message to **all-dhcp-relay-agents-and-servers** multicast address (**FF02::1:2**)
- servers reply with the message containing the configuration information
```
A Flag = 1 - use SLAAC to create an IPv6 address
O Flag = 1 - communicate with DHCP server for other information (DNS, Domain Name), here is my info (prefix, prefix length, default gateway) but you need to get info from DHCPv6 server
M Flag = 0
```

```lab-2-r1-config
int g0/1
ipv6 nd other-config-flag
```

### Stateful DHCPv6 Server
Router responds to the client's router solicitation with:
```
A Flag = 0
O Flag = 0
M Flag = 1 - (you must ask a DHCPv6 server for all information)
```

```lab2-r1-stateful
int g0/1
ipv6 nd managed-config-flag
```

What if the DHCPv6 server is on another link?
```Router
ipv6 dhcp relay destination <IPV6_DHCPv6Server>
```

DHCPv6 Commands:
```SLAAC
ipv6 unicast-routing
int g1/0/1
no ipv6 nd supress-ra ! this is default
```
```Stateful DHCPv6
int g1/0/1
ipv6 nd managed-config-flag
ipv6 dhcp server <POOL-NAME>

ipv6 dhcp pool <POOL-NAME>
address prefix <ipv6-prefix>/<prefix-length>
dns-server <dns-address>
domain-name <domain-name>
```
```Stateless DHCPv6
int g1/0/1
ipv6 nd other-config-flag
ipv6 dhcp server <POOL-NAME>

ipv6 dhcp pool <POOL-NAME>
dns-server <dns-address>
domain-name <domain-name>
```

## DNSv6
**uses AAAA records** instead of A records.
reverse lookup zones use the `ip6.arpa` address.
- sequence of nibbles in reverse order

DNSv6 Requirements:
- server must support IPv6
- DNS server software must support IPv6

deploy DNSv6 incrementally on existing networks
do NOT BREAK something that works fine (IPv4 DNS)