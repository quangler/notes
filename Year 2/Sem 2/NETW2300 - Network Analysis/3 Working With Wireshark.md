#### Why Wireshark?
**Analyzing general traffic** - what ports, what applications, who is talking - how much bandwidth an app is taking
**Troubleshooting** - can tell you where the problem starts
**Security** - filter on conversation of interest
**Time Analysis** - determine round-trip path latency

#### Display Filter Fields
| eq | == | equals (ip.src == 10.100.200.41) |
| ---- | ---- | ---- |
| ne | != | not equal (ip.src != 10.100.200.41) |
| gt | > | greater than ( frame.len > 10) |
| lt | < | less than (frame.len < 128) |
| ge | >= | greater than or equal to (frame.len ge 0x100) |
| le | <= | less than or equal to (frame.len <= 0x20) |
| and | && | logical AND (`<expression1> && <expression2>`) |
| or | \|\| | logical OR (`<expression1> \|\| <expression2>`) |
| xor | ^^ | logical XOR (`<expression1> ^^ <expression2>`) |
| not | ! | NOT (`!<expression>`) |
if you don't know the filter:
- analyze > display filter expression
to save filters:
- analyze > display filters > + icon > put filter in
find bar:
- edit > find packet
flow graph: shows the packet exchanges in a graph
- statistics > flow graph
fixing checksum errors:
- edit > preferences > IPv4 > uncheck validate the IPv4 checksum if possible
