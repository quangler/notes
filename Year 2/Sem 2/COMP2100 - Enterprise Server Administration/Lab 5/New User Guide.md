# New user creation - including UPN

On any domain controller `SRV1` or `SRV2`:
1. Hit the Windows button and type `Active Directory Users and Computers`, then press enter.
![[Pasted image 20240306195440.png]]

2. Navigate to the folder or organizational unit (on the left side of the screen) that you wish to make the user in.
![[Pasted image 20240306195602.png]]

3. To the right of the navigation pane, right click on an empty area. Click `New` and then click `User`. 
![[Pasted image 20240306195817.png]]

4. Here is where you can type the user's information in such as `First name`, `Last name`, their `User Principal Name (UPN)` - the name they should login with, and `domain`.
![[Pasted image 20240306195946.png]]

5. As an example, `TestUser@quinndomain.ca` was created. The domain was switched to `@quinndomain.ca` instead of `@brunsco.sf` to keep with the scheme of the company. Hit next at the bottom.
![[Pasted image 20240306200053.png]]

6. Next, you need to give the user a `Password`. Be sure to check `User must change password at next logon` to keep their account secure. Hit next at the bottom, then when prompted and the account info looks right, hit finish.
![[Pasted image 20240306201343.png]]

7. To get this new user synced to the cloud, navigate to `SRV2` if not already there, as this is the domain controller that has Azure AD Connect installed, and can be used to push changes to the cloud. Click the Windows button, then type `PowerShell`. Be sure to right click on PowerShell and click `Run as administrator`.
![[Pasted image 20240306200539.png]]

8. Now, type `Start-ADSyncSyncCycle -PolicyType Initial` and hit enter to push all the changes that were made up to the cloud.
![[Pasted image 20240306201218.png]]

9. Now, if we go to `admin.microsoft.com` and sign in with an admin user, we can see the brand new `Test User` in the cloud.
![[Pasted image 20240306201852.png]]
Note: The other users have been edited out for privacy.
