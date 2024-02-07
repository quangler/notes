each print job - "a click"

- these jobs have a price for maintenance

  

Why use a print server?

- Centralized administration
- security permissions - can lock down printers so not just everyone can print
- managing printers - if there is a stuck document, you can change the order
- driver updates - don't have to update a ton of computers > just update the server
- setting defaults - ex. black and white, plain paper etc.
- job prioritization - if someone needs printing done immediately > they can skip the queue and print
- without a server, the print device might get overwhelmed by many users requesting a print

  

Print server:

- install role "print and document services"
    
    - internet printing
- Print Management MMC
- Need to add print server to DC1 (print management)
- can use RSAT for this

  

Connecting to the printer downloads drivers/properties/network location info

  

Sharing:

- Sharing a printer is simpler than sharing a file
    
    - no share permissions list
    - searchable in active directory

  

Ports:

- Physical or logical connections to print devices - TCP/IP
    
    - can move queue from one printer to another in case of a malfunction
- Print Pooling - a single printer (driver) that is connected to multiple print devices
    
    - check multiple ports - distributes it to the multiple print devices, it will go into the next available device

  

Printer Properties

- Print Priority
    
    - multiple printers (driver) pointing to a single print device
    - can set priorities so things can cut the queue - 1 is default - 99 is highest
      
    
- Security
    
    - similar to NTFS permissions (AGDLP still applies here)
    - print - default, allows people to print (everyone - cancel/pause/resume their own documents)
    - manage documents - allows someone to clear queue or single documents in it (head of group - do it all)
    - manage printers - settings of the printers (IT group - manage properties of printer)
      
    

  
  

Internet Printing Protocol (IPP)

- IPP can print to a uniform resource locator (URL) over internet via HTTP
    
    - you can also install a printer from the internet