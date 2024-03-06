
| Account Name | Password                                                                                                                         |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| Break Glass  | q1jUg3gPsDBUztMr62SY7wa41s5r9Eu53BwCwsGj37kKBmXLE22lVah4N8Ne5ge9U5XxkJArfM7hIpaiqC2CHmfa6x4cNye4B4y2qU046C9ZiqLj99J6z0R895u1lyQ8 |
### External DNS Configuration
**Domain:** quinndomain.ca
**Hosted on:** GoDaddy.com

| Record Type | Name                 | Data                                                                                     | TTL  |
| ----------- | -------------------- | ---------------------------------------------------------------------------------------- | ---- |
| A           | @                    | Parked                                                                                   | 600  |
| NS          | @                    | ns33.domaincontrol.com.                                                                  | 3600 |
| NS          | @                    | ns34.domaincontrol.com.                                                                  | 3600 |
| CNAME       | autodiscover         | autodiscover.outlook.com.                                                                | 3600 |
| CNAME       | selector1._domainkey | selector1-quinndomain-ca._domainkey.qpc210024.onmicrosoft.com.\|                         | 3600 |
| CNAME       | selector2._domainkey | selector2-quinndomain-ca._domainkey.qpc210024.onmicrosoft.com.                           | 3600 |
| CNAME       | www                  | quinndomain.ca.                                                                          | 3600 |
| CNAME       | _domainconnect       | _domainconnect.gd.domaincontrol.com.                                                     | 3600 |
| SOA         | @                    | Primary nameserver: ns33.domaincontrol.com.                                              | 3600 |
| MX          | @                    | quinndomain-ca.mail.protection.outlook.com. (Priority: 0)                                | 3600 |
| TXT         | @                    | MS=ms51986761                                                                            | 3600 |
| TXT         | @                    | v=spf1 include:spf.protection.outlook.com -all                                           | 3600 |
| TXT         | _dmarc               | v=DMARC1; p=none; rua=mailto:dmarc@quinndomain.ca; ruf=mailto:dmarc@quinndomain.ca; fo=1 | 3600 |
### Scripts used:
This script was used to automatically change accounts from using the `brunsco.sf` domain upon login to the `quinndomain.ca` domain.
```UPN-Update.ps1
PS C:\> $LocalUsers = Get-ADUser -Filter {UserPrincipalName -like '*brunsco.sf'} -Properties UserPrincipalName -ResultSetSize $null
PS C:\> $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("brunsco.sf","quinndomain.ca"); $_ | Set-ADUser -UserPrincipalName $newUpn}
```
This script was taken from https://www.alitajran.com/change-users-upn-with-powershell/.

```Proxy-Address.ps1
# Import the Active Directory module
Import-Module ActiveDirectory

# Get all users in the domain
$users = Get-ADUser -Filter * -Server SRV1 -Properties SamAccountName, proxyAddresses

# Loop through each user
foreach ($user in $users) {
    # Construct the new proxy addresses
    $proxyAddress1 = "smtp:" + $user.SamAccountName + "@qpc210024.onmicrosoft.com"
    $proxyAddress2 = "SMTP:" + $user.SamAccountName + "@quinndomain.ca"

    # Add the new proxy addresses
    Set-ADUser -Identity $user.SamAccountName -Add @{proxyAddresses = $proxyAddress1, $proxyAddress2}
}
```
