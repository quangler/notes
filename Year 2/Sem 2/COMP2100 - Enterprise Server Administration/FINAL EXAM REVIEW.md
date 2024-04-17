### Intune / Endpoint Management

#### **difference between mobile device management and mobile application management**
- **MDM** - Mobile Device Management
	- goal is to reduce admin overhead and make mobile device setup quicker and easier
	- can be phones, laptops, desktops

- **MAM** - Mobile App Management
	- goal is to let admins remotely control apps that are installed on workstations / mobile devices
#### **know difference between different mobile device types in Intune**
- Windows
- iOS/iPadOS
- macOS
- Android
- Linux
#### **how apple devices are enrolled and the process**
**Mac/iOS** have additional setup steps:
- require `Apple MDM push certificate` - requires an apple ID then processed through normal CSR (certificate signing request) process
OR
- enrollment program tokens with DEP (requires partnership with Apple)
**Android** also has extra steps:
- requires `managed google play account` - four profiles:
	- personally-owned device with work profiles
	- corporate owned dedicated devices
	- corporate owned fully managed user devices
	- corporate owned devices with work profiles

#### **know process of which new windows device will join into Intune at boot up - what is that called**
**AutoPilot** - settings that allow devices to be configured at boot up
- A user will sign into their account on boot up
- Intune will check if autopilot has been setup
- if it has, it assigns the user a deployment profile based on group or other settings
- it can show the user an enrollment status (if you enable it)
#### **know process of deploying application to windows from Intune**
depends on the app:
**Microsoft Store App** - can assign an app to auto install to a user/group
**M365 App** - can install the m365 suite of apps - as many as you select | need license for the apps
**Web Links** - makes a shortcut to URL on the desktop
**Line of Business** - upload a file (.msi, .pkg, IPA, APK) - it will be installed on the device on bootup
**Windows App (Win32)** - need to use EXE to .intunewin tool -> upload the .intunewin file -> need install and uninstall command, and a command for detecting if the file exists properly or not

#### **Intune: what can you configure inside of a compliance policy (high level)**
- Email (mobile devices)
- Device Health - bit locker, rooted / jailbroken device control
- Device Properties - OS Version
- Microsoft Defender for EndPoint (licensed only)
- System Security - Password Requirements

#### **Intune: what can you control realistically - general overview of device settings, compliance policies, what works within each device type**
Config policies: (not on Linux)
- can be templates, or if you want custom settings use `setting catalogs`
- can be super broad - like GPO broad - easier to select on Windows and Mac/iOS than on Android
- basically you can setup: password policies, network policies, default apps, user experience, lock screens, power settings, etc.
### SharePoint / OneDrive

#### default storage capacity of SharePoint tenant
1.24TB, can be increased by $0.26 per GB (this is insane)
- personal libraries do not count to the tenant total
#### theoretical maximum of SharePoint single site (25TB)
25TB is shared between all sites, but theoretically you can just have one site use it.
#### SharePoint vs OneDrive - what is more permissive
SharePoint must always be higher than OneDrive for permissions
- OneDrive can match or be lower than SharePoint
### DLP / Labels

#### why would you implement DLP in an org
Organizations have data they legally have to protect
- client / employee sensitive data:
	- social insurance numbers
	- personally identifiable information (address, age, name)
	- credit card information (numbers, CVCs, cardholders, limits)
	- healthcare info (records, healthcare numbers, diagnoses)
	- financial / tax records
**DLP helps control this data to ensure it doesn't get out**

#### what sensitivity labels are / do
sensitivity labels classify data into different categories for easier management and protection
users can classify, or data can be classified automatically based on sensitivity info types
- can be used to control data sharing within tenant
- **labels can force encryption or mark content of files**
#### what are retention labels / what do they do
classifies information in m365 for how long they can stay
breaks down into categories, authority types, citations
- default to 7 years, can be set to infinite
- can be used to mark data as a "record"
#### where labels can be applied in m365
DLP: you should apply different policies internally and externally - no banking info should go out (external), banking info should be locked down to accounting and finance (internal) for ex.
- default DLP locations protect exchange, teams, SharePoint / OneDrive
#### remember laws - apply to Canadian data information (just review the entire slide deck) - rough idea of what is where
**PIPEDA (formerly PIPA)** - Personal Information Protection ad Electronic Documents Act
- Canadian
- collection, storage, retention of personal info
- $100k per offense

##### Canada: 
**AIA / FOIP** - Access to Information Act / Freedom of Information Protection and Protection of Privacy
- Canadian
- controls who can request access to information from what organization
- allows Canadians to request info on data that a company has on them
- $500k person providing info
- $10k person accessing info

**HIA** - Health Care Information Act
- CANADIAN
- ensures health care information is private
- still uses FAX, email is now allowed though!
- typically retains files for up 10 years
- starts at $2k - capped at $500k

**Income Tax Act**
- 7 year rule for financial documents
- almost all financial transactions - receipts, invoices, cheques, pay stubs, T4s, etc.
- record keeping: $250 per record (receipt), $1k per cumulative instance
- tax fines: $100k, back tax, total reportable income
##### Global:
**PCI DSS** - Payment Card Industry Data Security Standard
- every company that uses credit / debit processing has to comply with this
- $100k per month in non-compliance

**GDPR** - General Data Protection Regulation (UK)
- reduces amount of personal info that companies can hold, protects right to be forgotten
- provides end user consent before collection of personal info (allow cookies thing)
- $20 million euros, or 4% of worldwide turnover (whichever is lower)

**SOX** - Sarbanes-Oxley Act (US)
- Income Tax Act but for US based orgs
- forces a real-time reporting on financials
- falsifying reports - $1 mil or 10 years in prison
- certifying false reports - $5 mil or 20 years in person
- doing both - delisting public stock

**HIPAA** - Health Insurance Portability and Accountability Act (US)
- USA ***NOT*** CANADA
- 
#### where to apply DLP - what portal *important*
it used to be DLP admin portal, is now **Microsoft Purview**
- compliance.microsoft.com -> data loss prevention



## General Test Info
35 questions
1 hour test
4 short answer - point form
rest is multiple choice and true and false