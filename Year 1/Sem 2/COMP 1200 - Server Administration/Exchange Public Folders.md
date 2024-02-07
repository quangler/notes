**Exchange Public Folders**

Public Folders - special type of mailbox called a public folder mailbox

- the public folder hierarchy

- public folder content

  

to create a public folder, the admin **MUST** create a public folder mailbox called the primary hierarchy mailbox

  

public folder permissions

- a user must have permissions to post/send to the public folder

- public folder permissions can be managed via EAC, EMS, or outlook

- whole hierarchy has permissions

  

**Defining Public Folders administrators:**

- Public Folder Management - this is the role to manage

- max mailbox size 100GB (the whole thing)

- max individual public folder size - 10GB (personal)

- max number of public folders - 1 million (this is a bad thing)

  

**Shared Mailboxes**

- a mailbox that multiple users can share

- send, recieve, use a common mailbox

- generic email (help@..., info@...,)

- centralize calendar functions (vacations, shifts)

- allows multiple people to interact with a mailbox

  

RecipeientTypeDetails: SharedMailbox

interactable through the EAC

- 3 levels of access

Full Access

Send As

Send on Behalf

  

literally just better public folder

  

a distribution group just forwards something to all the members (sends them their own copy, rather than everyone gets the same one)

  

**Exchange Compliance Management**

- email is the most common way to communicate within a business

- sensitive data leaking - can have serious legal consequences - **data loss prevention, transport rules**

- some organizations have legal obligations to keep data for a certain amount of time - **retention policies, archiving**

- preserving email records for investigation/litigation - **eDiscovery, in-place hold (can also be used as snapshots)**

  

- **in-place eDiscovery** - search specific data in mailboxes across the exchange org > view, export, and store it

- **in-place hold** - freezes a mailbox indefinitely

  

- **data loss prevention** - allows for identifying and preventing critical information

  

- **transport rules** - server side rules that apply to incoming and outgoing emails > ex. every email that goes to a shared mailbox, send a copy to ____. very strong, be careful, test before rolling them out

conditions - when do we apply the rule

actions - what happens when the rule is applied

exceptions - DONT apply the rule when ...

- there are some pre-set rules :)

  

**Deleting Mailboxes**

- (ONLINE) if you remove a license, the user is disconnected and their mail is marked for deletion (default time is 30 days)

its common to convert to a shared mailbox so someone can review their stuff

- (ON PREM) delete = disconnect - SMTP address is deleted, but mailbox object still exists

disable - delete - mailbox is marked for deletion