- Admin shares are hidden shares (on both client and server)
- Hidden shares for every volume (C:\, D:\, etc.)
    
    - DC1 has a C$
    - DC2 has a C$ and a K$
    - AdminWS has a C$
- Hidden shares turned on by default
- Can be super useful, but increase attack surface

  

- Admin$ puts you in windows folder no matter where windows is installed
- IPC share
    
    - used for inter-process communication (communication between programs)
    - used by server service for connections to applications and services on server
- Domain Controller Shares
    
    - create two domain controller specific shares:
        
        - SYSVOL - used in replication - AD, File Replication Server(FRS) and Distributed file replication system (DFS-R)
        - SYSVOL also hold the GPOs
        - NETLOGON - mainly used to hold scripts that need to be replicated

[\\DC1\Admin$](file:///\\DC1\Admin$), [\\DC2\C$](file:///\\DC2\C$)

  

If you end any share with a $ you make it a secret share

  

Monitoring shares

- Computer Management
    
    - shared folders > sessions - tells you who
    - shared folders > open files - tells you what is open

  

You can disable admins shares through registry > DON'T on domain controller