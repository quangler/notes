
---
## ADFS Configuration
ADFS is setup on its own server that has the IP of `172.30.0.20`.
The domain address for SSO is `https://adfs.quinn.local/adfs/ls/idpinitiatedSignOn.aspx` for the `quinn.local` domain.
There is a trust setup between `quinn.local` and `mattt.lan` through ADFS. The settings used to achieve this are the following:
#### Claims Provider Trusts
There is `Active Directory` and `Mattt Corp` in this section.
`Active Directory` has automatically been added and no modifications have been made to it.
##### Mattt Corp
###### Identifiers:
Display name: `Mattt Corp`
Claims provider identifier: `https://adfs.mattt.lan/adfs/services/trust`
###### Certificates:
There is an imported certificate from the `mattt.lan` Root CA.
###### Endpoints:
The `WS-Federation Passive Endpoints` category has the following URL:
- `https://adfs.mattt.lan/adfs/ls` with binding being `redirect`, and default being `yes`.
#### Relying Party Trusts
Within relying party trusts there is only one category: `MatttCorp`
###### Identifiers:
Display name: `MatttCorp`
Relying party identifiers: `https://adfs.mattt.lan/adfs/ls` and `https://adfs.mattt.lan/MatttCorp`
###### Encryption:
This trust is using the certificate that was imported from the `mattt.lan` Root CA for encryption.

## CA Configuration
The Certification Authority service is installed on the ADFS server as an Enterprise Root CA.
The CA is named `quinn-ADFS-CA` and the certificate is configured with `SHA256` as the encryption algorithm.
A certificate for the partner domain `mattt.lan` was also needed. This was acquired from the `mattt.lan` CA, which was also installed on the ADFS server on that domain.
The `quinn.local` Root CA's certificate was also given to the `mattt.lan` ADFS to allow for trust.