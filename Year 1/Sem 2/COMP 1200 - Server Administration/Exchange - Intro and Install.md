MS Exchange - messaging and collaboration server, (also has calendar resources)

  

how email works:

- sender mail client (MUA) | gmail or outlook for example
- sender mail server (MTA) > looks for the recipients mail server (MTA)
- Recipient's Mail Server (MTA) does spam & virus checkers
- recipient mail client (MTU)

  

Mail User Agent (MUA) - user interacts

- how a user interacts with stuff, also known as a mailbox or email client

  

Mail Transfer Agent (MTA) - sends email out

- user writes and sends email to mail server using MUA
- software used by email server to forward the mail from the MUA

  

Mail Delivery Agent (MDA) - gets the email to the recipient

- if external to org, MTA sends the message via internet to destination mail server
- recipient mail server uses its MDA to deliver the email to recipient's mailbox
- then they access it through their MUA

  

**Mail Server DNS**

mail requires quite a few DNS records to function

need:

- MX record
- A Record
  

  

technically optional (do it anyways):

- PTR Record
- SPF Record

  

**MX (mail exchange) record**

- specifies a mail server that handles a domain's email
- used by mail servers to find other email servers on the internet

  

MX records have an additional attribute called preference/priority

- mail attempt to deliver to the lowest preference value first if they get a response for that server
- if you have round robin configured on DNS server, easy load balancing
  

  

**A (host) record**

- all servers and clients require at least a single A record
- these DNS records need to be externally published for other mail servers to determine your server (DMZ)
- Time to live (TTL) can be important especially during mail migrations/DNS changes

  

**PTR Record**

- basically checks to see if the email is actually coming from where it says its coming (this counters spoofed emails)

  

**SPF Records**

- special text record that proves domain ownership
- may be generated for you by a provider, or reference an external IP of your on-prem server
- you may be marked as spam and have your traffic rejected if this is missing
  

  

**Exchange on Prem Server Architecture**

- Exchange On-Prem will require that your AD Schema is modified - if your environment is not healthy, it will break your shit, dog.
- Data related to Exchange is stored in a special Database on the Server
- Multiple databases are supported and common. (locations, archiving, backups, executive, etc.)

  

on-prem servers have 2 roles:

- exchange will function with just a mailbox server, the edge roll increases security
- **mailbox server role** - handles all activity for the mailboxes and client access (hosts databases, etc)
- **Edge transport role** (optional) - deployed in the perimeter network, handles all internet-facing mail flow (applies anti-spam and anti-virus)

  

**Exchange online architectures**

- all in the background
- cant see anything easily
- magic :)
  

  

**Mail Access Protocols**

**POP3/POP3S - ports 110 and 995 (STAY AWAY AND SUCKS ASS DONT USE)**

- Post Office Protocol
- retrieves and REMOVES email from the server when the client accesses an email
- defunct (DO NOT USE) in favour of IMAP

  

**IMAP4/IMAP4S - port 143 and 993**

- Internet Message Access Protocol
- retrieves email from the server without removing it
- mailbox contents are synced between server and client - mailbox is persistent across devices :)

  

**HTTP/HTTPS - ports 80 and 443**

- used by browser for OWA (outlook, gmail, whatever website)

  

**Autodiscover service**

- allows quick exchange account setup without MUA entry/configuration
- leverages DNS to achieve this typically using CNAME and SRV records
- points to a server that contains all the default exchange configuration information for your mail client

  

**ActiveSync or Exchange ActiveSync (EAS)**

- used by mail clients (MUAs) to sync with exchange mailbox
- intended for high-latency/low bandwidth scenarios (roaming mobile devices)
- these days its autodiscover
  

**Availability service**

- allows clients to use calendar and meeting/booking scheduling

  
  

**Mail Transport Protocols**

**SMTP or ESMPT**

- Simple Mail Transfer Protocol (E = Extended)
- ESMTP is newer and is the mainly used one because it supports graphics, audio, video, and multiple languages
- port 25 or 587

**server to server, not client to server**

  

EAC (exchange admin center that is accessible via a webUI)

EMS (exchange management shell) - basically just powershell with extra shit for exchange

  

Exchange Online Setup

- running server in "the cloud"
- mail-flow is the same theory
- DNS is still required
- management is the same - Web GUI or shell
- requires active directory - can be on-prem or cloud
- with on-prem AD we make the sync process so data in the cloud and on-prem is the same

  

what we are doing:

- create a new tenant and sign up for a 60 day free M365 trial
- need credit card, can immediately cancel
- install the AD sync tool on the network and complete a sync
- assign licenses to users
  

  

**conclusion**

- exchange server is a huge application
- it is basically the only mail server than anyone ever uses (amazon uses this dog)
- will give you a good basic working knowledge of exchange
- complex but there is tons of info out there (GOOGLE!)
-