Why backup?

- Data integrity - corruption, deletion etc.

- Data archival - legal requirements

- Disaster recovery - in case things go south

  

How?

- windows backup feature

- virtual RAID on the server (not backups, just redundant)

- data backup when requested

  

Backup Types:

- Full backups - slow and take a lot of space, easier to recover

- Incremental - fast and not as much space, harder to recover

  

Media Types:

- tapes

- usb drives

- NAS - small, has its own IP, can directly connect

- SAN - block level storage, can't connect to it directly (would be the iSCSI target)

- cloud - free to put into cloud, costs to get it back (quicker = more expensive)

  

**Enterprise Backups - Terminology**

- on-site, local, on-prem

> storage is physically in the same place/network as the items being backed up

> you **own this hardware**

  

- off-site, remote, off-prem

> storage is physically **separated** from items being backed up

> **may** own the hardware (cloud you don't, but you could have a different site that has your "off-site" backups_

  

**Considerations:**

- price, reliability, speed to restore (pick 2)

- businesses will be using VMs - take a backup of the whole hypervisor or each individual VM?

- machine based or drive based is usually faster than file based.

  

**Enterprise Backups**

The 'default' nowadays is combining on-site and remote backups.

- on-site - running often, restore quickly, lower costs.

- remote - copies off-site in case of disaster, scale with long-term storage needs, synced from the on-site copies

> on-site is more often than off-site.

  

**Enterprise Media Types**

- NAS is the most common

- Tape is rare, but can be used in medical for really long archiving

- USB can be used as a physical "link" for off-site backup (drive to the off-site with the drive)

  

**Enterprise NAS or SAN**

- Manageable over the network.

- variable storage (can be a little or a lot)

- RAID for redundancy (not backup)

- network connection allows versatile operations

  

**How often do we need to run backups?**

- it depends.

- money talks, they make the decisions.

- for mission critical things, more often (maybe hourly), for something less important maybe like every 6 hours.

**- Frequency depends on need.**

- possibly every 15 mins, possibly every day.

- this means we use incremental backups, not full (that is just super overkill).

  

**Enterprise Backups - The Chain** #important

**- Incremental Backups**

- looks at the previous backup file, then captures the **CHANGES**.

- it only looks back to the **BACKUP BEFORE**

  

**- Incremental Backups**

- recovery process considers the whole chain back to the first backup.

- allows for point-in-time recovery - meaning you can start at any part of the chain

- smaller individual files are easier to upload and to recover.

  

**- if one of the incremental backups gets broken, everything after is gone.**

  

**- The "chain" of backups requires management.**

- common option is "consolidation"

- whole chain can be compressed down to a single file. (hourly becomes daily, daily becomes weekly, etc.)

  

**Consolidation:**

**-** more files = more points of failure, this minimizes it.

- helps preserve space on storage destination

- increase speed of recovery - doesn't have to go through 30 daily files, could be just 4 weekly files.

  

**What we have so far**

- backing up each server individually

- multiple files per day per server

- storing data on local NAS

- data is a chain of files

- the whole chain is referenced as a single unit for recovery

- complexity increases exponentially as our environment grows

- we use software to handle it!

  

**Enterprise Backup Solutions**

- software helps with overhead:

> timing for when backups run

> location backups are saved

> location backups are uploaded

> consolidation

> error checking

> recovery options

  

**Software can be:**

- Agent based, agentless, or both

- centrally controlled

- sold with an appliance, or use your own NAS

(nomenclature changes between vendors)

  

Generally,

- each server has their own backup settings, schedule, etc.

(this is called a **backup job**)

- the jobs create a chain of backup files

- each chain is then managed separately from each other

- each job can be set up independently as needed

  

**We will use ShadowProtect SPX**

3 main portions:

- the agent

- the controller

- image manager

- we are using a virtual NAS to store backups

  

**Agent - endpoint**

- installed to every server you want to back up

- controls processing jobs according to job settings,

- runs a handful of services

  

**Console - centralized**

- used to configure and check jobs

- set target disks backup destination, type and frequency

- check health of job

- see status of job

- only one of these needs to be installed

  

**Image Manager**

- service used to protect your chains

- **Required** for incremental backups

- one per environment

- automates verifying and consolidating your chains

- helps synchronize offsite backups

- recommend a dedicated VM to run this service.

  

**a note on other tools:**

- shadowprotect breaks out into 3 tools,

- other vendors could have it all in one, or less tools.

  

**a note on performance**

Network Traffic

- don't backup things all at the same time maybe (it could just murder your network every hour or whatever)

  

**A note on automation**

**CHECK EVERYTHING MANUALLY** #important

- regardless of software choice, most of the process is automated

- automation is not perfect

- backups could be failing and you wouldn't know.

**ALWAYS CHECK BY HAND.**

  

**A note on security**

- a copy of your entire environment is on your NAS. don't lose it.

- physical security is important.

- backups should be encrypted. (password protected)

  

**a note on encryption**

- **backups should be immutable**

> cannot be changed after they are written

> use separate credentials for everything

> NAS should not be Domain Based, should be unique

> if possible, separate VLAN