**PKI is based on trust.**
**PKI - Public Key Infrastructure** is all components that are necessary for different types of users and entities to be able to communicate securely and in a predictable manner.
- communication takes place using public key cryptography and symmetric keys for digital signature, data encryption, and integrity.
PKI environments have entities called **registration authorities (RAs)** and **certificate authorities (CAs)** - these entities provide services similar to a DMV
- in the sense that if you have a cert by a **CA**, and someone else trusts the **CA** they will trust **me**. (think like a drivers license and the police, he's never seen you but your drivers license is from a trusted place)
Without PKI infrastructure, man in the middle attacks with public keys can happen.

**third-party trust model**
- **RA** requires proof of identity from the person requesting a certificate and will validate the information
- **RA** advises the **CA** to generate a certificate
- **CA** digitally signs the certificate using its private key
- The use of the **CA**'s private key ensures that the certificate came from the **CA**

#### Certificate Authorities
a **Certificate Authority (CA)** is a trusted authority that certifies individuals' identities and creates electronic documents indicating that individuals are who they say they are.
- the electronic document is referred to as a **digital certificate** - it establishes an association between subject's identity and a public key.
- the private key that is paired with the public key that's in the certificate, is stored separately.
every CA should have a **certification practices statement (CPS)**
- how identities are verified
- steps **CA** follows to generate, maintain, and transmit certificates
- why the CA can be trusted to fulfill its responsibilities
certificate server is the actual service that issues certificates based on the data provided during the initial registration process

#### Registration Authorities
a **Registration Authority (RA)** is the PKI component that accepts a request for a certificate and then registers and authenticates the person requesting.
- authentication requirements are depending on the requested certificate type
- most **CA**s offer multiple classes of certs based on trust
#### Local Registration Authorities
a **local registration authority (RLA)** performs the same function as an RA, but: 
- but is closer to the end users and reduces WAN traffic.
- it is implemented in companies with their own internal PKIs and in companies with distributed sites
- performs identification, verification, registration functions; sends request, and user's public key, to a centralized CA so that the certificate can be generated.
- acts as an interface between the users and the CA
- LRAs simplify the RA/CA process for entities that desire certificates only for in-house use.
#### Digital Certificates
binds an individual's identity to a public key
- contains info on public key owner - for receiver to validate
#### Certificate Extensions
certificate extensions allow for further information to be inserted within the certificate
- more functionality to a PKI implementation
- standard certificate extensions are implemented for every PKI implementation
- can add nonrepudiation service via third party notary
- can add a time stamp authority (TSA) which gives a higher level of confidence for **when** specific messages were signed.
#### Certificate Attributes
four main certificate types:
- **End-entity certificates** - issued by a CA to a specific subject
- **CA certificates** - self-signed, in the case of a standalone or root CA (root CA is not domain joined), or issued by a superior CA within a hierarchical model.
- **Cross-certification certificates** - used when independent CAs establish a peer-to-peer trust relationship
- **Policy certificates** - used for high-security applications where you need to provide centrally controlled policy information to PKI clients
#### Certificate Lifecycles
- keys and certs should have lifecycles - should have to register a new certificate after a certain amount of time
- tradeoffs though:
	- shorter lifetimes limit the ability of attackers to crack them
	- longer lifetimes lower system overhead
- more-sophisticated PKI implementations use automated certificate refreshes
#### Registration and Generation
a key pair (public/private key) generated locally by an application can be stored on a local key store on the user's workstation.
- proof of possession - verifying that an individual has the corresponding private key
#### CSR - Certificate Signing Request
a **Certificate Signing Request (CSR)** is the actual request to a CA containing the public key and the info needed to generate a cert
the **CSR** contains all of the identifying info that is to be bound to the key by the cert generation process
#### Renewal
The cert itself has its own lifetime
- different from the key pair's lifetime
- specified by date inserted into cert
the renewal process is different than a registration phase
- RA assumes the individual has already successfully completed registration previously
- if the cert has not actually been revoked, the original keys can be used to provide the necessary authentication information and proof of identity for the renewal phase.
- the cert may or may not need to change during the renewal process
#### Suspension
you can have a cert get suspended, meaning it gets put on hold.
Reasons to suspend:
- extended vacation - ensure certificate will not be compromised or used during that time
- suspicion that a private key might have been compromised
#### Revocation
a certificate can be revoked when its validity needs to be ended before its actual expiration date is met
- lost private key
- data within certificate no longer applies
certificate revocation is permanent and final. can't be reinstated

**Certificate Revocation List (CRL)** - a list of serial numbers of certificates that have been revoked.
- the CRL has a statement that explains why the cert was revoked, and the date it was.
- list usually goes for the entire lifespan of the **CA**
- a CRL can be requested by individuals

Expired cert are not the same as revoked certs.

**Online Certificate Status Protocol** (OCSP)
- used for online revocation services
- request and response protocol that obtains the serial number of the cert being validated and reviews revocation lists for the client
- protocol has a responder service that reports the status of the certificate back to the client - revoked, valid, unknown status
- protocol and service saves the client from having to find, download, and process the right lists