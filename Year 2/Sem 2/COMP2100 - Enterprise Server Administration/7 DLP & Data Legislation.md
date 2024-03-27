**DLP** - data loss prevention

### Security and Compliance
- orgs have data that they are legally required to protect

#### Sensitive Data Types
- SIN # - CAN
- SSN # - US
- Personal info - address, age, birthdate, location
- Credit card info - numbers, CVCs, cardholders, limits (this can be used for advance checks that ask about banking info)
- Intellectual Property (IP)
- Healthcare Info (healthcare records, healthcare numbers, diagnoses, prognoses)
- Financial Records (account numbers, balances, signatories)
- Tax Records (T4 - CAN, W-2 - US, SA-100 - UK)

### Data Loss Prevention
- the act of proactively controlling data within and outside of our network's boundary
5 steps:
- identification - organization must identify what data exists - what DLP does it need
- Classification - org must classify data into different sections - should be done automatically nowadays - flag for how sensitive it is
- Protect - what technologies do we use to protect this info
- Detect - how do we detect if the data is leaving our control
- Training - training the users where they can store data, how they can securely use data, what can leave the organization

### Alberta / Canada privacy acts:
- FOIP / AIA - access to information act
- PIPA / PIPEDA - personal information protection act 
- HIA - health information act
- Income Tax Act

#### PIPEDA - Personal Information Protection and Electronic Documents Act (formerly PIPA)
Controls:
- collection of personal info
- storage of personal info
- retention of personal info
Fines:
- $100K CAD per offense

**Home Depot violated PIPEDA**
- E-Receipt information shared with Meta through use of "Offline Conversations" marketing tool
- Home Depot failed to get content for this information

#### AIA / FOIP
Access to information act is Canadian federal law regarding access to information
Provincial acts must meet or exceed this federal standard
FOIP controls:
- who can request access to information from what organization
Fines:
- 10K - misuse of information requests
- 500K 

**Tim Hortons FOIP violation**
- collected tons of data
- asked for geolocation data under false pretenses
- app ended up tracking users as long as it was installed

### HIA - Healthcare Information Act
- Ensures Canadian health care information remains private
- Originally the act prevented from any electronic transmission of healthcare records other than by fax
- Now we can use encrypted methods - some people don't like that...

Fines:
- Start at $2K
- Capped at $500K
- court can also double up with other privacy laws

**HIA Violation**
Marie Mushinski found guilty of accessing:
- 189 individuals' health information 985 times over a two-year period
Fines:
- $5000
- $1000 victim surcharge
- 18 months probation
- never work in healthcare again

#### Income Tax Act
- typically known as the 7-year rule for financial documents
- includes almost all financial transaction related documentation; receipts, invoices, cheques, pay stubs, T4's, etc.
##### Fines
Taxpayer
Corporation / Record Keeper
- Record Keeping fines:
	- $250 per record (aka receipt)
	- $1000 per cumulative instance
- Tax Fines
	- $100K
	- Total Reportable Income
	- Back Tax

**Violation**
Directors of SSI & TSI
Fines & Sanctions
- $3.3 mil in fines
- $4.4 mil in back taxes
- 10 people went to jail for 15.3 years total

### Global Compliance Acts / Standards
**Common Global Acts / Standards**
- PCI DSS
- ISO
- GDPR (EU)
- HIPAA (US)
- SOX (US)

#### ISO
International Standard Organization
- provides 35 global standards regarding IT alone
- following ISO is not mandatory unless required by a governing body
- no direct fines for violations
#### PCI DSS
PCI - payment card industry security standards council
PCI DSS - payment card industry data security standard
need to have a FortiGate with IDS (or something)
Fines:
- up to $100K per month in non-compliance

**Violation - Equifax**
- 145 million Americans affected
- initial settlement total of $425 million
- true figure likely never to be disclosed

#### General Data Protection Regulation (GDPR)
Purpose:
- reduce amount of personal information that companies can hold
- users need to consent before collection of personal info
- to protect the rights of the personal data being stored (the right to be forgotten)
Fines:
- up to 20 million euros
- or 4% of the worldwide turn over for the preceding financial year

**Violation - Amazon**
- 746 million euros
- full details not yet released, has to do with failure to obtain cookie consent

**Why do we care about this bro??**
- you might do business across the world.

#### SOX
- Sarbanes-Oxley Act
- Similar to the Canadian Income Tax Act but for US based organizations
- Put in place to provide Realtime reporting on a firm's financials
**Fines / Sanctions**
- submitting reports / not meeting criteria 
	- $1 mil or 10 years in prison
- certifying reports not meeting criteria
	- $5 mil or 20 years
- both
	- can get your stock wiped off the face of the earth

#### HIPAA - in the USA
Health Insurance Portability and Accountability Act 
Often mistaken that it applies to Canada too, it doesn't unless you traveled to the USA

**Largest single HIPAA fine - Anthem, Inc**
- cyber attack resulted in 78.8 million people's healthcare records lost
- largest single fine of $16 million
- additional $48.2 million financial penalty

## What can we do?
#### M365 Tools
- need to get a business license
- now data compliance center or something
 
 **Data classifications**
applied on incoming and outgoing

**sensitivity labels**
- files, emails, groups, sites, azure assets
- M365 users can classify data labels
- can also be applied automatically
 
**Retention labels**
- how long data stays in there
- default to 7 years

### Data Loss Prevention
sets of policies and application permissions
used to control data egress m365 tenant
can be used to control data sharing within the tenant

### Data loss Prevention: Policies
- templates based on global privacy laws
- custom policies allow admins to configure specific data loss prevention
- default locations protected are: exchange, teams, SharePoint/OneDrive
- DLP policies can be enabled / disabled per user or **group**
==**NEED TO START LAB BEFORE APRIL 3RD**==

