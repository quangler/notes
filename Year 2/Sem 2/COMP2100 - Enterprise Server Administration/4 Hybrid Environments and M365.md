Authentication vs Authorization
What the hybrid scenarios are - how we actually administer them

### **Authentication**
- who the person is
- who the service is
- who is this account 
### **Authorization**
- what a person can access
- applications a person can use
## **Entra AD**
- cloud based identity management service that provides authentication / authorization
	- on prem AD - inverted tree structure (domain root, domain, OU/containers, sub OUs, users) - group / user based access
	- Entra AD - flat structure, no structure, groups and users at same level - **role based access**
everyone/everything uses Entra AD

### Features
- authentication - who 
- SSO - multi platform
- application management - what apps you can sign in to
- device management - what devices you can sign in to

## Entra AD Connect
- synchronizes AD with Entra AD 
- allows features such as;
	- self serve password reset
	- MFA
	- SSO

## Hybrid Environments
- infrastructure / services split between on-prem & cloud
- administration of the environment is also split between on prem & cloud - admin burden
	- where things are stored - VMs hosting
	- users - data integrity
### Challenges behind hybrids
- No central administration - azure portal, 3rd party, etc.
- authentication challenges - ADFS / Entra AD / SSO
- data governance - where does the data actually live - what are the rules
- End user training - where do end users save things (desktop, fileserver, SharePoint ??)
- New users / terminated users - where do you create account, when do you disable, how do you terminate

scenario 1 - new employee
- need to make a domain user
- set up permissions
- add a license - for exchange
- teach the user

scenario 2 - sally is an embezzler - need to get her GONE
- secure the account - block the sign ins, disable account, lock them out (make sure they can't do anything for that 60 minute countdown)

where are your users - where do they authenticate

follow user creation and user termination to a T.
- documentation is key here

# Intro to M365
Microsoft's SaaS model (O365 is now M365)
- M365 focus:
	- teamwork / compatibility

- learn to use Microsoft search function

## Basic M365 Functionality
- M365 apps (PowerPoint, Excel, Word, OneNote, Publisher, Access)
- Email and Calendar (Outlook, Exchange)
- Meetings / Voice / IM teams
- intranet (SharePoint)
- files / content (OneDrive, stream , sway, lists)
## M365 Subscription Models
4 basic M365 subscription models:
- M365 Enterprise
- M365 Business
- M365 Education
- M365 Home
### M365 Business
**M365 Business Basic**
- basic m365 function
- cloud only apps
**M365 Business Standard**
- basic m365 function
- productivity tools
- desktop apps
**M365 Business Premium**
- basic m365 function
- management
### M365 Users
Two main types of users
- Licensed Users
- Unlicensed Users
### M365 Admin Roles - primary
- Exchange Admin - full access to exchange
- Global Admin - full access to everything
- Global Reader - read only for everything
- Helpdesk Admin - can re-auth users, change passwords
- Service Support Admin - 
- SharePoint Admin - full access to SharePoint
- Teams Admin - full access to Teams
- User Admin - can manage users
Microsoft follows principle of least permission - exchange admin and global admin can lock you out