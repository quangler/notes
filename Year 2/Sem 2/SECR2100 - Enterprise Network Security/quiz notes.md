how is a digital signature signed
how can you tell its a legit signature (process of the signature)


long answer:
- PKI - one advantage and one disadvantage of modifying default CRL time (one week) - provide examples
**ANSWER: 
advantage: lowering the default amount of time can increase security by ensuring that revoked certs are acknowledged more quickly than once every week (say once daily for example)
disadvantage: lowering the default amount of time can also increase the power needed for doing the checks - use more network bandwidth or cpu usage if you are checking hourly for example**

---
- Data-in-use DMA abbreviation (from presentation)
**ANSWER: direct memory access - was used in the kernel level anti-cheat presentation - a piece of hardware that goes between your hardware and software, it has direct access to your memory and allows you to connect to another device that is cheating so that "you" are not technically cheating, but another device is.
---
- regarding cryptography - what does ECC abbreviate? Describe it's functions, and identify one of its major competitors (from presentation)
**ANSWER: elliptic curve cryptography - makes a public and private key based on the math behind elliptical curves - calculates some value - this is your private key, then it finds another number on the curve that matches somehow - this is now your public key (they are different numbers). One of its major competitors is RSA, ECC is the favourite when it comes to resource-starved environments
---
- regarding PKI - what is CSR, give an example
**ANSWER: a CSR is a certificate signing request - its the actual request to a CA that has the public key and info needed to generate a certificate. the CSR contains all of the identifying info that is to be bound to the key by the cert generation process
---
- as it relates to a PKI (pki out-sourcing), briefly describe why it is important for an in-house system administrator (who is doing the request to the service provider PKI) to understand and follow up on all Certificate Practice Statement (CPS) process before signing off on a contract. Ensure to give two examples of what these processes are.
**ANSWER: a CPS outlines how identities are verified, how the CA will generate, maintain, and transmit certificates, as well as how the certs will be revoked if needed, and why the CA can be trusted to hold its end of the deal up and be trusted to secure the keys.

---
- big one:

since the file is to big to use RSA with, i will encrypt it using AES256 and then put the password in a text file and encrypt that text file with RSA. That way there are two separate cryptographic methods in place to ensure the data is safe. that also deals with the issue of safely carrying a key to the end user without it being compromised. The hash was also provided in that file so that the integrity could be checked before being opened (after being decrypted though).


- briefly describe the three types of PKI trust models and ensure to state their advantages and disadvantages:
**ANSWER:
hierarchical trust model: has a ROOT CA, INTERMEDIATE CA, LEAF CA, and END-ENTITIES (INVERTED TREE) | easy to follow path of trust, single points of failure
peer-to-peer trust model: a bunch of CAs have bidirectional trusts - each end-entity looks at its own CA, CAs are creating certs for EACHOTHER | no single point of failure, hard to scale up
hybrid trust model: two separate hierarchical trust models - connect through a peer-to-peer trust (using cross-certification) | allows integration of two separate sites, a hassle to re-setup if one site is compromised


---
- list 4 characteristics of a root ca
**ANSWER: 
1. the main certificate authority that assigns certificates.
2. can be domain joined (enterprise root CA) or not domain joined (standalone root CA)
3. they have self sign certificates for themselves
4. if there is a subordinate CA, the root can be taken offline to keep it secure
5. 
--- 









short answer/multiple choice
- the only means of social engineering is through direct contact between the target and the attacker
**ANSWER: FALSE**
---
- pki component that accepts a request for a digital certificate and performs the necessary steps of registering and authenticating the person requesting the certificate
**ANSWER: certificate authority???**
---
- why social engineering is successful
**ANSWER: people have a basic desire to be helpful**
---
- if the root CA's private key was compromised what would happen?
**ANSWER: subordinate CA's and end users/subjects would be affected**
---
- equation for operational model of security
**ANSWER: protection = prevention + (detection + response)**
---
- alice sends bob a message along with the MD5 hash of the message - bob runs the hash and finds it matches the one alice sent, this application of encryption is an example of: 
**ANSWER: integrity**
---
- what application of encryption verifies that a document was sent by the person it says it is from?
**ANSWER: digital signatures**
---
- into which category does information warfare fall into?
**ANSWER: highly structured**
---
- a digital certificate binds an individual's/subject's identity to a public key
**ANSWER: true**
---
- which term refers to an attack conducted against a site with software that is vulnerable to a specific exploit
**ANSWER: target of opportunity**
---
- a social engineer uses various deceptive practices to convince someone to give up info or do something they normally wouldn't do
**ANSWER: true**
---
- individuals that do not have technical expertise to develop scripts or discover new vulnerabilities in software - are able to download and run scripts that other people made
**ANSWER: script kiddies**
---
- elite hackers are responsible for the majority of computer system intrusive activities
**ANSWER: false**
---
- pki does not refer only to registration authorities and certificate authorities it also refers to certificates (containing keys) certificate revocation lists, and trust models
**ANSWER: true**
---
- trusted authority that certifies individuals identities and creates electronic documents indicating that individuals are who they claim to be
**ANSWER: Certificate Authority**
---
- why is vishing successful?
**ANSWER: people trust the telephone system**
---
- public key infrastructure
**ANSWER: provides all of the components needed for entities to communicate securely and predictably**
---
- what is the process of giving keys to a third party so that they can decrypt and read sensitive information?
**ANSWER: key escrow**
---
- which security principle states that access should be based on more than one item?
**ANSWER: separation of privilege**
---
- a very special type of encryption algorithm that takes an input and mathematically reduces it to a unique number which is not reversible
**ANSWER: hashing**
---
- the list of serial numbers of certificates that have been revoked is called the:
**ANSWER: CRL**
---
- an individual who loses a laptop that had a private key stored on it should request a revocation of the related certificate:
**ANSWER: TRUE**
---
- which security principle is described as always using simple solutions when available?
**ANSWER: economy of mechanism**
---
- what is one of the most fundamental principles in security?
**ANSWER: least privilege**
---




**X.509** WHAT