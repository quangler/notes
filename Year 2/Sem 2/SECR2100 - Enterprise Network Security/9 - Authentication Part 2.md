### Remote Access Process
Three steps to establish proper privileges are:
- Authentication, Authorization, and Accounting (referred to as **AAA**)
	- **Authentication** - matching user-supplied credentials to previously stored credentials on a host machine, and it usually involves an account username and password
	- **Authorization** - granting of specific permissions based on privileges held by an account
	- **Accounting** - collection of billing and other detail records
Once the user is **Authenticated**, **Authorization** takes place.
- Remote authentication usually takes the common form of an end user submitting their credentials via an established protocol to a **remote access server (RAS)** which acts upon those credentials, either granting or denying access
### Identification
The process of ascribing a computer ID to a specific user, computer, network device, or computer process (user ID must be unique)
- identification process is typically performed **once** - when a user ID is issued to a particular user
- user identification enables authentication and authorization to form the basis for accountability
- for accountability purposes, user IDs should not be shared, and for security purposes, they should not be descriptive of job function.
### Authentication
**put simply: verifying a user is who they say they are.**
The process of binding a specific ID to a specific computer connection
- two items need to be presented to cause this binding to occur - the user ID, and some "secret" to prove that the user is the valid possessor of the credentials
Categories of secrets:
- what users know (password)
- what users have (device)
- what users are (username??)
- what users do (??)
Password is the most common authentication method
- element from a separate group can be added for greater security, such as a smart card token - something a user has in their possession
- the use of something that only valid users should have in their possession
- something that is unique about you
#### **Basic authentication** 
The simplest technique used to manage access control across HTTP
- passes information encoded in base64 using standard HTTP headers
- plaintext method without any pretense of security
#### Digest authentication
Used to negotiate credentials across the web
- digest authentication uses hash functions and a nonce to improve security over basic authentication - (nonce is an arbitrary number that may only be used once - typically pseudo-random number to ensure communications cannot be reused in replay attacks)
- digest authentication improves security over basic authentication - still does not provide any significant level of security
	- passwords are not sent in cleartext
	- digest authentication is subject to MiTM attacks, and potentially replay attacks
#### Authentication Process:
1. Client requests login
2. server responds with a challenge and provides a nonce
3. client hashes the password and nonce
4. the client returns the hashed password to the server
5. the server requests the password hash from a password store
6. the server hashes the password and nonce
7. if both hashes match, login is granted
### Kerberos Authentication
Kerberos Server contains user IDs and hashed password for all users that will have authorizations to realm services, also has shared secret keys with every server to which it will grant access tickets.

**Kerberos** is a network authentication protocol designed for a client/server environment.
- built around the idea of a **Key Distribution Center (KDC)** which consists of two logically separate parts:
	- **an Authentication Server (AS)**
	- **Ticket-granting server (TGS)**
Kerberos communicates via "tickets" that serve to prove the identity of users
The basis for authentication in a Kerberos environment is the ticket
Tickets are used in a two-step process with the client
#### How Kerberos works:
tickets are used in a two-step process with the client
- a client requests a ticket - ticket-granting ticket (TGT) issued by Authentication Server (AS), AS gives ticket to client
- client can then present this ticket to the Kerberos server with a request for access to a specific server. The client-to-server ticket (service ticket) is used to gain access to a server's service in the realm
#### NTLM vs Kerberos
NTLM is proprietary AuthN protocol invented by Microsoft whereas Kerberos is a standard protocol.
**NTLM uses a three-way handshake between the client and server.**
**Kerberos uses a two-way handshake using a ticket granting service (key distribution center)**

In Kerberos - the client must have access to a domain controller (which issues the tickets), whereas in NTLM the client contacts the server which contacts the domain controller
**Faster Authentication** - Kerberos is faster because the resource server has enough information to authenticate the client
**Mutual Authentication** - in Kerberos - clients authenticate to the service, but the service also authenticates to the clients.
NTLM does NOT support mutual authentication - it only provides client authentication.

### Authentication
**Certificates** - a method of establishing authenticity of a specific objects such as an individual's public key or downloaded software
**Digital Certificate** - a digital file that is sent as an attachment to a message and is used to verify that the message did indeed come from the entity it claims to have come from
**Multifactor Authentication** - term that describes the use of more than one authentication mechanism at a time
- something you have and something you know mechanisms are used as factors in verifying authenticity of the user
**Mutual Authentication** - each side of an electronic communication verifies the authenticity of the other
- provides a mechanism for each side of a client/server relationship to verify the authenticity of the other to address this issue
- a common method of performing mutual authentication involves using a secure connection, such as Transport Layer Security (TLS), to the server and a one time password generator that then authenticates the client.
### Authorization
Process of permitting or denying access to a specific resource
- once identity is confirmed via authentication, specific actions can be authorized or denied.
Purpose is to determine whether a given user who has been identified has permissions for a particular object or resource being requested
- functionality is frequently part of the OS and is transparent to users
- separation of tasks has several advantages - hardware / software components can use their own authorization once authentication has happened (separate authentication and authorization)