goal of imaging and deployment -> if the time it takes to setup a new device is minimal, the device is basically disposable

  

**What is it?**

- process of installing a pre-configured OS (all drivers, apps, settings,)
- reduce workload on the it staff
- allows faster turnaround of new systems
- allows quick refreshes of faulty systems

  

**Image -** file that contains the OS (.iso, .img, .wim)

  

Multiple Images can exist next to each other

- depending on drivers (AMD, Intel, etc.)
- different software (accounting, engineering, etc.)
- different OS (server, desktop)

  

Gold Image - common "factory default" image from a company

  

**Deployment -** the process of installing an image onto a piece of hardware, or VM

- can be done from a USB, CD, or most commonly **network**
    
    - ****need DHCP**, DNS needs to work too, physical infrastructure**
- requires extra infrastructure to enable

  

2 main deployment methods: Image based and orchestration based

- **Image based:** capture a specific state and save it, then deploy - quicker, easier
- **Orchestration based:** applies a series of steps to modify an existing OS - more customizable, more setup
  

  

**Why?**

for IT team:

- minimizes mistakes (we're human)
- save time vs manual installs
- allow quick turn around of re-installing OSes

  

for End Users:

- standard environments, less learning curve
- minimize interruption of users

  

**Deployment Strategies:**

High-Touch:

- manual deployment, you run installer yourself

Lite-Touch, High-Volume Deployment:

- limited interaction during deployment, basically you need to click start

Zero-Touch, High-Volume Deployment:

- requires no interaction, fully automated process (through system center configuration manager)
  

  

**Deploying an Enterprise Workstation: (image)**

1. Build a deployment share
2. location on the network that holds your images, accessible to the workstation
3. perform a reference computer installation
4. setup a pc or VM to be the gold image
5. capture an image of reference computer
6. software will create an **image** of that reference computer
7. boot the target computers
8. turn the PCs that are getting deployed to on
9. apply the windows 10 reference computer image
  

  

**Image types:**

Thick Image

- everything is on reference PC, and included in capture

Thin image

- minimum installed on the reference PC, other items are installed after deployment (orchestration)

Hybrid:

- install a baseline, but some people need some more software - this is how you do it

  

Deployment Tools (1st party):

- Windows Deployment Services (WDS) - server role, network and file sharing, Lite-Touch deployments
- Microsoft Deployment Toolkit - extends WDS and allows some orchestration
  

  

**Windows Deployment Services (WDS)**

- server role in server 2016+
- used to deploy images over network rather than in person
- DHCP is required
- Pre-Boot Execution Environment (PXE) must be supported across infrastructure - both server & end device

  

**Microsoft Deployment Toolkit (MDT)**

- requires Win10 ADK to function for deployments
- creates **Task Sequences** for automation
- Tasks can be before or after installation (partition drives, inject drivers, install apps, etc.)

  

MDT Ex.

- gather info (hardware, type of CPU)
- partition and format drive
- inject drivers
- apply OS
- windows update
- install apps

  

**Windows 10 ADK**

- customize existing Windows Images
    
    - WinPE, sysprep, etc to do that
- WinPE is a mini OS used to install, deploy and repair windows Oses
- also can be used to capture windows images
- can help testing performance
  
- has a bunch of pre installation, and management stuff on it (comes with windows)

  
  

**Capturing Images**

- manual or automatic
- simple or complex
- one single image
- one image per department

  

**Capturing using WDS**

- automates capture process
- wizard-based
- create capture image and upload to WDS server
- can be deployed immediately

  

**Deployment Image Servicing and Management (DISM.exe)**

used to modify image files while offline

- add drivers
- languages
- packaged updates
- enable or disable OS features
- append a volume image to a workstation image
- combine multiple images in a single Windows Imaging File

  

**Deploying Images Using WDS**

- any image can be uploaded to WDS (regardless to deployment method) and deployed (needs boot image, WinPE)
- Multicast with WDS (aka deploying to many things at once)
  

  

**Deployment Images Using MDT**

- some overhead is required
- add images to deployment share
- create **task sequences** to apply images to target computers
- multiple sequences can be created as needed
- sequences can be simple or complex
- more complex = more work

  

**Performing a Lite-Touch Deployment**

with WDS

- boot computer, specifying a network boot
- select the correct image to be installed
- more interaction may be required depending on the OS

with MDT

- Boot the computer
- run deployment wizard
- select task sequence
- more interaction may be required depending on sequence

Less interaction = more preparation for deployment

  

**System Center Configuration Manager** **(SCCM)**

- required for Zero-Touch installation
- complex
- can be used to capture and deploy image files in the same basic sequence as LTI (?)
- SCCM tools instead of Deployment Workbench

  

- only use this product for deployment if you are already using it
- huge pain in the ass and very complex
- stores data in SQL database
- requires client agent on each computer it manages
- very expensive but powerful

  

**Common Issues**

- networking - need **DNS, DHCP,** and support for **PXE booting**

drivers - not a problem for VMs but for stuff with different hardware :/

- need to keep images up to date (windows updates, driver updates, etc.)