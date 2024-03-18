we are now just answering tickets for labs
uses HESK: http://hesk.ultracloud.isp


most of them are policy creation or responding requests

we will use a template to generate tickets

hesk > admin panel > log in
- qparent1 | P@ssw0rd

create new ticket > 2AO1 - qparent1
Name / Email: (this would be the person creating the ticket - the client) we will use the info in the labs
Pick the ticket template - COMP2100 blah blah
Assign the ticket to yourself
CREATE

this is now when you are typing stuff
the timer is only running when the page is open - make sure that everything is pretty realistic time (don't paste everything in)
- anything in the time box - EXTERNAL NOTES
- for INTERNAL NOTES - click "add note" - keep it professional - THEY CAN REQUEST THE INTERNAL NOTES

Barett notes:
- all based on real world examples - meant to be realistic
- NOT ALL OF THEM ARE DOABLE - get BEST POSSIBLE SOLUTION
- marked based on solution of ticket - follow the lab submission guidelines on moodle
- be aware of the effects of someone's ticket - assume the people have the permission to make the request
- in internal notes - show steps, guides you used, URL.
- proof of delivery screenshot in INTERNAL NOTES - proof that you changed something (screenshot of user logged in, work is done)

ALL THE TICKETS IN THE DOCUMENT ARE FOR THE LAB (like 15 of them???)
NO SUBMISSION TO MOODLE

DEMO:
- admin > show all > teams admin
	- self-help diagnostics can be useful
- teams > manage teams - can create and view the teams | private team - invite only, public team - can search to join
- click on the team > settings - these can all be controlled by a teams template
- team templates > create a template - can use a team as a template | can control channels and apps that exist by default
- teams policies > global - applies to all users. create a policy - have to assign it to a user - edit settings | WORKS FOR ALL POLICIES
- teams apps > manage apps > find app > add to team
- teams apps > setup policies > firstlineworker starts with some apps for shift work

also a bunch of stuff exists under the admin panel
- see teams, manage users in teams, *some* policies 







```TICKET-1
Resource group was created for jet@quinndomain.ca
Full access and delegation rights were granted to Marion. Set owner of mailbox with this command:
- Set-MailboxFolderPermission -Identity jet@quinndomain.ca:\Calendar -User "D'AmicoMari@quinndomain.ca" -AccessRights Owner

Used these PowerShell commands to assign Waylon Smithers and Charles Montgomery Burns as PublishedAuthors for the mailbox permissions: 

- Add-MailboxFolderPermission -Identity jet@quinndomain.ca:\Calendar -User "WaylonSmit@quinndomain.ca" -AccessRights publishingauthor
- Add-MailboxFolderPermission -Identity jet@quinndomain.ca:\Calendar -User "CharlesMontgomeryBur@quinndomain.ca" -AccessRights publishingauthor

Default had permissions removed so that only the allowed users could view/book the jet. Command:
- Set-MailboxFolderPermission -Identity jet@quinndomain.ca:\calendar -User default -AccessRights none
```

```TICKET-2
$resource = "FT0001"
$user1 = "default"
$user2 = "MarionD'Am@quinndomain.ca"
Set-MailboxFolderPermission -Identity "$resource@quinndomain.ca:\Calendar" -User $user1 -AccessRights PublishingAuthor
Add-MailboxFolderPermission -Identity "$resource@quinndomain.ca:\Calendar" -User $user2 -AccessRights Owner
Get-MailboxFolderPermission -Identity "$resource@quinndomain.ca:\Calendar"
```

