**MFA** - **Multi-Factor Authentication**
- Combines two or more security elements for full **authentication**

**Security elements:**
- something you **know** - password
- something you **have** - token
- something you **are** - biometric marker

**3rd party MFA options**
- Duo - cloud / on-prem / machine logins (free trial, could use in PROJ)
- One Login
- Secure ID
**Open Source**
- Open OTP
- OAuth
**Microsoft**
- Azure MFA - FIDO compliant 

**MFA in Hybrid environments**
- cloud only deployment - only protecting cloud
- local deployment - only protecting on-prem machines
- hybrid deployment - everythang (ideal solution)
- split deployment - different solutions on-prem and in cloud

**Deploying MFA**
- plan your deployment
	- roll out to smaller groups
	- identify setup issues or unsupported apps
- communicate deployment plan
- continuously evaluate the results and adjust as needed
	- make updates if things are broken

**Customizing MFA deployments** - conditional access
- ***if*** statements
	- do I need MFA ***if*** the client is authenticating through RADIUS already
	- do I need MFA ***if*** a specific cloud app is accessed
	- do I need MFA ***if*** a user is accessing from an unknown device

**Deciding on Authentication Methods**
specifically in Azure AD MFA, have multiple authentication methods (have at least two, one as primary, one as backup)
Method Supports:
- Push to app verification
- mobile app verification codes
- hardware token
- call to phone
- text to phone