## Key Destruction
Key pairs and certs have a set lifetime
- they will expire at a set time
- important that keys and certs are properly destroyed when that happens
- have to make sure that no one can get access to a key after the lifetime has ended and use it for malicious purposes.

## Certificate Repositories
- a CR describes a centralized directory that can be accessed by a subset of individuals
	- usually LDAP compliant
- a CR is a holding place for people's certs and public keys that are in a particular PKI environment

## Centralized vs Decentralized infrastructures
### Decentralized
software on the user's computer generates and stores the crypto keys local to the system itself
advantages:
- have the key on the local device, not in the same space as all the other keys (like in centralized)
disadvantages:
- user's computers could be lacking the power to process larger keys in a timely manner
### Centralized
advantages: 
- easier to back up the keys and implement key recovery procedures
disadvantages:
- need to send keys in an encrypted manner, otherwise the key could be compromised on the way to the intended user
- fault tolerance or redundancy is needed for server that stores keys
- for *true* authenticity and nonrepudiation, digital signature key pairs shouldn't be generated at a centralized server
## Private Key Protection
Private key needs to stay private
- key store is a storage area for the private key
	- key store is usually created by the application registering for a certificate
	- many applications don't require strong password to protect the key store :/
- if digital signatures are used for legal purposes, auditing may happen to ensure authenticity and nonrepudiation are provided

## Public Certificate Authorities
Public CAs are already established and being used by many other individuals and companies
- specialize in verifying individual identities and creating and maintaining their certs
- issue certs that are not bound to a specific company / department
advantages:
- well known and easily accessible to many people (good thing)
- hosted by professionals who do this as their job
disadvantages:
- if someone else has the Root CA, they have your private key which some people don't like
## In-House Certificate Authorities
in-house CA is implemented, maintained, and controlled by the company that implemented it
- can be used for certs for internal employees, devices, applications, etc.
- this approach gives the company complete control - who can use the certs, who has access to the CA, what classification of the cert, etc.

can also do a hybrid public / in-house
- request a cert from a public CA, then use that to generate more certs for in-house purposes.
- if the big cert gets compromised, just ask for another one and regenerate the in-house ones.
## Outsourced CA
CA, RA, CRL are the things that are outsourced

## Trust Models
if you need a peer-to-peer connection with 2 separate CAs,
- one (or both) CA issues a cert for the other CA's public key
- each CA validates the other CA's info and generates a cert containing public key for that CA to use.
	- this creates the trust path - either both trust each other (bidirectional) or only one trusts the other (unidirectional)
## Stolen Certs
- specifically crafted malware designed to steal both private keys and digital certs from machines
	- zeus bot
	- stuxnet attack - used on Iranian nuclear production facility
	- Sony Pictures Entertainment attack happened, malware using Sony certs appeared.