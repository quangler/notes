installing DNS/BIND

'sudo yum install bind-server.x86_64' or just bind i dont remember lol

  

>create DNS zone > (FW) quinn.local | (Reverse) 192.168.x

>address (A record) - add hostname of server (dont need domain in here)

>start bind (thru webmin)

>'sudo systemctl start named'

>'sudo systemctl enable named' - makes dns start on boot

>**remember**: first time install needs to change the bind config (/etc/named.conf) and add "any;" to 'listen-on port 53' and 'allow-query'

  

>should be able to dig from client (if dns is set to the dns server)

>need firewalls off (preturned off)

  

>might need to add a forwarder (8.8.8.8 or 1.1.1.1)

  

Installing DHCP

'sudo yum install -y dhcp-server.x86_64'

>webmin to manage (might have to refresh modules at bottom)

>add new subnet > network address 192.168.x.**0**

>then add the address ranges you want for DHCP

client options:

>default routers 192.168.x.254

>dns servers > whatever the dns server's ip is

>NTP server > whatever the ntp server's ip is

>server is authority for this subnet? yes (in subnet settings)

  

'sudo systemctl enable dhcpd'

  

NTP/Chrony

>'/etc/chrony.conf' - configuration

- on servers you want this to have "allow 192.168.x.0/24" and some time pools
- on clients you want the pool location to be server ('pool server.quinn.local iburst')

>'sudo chronyc sources'

>restart service when changes are made 'sudo systemctl restart chronyd'

  

>more detailed sources 'sudo chronyc sources -v'

>'timedatectl' on both server and client to check time

  

Apache:

>needs DNS to work.

'sudo yum install -y httpd'

>create virtual host > document root "/var/www/html/site1"

>site's index.html file is in /var/www/html/site1/index.html

  

>restart httpd service to confirm changes