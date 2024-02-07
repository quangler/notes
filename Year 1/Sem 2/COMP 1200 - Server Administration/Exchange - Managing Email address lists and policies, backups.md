**Address List:**

- contains any type of exchange recipients:
- mail groups
- mailbox users
- mail contacts
- mail users
- room and equipment resources
  

  

the one main list that microsoft exchange comes with is the **Global Address List (GAL)**

- need to use powershell to manage it

5 sub-lists that are built in

- all contacts
- all distribution list
- all rooms
- all users
- public folders

  

  

- smaller custom address lists (can be based off of tags on the user's account or groups)
- must be done in powershell

  

- don't make too many lists - you might have people confused about which to use
- proper naming convention and hierarchy - lets people know who are in it
- Exchange Online uses Object Attributes - like role, group, etc.

  

- resource policies determine how a resource mailbox can be booked

- how early you can book a meeting
- max time
- repeated meetings allowed or not
    
    - you can set a booking delegate - this is the person who can allow or disallow the use of the room
    - resource mailboxes have a **booking attendant** service turned on by default
- used to auto respond to scheduling requests, and to forward scheduling requests to those who are delegates
  

can do most of it through EAC

Set-CalendarProcessing

  

- SMTP (small mail transfer protocol)
- there can be multiple SMTP addresses assigned to recipients
- email address policies define the rules that create email addresses for recipients in the exchange organization

- you can change the email address format, priority (lower number better), and what recipients it applies to
- default email address policy can be changed (probably dont) but not deleted, default has the **lowest priority (highest number)**
- can set 2 SMTP address, can send from whichever you want (only one tho)
  

- backups and restore are **VERY** important
- used for:

- disaster recovery
- recovery of accidentally deleted items
- long-term retention of data
  

Microsoft will make sure your infrastructure is good, but your data is on you.

  

- a restored mailbox should not be older than 1 day
- a deleted mailbox should be restored within an hour and containing data should not be older than 30 days
- a deleted email should be restored within 1 day and you should be able to restore emails up to 60 days
  

- delete an email > trash bin (30 days <?>) > delete again > exchange recycle bin (14 days <?>)
- point-in-time backups are **not supported** inside exchange online (i want to see my mailbox from 3 days ago)
  

**Exchange Native Data Protection**

- NDP relies on multiple technologies (replication, item retention) to ensure that **multiple copies of every database exist for redundancy**
- if a copy of a DB becomes unavailable, another one is activated automatically - (the mailbox databases are part of a **Database Availability Group**)
- single item recovery - get single items back that have been deleted or purged
- in place and litigation holds - freeze the state of a mailbox for legal reasons
- deleted item retention and soft-deleted mailboxes - how to handle the removal of entire mailboxes

  

**Database Availability Group** - just bigger RAID + off site (2) that has backups of everything that is in site1

  

**Email Retention settings** - by default 14 days - can be changed

single-item recovery - ability to recover individual messages after retention period expires (enabled by default online)

**mailbox retention settings** - by default 30 days - can be changed

**Custom Address Lists**

  

**Best Practices for creating additional address lists**

  

**Managing Resource Booking:**

  
  

**Managing Email Address Policies:**

**Email Address policy:**

  

**Microsoft Exchange Backups**

  
  

**Microsoft Exchange Backups**

  

Exchange has some built in protections for individual users:

  

an alternate backup: