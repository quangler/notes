form follows function

  

function - does it work

form - best practices / design

  

**Network Design Goals:**

  

1. Function - it must work!
2. High Availability
3. Scale - it must able to grow and adapt
4. Manageability
5. Security

  

Make a diagram first (it is good)

  

When you can, focus on standards (sometimes you cant use the standard)

  

DOCUMENT - you're a fool if you don't

(you must troubleshoot, aka doomed)

  

**Network Architecture Characteristics:**

  

1. High Availability
    
    1. fault tolerance - multiple switches, EtherChannel
    2. redundancy -
2. Scalability
3. Manageability
4. Security

  

**Network Security principles:**

  

Integrity - things that are how they are supposed to be

Confidentiality - only who needs to know, knows.

Availability - it hasn't been hacked/stolen

  

Identification - user claiming to be someone

Authentication - validates who the user is

Authorization - permissions allocated to user

Accountability - logging behaviours of a single individual

  

**Best practices:**

Policy - WRITTEN IN STONE - overall thing that makes the company work

- formal statements made and supported by senior management
- think like academic integrity, code of ethics and conduct, or security policies
- NAIT slide template

Standards - required protocols

- mandatory actions/rules that support policies
- think like employment standards

Procedures - following policy WRITTEN IN STONE

- step by step guide, how to do something

Guidelines - examples for procedure, WHAT YOU SHOULD DO (not specifically have to do)

- recommendation, not what you HAVE to do, but what you should do

  

- IETF makes RFCs (request for comments)

  

**What makes a standard:**

1. voluntary
2. collective work & arrived at by consensus
3. approved by a recognized body

  

**de jure** (by law) - recognized and official standard

**de facto** - no formal recognition, but accepted and adopted by the market

  

**Why standards are required:**

- proprietary hard/software would never be able to interact with each other
- standards allow them to interact and interface with each other

  

**Layered:**

- allows for modification to a single layer without fucking up everything else (this was hugely important)

  

Telecommunications - tele > far off, communicare > to share

  

International Standards Bodies

- ISO (international organization for standardization) - means equal
- IEC (international electrotechnical commission)
- ITU (international telephony union)

  

- IETF (internet engineering task force) - only USA I think?
- EIA (electronic industries alliance)
- TIA (telecommunications industries association)
- IEEE (institute of electrical and electronics engineers)

  

**Three-tier model / Three Layer Design model:** the building block of large enterprise or campus networks, enterprise comprised of multiple of these blocks

  

ACCESS - provides access to network for users / end-devices

DISTRIBUTION - provides policy-based routing for access to and through the core

CORE - provides connectivity between blocks, to the internal (private) and external (public) Data Center and also internet

  

Two-Tier Model / Top-of-Rack (ToR):

  

Version 1:

Collapsed Distribution / Access

CORE

  

Version 2:

Access

Collapsed Core / Distribution

  

Collapsed - meaning they are in the same spot as whatever they are collapsed into