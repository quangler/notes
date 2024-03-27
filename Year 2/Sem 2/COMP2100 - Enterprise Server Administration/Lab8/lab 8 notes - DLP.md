==yellow is good==
~~strikethrough is bad~~

need the E5 license first WE ARE NOT DOIN THE E5 LICENSE, WE ARE USING MICROSOFT BUSINESS PREMIUM
SharePoint needs to be done before (it will drip DLP)

testing from end user perspective

need to edit data like in lab

might not be able to send the email with the attachment (take a screenshot of that failure)
==**need to see identifiable information in the screenshot**==
just need the block stuff screenshot

if it don't work, download the zip file in the NAIT OneDrive and it will scream at you

can take up to 10 days to get things to work
- set it up, test it daily until it works

MFA - worth a percent bonus on the last exam (5%)
- can be done at the same time as DLP

DEMO NOTES
================
**Disable the reoccurring billing broooooo**
everything moves around - cry about it

open up both security and compliance admin centers
<sup>get an error. just.. dont??</sup>
get trial - make sure its a trial - start with 1 user
- Microsoft 365 business premium
==immediately go cancel that trial brother==
- reoccurring billing OFF
- replace some licenses with business premium
*in the real world, when you get rid of a user - decrement the number of licenses so you aren't paying for nothing*

lmao you actually need the E5 probably - he skipped this part because we aint doin E5

**Data Loss Prevention Policies**
template - financial - Canada financial
`Canada Financial Data - External`
to do selected groups and whatever you need E5 - we are not using E5 for this lab

where to apply!? - just leave as is
- exchange
- sharepoint
- onedrive
- on prem
Define policy settings > custom
*low volume = sending alerts | high volume = making incident reports*
set the high instance count to 1 (for Canada financial data)
this course has bad vibes rn so we cant turn on simulation mode - immediately turn that bad boy (whole policy) on

**Sensitivity Labels**
compliance admin > information protection > labels > click the button!! woo!! we can do it now!!
new sensitivity label:
- `Sensitive Documents: HR`
- all the descriptions can just be copied and pasted
scope:
- files and emails - leave it as is
- might need to use PowerShell :(
items:
- select both - lets you make a watermark on your files
- ACLs lets you select who
you cant do security groups anymore, gotta turn them into m365 groups - ***suffer***
for demo he added everyone
content marking - make a watermark text, headers, and footers
**enable auto-labeling**
- condition should be based off of sensitive info types > select the Canada Bank Account ("we'll call that good")
<sup>get another error. lets go</sup>

**TASK ONE BABY LETS GOOOOOOOOOO**
- need to do it in powershell.
- ''rights management is not active for tenant" - need to enable the AIP rights management thing with powershell

MFA DEMO
==============
Entra Admin > Protection > Multifactor Authentication - new location alert (thanks obama)

enabling of MFA

*mfa | providers > conditional access | overview*
enabling of conditional access (there are one billion templates, no exaggeration)
- don't just apply MFA on everyone immediately, bad idea
- require mfa for azure management - probably good to put on

takes 20 mins to get thangs to load on up