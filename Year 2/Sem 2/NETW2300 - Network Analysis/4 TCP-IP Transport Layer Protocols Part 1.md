**UDP and TCP** are transport layer protocols - help provide transport for IP
- provide error control and flow control to facilitate and verify the successful delivery of data and an interface for network application
- IP (network layer) is considered a **connectionless** protocol - responsible for getting the packets from source to destination, no guarantees of successful deliver

**UDP with IP** - connectionless - best-effort delivery
- no built in error checking or retransmission
- checksums are optional per datagram
**TCP with IP** - connection-oriented - with sequencing, error-recovery and sliding window mechanisms
- provides end-to-end reliability - preferred protocol for applications that require reliable delivery
#### Understanding Transport Control Protocol (TCP)
TCP Hosts create a virtual connection by using a handshake process:
- **SYN** - sets the initial sequence number
- **SYN/ACK** - response to SYN that agrees with the received SYN
- **ACK** - acknowledges the SYN/ACK response
TCP transfers data as a continuous stream of bytes:
- TCP Streams - blocks of data sent by applications to the transport layer which divides them into segments to send and reassemble on the receiving host
- (max MSS is 65,495 bytes)
TCP Header's size can vary between 20-60 bytes
- **10 required fields (20 bytes)** - optional 40 bytes of additional data

**Source Port Number** -
**Destination Port Number** -
**Sequence Number** - 
**Acknowledgement Number** -
**Data Offset** -
**Reserved** - 
**Control flags** - 6 mandatory - 9 bits
	- **U** - Urgent - not used much
	- **A** - ACK
	- **P** - Push - SSH - text is pushed through immediately (you don't see it)
	- **R** - Reset - if something crashes or a firewall is blocking
	- **S** - SYN
	- **F** - FIN - used at the end of the connection to sort of "shut down"
**Window Size** - 
**Checksum** - 
**Urgent Pointer** -
**Optional Data** - 
#### Primary functions and Features of TCP communications:
- Start-up connection process (TCP Handshakes)
- keep-alive process
- connection termination
- sequence and acknowledgement process
- error-detection and error-recovery processes
- congestion control

##### Start-up connection process (TCP handshake)
Process of negotiation between two communicating hosts
- parameters of TCP socket are negotiated before the actual data transmission
- one host initiates the handshake to another host to:
	- ensure the destination host is available
	- ensure the destination host is listening on the destination port number
	- inform destination host of initiator's **sequence number**
- **sequence number** is used to keep track of how much data is sent
- **acknowledgement number** informs sender that the data was received successfully

1.  **SYN** - host 1 initiates the connection to host 2 to ensure it is available and listening
	- the packet contains: 
		- host 1's starting seq number 
		- source and destination port numbers 
		- the MSS that can fit into each segment
MSS - maximum segment size - usually around 1460
MSS = total length - IP header (20 bytes) - TCP header (20 bytes)

2. **SYN-ACK** - host 2 responds with its own starting sequence number (**SYN bit = 1**) and an indication of MSS, as well as the destination and source port number. 
	- also **sets ACK bit to 1** and acknowledges the receipt of the first packet in the handshake and indicates the **next Seq number expected to be received** from host 1

3. **ACK** - Host 1 acknowledges the receipt of host 2's seq number and MSS value

TCP Half-Open connections:
- can occur when a handshake process **does not end successfully** with a **FIN** ack
- happens in this order:
	- `SYN >>>>>`
	- `<<<<< ACK SYN`
	- `<<<<< ACK SYN`
	- `<<<<< ACK SYN`
- known as a **two-way handshake**
- can indicate a syn-attack


##### keep-alive process
maintains the connection when there is no data being sent across the wire, eliminates the need for a three-way handshake to be done again
- either application layer or transport layer's responsibility
- disabled by default on windows server and client
- application programmer may enable it
- KeepAliveTime setting - how long to wait before sending first TCP keep-alive packet
##### connection termination
requires 4 packets
- **Packet 1** - host 1 sends a TCP packet with the **FIN** and **ACK** flags set
- **Packet 2** - host 2 acknowledges by sending back a packet with the **ACK flag set** and no longer accepts data from host 1, still can transmit data to host 1
- **Packet 3** - if host 2 has no more data to transmit, it will also terminate the connection by sending a packet with the **FIN** flag set, **ACK** flag is still valid in the packet
- **Packet 4** - host 1 acknowledges by transmitting a packet with the **ACK** flag set