Windows tools

- computer management
- GPresult
- ipconfig
- nslookup
- traceroute
- systeminfo
- tasklist / taskkill

  

computer management

- compmgmt.msc
- gives you access to a bunch o utilities

  

ipconfig

- /all
- i know what this is

  

nslookup

- easy to figure out IPs (if you have dns)

  

traceroute

- shows you hops between source and target
- **we should use this more often**
  

  

systeminfo

- returns info about PC
- 'systeminfo'
- /s <computer> /u <domain>\<username> /p <password>
- /fo - formats the results as table, list, csv

  

tasklist

- displays running processes
- /s - goes to another PC | /fo - format | /fi - filter

  

taskkill

- /s - go to another computer, /fi - filter, /pid - the PID you want to kill, /im - to kill by name
- ex. taskkill /pid 2001
  

  

GPResult

- /r - displays the RSoP summary data
- /z - displays ALL info
- /v - verbose
- /scope:
  

  

IP/Port scanner

- can scan for open IP addresses
- can also scan for open ports (which is kinda dangerous)
- can generate a shit load of generate a ton of network traffic

  

disk health checks

- power-on hours, temp, SMART checks
- (read error rate, spin up time, start/stop count, power on hours, disk shift + more)

  

Email header analyzer

- check if an email is spam
- the header gives you all info you need > header analyzer gives you nice info

  

Storage Scanner

- shows file storage (what things are taking up space)
- break it down by location, size, and folder type
- WizTree or TreeSizeFree

  

MSRA (Microsoft Support and Recovery Assistant)

- can do advance diagnostic of office and windows 10 config problems
- detailed reports
- auto fix common issues

  

Remote connectivity analyzer

- web resources by MS to check connectivity to exchange or 365 servers
- for fixing mail problems
- IMAP or POP checker
- check SSO issues
- can check Exchange active sync

  

ForensIT

- tool that migrates user profiles
- capture profile as a zip file > extract it to a target PC
-