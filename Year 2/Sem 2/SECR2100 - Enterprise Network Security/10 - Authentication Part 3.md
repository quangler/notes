### IEEE 802.1x
802.1x is an authentication standard that supports port-based authentication services between a user and an authorization device, such as an edge router.
- used by all types of network
- describes methods used to authenticate a user prior to granting access to a network and authentication server (such as RADIUS)
- acts through an intermediate device, such as an edge switch, enabling ports to carry normal traffic if the connection is properly authenticated
until a client has successfully authenticated themselves - only Extensible authentication protocol over LAN (EAPOL) traffic is passed by switch
- EAPOL is an encapsulation method of passing EAP messages over 802.1 frames. EAP supports: one-time passwords, Kerberos, public keys, and security devices (like smart cards).
- Once a client successfully authenticates themself to the 802.1X device, switch port opens for normal traffic.
802.1x is commonly used on wireless access points as a port-based authentication service prior to admission the wireless network

### RADIUS
Remote Authentication Dial-In User Service (RADIUS) is a AAA protocol
- designed as a connectionless protocol
	- UDP employed as its transport layer protocol
	- connection issues handled by the RADIUS application
- A client/server protocol
	- client is typically a **network access server (NAS)** - we used cisco switches for this
	- server is a process or daemon
	- communications between a user and the RADIUS client are subject to compromise
Uses **UDP port 1812 for authentication and authorization,** and **UDP 1813 for accounting functions**

#### RADIUS Authentication
When server is given a username and password, it can support:
- Point-to-Point Protocol (PPP)
- Password Authentication Protocol (PAP)
- Challenge-Handshake Authentication Protocol (CHAP)
- UNIX Login
- and more!
depending on what was established when the server was set up.

A user login authentication consists of a query (Access-Request) from the RADIUS client, and a corresponding response (Access-Accept, Access-Challenge, or Access-Reject) from the RADIUS server

#### RADIUS Authorization
- the authentication and authorization steps are performed together in response to a single Access-Request message, although they are separate steps.
- once an identity has been established, either known or default, the authorization process determines what parameters are returned to the client.
	- typical parameters include:
		- service type allowed
		- protocols allowed
		- IP address to assign to the user
		- access list to apply or static route to place in the NAS routing table

#### RADIUS Walkthrough:
- user initiates PPP connection to NAS (cisco switch)
- NAS prompts user for either:
	- username and password (PAP)
	- challenge (CHAP)
- user replies to NAS with credentials
- RADIUS Client sends username and encrypted password to RADIUS server (in the form of an Access-Request)
- RADIUS server responds with either:
	- Access-Accept
	- Access-Reject
	- Access-Challenge - this initiates a challenge/response handshake - if client can't support it, considers it an Access-Reject
- RADIUS Client acts upon authentication, authorization, and accounting rules, allowing access to remote resources.
