**VoIP basic operation**

DHCP server

- assigns network config to a phone

  

TFTP server

- phones contact TFTP server (usually running on call server) for configuration download

  

Call server

- phones then register with the call server, which makes the server aware of the phone and the phone's MAC and IP address tied to that phone number

  

**Call setup and connection**

- once phones are registered, call sessions can be initiated
- the calling end point signals the call server indicating the number dialed - phone 1 dials phone 2 and the call server sees this
- call server contacts destination and routes call to it if available
- RTP protocol is used to transmit voice data

**Call termination**

- signalling protocols come back into the connection and provide messages to the calling parties regarding tearing down the session
  

  

**VOIP Protocols**

- Signaling Protocols: **SIP, SCCP, H.323**
- Transport Protocols: **RTP**

  

**SCCP - Skinny Client Control Protocol** (CISCO PROPRIETARY)

- lightweight cisco proprietary signaling protocol for VOIP devices
- used for phones' registration, call messages, and controlling phone display
- TCP port 2000
- messages are easy to read on Wireshark

basic header format:

- data length - tells you amount of info carried in the packet
- header version - tells you the version of the skinny header
- message id - provides hex value for type of SCCP packet

registration process:

- post boot and once it has network config and TFTP, it communicates with call manager via UNICAST
- **Message ID: RegisterRq**
- **DeviceName**: includes mac address of phone
- call server responds with
- **RegisterACKMessage**
- and a **KeepAliveInterval value**
- they then exchange info regarding interface setup and features
- do this through **Capability** and **Template** messages

calling process:

- picking up the handset is called "going off-hook"
- phone informs server it is off-hook
- server sends a call-state message acknowledging the off-hook state
- server sends **StartTone** message

  

- dialing a number
- generates dial tone, destination number can be dialed
- server routes the call to destination and sends a message to the source that is time to ring

  

tearing down the call:

- begins with **OnHook** message
- followed by **CloseRecieveChannel**
- then **StopMediaTransmission** messages

  

**RTP - Real-Time Transport Protocol**

- used for voice packets containing voice data
- also has Real-Time Control Protocol (RTCP)

  
  
  
  
  

**SIP - Session Initiation Protocol**

- generic standard from IETF
- operates at **application layer**

  

**SIP Registration:**

- boot up and contact **DHCP** for networking
- contact **TFTP** for profile configs
- register with **call server/registrar**

  

**SIP Components:**

- **user agent client (UAC) -** the SIP phone, initiates requests or responds to SIP transactions
- **User Agent Server (UAS)/Registrar** **-** accepts requests and sends back responses - accepts REGISTER messages and updates location
- **URI (uniform resource identifier)** **-** part of SIP addressing - IP or username

  

sip:<user>@domain:port

sip:<user>@host:port

sip:<phone number>@domain

sip:<phone number> @ host

  

SIP is designed to setup and teardown calls

- also includes user availability, session handling info, but it relies on another protocol called **SDP (session descriptor protocol)** for negotiating parameters of the multimedia connection

  

SIP messages and message structure

**start lines:**

- SIP URI (uniform resource identifier)
- VERSION
- METHOD (REGISTER, ACK)

  

**message headers:**

- contain mandatory fields and rules

  

**Requests:**

- **VIA :** tells nodes involved where to send SIP packet, rules
- **FROM :** identity of the initiator in URI format
- **TO :** specifies the recipient of the request in URI format
- **CALL-ID :** value that groups all of the messages from a dialog together
- **CSEQ** **:** helps you find out what number of packet that is in a transaction

  

**Responses:** ??? are these request or responses #important

- **1xx Provisional :** request received, processing
- **2xx Success :** request successfully received, understood and accepted
- **3xx Redirection :** further action needs to be taken for completing the request - forwarding a call
- **4xx Client Error :** request contains bad syntax, or cannot be fulfilled by server - probably a mistyped number
- **5xx Server Error :** the server failed to fulfill a valid request - server might be down
- **6xx Global Failure :** the request cannot be fulfilled at any server - system is down

  

**SDP - Session Description Protocol** - provides purpose of the session and describes the media content to be transferred

includes:

- Version
- Originator (owner)
- Session ID
- Session Name
- Connection Information
- Media Type
- Media Port
  

  

**SIP Trunks**

- replace the need for physical lines and allow for easier management of phone services
- backbone of users phone lines connected to a telephony network
- allows connecting a VoIP PBX system to a PSTN network or connecting two different VoIP systems
  

  

signaling protocols: SIP, SCCP

transport protocols: RTP