The main function of an 802.11 WLAN is to provide a portal into a wired network.

- if this portal is not protected, unauthorized users could gain access which can lead up to many different wireless attacks.

  

**Wireless Attacks**

Rogue Wireless Devices

- potential open and unsecured portal into network infrastructure
- usually installed by employee who didn't realize what they did
- ad hoc wireless can also provide access

Peer-to-peer attacks

- 802.11 client stations can be configured as infrastructure mode or ad hoc mode (peer-to-peer)
- people hacking users that are associated to the same access point

  

Eavesdropping

- casual or malicious
- casual eavesdropping is finding open WLAN networks and discovering layer 2 information about the WLAN
    
    - this can be through passive scanning - where the client radio listens for AP beacons
    - or through active scanning - where the client radio transmits probe requests
- malicious eavesdropping is using protocol analyzers to capture wireless communications, this is typically considered illegal
- if there is no encryption, cleartext communications can be captured. layer 3-7 can be captured if WPA2 (or better) is not in place.
- unencrypted 802.11 frames can be reassembled at the upper layers (VoIP can be turned to a WAV file for example.)

  

Encryption Cracking

- WEP (wired equivalent privacy) is an old 802.11 encryption method that has been cracked for a while.
  
- WPA (Wi-Fi protected access) replaced WEP, still vulnerable today as it was based on WEP - introduced TKIP (temporary key integrity protocol) and MIC (message integrity check)
  
- WPA2 (Wi-Fi protected access 2) provides stronger data protection and network access control, replaced WPA in 2004. Introduction of AES (2 types): **WPA2 - Personal** - (implements PSK) - still weak and susceptible to dictionary attack & **WPA2 - Enterprise** (implements RADIUS) - based on 802.1x

  
  
  

- WPA3 (wi-fi protected access 3) latest wireless security protocol - adds new features for WPA3 Personal. Mandatory certification for Wi-Fi certified devices.
    
    - **WPA3 Personal** - enhances security through replacing the PSK with simultaneous authentication of equals (SAE). Key is generated with each authentication - 128 bit encryption plus forward secrecy (PFS) - prevents compromising session keys.
    - **WPA3 Enterprise** - requires a server certificate validation for confirming the identity of the server to which the device is connecting
      
    

  

Wireless Hijacking (evil twin attack)

- hacker makes a device that pretends to be an AP in a WLAN.
- AP uses the same SSID and users can connect to it.

  

Social Engineering Attacks

- talking to people and either getting their password from the things they say or from phishing or something

  

**Wireless intrusion monitoring**

  

Wireless Intrusion Prevention System (WIPS)

- software/hardware that is a central point of monitoring security and performance data collection
- sensors can use 802.11 radios to collect information in securing analyzing WLAN traffic
- most vendors have fully integrated WIPS capabilities

  

**Wireless Network Security Architecture**

at least 5 major components should be covered when securing a wireless 802.11 network:

- **Data privacy and integrity** - using strong encryption
- **AAA (authentication, authorization, accounting)**
    
    - authentication - verifying identity credentials #important
    - authorization - determines if they are allowed to have access to the resources
    - accounting - tracking the use of network resources by users and devices
- **traffic segmentation** - separating user traffic within a network #important
- **monitoring** - watching the network
- **policies** - making sure the users are following the rules and not doing things that are not allowed

  

**MDM** - mobile device management - system used for onboarding personal mobile devices or company-issued ones, also monitors and secures them- company mobile device - purchased by the company with the intent of enhancing employee performance - in-depth security and monitoring since they have corp info on them

personal device - your own device that requires a different method of management

  

Guest WLAN access - separate SSID used for guests so they don't have to go through your network and possibly have access to sensitive information

- firewall is important here - prevents them from getting near company network
- captive portals - making a guest sign in before having access to the internet
    
    - one of the most important things is telling them the appropriate use of the network
- client isolation is important so guest WLAN users can't do peer-to-peer attacks
- often have bandwidth reserved for employees

  

**Wireless Security Policies**

Remote-Access WLAN policy - used for when users take their devices off site

- should include the required use of IPsec or SSL VPN solutions & user authentication, strong encryption

  

Rogue AP Policy - no one should be able to install their own wireless devices on the corp network, or set up ad hoc / peer-to-peer networks

  

WLAN Proper Usage Policy - should outline the proper use and implementation of the main corp wireless network