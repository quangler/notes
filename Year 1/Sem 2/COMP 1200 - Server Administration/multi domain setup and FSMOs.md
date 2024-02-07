- AD DS is a hierarchy that stores info about objects on a network

  

Multiple domains:

domains are triangles - they all have their own:

- domain admins
- domain root servers
- security groups
- trust relationships between domains

  
  

- domain admins - the administrator for that domain
- enterprise admins - they are the admin of the whole forest > **be careful who is in this**

  

adding a child domain:

- in AD DS configuration > add a new domain to an existing forest
- domain type > child domain
- parent domain name > 'acme.ca'
- credentials need to be of the DOMAIN not of local admin

  

verifying child domain:

- active directory domains and trusts > should be under the main domain now
- dns manager > should be under the main domain name as a name server (this is to check for file servers or whatever on the child domain from the parent one, and vice versa)

  

# to remove child domain:

- remove AD DS feature/roll

  

AGUDLP -

- global - only come from local, can access any domain
- domain local - can come from any domain, only access local domain
- universal - can come from any domain, can access any domain

  

Flexible Single Master Operations (FSMO)

- to prevent conflicts, only one DC in the entire directory is allowed to process updates
- standard replications use Multiple Master Model (multi replications)

five operations master roles:

- schema master
- domain naming master
- RID master
- PDC emulator
- Infrastructure master

  

- Forest root server - first DC installed in top level domain
- Domain root server - first dc installed in any domain

  

FSMO: Schema Master

- schema master is the DC responsible for performing updates to the directory
- schema = blueprint/framework for AD database - objects and properties where they get stored in NTDS.dit
- this DC is the **ONLY** one that can process updates to the directory schema
- one per forest - is the forest root server
  

  

FSMO: Domain Naming Master

- the domain naming master is the DC responsible for making changes to forest-wide domain name space of directory (like quinn.local)
- This DC is the only one that can add or remove a domain from the directory
- one per forest - is the forest root server

  

FSMO: RID (relative ID) master

- RID master is the single DC responsible for processing RID Pool requests from **ALL DCs** within a given domain
- when a DC creates an object it gets an SID #. It gets them from the RID Master - max of 500 SIDs at a time
- one per domain - domain root server

  

FSMO: PDC Emulator

Primary Domain Controller was a role from Windows NT (1993-1999)

was the "boss" server and held the only editable copy of the NTDS

- responsible for windows time service for kerberos authentication
- all DCs sync their clocks to the PDC emulator - does it every 60 minutes
- used for account lockouts are also managed by this role
- one per domain - domain root
  

  

FSMO: Infrastructure Master

- infrastructure FSMO is the DC responsible for updating object SIDs and distinguished name to other domains
- this Infrastructure master in one domain will update the changes for its objects with an infrastructure master from another domain
- one per domain - domain root
  

  

Transferring Roles to Another Server:

- Active Directory Users and Computers > delegate control
- or ntdsutil.exe
- if a DC dies suddenly, seize the role and transfer
- **DO NOT BRING IT BACK ONLINE**