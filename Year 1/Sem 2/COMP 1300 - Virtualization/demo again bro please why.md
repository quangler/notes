- add 120 gb drives to your ESXi01
- turn dc on again, might have to restart vCenter server

  

go to storage > datastores:

- wanna expand the size of the disk?
- click increase capacity of datastore, > expand datastore (2nd guy)

if drives dont show up....

- storage > devices > should show the drives ? > expand storage drive, add the whole drive and shit
- if that doesnt work gg restart esxi and add drives again loser
  

  

could also create a new datastore > this will see the disks maybe ?????????????? god i dont know

  

^^^^ all from inside of ESXi ^^^^

  

now we on vcenter >:)

- make sure the names of your datastores are good, otherwise youre gonna be sorry mister
- select a datastore > actions > increase datastore capacity --- vcenter wont let you do this because it would be reaaaal bad if you could
- however, you can create new datastores from scratch !
- storage > new datastore > wizard and shit

just use the lab - stopped paying attention