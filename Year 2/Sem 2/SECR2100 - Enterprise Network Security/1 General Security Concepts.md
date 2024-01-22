**Hacker** - used to be someone with a lot of knowledge
- now is bad guy trying to get unauthorized access
**Phreaking** - hacking a telephone company to be able to operate the phone network
**Cybersecurity** - the availability of the systems and information
**Computer security** - ensuring a system is protected
- authentication and authorization in terms of computer
**Network Security** - protection of a network (multiple computers and other devices connected together)
**Information Security** - focus on the security process of the data
**Information Assurance** - refers to system and information availability
##### "CIA" of Security
**Confidentiality** - ensures that only the people who are authorized can see the information
**Integrity** - deals with generation and modification of data - only authorized people should be ever be allowed to create or modify
**Availability** - makes sure that the system is available when wanted
**Authentication** - makes sure the user is who they claim to be
**Nonrepudiation** - ability to verify that a message has been sent and received and that the sender can be identified and verified
**Auditability** - makes sure that something can be verified to be functioning properly
##### Operational Model of Computer Security
Prevention was the old goal, now the goal is **Protection**.
Protection is considered: 
- Prevention - ACLs, Firewalls, Encryption
- Detection - Audit logs, IDS, Honeypots
- Response - Backups, incident response teams, computer forensics
##### Security Approaches
Ignoring security situations - yolo
Provide **host security**
- focuses on protecting each computer individually
- computer protects itself
Provide **network-level security**
- control access to internal devices from external entities
- controlled through devices - routers, firewalls, IPS/IDS, authentication stuff (RADIUS)
Combine **host and network-level security** 
##### Security Principles
**Least Privileges** - a user should only have the **required permissions** and no more.
- Limits amount of harm that can be done - can't be compromised and have all info taken, application run as admin on a normal user account, etc.
**Separation of Privilege** - needing more than one piece of information to make access decisions 
	**Separation of Duties** - an application of Separation of Privilege, more than one person needs to be involved.
downsides:
- costs time and money
- requires more than one person to complete a task (when it could have normally just been one guy)
- if someone is not there, uh oh :/
**Fail-safe defaults** - when something fails it should fail to a safe state.
**Default Deny** - only grant access with explicit permissions
**Economy of Mechanism** - always using simple solutions when available.
- disable the things that aren't necessary for a system
**Complete Mediation** - each request that is made should be verified - results are cached and used for increased performance
**Open Design** - protection of an object should not rely on secrecy of the protection method itself - rely on strong security, not hiding
**Security through obscurity** - protecting something by hiding the information around it
**Least common mechanism** - mechanisms used to access resources should be dedicated and not shared.
**Psychological acceptability** - refers to users accepting security measures
- if the users view it as work, they probably wont do that
- this part is often overlooked
**Defense in Depth** (layered security) - using multiple layers of defense to protect from an attack.
**Diversity of defense** - different types of security layers
**Access Control** - ACLs - allows or disallows control to various things
##### Authentication Mechanisms
- something you know - password, security questions
- something you have - a device
- something you are - biometrics