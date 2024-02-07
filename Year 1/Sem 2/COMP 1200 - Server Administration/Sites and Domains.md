**Sites:**

Control Replication:

- interval of replication
    
    - instant or 15 seconds wait for update (intra site replications)
- replication routing

Client Affinity:

- which DC a client logs into

  

Intra site - within same site

inter site - in multiple sites

  

Site - AD objects that represent **one or more TCP/IP subnets** **- highly reliable, fast network connections** (definitions of this may vary)

- we use 192.168.10**X**.x for example in different "sites" or vmnets
- makes replication easier (intra site DCs replicate nearly immediately, without it delay and chaos would ensue)
- allows clients to log into a closer DC rather than having to go across the world every time (client affinity)

  

Inter Site Connectivity:

- sites are connected by site link objects - we can assign a cost (lower = better) for priority
- replication interval by default is 180 (minutes or 3 hours)
- the site link is made by the KCC (knowledge consistency checker)
- you can also set a schedule for when inter site replication happens if you need to conserve bandwidth
  

  

**INTRA** site replication - Immediately or 15 second delay

**INTER** site replication - 3 hours by default (can force replication)

  

**Bridgehead** **Server** - responsible for replicating changes for its whole site to other bridgehead servers

**Client Affinity** - prevents logon authentication traffic from leaving site, this preserves WAN bandwidth

  

Why are sites important?

- replication traffic control
- login authentication traffic control