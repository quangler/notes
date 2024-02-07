test: will have 5 routers

  

- IPv6 only - auto-configuration where the client gets an IP from the router network

  
  

**R1:**

  

en

conf t

  

ipv6 unicast-routing - this allows you to use IPv6

  

int g0/0

ipv6 enable - enables ipv6 on the interface

ipv6 address 2620:FC:1::1/64 -

do show ipv6 int g0/0

  

ipv6 address FE80::1 link-local

no shut

  

**S1:**

en

sho flash - check to see if you are using version 15

**to enable ipv6 on a switch:** #important

sdm prefer dual-ipv4-and-ipv6 default

**to go back to only ipv4 on a switch:**

sdm prefer default

en

conf t

int vlan 1

ipv6 enable

ipv6 address autoconfig

no shut

  

show ipv6 interface vlan 1

ip should now be on there??

  

**R1:**

int g0/1

ipv6 enable

ipv6 address FE80::1 link-local

ipv6 address 2001:db8:1::1/64

no shut

  

exit

ipv6 route 2620:FC:2::/64 g0/1 2001:db8:1::2

  
  

**R2:**

en

conf t

ipv6 unicast-routing

int g0/0

ipv6 enable

ipv6 address FE80::2 link-local

  

ipv6 address 2620:FC:2::1/64

no shut

  
  

**S2:**

en

conf t

sdm prefer dual-ipv4-and-ipv6 default

reload

int vlan 1

ipv6 enable

ipv6 address autoconfig

no shut

  

**R2:**

int g0/1

ipv6 enable

ipv6 address FE80::2 link-local

ipv6 address 2001:DB8:1::2/64

no shut

  

ipv6 route ::/0 g0/1 2001:DB8:1::1

  
  

**PC1 should now be able to ping PC2** #important

  
  

**R3:**

en

conf t

ipv6 unicast-routing

int g0/0

ipv6 enable

ipv6 address FE80::3 link-local

ipv6 address 2620:FC:3::1/64

no shut

  
  

**S3: - only difference is you don't need to enable it globally (like on layer 2 switch)**

en

conf t

int vlan 1

ipv6 enable

ipv6 address autoconfig

  

terry likes to do global unicast first because:

- common practice for default gateway is ::1
- it automatically sets it to the EUC-64 ID
- if the link-local address is made first, the global unicast takes from the link-local address