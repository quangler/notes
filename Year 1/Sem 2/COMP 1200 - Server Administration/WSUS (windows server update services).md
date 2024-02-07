downloads updates from windows > then acts as the server that updates client PCs

  

different types of microsoft updates:

- critical update - fix critical, non-security related bugs
- definition updates - additions to definition database
- feature packs - adds new product functionality (ex. 21h2)
- security updates - updates for security vulnerability
- service packs - dont really exist anymore - used to be hotfixes, security updates, and regular updates
- update rollups - basically new service packs, hotfixes, security updates, critical updates, and regular updates, packaged all nice
- monthly rollups - multiple updates packaged - every second tuesday

  

WSUS: can act as the windows update server

- control the timings of updates
- bandwidth of updates
- types of updates
- allows testing

  

**Timing:**

- if something goes down it can be annoying to catastrophic (surgery, or in the middle of the work day)
- Does all updates when everyone is at home

  

**Bandwidth:**

- WSUS server acts as a relay
- this means you don't flood your network with downloading and installing windows updates on every single PC in your environment (do it from one location already on your network)
  

  

**Types of Updates:**

- can prioritize different update types
- can categorize server updates, client updates, azure updates
- can pick and choose updates we want on hand

  

**Testing:**

- can test an update to make sure nothing gets broken with the new update

  

Windows Server Update Services:

- role in windows server
- centrally manages updates
- synchronizes with microsoft update servers to see what is out there available for updates (goes back forever) (THIS DOES NOT DOWNLOAD, IT JUST INDEXES)
- can distribute updates to all, or groups of clients (separate from AD)
- allows uninstalling updates from clients

  

WSUS deployment strategies:

single WSUS deployment

- microsoft update server > through cloud > firewall > WSUS > clients
  

  

Hierarchical WSUS deployment #important

- microsoft update server > (a downstream from updates) > server a > (b downstream from a) > server b > clients
- server b can search only server A
  

(Hierarchical) Autonomous Mode (default)

- upstream WSUS server shares its updates with downstream servers
- downloaded updates are approved from each downstream servers
  

(Hierarchical) Replica Mode

- upstream WSUS server shares its updates with downstream servers
- downloaded updates a re not approved from each downstream server, but from upstream WSUS server
  

  
  
  

note:

- WSUS isn't always necessary, especially more recently - bandwidth is available, and updates are stable.
- 3rd party management platforms are being used more and more (RMM, Intune, SCCM)
- probably need **something** to centralize / control updates