### Administrative Items:
General Policies
Teams Templates
Meeting Policies
Live Event Policies
Teams Port Usage
Messaging Policies
Application Policies
External Communication

### Teams has:
- instant messaging
- meeting / scheduling - little tablets that can book rooms
- file sharing
- calendar access
- application embedding - apps for integrations
- VoIP - taking over physical phones

#### Teams History:
- Exchange 2000 conferencing
- Living communications server 2003/2005
- Office communications server 2007 / R2
- Lync 2010 / 2013
- skype for business 2015 / 2016 / 2019

## Teams Administration
Teams admin center - found in M365 Admin panel
### General Teams Settings
**Manage Teams** - who can make teams
- Manage Members - who can make teams
- Manage Channels - what can be put in the channels
- Manage Team Setting
**Teams Policies** - how use use teams
- used to control settings that are available to users when using teams
- older location for a lot of teams policies
- currently only controls ability to create private channels
**Update Policies**
- used to control Teams and Office preview functionality
- control a test group of users with teams functionality before deploying to large scale user base
**Teams Templates** - easy deployment
- Used to help users create a standardized team inside of teams - think moodle making course team
- orgs can control the standard setup here
- Microsoft default provides some defaults
- administrators can build organization specific templates here
**Templates Policies** - what can be a template
- same as above

### Devices
- Teams enabled devices that have been setup with your tenant will display here
	- Teams Rooms - meeting booking tablet - using teams
	- Collaboration Bars
	- Teams Displays
	- Surface Hub
	- VoIP Phones - using teams in the background
- Device specific settings are set from this area

### Meeting Policies
Allows for granular control of meetings such as:
- transcription - text log
- recording - who can record?
- stream rate
- content sharing - can guests screen share?
- participant control / guest control - can guests join the meeting?
- general meeting behavior
### Meeting Settings
Global Meeting setting
- Control what team meeting requests look like internally and externally to your org
- allows admins to control network behavior of teams meetings - QOS markers, outbound port usage

### Live Events Policies / Settings
Live Event Policies
- Who can allow scheduling of a live event
- who can allow transcription for attendees
- who can join live events
- who can record live events
Live event settings
- support URL customization (global rule)
- Third party distribution partner (hive, kollective, riverbed)
### Messaging Settings
**General Messaging Settings**
- deletion of sent messages - show as deleted and save in background? can end users delete things at all?
- edit of sent messages
- ability to chat - don't want people to message during meetings
- giphy content settings - remove some of the gifs
- read receipts
- etc.
### App settings / setup policies
- global settings can disable apps org wide
- permission policies allow you to customize this for different groups
- setup policies control how teams looks for users
- customize store allows organization to customize the teams app store for internal branding
### Voice
manages VoIP functionality
- phone numbers
- emergency policies
- dial plans
- direct routing (not network routing)
- voice routing policies
- call park policies
- calling policies
- caller ID policies
### Policy Packages
Prepackaged policies available for admins to set settings quickly (think whole teams template)
- Packages:
	- education (primary, secondary, higher education)
	- firstline worker (shift software)
	- healthcare worker / patient room (HIPPA)
### Analytics & Reports
Usage reporting:
- apps usage
- PSTN blocked users
- PSTN minute and SMS
- PSTN and SMS
- teams device
- teams live
- teams usage
- teams user activity
- call diagnostics
### Org-wide settings
Tenant wide settings:
#### External Access
- allows or disallows external access to teams
- admins can block access from teams / skype for business
- When external communication is enabled, by default all domains are available
- When external domains are added to the allowed list all other domains are blocked
#### Guest Access
- Controls how guest (external users) are allowed to interact within your organization's teams environment
- Guests can be added directly into teams and can interact as normal users - external 3rd party trainer, granted access
### Teams Settings
Controls more global user settings
- Notification feed suggestions
- Tags within teams - A01, A02, A03
- Email integration
- Files (external file sharing access)
- Organization (org chart) - chain of command
- Devices (authentication for teams enabled devices) - make sure people can't just walk in with a teams enabled device and plug it in
- Search functionality
### Teams Upgrade
Used for organizations with pre-existing skype for business servers - realistically used for planning a teams deployment
Coexistence modes
- 5 modes available (islands, skype only, skype with teams collab, skype with teams collab & meetings, teams only)
Allows administrators to control upgrade notification

### Planning
Teams has two primary planning tools that can be used to plan teams deployments
- Teams Advisor - microsoft tool that can help you figure out what you need for your teams
- Network Planner - put in how many users and how many phones you are going to use - will show bandwidth estimate
### Microsoft Call Quality Dashboard
- Allows admins to view call quality for all teams meeting and VoIP calls existing in the tenant
- With network location reporting you can narrow down problems such as audio / video pixilation (can find the location if setup properly)
- You can also view your VoIP SLA from this area