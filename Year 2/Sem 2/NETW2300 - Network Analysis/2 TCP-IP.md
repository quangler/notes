#### What is TCP/IP?
A large collection of networking protocols and services that supports network communication.
**Network Protocol** - a system of rules on which the network communication process is based on
- defines how data should look, and what information it should contain so the host can correctly interpret the message
- defines how data should be processed, transmitted, and received on a TCP/IP network
##### Two Key Protocols:
**Transmission Control Protocol (TCP)** - reliable deliveries of messages
**Internet Protocol (IP)** - manages the routing of network transmissions
###### Bonus!:
**UDP** - part of TCP/IP suite, critical for applications that are time sensitive (VoIP)

#### Standards and Groups that oversee TCP/IP
**Internet Society (ISOC)** - makes sure the internet stays open
**Internet Architecture Board (IAB)** - oversees IETF and IRTF. Oversee technical evolution of the internet
**Internet Engineering Task Force (IETF)** - tries to make the internet work better by providing high quality, relevant technical documents.
**Internet Research Task Force (IETF)** - long time research of internet
**Internet Corporation for Assigned Names and Numbers (ICANN)** - the owners of registered domain names, looking over IP address distribution

#### TCP/IP Standards and RFCs
**Request for Comments (RFCs)** - the professional documentation, this is the standard.

#### OSI Reference Model Overview
- seven-layer model
- designed to replace the TCP/IP model
- standard way to explain how networks operate
##### Breaking Network into Layers:
- lets you break things down and solve issues individually.
- been part of TCP/IP since early design
Layers:
- exist to encapsulate or isolate specific types of functionality
- provide services to the layer above, deliver or accept data from layer below.
**Protocol Data Units (PDUs)** - include "envelope information" in the form of specific headers and trailers.

##### Physical Layer - 1
- how are things connected together
- what is the medium that we are using (ethernet, fibre)
##### Data Link Layer - 2
- connection from physical to network layer (SWITCH LAYER)
- holds the MAC address
##### Network Layer - 3
- IP addresses and routing (ROUTER LAYER)
- packets
##### Transport Layer - 4
- has TCP/UDP protocols,
- contains ports
- segmentation - cutting up a big messages into a numbered sequence of chunks, usually at the sender side

##### Session Layer - 5
- mechanisms that:
	- permit senders or receivers to request that a conversation start or stop
	- keep a conversation going even when traffic may not be flowing (keep alive)
	checkpoints: what data has been confirmed sent

##### **Presentation Layer - 6**
- what file type are we sending?
- local files and remote files
- translates between network and applications

##### Application Layer - 7
- this is where applications live
- most things

#### TCP/IP Model
##### Network Access Layer
- collection of services and specifications - provide and manage access to network hardware
- combine layer 1 and 2 of OSI model
##### Internet Layer
- handle routing, logical addressing, and MTU fragmentation
##### Transport Layer
- handles TCP / UDP
##### Application Layer
- aka process layer
- network applications and services that communicate with lower layers through TCP / UDP port numbers

#### TCP/IP Protocols, Service, Sockets and Ports
- Source Port Numbers - identifies the process that sent the data
- Destination Port Number - identifies the process that receives the data
well known ports - below 1024
registered ports - 1024 - 49151
dynamic ports - 49152 - 65535
- TCP/IP sockets - combination of a particular **IP address** and a **dynamically** assigned port address
	- ensures that a system can maintain multiple open connections and assign each connection its own unique dynamically allocated port number