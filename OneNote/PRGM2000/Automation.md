automation includes some form of:

- remote-control
- multitasking
- monitoring

  

**WS-MAN (web services for management)**

- operates over HTTP/HTTPS
- uses background service "Windows Remote Management" (WinRM)
- WinRM is installed with PS2 or higher
- **started by default** on windows server 2008 or higher
- also installed on most workstations but **disabled by default**

to convert the output from remote commands to be transferred over the network you need to serialize it

- to do this we convert the information to an XML format
- then when it is at its destination we must deserialize it back into an object
- ^ this means that the information is not real time

requirements:

- windows powershell v2 or higher
- ideally they are both domain joined
- allow WMI rule through firewall (in and out)

**to enable WinRM for remoting in on clients:**

**"Enable-PSRemoting"**

could also do it through a GPO (computer config>admin template> windows components)

  

**Enter-PSSession** - less resource intensive RDP | passes through your user credentials

  

PowerShell uses remoting in 2 ways:

one-to-one:

- "Enter-PSSession -computername Server01" - remotes into server01
- "Exit-PSSession" ( or close PS window)

  

one-to-many:

- "Invoke-Command" - sends a command to multiple remote computers **at the same time**
- by default, PS can talk to up to 32 computers at once; if you ask for more it will queue computers up
- if you want to increase the limit for remote PCs, you can use "-throttleLimit"

**Invoke-Command -command {<code here>}**

**- computerName (Get-Content <path to list of computers.txt>)**

  

Get-Content outputs a string which is what -computerName needs;

Get-ADComputer returns objects which -computerName won't know understand

  

WMI is the older version of CMI, it works on more devices and is designed for older servers.

**Get-WMIObject -list** | shows all classes that you can use

Get-WMIObject -Namespace root\CIMv2 -list | where name -like "*dis*"

  

CMI doesn't have a list, but it has:

get-Cimclass -namespace root\CIMv2

  

if you want to use credentials for remote computers with CIM: (??)

Get-CimInstance via Invoke-Command

**invoke-command -scriptblock {Get-CimInstance -ClassName win32_logicaldisk} -computername server-1 -credential DOMAIN\Administrator**

  
  

**Managing Background Jobs**:

help *job

- background jobs are commands that run separately in the background
- **background jobs don't give you errors which is no good** #important
- have to decide if you want to run a job in the background **before** you run the command

  

synchronously / real-time: run a command and you wait for the command to complete

asynchronously / background: run a job in the background and continue to use the shell to do other jobs

  

**TEST YOUR COMMAND BEFORE YOU SET IT TO A BACKGROUND JOB** #important

  

how to create a job:

**Start-Job -ScriptBlock {<code>}**

or

**Start-Job -Command ()**

  

-name | allows you to specify the name of the job

-credential | asks for credentials to run command

  

**Get-Job** - all this does is shows you the status of the jobs that have run or are running

Get-Job | Format-List - this shows you more information about the job itself (not the data)

the property "HasMoreData" being true means you can view the data #important

  

**remove-job** - gets rid of the job in get-job

**stop-job** - terminates the job

**wait-job** - forces shell to stop and wait until job is completed, then allows the shell to continue

  

**Receive-Job [<name/ID>]** - this is how to view the data that the command has obtained

- if you want to view the results more than one you have to use **-Keep (you have to type it every time you want to view it)**, otherwise its viewable only once (stored in cache)

  

To make a command act in the background:

add a **-AsJob** parameter

  

ex: **Get-WMIObject win32_operatingsystem -computerName (get-content computernames.txt) -asjob**

or: **invoke-command -computername localhost -scriptblock {get-process} -asjob -jobname testing1**

  

**Scheduling tasks:**

**New-JobTrigger** - used to schedule a job by creating a trigger that activates a task

**New-ScheduledTaskOption** - use to set options for the job

**Register-ScheduledJob** - used to register the job with task scheduler; creates job definition in task scheduler's XML format - creates folder hierarchy to hold results

  

**Register-ScheduledJob -Name DailyProcList -ScriptBlock {Get-Process} -Trigger (New-JobTrigger -Daily -At 2am) -ScheduledJobOption (New-ScheduledJobOption -WakeToRun -RunElevated)**