## Primary Functions and Features of TCP Communications:
- header fields and functions
- start-up connection process (TCP handshake)
- keep-alive process
- connection termination
- sequence and acknowledgement process
- error-detection and error-recovery process
- congestion control

### Sequence and Acknowledgement Process
- guarantees that packets are ordered properly and protects against missing segments
- during handshake process: each side of connection sets its own starting sequence number
- except during the TCP start-up and teardown sequences, the ACK number field increments only when data is received
- each side increments its sequence number value by the **amount** of data included in the outbound packet
- ex. ACK = 2921 | means it has received 2920 bytes and is expecting the next segment to start at 2921
- ![[Pasted image 20240129102843.png]]- client expecting next data starting at seq=11681
- ![[Pasted image 20240129102914.png]]- server sending data that ends at 11680
### Error-Detection and Error-Recovery Processes
many reasons for a communication sequence to fail:  
- routing issues, firewalls, software, hardware misconfigurations, congestion etc.
TCP error-detection and error-recovery mechanisms:
- checksums
- acknowledgements
- retransmissions
#### Retransmissions
Two events that generate retransmission of segments:
1. sender receives 3 duplicate acknowledgements from other host - packet loss detected by the receiver
2. retransmission timer expires - timing out and resending unacknowledged segments - sender side
##### Three duplicate acknowledgements - sent by receiver
when a receiver does not get the expected  sequence number in a packet, it assumes the packet has been lost  
receiver adjusts it's ACK number to the expected (missing) SEQ number of the peer.  
when the sender get 3 packets with the same ACK number, a retransmission of the missing packet is triggered
(ex. if the receiver doesn't get the packet with SEQ=1, it will send 3 ACK=1 packets)

##### Retransmission timer expires - sender side
Every time data is sent, **the sender** starts the "Retransmission Time Out (RTO)" timer.
- if receiver sends ACK and the replies are received, the timer is stopped'
- if there are no ACK for the send data withing the RTO period and the time expires, the sender triggers a retransmission
(in TCP, RTO value is based on the Round Trip Time (RTT) value of the segments)

**Know the difference between fast retransmission and normal retransmission - ????

### Congestion Control
Congestion - overloading the network or the receiver
**Overloading the network** - too much data on the network medium
**Overloading a receiver** - number of data bytes is greater than the **advertised window**

**Congestion Window** - dynamically determined based on the **receiver TCP buffer advertised** and the **amount of traffic allowed on the network** (based on network congestion and packet loss)
- the window is always going to be lower of the two values.
TCP has 4 defined congestion control mechanisms - they determine the congestion window after packet loss occurs:
- **slow start / congestion avoidance**
- **fast retransmit / fast recovery**
#### Slow Start / Congestion Avoidance
- congestion window is not known when TCP host starts communication
- initial value of the window = 2x the sender's MSS setting
- if the receiver sends an ACK back, the window increases exponentially, and more data is sent
	- the process repeats for each ACK received based on the slow start algorithm until an error occurs (timeout, three duplicate ACKs detected) 
When a loss is indicated by a timeout:
- congestion window is set to 1 MSS
- window then grows exponentially (as in slow start) to threshold, then grows linearly
When a loss is indicated by 3 duplicate ACKs:
- congestion window is cut in half, then it grows linearly
**Slow Start** - exponential increate until receiver's window is reached, or receiver can no longer acknowledge
**Congestion Avoidance** - additive increase
- when congestion occurs, slow start threshold cuts in half, then:
	- linear increase
	- 1 MSS per RTT
	- normal operation
#### Fast Retransmit / Fast Recovery
**Fast Retransmit** - if out of order data is received (packet loss), receiver must send duplicate ACKs, ACKing the sequence number that was expected
- upon receipt of three duplicate ACKs, the TCP sender retransmits the lost packet
	- **at least** 4 identical ACKs (original ACK and 3 duplicates) are transmitted
- **no waiting for RTO**

**Fast Recovery**
- after fast transmit, the congestion window is cut in half and the congestion avoidance mechanism starts
	- linear increase of the window

**Congestion window (CWND)** value is not displayed in Wireshark.
- calculated according to the host's algorithm, increased for every ACK (not duplicate ACK), respectively decreased for Duplicate ACK and Time OUT
- CWND is between defined start value (depending on algorithm) and Receiver Window Size (RWND) as advertised by the receiver

---
**important parts:**
when do you see which flags
- syn you only see during the 3 way handshake
- ACK you see all the time
- FIN-ACK
know the sequence and acknowledgement process
error-detection and error-recovery process

know the 3 way handshake sequence numbers