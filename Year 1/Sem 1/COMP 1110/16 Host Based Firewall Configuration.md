in Linux, the subsytem that handles network filtering is called **netfilter**

you can either use iptables, or firewalld (we use firewalld)

  

firewall-config (GUI)

firewall-cmd (CLI)

  

firewalld is the service/daemon

  

firewalld uses seven predefined zones to classify network traffic (you can add some)

  

'firewall-cmd --get-zones' - shows the zones you currently have

  

'firewall-cmd --get-default-zone' - shows what the default zone is

  

'firewall-cmd --info-zone public' - shows info on public

(services that are listed are allowed)

('firewall-cmd --list-all-zones' for info on all zones)

  

'firewall-cmd --get-services' - shows hella services

  

to add or deny a service:

'sudo firewall-cmd --remove-service <servicename>'

'sudo firewall-cmd --add-service <servicename>'

  

if you know the port number and want to allow it:

'sudo firewall-cmd -add-port=<portnumber>/<protocol>'

ex.

'sudo firewall-cmd -add-port=8080/tcp'

  

UDP - just throws shit until it sticks

TCP - needs a direct connection

  

Runtime vs Permanent

runtime - like running config, immediately works but doesnt hold over restart

need to add **--permanent** to make it persist after restart

- this will not affect your runtime config

  

to make your running config stick

**'sudo firewall-cmd --runtime-to-permanent'**