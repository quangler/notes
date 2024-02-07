use vCSA to install vCenter - through a VM, doesnt need to run on top of windows server

- runs on photon os (linux fork)
- supports external oracle database
- supports AD integrated authentication

  

max of 2000 hosts per vCenter server

make sure DNS is setup and working, and there is an A record and pointer record for your ESXi server #important

  

login - [https://(ip-address)](https://(ip-address)) or FQDN/

  

ESXi host license and vCenter server licenses are different, in PROJ 1000 ask for a vCenter server license (ESXi already licensed)

  

NTP - important to have everything synced up for PROJ, not super important in this class #important

  

folders can be made with different permissions like in windows on vCenter server

  

- add ESXi hosts under a data center, folder, or a cluster

  

demo start:

  

ESXi - setup a DC (in a vm)

- ctrl alt del > actions, ctrl alt del
- setup ad ds and DNS
    
    - make a new reverse lookup zone
    - make a new DNS A record - "vcsa"
    - install chrome/firefox on DC (cant use browser on host pc)

make sure hostname and IPs are right for ESXi

  

on sharepoint: course materials ISOs vcenter_7 (download the OVA)

  

ESXi2 :

- new VM "vcsa"
- upload OVA from sharepoint
- deployment options - use VM Network to install vCenter
    
    - TINY vCENTER
    - thin provisioning
    - power on automatically : uncheck
      
    

  

important dont skip

- additional settings:
- host network IP address family - "ipv4"
- host network mode - "static"
- host network ip address - "192.168.91.50"
- host network prefix - "24"
- host network default gateway - "192.168.91.2"
- host network dns server - "192.168.91.10"
- host network identity - " vcsa.comp1300.local"

  

- sso (single sign on) config:
- "P@ssw0rd"

  

- system config:
- "P@ssw0rd"
  
- misc:
- CEIP enabled - make sure its unchecked
  
- networking properties:
- domain name - comp1300.local
- domain search path - comp1300.local

  
  
  

warning, then finish > patience

MINIMUM RAM IS GOING TO BE 12GB, DO NOT REDUCE

  

power on: patience (bless up) let it sit for like 20 mins please god

  

go to website on DC > "[https://vcsa.comp1300.local:5480](https://vcsa.comp1300.local:5480)" (IP NOT WORK, MAKE DNS GOOD!!!!!!!!!!!!!)

- setup
- root , P@ssw0rd
- make sure the settings are the same as we set before > save
- SSO config - this makes a single sign on domain for vCenter
- single sign-on domain name - "vsphere.local"
- password - "P@ssw0rd"
- only 1 vcenter server
- UNCHECK join vmware thing
- finish

it will then load, if it is taking a long time on a percentage, refresh the browser

now suffer :)

it will load !

  

vcenter server is gonna look different now !!!

"[https://vcsa.comp1300.local:5480](https://vcsa.comp1300.local:5480)" is now vCenter management (ip address works now)

administrator@vsphere.local

P@ssw0rd

  

for PROJ 1000 - we need vSphere 6.5 (cant use 7 :( ! ) #important

  

Adding Host:

right click the vcsa.comp1300.local > add vm

- IP address of ESXi server
- username - root
- password - P@ssw0rd
- yes i want to connect
- license 😳 (dont do it)
- lockdown mode: disabled
- finish :)

  

you should be able to manage the VMs that are on the ESXi servers through vCenter as well as the ESXi servers themselves