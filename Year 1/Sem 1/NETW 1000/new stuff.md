![Exported image](Exported%20image%2020240206202408-0.png) ![Exported image](Exported%20image%2020240206202408-1.png)

SPAN

DHCP

SSH

requirements:

- hostname
- ip address
- enable secret

  

1. s1 (config)# 'username admin password cisco'

  

local domain:

1. 'ip domain-name bubba.local'

  

encryption keys:

1. 'crypto key generator rsa'
    
    1. '1024'

  

1. 'ip ssh version 2'
  

  
![Exported image](Exported%20image%2020240206202408-2.png)  
  

1. 'ssh -l admin 192.168.1.100'

![Exported image](Exported%20image%2020240206202408-3.png)

  
  
  
  

![Exported image](Exported%20image%2020240206202408-4.png)