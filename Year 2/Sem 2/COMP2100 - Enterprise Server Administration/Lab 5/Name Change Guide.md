# Name Change Procedure
On any domain controller `SRV1` or `SRV2`:
1. Hit the Windows button and type `Active Directory Users and Computers`, then press enter.
![[Pasted image 20240306195440.png]]

2. Find the user who's name you'd like to change. In this case it is `Test User` in the `Example OU`, which can be found on the left - in the navigation pane.
![[Pasted image 20240306202205.png]]

3. Right click the user and click `Rename`. Change the name to their new name and press enter. A window will appear that will let you easily change all the information tied to the user's name.
![[Pasted image 20240306204104.png]]

4. Change the information in the `Full name`, `First name`, `Last name`, and `User logon name` according to the user's new information and ensure the rest of the fields match properly.
![[Pasted image 20240306204245.png]]

5.  Hit `OK`. Now, to get this user's name updated to the cloud, navigate to `SRV2` if not already there. This domain controller has Azure AD Connect installed on it and can be used to push changes to the cloud. Next, click the Windows button, then type `PowerShell`. Be sure to right click on PowerShell and click `Run as administrator`.
![[Pasted image 20240306200539.png]]

6. Now, type `Start-ADSyncSyncCycle -PolicyType Initial` and hit enter to push all the changes that were made up to the cloud.
![[Pasted image 20240306201218.png]]

7. Now, if we go to `admin.microsoft.com` and sign in with an admin user, we can see the updated `Another Test` in the cloud.
![[Pasted image 20240306204551.png]]
Note: The other users have been edited out for privacy.