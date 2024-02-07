**AD:**

- database that contains info about all users computers and accounts in the domain
- domain represents a single company
- controls authorization and authentication, policy, and control
- multiple servers can share a single database (replication)

  

**AD installation:**

IP MUST BE UNIQUE AND STATIC

NAMES MUST BE UNIQUE

install AD DS

promote to DC

create a new domain or join existing domain

DNS zone is created

  

**DNS:** actually required

ties names to IP addresses

reverse - IP to names

  

**DHCP:** basically required

assigns IP addresses and (can be setup for) other info to devices on the network automatically

  

**Best Practices:**

- Default Administrator is **NEVER** used. Copy it so you have a template user, then **disable** it.
- Domain Admins are **not used for normal operations.**
- Techs will have 2 accounts: a **normal user**, and an **admin user**.
- Add users to groups based on their role.
- Permissions are assigned to Groups, **not users.**
- Documentation is **VERY** important.
- Firewalls should stay on. Configure rules to allow traffic if needed.
- A GPO can set basic firewall rules for the domain. (default for ICMP traffic for example | hint)
- ADP can be managed remotely
    
    - Remote Desktop (RDP) - individual endpoints
    - Remote System Administration Toolkit (RSAT) - Domain Users, GPOs, DNS
    - Windows Access Center (WAC) - server and domain management
- Most admins set up a dedication workstation with those tools installed and set up (hint)

  

**Expectations:**

- use admin workstation
- login with normal user, elevate if needed
- firewalls stay on

if not: penalties can occur (if thing that is submitted does not follow those)