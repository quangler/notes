### IPv4 DHCP
- **Client: UDP/68**
- **Server: UDP/67**
lease renewal happens at 50% of lease time, then at 87.5% lease time, if lease expires DORA happens again
#### DORA Process
discover, offer, request, acknowledgement
**D** - client -> broadcasts (src: 0.0.0.0, dst: 255.255.255.255, **UDP 67**) a DHCPDISCOVER message to all DHCP servers
**O** - server -> responds via broadcast (dst: 255.255.255.255, **UDP 68**) with DHCPOFFER - lets client know they exist, gives them the scope information
**R** - client -> broadcasts (src: 0.0.0.0 dst: 255.255.255.255, **UDP 67**) with DHCPREQUEST - asks DHCP server for an IP address and other info
**A** - server -> broadcasts (DST: 255.255.255.255, **UDP 68**) with DHCPACK that gives client requested info
### HTTP/HTTPS
#### understand request / response operation - understand TCP initial connection process
1. user issues URL from browser (http://host:port/path/file)
2. browser sends request message to server
3. server maps the URL to a file or program under the document directory
4. server returns a response (or error) message
5. browser formats the response and displays it
---
TCP 3 way handshake to establish connection on port 80 or 443:
- one connected:
- client makes an `HTTP GET` request,
- server responds with status code (indicates success or fail)

### ICMPv4
#### know most common ICMP types and codes - when are they sent to the initiating host
- **ICMP Type 3** - destination unreachable - packet sent could not be delivered
- **ICMP Type 5** - redirect - the taken path is not the best way to get to the destination
- **ICMP Type 11** - time exceeded - ran out of TTL
- **ICMP Type 8**, code 0 -  ICMP echo request - sending a ping or traceroute
- **ICMP Type 0**, code 0 - ICMP echo reply - getting a reply from a ping or traceroute (the last one)

#### know the traceroute process on windows and linux/unix hosts
##### Windows:
- **sends 3** ICMP Type 8: Code 0 - ICMP echo request
- **starts with 1 TTL**, then increases each hop (as it continues down the line of routers)
- when the TTL reaches 0 the routers return **ICMP type 11 - TTL exceeded** packet
- number of hops is one less than the reply
##### Linux:
- uses **UDP** packets instead of ICMP packets
- still sends 3 packets
- still starts with 1 TTL and increments per hop
- still has an ICMP TTL packet return

### FTP
- **FTP** uses TCP
- TFTP uses UDP
- **command channel - TCP : 21**
- **data channel (data transfer) - TCP : 20** (usually uses dynamic ports)
- sometimes there are multiple data channels (using dynamic ports)
Connection process:
	TCP 3 way handshake (SYN, SYN-ACK, ACK) - this creates the command channel connection
	- waits for a PORT or PASV command - (PORT = active, PASV = passive)
#### understand passive / active modes
##### **Active mode:** PORT command
- client connects from **random TCP port** above 1023 to FTP server **port 21** (command channel)
- **FTP server establishes the data channel**

##### **Passive Mode:** PASV command
- **client initiates connection for both channels** - command and data
	- done as a workaround to some firewalls blocking unauthorized connection requests from external parties
- client requests server (on command channel) to start listening on a port (server chooses)
- some FTP servers don't support passive mode
	- if not supported:
		- responds to SYN with TCP RST
		- if server is using different port than client - FTP can't establish properly
### Troubleshooting
#### steps in troubleshooting methodology
1. define the problem - what does "the network is slow" mean?
2. collect information (system, network, applications, OS)
3. capture and analyze packets and flow - capture as close to the problem as possible, check TCP handshake, check the round trip time
4. consider other tools - tcpdump, fiddler (web debugging), WLANPi (wifi)
#### issues and symptoms presented in the slides
1. issue: TCP connection refused by server | possible symptom: client's SYN packet followed by `destination unreachable`
2. issue: connection blocked by a firewall | possible symptom: no response to SYN packet, no response to UDP application request
3. issue: slow application at server / slow load of remote content | possible symptom: TCP Based - high `tcp.time_delta` (large delay between ACK and data), UDP based - high `frame.time_delta` (large delay between request and response)
4. routing loop | identical packets - no TCP retransmissions, TTL exceeded a bunch
5. switching loops | huge amount of identical packets
i aint typing them all - go and read
#### most common elements you put in Wireshark as part of a troubleshooting profile
- TCP delta (`tcp.time_delta`) - time delay in TCP conversation
- DNS delta time (`dns.time`) - time delay for DNS request and response
- HTTP delta time (`http.time`) - time delay between HTTP request and HTTP response
- TCP stream number (`tcp.stream`) - TCP conversation number
- window size (`tcp.window_size`)- indicates calculated TCP window size
- DNS errors
- HTTP errors