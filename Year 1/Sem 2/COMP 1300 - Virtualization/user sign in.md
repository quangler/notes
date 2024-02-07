to let a user sign in with AD DS credentials:

- menu > administration > single sign on > configuration > active directory domain
- join AD - domain: comp1300.local | organization unit (for admin account being in OU) | username: firstnameAdmin(bestpractice) | password: P@ssw0rd
- gotta restart vCenter :/ (do it from ESXi menu, then hit restart :)
- still gotta sign in with administrator@vsphere.local account
- add identity source > use machine account
- ~~right click on 'vcsa.comp1300.local' > add permission >~~ menu > administration > global permissions > plus > make sure is domain comp1300.local >firstnameAdmin as administrator > CHECK PROPOGATE TO CHILDREN (inheritance)
- firstnameAdmin@comp1300.local P@ssw0rd for new login!
- logging in with DC01 > caches user (must have signed in before hand)