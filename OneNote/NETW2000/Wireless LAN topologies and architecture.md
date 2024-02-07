wireless topology - the physical and logical layout of wireless hardware

  

**4 major wireless topologies:**

- wireless wide area network (WWAN)

ex. EDUROAM - uses RADIUS

  

- wireless metropolitan area network (WMAN)

ex. New York City / Edmonton Rec Centers

  

- wireless personal area network (WPAN)

ex. Bluetooth, peer-to-peer (ad hoc)

  

- wireless local area network (WLAN)

ex. home Wi-Fi

  

components of WLAN:

main component is **radio**, or the **station service (STA)**

- **client station** - non-AP station (tablet, phone, laptop, etc.)
- when a client station establishes a layer two connection with an AP, they are **associated**

  

- **access point station** - radio that functions as the wireless portal from which other client stations can communicate
- the AP manages client associations - maintains an **association table** of connected WLAN clients and **directs traffic**

  

AP acts as a bridge from wireless to wired, or wireless to wireless

  

- all devices that are associated with an 802.11 WLAN are part of a **service set**
- **service set identifier (SSID)** is a logical name used to identify a wireless network
- 32 characters, is case sensitive

  

802.11-2016 standard defines 4 topologies (SERVICE SETS)

- basic service set (BSS) - 1 WLAN - 1 unique SSID and 1 unique BSSID

a group of wireless devices served by a single AP

**- basic service set identifier (BSSID)** - media access control (MAC) address of AP | BSSIDs are incremental off the original MAC address of the AP's radio

- **basic service area (BSA)** - physical area of coverage provided by an AP in a BSS

  

- extended service set (ESS)

group of two or more identically configured BSS networks, connected via common distribution system

typically multiple APs and their associated clients

**extended service area** is coverage area of the ESS in which all clients can communicate and roam

  

- independent basic service set (IBSS)

a group of two or more clients that communicate without an AP ( ad hoc or peer-to-peer )

when no connection to internet or external network is needed

**for IBSS to work** all stations must be transmitting on the same frequency channel, share the same SSID

  

- mesh basic service set (MBSS)

mesh topology where wired network access is not possible

used to provide wireless distribution of network traffic between a set of APs (bridging traffic)

**mesh APs usually have multiple radios** - one for traffic of network, the other to maintain BSS for wireless clients

one or more APs are connected to a wired infrastructure **- mesh portals (gateways)**

APs not connected to the upstream wired infrastructure are called **mesh points**

  
  

**WLAN Architecture:**

  

Autonomous WLAN Architecture

- most common with a "standalone" AP | AKA **autonomous access points or fat access points**
- all configs are in the AP itself
- at **least** two physical interfaces, PLUS one for management
- RF radio, ethernet port, BVI (bridge between the two, for management)
- typically POE and deployed at access layer

  

Centralized WLAN Architecture

- requires **wireless controller** - this allows you to manage and configure APs | AKA **lightweight APs or thin APs**
- lightweight APs do not contain the management and configuration functions
- WLC can be centrally configured, settings auto distributed to all APs | can be placed at the core, distribution, or access layer

  

- wireless controller features:
- AP Management
- WLAN Management
- User Management
- Device Monitoring
- VLANs
- Layer 2 security support
- Captive portal - have to sign in on a website before data can flow

  

**Controller Data-Forwarding Models:**

- centralized data forwarding

where all data is forwarded from AP to the WLAN controller for processing.

usually used, especially when WLAN controller manages encryption / QOS

  

- distributed data forwarding

where AP performs data forwarding locally

maybe used where it is better to perform forwarding at the edge, rather than the central server