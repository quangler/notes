802.11 - WiFi - **know this**

802.15 - Bluetooth - BLUETOOTH IS NOT WIFI

- predominately for peripherals

  

**wireless:** communication over wireless link

**mobility:** handling the mobile user who changes point of attachment to network

  

mobility benefits:

- access / availability
- coverage area
- increased flexibility
- cheaper

  

WiFi - Wireless LAN (WLAN)

  

1G: analog, voice only

2G: digital, voice and limited data (SMS only)

3G: digital overlay on 2G networks (adds mobile internet, video, mobile TV)

4G and 5G: faster speeds but less coverage

  

Collision avoidance vs Collision detection

  

802.11 Wireless LAN (WLAN)

- management frame and data frame - never collide

  
  
  

connection type

802.11 (WLAN) - Shared

802.3 (LAN) - Dedicated

  

wireless LAN components:

wireless client

- need a radio and antenna
- compatibilities vary according to:

battery

size, type & number of antennas

802.11 standard supported

  

  

wireless access point (AP)

- requires radio and antenna
- usually has a wired 802.3 port

(for connecting to network, and POE)

  

  

Autonomous AP = Thick AP = Standalone AP = (WAP)

- this means you need to manage the unit by connecting to the device (individually configured)
- super rare for being in a business
- multi-functional (can do DNS kinda)
  

  

Lightweight AP = Thin AP = Intelligent Antennas

-managed by a WLC

have a central configuration

  
  

wireless LAN controller

- software or hardware
- embedded or standalone
  

  

**Antennas**

- omnidirectional Wi-Fi antennas (this is used the most) at most like 150m
- Directional Wi-Fi Antennas (like satellite dish) can go km
- Yagi antennas (shortwave, looks like the old RV antenna) can go km
  

  

802.11a - single input, single output (SISO)

  

802.11n - multiple input, multiple output (MIMO)

- multiple streams (rx and tx)

  

Multi-User MIMO - the standard for today

- serves multiple devices at the same time

Single-User MIMO

- serves one device at a time

  

CAPWAP - management frames > absolutely needed with multiple standalone APs

  
  

WLAN topology

- doesnt matter where the AP is, its where its being used
- usually in distribution or edge tho

  

Ad Hoc Mode

- like airdrop
- you are connected device to device to transfer data

  

Tethering

- linking a device to another thing that has connection
- like an ipad to an iphone

  

**Infrastructure Mode** - it is the network

  
  

Service Set Identifier (SSID)

- name of network

  

Basic Service Set (BSS)

  

Basic Service Set Identifier

- AP MAC address
  

  

Extended Service Set (ESS)

- all BSS in a WLAN

  
  

Wireless Connectivity Process:

- beacon or probe for a network (DORA basically, probe, authenticate, associate)

  

Discovering AP

passive mode

- ap advertises its service by sending broadcast beacon frames containing the SSID
- beacon's primary purpose is to allow wireless clients to find networks

active mode

- clients must know the SSID
- client initiates the process by broadcasting a probe request frame on multiple channels

  

**authentication frame** - always send one of em

open - no password, still needs it

shared key - need a password (WEP - terrible (sucks), WPA2 - key stored internally (good))

SAE Handshake (WPA3 - key stored externally (great))

  

802.1x - adds authentication to port security (you use 802.1x _and_ port security)

  

802.11n - wifi 4

802.11ac - wifi 5

802.11ax - wifi 6

  

management frame - important #important

- a series of management frames checks the network (in a type field)
  

  

carrier sense multiple access with collision avoidance (CSMA/CA)

  

radio frequency spectrum -

- 902 - 928 MHz
- 2.4 - 2.4835 GHz
- 5GHz

  

**Security:**

  

Rogue AP - dangerous

- man in the middle attack
- allow a malicious intruder in, capture data, >make changes to it > send it back into the network

  

Packet Sniffing:

- you can get them easily
- if you know what you're looking for you can find some crazy shit

  
  

- things he didnt discuss until later

  

wifi security WPA2 BARE MINIMUM

think about 802.1x

  

hiding SSID doesnt do much

MAC filtering - think of it like port security (not sticky, but manually set - for things that will never be changed)

- not really that secure, because MAC address spoofing = im in
  

  

wireless technology is not controlled like ethernet

- its out there, just everywhere
- the cable acts like the sound proof bubble in get smart