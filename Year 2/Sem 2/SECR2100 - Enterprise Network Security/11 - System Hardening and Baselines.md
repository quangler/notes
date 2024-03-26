**Hardening** - Securing and preparing a system for the production environment
**Baselining** - establishing a system's security state
- results in a baseline - has the typical usage for: RAM, CPU, disk, etc.
- the baseline can be used to predict needed upgrades
**Network Operating System (NOS)** - operating system that includes additional functions and capabilities to assist in connecting computers and devices

#### OS Hardening
- **Hotfix** - usually small software update designed to address a specific problem
- **Patch** - more formal, larger software update that may address several software problems
- **Service Pack** - large collection of patches and hotfixes rolled into a single large package
#### Application Updates
- apps require patches
- apps also need to be tested before being purchased - is it secure? are there firmware updates available? 
#### Antimalware
**Antivirus (AV)** products attempt to identify, neutralize, or remove malicious programs, macros, and files
- signature-based scanning catches known viruses - limited by known virus list
- **Heuristic Scanning** typically looks for commands that are not usually found in apps - like attempts to access a reserved memory register
#### Whitelisting vs Blacklisting
**Whitelisting** - a list of allowed applications on the machine
**Blacklisting** - a list of applications that are **not** allowed on the machine
#### Hardware Security
- can make hardware profiles that lock specific things (USB1, USB2, CD/ROM)
- cable locks
#### Firmware Version Control
- **Compatibility** - does the software work for you?
- **Legit** - is it from the company?
#### Hardware-based Encryption Devices
**Trusted Platform Module (TPM)** - hardware solution on the motherboard that assists with key gen/storage.
- use different channels than the typical software channels
**Hardware Security Module (HSM)** - device used to manage or store encryption keys
#### Handling Big Data
**Volume** - how much data
**Velocity** - how fast is it coming in and going out
**Versatility** - what types of data
#### IPv4 vs IPv6
- if you setup IPv4 and IPv6 but only make the firewall policies on one of them, you're better off doing just one type and not dualstack.