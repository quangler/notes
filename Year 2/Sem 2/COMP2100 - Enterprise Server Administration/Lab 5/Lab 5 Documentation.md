## Decommissioning of Servers
On February 14 2024, SRV4-7 was decommissioned in the `brunso.sf` domain.<br>Servers were removed from domain and shut down. <br>Computer accounts were removed from the Computers OU in `Users and Computers`.<br>DNS records for the decommissioned servers were removed.
## Azure AD Connect
In order to synchronize the on-prem information to the cloud, Azure AD Connect was installed on `DC2`. <br>The domain `qpc210024.onmicrosoft.com` was used for setting up the `brunsco.sf` domain to the azure environment.<br>The command: `Start-ADSyncSyncCycle -PolicyType Delta` was used to force replication from on-prem to the cloud.<br>While installing the software, the following settings were used:
- Custom install settings:
	- Use password hash sync.
	- Enable single sign-on.
	- Check continue without matching UPN suffixes.
	- Enable password writeback.
## Azure Tenant Information
| Account | Login Location | Purpose |
| ---- | ---- | ---- |
| `quinn@qpc210024.onmicrosoft.com` | `portal.office.com` | Main tenant account login |
| `adminbo@qpc210024.onmicrosoft.com` | `portal.office.com` | Barett Global Admin login |
