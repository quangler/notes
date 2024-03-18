Server Admins and Network Admins have their sections cut out for them, the missing section is usually Transport Layer.
- both sides blame each other!
Troubleshooting should be based on *collaboration*.

1. Define the problem - is it an app? is it browser?
2. collect system, application, and path information - where are the disconnects? go as close to the source as possible
3. capture and analyze packets and flows - find the issue!
4. consider other tools - web apps? try fiddler | TCP dump so you don't use a ton of resources with WireShark

### Step 1 - Define the Problem
- figure out what the "the network is slow" means
	- what is the expected result, what is happening instead?
	- is anyone else having this happen?
### Step 2 - Collect System, Application, and Path information
- system
- network
- infrastructure
- applications
- OS
Try to talk to the person having the issue
### Step 3 - Capture and Analyze packets and flow
**Capture Location**
- capture as close as possible to host having issues - see the traffic from that host's perspective
- use a tap rather than a switch port - switch might be the issue, or might be oversubscribed
- maybe use something that requires less resources - TCPDUMP
- Examine RTT to the target - round trip time crazy high?
- check TCP handshake connection establishment process if its TCP traffic
Focus on the traffic related to the complained issue - use filters in Wireshark
Use profiles with specific filters to detect common issues - DNS errors - HTTP errors
Check "Expert Info" errors / warnings
use a troubleshooting checklist - check Moodle
### Step 4 - Consider other tools
- try CLI tools like tshark or tcpdump
- large files with Wireshark don't work well
- other tools: 
	- Fiddler - web debugging
	- WLANPi - WIFI

**EXAMPLES IN: NETW2300-Troubleshooting with Wireshark**
TCP issue - check if it's established first
- then check the TCP commands - `tcp.time_delta`
	- how long do they take to get to the server?
	- how long time does it take to respond?
