Recipient Object - anything that can send or receive an email.

**types of recipients:**

- mailboxes
- mail contacts
- distribution groups
- shared folders
  

  

**User Mailbox:**

- syncs to the user account **and** their mailbox

  

**External Contact:** (doesn't really exist in cloud exchange)

- a contact email (aka forwarder)
- they can't login to the domain
  

  

**Mail Contact:** (this is what we use instead of external contact in exchange online)

- just a contact, no forwarding (they use their own email, not your local domain)
  

  

**Mail User:**

- holds user account and local email address **(NO MAILBOX)** in the AD forest/exchange
- (they get an AD account but not a mailbox)
- would be used for a temp employee or external contractor
- forwards to their email that already exists (gmail or something)

  

**Resource Mailbox:**

- object that you can assign when scheduling a meeting
- used for booking rooms, equipment, cars etc.
- can setup options with automation, or manually (max # of people, max length of meeting, etc.)

  

**Mail-enabled Groups:**

- can create a group in AD
- allow you to email the group (will get responses individually)
- **security group** - assign permissions to resources and emails
- **distribution group** - only emails
- **dynamic group** - auto updates membership (based on conditions and attributes) emails send to a group send to all with that condition or filter. ex. send email to all 'Managers'

  

**Shared Mailboxes:**

- basically a shared email client that users and groups can be shared into
- can be setup to send/receive email

  

**Public folders - stay away**

- public directories are a mess, don't do them

  

**Administration Groups** - not fully translated over to exchange online

- Recipient Management Role group
- Organization Management Role group - this one is god mode
  

  

**Admin Roles**

- Global Admin - controls everything in the tenant
- Exchange Admin - controls only exchange

  

**Microsoft Exchange Recipient** (role thing?)

- object that sends system-generated messages internally

  

**Postmaster** (account)

- the object that sends system-generated messages externally
  

  

**Mailbox Configurations:**

- assigning license to an AAD - the mailbox is created automatically
- user's alias will become the user's SMTP address (by default) - (alias@domain.onmicrosoft.com)

  

**SMTP Addresses**

- SMTP - protocol that passes mail between servers
- primary SMTP address is someone's "sending" address
- secondary SMTP address (AKA alias) is configured as an additional email (think like quinn-facebook@gmail.com > quinn@gmail.com)
- you will still send as your primary SMTP address
- (used for changed names)

  

**Delegations:**

- often needed for different levels of permissions to another user's mailbox
- contains 3 perm types:
- **Send As**
- **Send on Behalf**
- **Full Access**

  

**Send as:**

- you send a message that appears on the recipient side as coming from the mailbox owner
- (grant "Send As" on the 'vacant' mailbox)

  

**Send on behalf of:**

- allows user to send a message that appears on the recipient side as being sent from the user on BEHALF of the mailbox owner
- used for assistants sending messages for their bosses

  

**Full access:**

- allows user to log into that mailbox and access its contents fully
- **does not allow you to send as that mailbox**

  

Import-Module ADSync

Start-ADSyncSyncCycle - PolicyType Delta

  

^ sync local to online