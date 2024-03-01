**FTP** uses **TCP** for connection
- establishes the connection
- tracks the order of packets
- defines and adjusts the data transfer window
TFTP uses UDP for connection

- 2 communication channels:
	- **command channel** - TCP port 21
	- **data channel (data transfer)** - uses dynamic port numbers (FTP specification defines port 20 for data transfer - but actually dynamic ports are used)
- sometimes there are a single **command channel** and **multiple data channels** (using multiple dynamic ports)

### **FTP Active Mode**
- client connects from random TCP port above 1023 to FTP server's command port (port 21).
- **FTP server establishes the data channel**

### **FTP Passive Mode**
- **Client initiates connections for both channels, the command and the data**
- done as workaround to some firewalls blocking unauthorized connection requests from external parties
- client requests the server (on command channel) to start listening on a port (server chooses) rather than trying to establish a connection back to the client
- some FTP servers don't support this 
	- if not supported, responds to SYN with TCP RST.
	- if server is configured for different port than client, FTP connection cannot be established properly
	- if firewall blocks passive mode, passive mode fails and the server does not respond to the attempted connections

### Commands / Wireshark
some of the commands that are sent by the user over the command channel get interpreted by something else by the server:
- ex. PUT turns into STOR, and GET turns into RETR
- Wireshark FTP traffic filters:
	- `ftp || ftp-data` - only displays FTP traffic
	- `ftp.request.command == "USER"` - display FTP USER packets
	- `ftp.request.command == "USER" && ftp.request.arg == "FRED"`
	- `ftp.response.code == <#>`
	- `ftp.request.command == "PASV"`

the **PORT** command sets up an active mode FTP connection (FTP server establishes the data channel)
the **PASV** command sets up a passive mode FTP connection (client initiates connections for both channels)

### Connection Start
Starts with the TCP 3 way handshake on port 21 as destination (SYN, SYN-ACK, ACK) - this is the command channel (stream 0)
- then a PORT or PASV command is sent to see what connection type is going to be made (PORT= ACTIVE, PASV = PASSIVE)

### Reassembling FTP Traffic
- right click a packet > follow TCP Stream > Define format as Raw > save as (look at original name file and extension determined from the info column)