Import-Module ADSync

Start-ADSyncSyncCycle -PolicyType Delta

  

Import-Module ExchangeOnlineManagement - imports exchange online module for powershell

Connect-ExchangeOnline - connects exchange online to AD DS

  

Get-AcceptedDomain - this is to see what domain you are connected to for exchange

  

Get-MailboxFolderPermission -Identity fred@qparent.onmicrosoft.com:\Calendar | this gets the calendar permission for fred on exchange

  

Add-MailboxFolderPermission -Identity fred@qparent.onmicrosoft.com:\Calendar -user wilma@qparent.onmicrosoft.com -AccessRights Reviewer

- this is the command to add wilma to see fred's calendar

  
  

Set-MailboxFolderPermission -Identity fred@qparent.onmicrosoft.com:\Calendar -user wilma@qparent.onmicrosoft.com -AccessRights editor

- this command allows wilma to edit fred's calendar

  
  

proprac -

  

Add-MailboxPermission -Identity mark@qparent.onmicrosoft.com -user bo@qparent.onmicrosoft.com -AccessRights full | gives bo full access to mark's mailbox

  

Add-RecipientPermission -Identity mark@qparent.onmicrosoft.com -Trustee wayne@qparent.onmicrosoft.com -AccessRights SendAs | grants wayne send as permission on mark's mailbox

  

Set-Mailbox -Identity mark@qparent.onmicrosoft.com -GrantSendOnBehalfTo @{Remove="wayne@qparent.onmicrosoft.com"} | removes the send on behalf to permission from wayne to mark

  

Set-Mailbox -Identity wayne@qparent.onmicrosoft.com -MaxReceiveSize 1MB -MaxSendSize 1MB | this changes the max send and receive size to 1MB for wayne

  
  

Add-MailboxFolderPermission -Identity mark@qparent.onmicrosoft.com:\Calendar -user wayne@qparent.onmicrosoft.com -AccessRights PublishingAuthor | sets publishing author for wayne on mark

Add-MailboxFolderPermission -Identity mark@qparent.onmicrosoft.com:\Calendar -user bo@qparent.onmicrosoft.com -AccessRights PublishingAuthor | sets publishing author for bo on mark

  

New-Mailbox -Shared -Name prospects -DisplayName prospects -Alias prospects -PrimarySmtpAddress prospects@qparent.onmicrosoft.com | creating the shared folder

  

Add-MailboxPermission -User wayne -Identity prospects -AccessRights fullaccess -InheritanceType all | full access to wayne for shared folder

Add-MailboxPermission -User bo -Identity prospects -AccessRights fullaccess -InheritanceType all | full access to bo for shared folder

  

Add-RecipientPermission -Identity prospects -AccessRights SendAs -Trustee bo | send as permissions to bo for shared folder

Add-RecipientPermission -Identity prospects -AccessRights SendAs -Trustee wayne | send as permissions to wayne for shared folder

  

Get-RecipientPermission -Identity prospects | to see who has access and what level they have

  

New-AddressList -Name CenterDepartment -RecipientFilter "(Department -like 'Center')" | to create address list