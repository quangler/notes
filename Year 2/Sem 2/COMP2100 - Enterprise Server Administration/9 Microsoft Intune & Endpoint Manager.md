### What is Mobile Device Management (MDM)
- lets admins manage mobile devices (tablets, smartphones)
- goal is to reduce admin overhead required to manage many mobile devices
- MDM's allowed admins to control device configuration for corporate owned devices to speed up setup
#### Where is MDM today?
- now for BYOD too!
- MDM needed to be expanded into desktop/laptops
- enterprise MDMs can do all this stuff now

### What is Mobile Application Management (MAM)
- similar to MDM but application specific
- many MDM solutions have MAM built in
- allow admins to remotely control applications that get installed on workstation or mobile device
- can be used in enterprise or BYOD environment - easily control applications and patch levels
- ninite is a basic version of MAM
### Microsoft Endpoint + Security Management
- Microsoft's MAM and MDM combined solution
- supported by Intune and Configuration Manager
	- separately licensed
	- configuration manager is more feature rich than intune
- endpoint + security management licensing enables endpoint security and SCCM functionality
### What about SCCM?
- SCCM is being replaced by Configuration Manager
- all prior versions will remain SCCM but anything newer is called Configuration Manager
- Configuration Manager is now licensed and managed through the cloud (still requires onsite install)
### Intune
- encompasses both MDM and MAM
- Device Policies control both config and application install
	- can be controlled by user / group
	- users have a limited number of enrollment tokens
- device managers can enroll a larger quantity of devices
	- devices must be enrolled in order to get config settings
- deployment can be automatic or manual

Intune configs can be found under devices and applications
- endpoint security is only available with the extended licensing and feature set that replaces SCCM

### Intune Setup
- compliance policies are used for baseline device settings
- configuration policies are used for more granular control and settings will differ between platforms
- application deployment is then layered on top of device configuration
#### Compliance Policies
- each platform type requires its own compliance policy
- may need multiple policies for the same platform (many types of android for ex.)
- windows 8.1 is also its own thing
#### Compliance Policy Components
- email (mobile device only)
- device health (all)
	- bit locker
	- rooted / jailbroken device control
- Device properties (all)
	- OS version
- Microsoft defender for EndPoint (all - licensed only)
- system security (all)
	- password requirements

#### Configuration Policies
- mobile devices are broken down by configuration settings
- Mac / Windows configuration policies are based off templates
- settings catalogs will replace templates for configuration
- windows configuration policies may conflict with GPO settings
	- Intune settings can be set to override GPO or allow GPO to override conflicting settings

### Device Enrollment
- all Intune devices must be enrolled to get configs
- enrollment can be automatic or manual
- additional setup is required for Mac/iOS and Android
- azure AD joined devices are auto enrolled with Intune
- on prem devices require an on-prem Intune connector
### Windows Enrollment Options
- auto enrollment can be turned off, enabled for some or all users in the organization
- custom MDM and MAM URLs can be specific in M365
- domains must be validated for automatic enrollment
- **Windows Hello** can be controlled from the enrollment settings page (windows hello can be a real pain, bypass long password with a 4 digit pin)
- AutoPilot settings allow devices to be configured at boot up (using network)
### Mac / iOS enrollment
- Requires Apple MDM push certificate
	- acquiring certificates requires an apple ID and then is processed through a normal CSR process
- Two primary method for enrollment
	- apple configurator
	- enrollment program tokens with DEP (requires partnership with Apple)
### Android Enrollment
- Requires a managed google play account
- Four different enrollment profiles
	- personally-owned devices with work profiles
	- corporate owned dedicated devices
	- corporate owned fully managed user devices
	- corporate owned devices with work profiles
### Application Management
- All applications are managed per platform
- Applications can be assigned / available / blocked
- Applications can be deployed via device type or user group
- Custom configuration policies can be set up per application
- Ebooks can be deployed using Intune (apparently schools do this, and its apple??)
### Windows Application Management
kinda sucks
- Application Deployment options
	- Microsoft store URLs
	- M365 Apps
	- Web links
	- Line of business apps (MSI)
	- Windows App (win32) - exe to .intunewin
### Android Application Management
- Two options available for application management
	- managed google play app
	- android store app
- Android store app requires personal google account for download
- managed google play app requires centralized managed account
- further app management available on android
	- Web Links
	- Built in Apps
	- Line of Business Apps
	- Android Enterprise Apps
