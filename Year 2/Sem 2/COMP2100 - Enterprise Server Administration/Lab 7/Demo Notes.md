M365 - show all - `SharePoint Admin Center`
- active sites > by default: `all company`, `communication site`
- team site - focused more on collaboration
- communication site - focused on delivering information

making a demo site > using team site
- site owner should be the person who is going to be "owning" the site (the manager)
- adding users - can make them owner (owner = full access into site)
- can change the name of the site > have to edit SharePoint address to change the URL
by default a site will make a group for the:
- users, owners, visitors
sharing settings can't go above the global permission access

look at the "about membership and permissions" for more info

on the actual site - securing document libraries
- new folder > `Protected - HR` - default everyone has access to that folder
- right click > manage access > groups - can change the different folder permissions on members or visitors
- can grant access to on prem groups (click + guy at top right) > (disable notify group)
you can still follow permissions with the groups (read/write, and just read)

Unique / Inherited permissions: (in the old view - forget how to get here)
- when importing NTFS folders, things will have inherited permissions
- have to convert to unique permissions

making a sharing link > can change the permissions for the links
- can see the links in the manage access of the site

moving a site to the `deleted sites` - immediately kills the site for everyone
- only do if we are cleaning up sites and getting rid of them
- **93 days of storage after deletion**

#### Policies
`Policies` > `Sharing`
SharePoint is the standard - if it moves down, OneDrive moves down with it
- OneDrive **can't** be higher than SharePoint
Most companies bring SharePoint and OneDrive to `New and Existing Guests`

`Policies` > `Access Control`
- can make only domain users join
- idle session sign out
- network location (certain IPs)
- force MFA (i believe?)

Advances Management: need a better license (??!?!?!)
- does some crazy shit

Migration
- other migration solutions - SharePoint on prem > some things just don't make it if you have multiple version old SharePoint server (ex. 2010)
file share migration > download agent (one agent per file server)
they took away OneDrive migration ?! one less lab task! yippee!!

^^^^ high level overview of SharePoint

LAB 7:
bulk of lab is migration
- basic communication site
- using HESK still bro :// all tickets
- only 5 tickets!? - some of these are gonna take some time to sync :/
- **no documentation - WOOOOOOOOOO!!!!!!!!!!!!!!!!!!**

install migration agent onto FS1 (SRV3)
- migrate CORPDATA - MAINTAIN FILE PERMISSIONS (NFTS)
- EXCLUDE SOME FILES - .xslx (this is part of the migration, if they are in there you failed.)

**skip ticket 4!! WOOOOO!!!!**

can't skip ticket number 5 (the soldier staring picture guy)
1.7gb of data in the dropbox - **DON'T ENABLE MFA** (unless you don't want to do that ticket !? ;) 