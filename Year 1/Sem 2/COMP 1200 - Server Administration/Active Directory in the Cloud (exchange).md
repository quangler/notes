exchange relies on AD to exist for it to work, in the cloud this is true as well.

  

**on-prem:** your hardware

**hosted:** some else is running the hardware

**hybrid:** combo of on-prem & hosted

  

hosting the AD in the cloud:

- would work in theory
- cost a shiiit load of money (super resource intensive = super money intensive)
- plus now you need to know about cloud stuff too which is :/

  

Microsoft cloud structure:

- create a 'tenant' - container for all the Azure subscriptions
- tenants are hosted on MS hardware, in MS datacenters
- they are also independent from each other, no tenants can interact
- many products/services can exist in the tenant, it can also be bundled (ex. M365)
  

  

everything is in your tenant - big ol container

  

**Microsoft 365**

- used to be called office 365
- SaaS, ADDS functions and services in the cloud
- includes a whole ton of shit
- fully cloud

  

Traditional AD is **fully On-Prem**

- can connect our local AD to our tenant using Azure Active Directory (AAD)
    
    - passwords, users, GPOs, policies - on prem
    - licensing, data storage, email - in cloud
- hierarchy, DCs contain OUs, contain Objects and groups

  

Azure AD can be **fully online**

- good for new, small businesses (don't need a ton up front for servers)
- need more functionality ? click button and pay :)
- flat structure, access controlled by assigning roles
- requires a service running in AD to sync at regular intervals

  

**Azure AD Sync**

- utility that runs on one of our DCs
    
    - run with service account #important
- takes AD hierarchy and convers it to a flat format, then pushes to Tenant
- default - only writes one way (AD to Tenant) but can be configured to by synchronous

  

**Azure Tenant Accounts**

- users in local AD will be given an account in Azure AD
- on-prem, username format is DOMAIN\qparent or qparent@domain.local
- default Tenant accounts will be qparent@domain.onmicrosoft.com

(same account, just has a different UPN because cloud v on-prem)

  

  

**users in the tenant need to pay for things via licensing**

- this is expensive as balls

  

**Exchange Online**

- Azure AD - allows us to do exchange online
- exchange 2025 probably the last on-prem exchange thing ever ???
- running in the cloud - waaaay easier

  

Shit will change, Microsoft sucks.

- screenshots are dumb as hell fuck this shit bro i wanna go home :(