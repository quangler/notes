#### Certificate Review
Electronic document proving ownership of public keys
includes the following:
- key information
- owner identity (**subject**)
- digital signature verifying contents (**issuer**)
#### AD Certificate Services
- allows you to generate and maintain Public Key Infrastructure (PKI) with your existing infrastructure
- can support the following certificate usage scenarios:
	- securing data fils
	- securing communications
	- securing email messages
	- securing logons
	- securing websites
##### AD Certificate Services Roles
- certificate authority - issues certificates out
- web enrollment - lets users go through web server to get to CA, also goes to CRL (revocation list)
- online responder - decode CRL, send signed request back and forth
- network device enrollment service - protects a network device (something that doesn't have a user/computer account)
- certificate enrollment policy web service - lets users and computers to obtain certificate enrollment policy info
- certificate enrollment web service - allows users and computer to perform certificate enrollment by using the HTTPS protocol

^ need all 6 to function properly - will allow policy based certificate enrollment for computers on and off the domain
first 3 can be installed all at once,  
then they need to install one by one

#### Types of CAs
##### Stand Alone CA
- not integrated in ADDS
- runs on a member server or stand-alone server
- can be used as internal root CAs that are taken offline after they are used to generate certificates
- certificate issuing and approvals are performed manually
##### Enterprise CA
can't be installed on a DC
- integrated in AD DS
- member servers are used as issuing CAs
- issuing CAs remain online at all times
- issuing and approval of certificates are handled automatically by members of the directory

#### Active Directory Federated Services
(when you sign in to Microsoft and it sends you to the NAIT website, that's what it's using)
- provides simplified identity federation and web SSO for end users
can be used in:
- FS secured enterprise (in your domain)
- federated partner organization (trusted domains/services)
- or in the cloud (M365/Azure AD/Web SSO)
#### ADFS pre-requisites
- windows 2008+
- Certificate Authority with certificates
- DNS must be in place
- database
	- WID can be used for smaller implementations - 500 users
	- MS SQL should be used for larger implementations - 1000+ users
#### ADFS Installation Notes
- very complex installation process
- 2012 R2 + the deployment was simplified
- older implementations of ADFS were reliant on IIS
- stand-alone ADFS deployments are no longer supported