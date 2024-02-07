Port Security - used to restrict input to interface by only allowing specific MAC addresses to the switch port

- config#'switchport port-security'
  
- config#'switchport port-security maximum [# of MAC addresses]' #important

  

*MINIMUM OF 3 PORT FOR VOIP* (OPTIONAL) (least you can have for max is 3 for us because cisco and stuff)

  

  
- config#'switchport port-security mac-address sticky' #important

learns MAC addresses (up to max) to lock down switch port

remove sticky to manually do MAC addresses

  

  
- config#'switchport port-security violation [<protect> | <restrict> | <shutdown>]'

(OPTIONAL, DEFAULT TO SHUTDOWN)

- protect - don't allow the MAC address through, leave the interface up
- restrict - don't allow that MAC address through, leave the interface up , but store as a LOG
- shutdown - if a violation occurs, 'err-disabled' aka shut that bitch DOWN (and log event) [MUST BE SHUTDOWN THEN BROUGHT BACK UP TO FIX]

  
  

- 'show port-security interface {interface type/number}'

Port Security Settings

  

- 'show port-security address'

secure MAC address

  

Config Guidelines:

- secure port cannot be destination port for SPAN (can't be done on a trunk)
- a secure port cannot be a part of EtherChannel (can't be on a trunk)
- when switchport is a member of Voice VLAN, ensure max is AT LEAST 2 (3 for us)