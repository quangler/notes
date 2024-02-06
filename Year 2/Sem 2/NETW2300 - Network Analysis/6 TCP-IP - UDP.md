- The only connectionless protocol at the Transport Layer.
- used by apps that contain their own connection-oriented parameters and retry counters (in application layer)
## Characteristics and Limitations of UDP:
**No reliability mechanisms for guaranteed delivery** - datagrams are not sequenced and acknowledged
**No connection handling** - each datagram is an independent message transmitted - no processes of establishing, maintaining or closing a connection
**Optional checksums** - for each datagram, UDP might calculate a checksum value and put it in the header; up to application to use it or not, UDP does not require receiver to verify.
**No buffering services** - it relies on the application for this role - UDP sees one datagram at a time
**No segmentation** - does not break up large data in segments and label them for reassembly at the other end - up to application to handle it
only handles checksum and **identification of the higher layer protocol (port numbers)**

## UDP **header**
- short and simple - **only 8 bytes**
- defines the process or application that is using the IP and UDP Network and Transport layers
**Source Port** number field
- defines the application or process that sends the packet using the UDP header
**Destination Port** number field
- defines destination application or process that uses the IP and UDP headers
**Length** field
- defines the length of the packet from the UDP header to the end of valid data
**Checksum** - optional. (in IPv6 it is required)


delta time - calculates time from previous packet (in the actual capture)
delta time displayed - previous packet in the current Wireshark filter
