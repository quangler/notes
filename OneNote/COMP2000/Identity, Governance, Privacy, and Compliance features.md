Secure access to applications using azure identity services

Cloud governance strategies in azure

Privacy, compliance, and data protection in azure

  

**Authentication vs Authorization**

- **Authentication** (who)

Who is this person

Who is this service

Who is this account

- **Authorization** (what can they access)

What can this person use for applications

What data can this person access

Authentication and authorization are always combined

  

**Azure Active Directory**

Azure AD is Microsoft's cloud-based identity management service that provides authentication/authorization

How does it compare?

- On-prem AD - inverted tree structure; domain root, domain, OU / containers, sub OUs, user accounts
- Azure AD - Flat structure, no structure, groups and users exist at the same level (use the search) - role based access

Who uses Azure AD? - everyone and everything; IT admins, App devs, Users, lots of SaaS (M365)

  

**Azure AD - Features**

- **Authentication** - identity verification - self-service for users - no more P@ssw0rd
- **Single Sign-On -** one username and password combination for everything
- **Application Management** - manage cloud / on-prem devices; my app portals
- **Device Management** - device registration and management - allows devices to be controlled through inTune

  

**Azure AD - AAD Connect**

- Software application installed on-prem
- Synchronizes AD with AAD
- Allows features like: self-serve password reset, MFA, SSO

  

**MFA - Multi Factor Auth**

- Additional form of identity for identity management
- Broken into three categories:
    
    - Something you know - user/pass
    - Something you have - token/code (RSA token, Push app)
    - Something you are - biometrics (fingerprint, face scanning, retina scanning)

**MFA is at least two of those at once ^**

  

**Azure AD - MFA**

- Free edition works for:
    
    - Azure AD
    - M365
- Microsoft Authenticator App used primarily
- Phone call or SMS can also be used
- AAD Premium - allows for conditional access policies

  

**Azure AD - Conditional Access Control**

- Access to resources controlled through signals
- Allows admins to control who has access to what and when
- Signals include; who you are, where you are, and how are you accessing
- Used heavily for highly secure environments, but applicable for smaller environments as well

Ex. HR director travelling and needs access to records, have to use a public computer. - this would authenticate that computer shortly

  

  

**Azure RBAC**

- Role based access control
- Allows for access control based on the flat structure of Azure
- Roles are applied to scopes
- Scopes include:
    
    - Management group
    - Subscription
    - Resource group
    - Resource
- Managed from Access Control (IAM) form the Azure portal
- Accidental changes can be prevented in Azure using resource locks
- Resource locks are applied to resources with different levels of locks based on role
- Two levels of locking: CanNotDelete and ReadOnly

  

**Azure Tags**

- Tags are used to organize all of your Azure resources
- Tags can be applied to all azure resources, groups, subscriptions, etc
- Tags contain resource metadata
- Metadata can be used for:
    
    - **Resource management** - tags enable you to locate and act on resources that are associated with something (specific workloads, environments, etc.)
    - **Cost management / optimization** - allows you to group resources so that you can report on costs, allocate internal costs, track budgets, etc.
    - **Operations management** - allow you to group resources according to how critical their availability is to your business - allows you to create SLAs
    - **Security** - allow you to classify data by its security level (public / confidential)
    - **Governance / regulatory compliance** - allow you to identify resources that align with governance or regulatory compliance requirements
    - **Workload optimization / automation -** help you visualize all of the resources that participate in complex deployments

  

**Azure - why tag?**

- Azure policy generation
    
    - VM creation boundaries
    - Subscription management
    - Subscription limits
    - blueprints
      
    

  

**Azure - Privacy / Compliance / Data Protection**

- Regulatory requirements are a large part of cloud-based data
- Recognized regulatory requirements
    
    - GDPR - UK rules for data being forgotten allowed (cookies popup)
    - HIPA - American healthcare privacy laws
    - PCI DSS - credit card processing standards
    - PIPA - personal information privacy act - Canadian

  

**Azure - Trust Center**

- Trust center allows for administrators and organizations to view their compliance compared to regulatory requirements
- Trust center allows you to audit requirements as well

  
  

Nice to know:

US govt. has their own instance of azure (this is private, you cannot access it)

China also has their own instance of azure - owned by 21vianet - basically light version of azure