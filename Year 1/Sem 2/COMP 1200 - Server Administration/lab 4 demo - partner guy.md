plug Vmnet 1 into Vmnet 1 for both side of partner guy

  

hosted server:

- open server manager
- change IP address to a static IP
- they can now do everything they need

  

on your DC - active directory sites and services

- make links for all your guys
- setup subnets of your guys

  

when you're promoting DC3 to AD DS

- add a new domain to an existing forest
- child domain
- parent domain > quinn.local
- child domain > parent
- create DNS delegation > check that box yo
  

  

you can use the same account you already have (firstnameAdmin)

  

AGUDLP

  

accounts

global groups

universal groups

domain local

permissions

  

users > global group "G_<name>" on all domains that it must exist

  

global group > universal group "U_<name>" on the parent domain usually (only needed once)

  

universal group > domain local "DL_<name>" on the same domain as the resource you are trying to access