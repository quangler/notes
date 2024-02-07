Azure compute is the on-demand service running cloud apps.

Azure compute provides you with: (basically a VM)

- disks
- processors
- memory
- networking
- OS - linux, windows, SQL server, oracle, IBM, and SAP

pay as you go

  

**4 Main service handled by Azure compute:**

**Azure VMs:**

- functions just like regular VMs
- created in cloud vs on prem
- cloud based VMs provide IaaS
- can remote in

Designed for scale,

- machine scale sets are a form of templating but are **groups of identical VMs**
- easy templates to setup
- easy to tear down
- auto scaling or manual control by admins

  

**Azure Containers:**

- Container Instances are Azure Kubernetes Service that allows you to deploy and manage containers in Azure

Containers:

- packages of application code, their dependencies, and libraries required for the application to function.
- typically designed to be run without an OS
- container runtimes sit on top of an operating system in which containers run
- basically hypervisor but no guest OS

  

Kubernetes:

- opensource platform allowing admins to manage containerized workloads/services

  

**Azure App Services:**

- allows for building and deployment of web, mobile, and API applications on any platform.
- app services can quickly scale as demand needs
- app services function as PaaS
- organizations can still control security and compliance requirements even if they are running serverless
  

  

**Azure Functions:**

- allow developers to run code directly without need of an underlying platform/infrastructure
- typically event-driven snippets of code that need to run when triggered

  

**When to use VMs?**

- need total control over OS
- need ability to run custom software
- need custom hosting configs
- (disaster recover scenarios)

  

**When to use VM scale sets?**

- when you need to setup infrastructures infrequently, but don't want to do it all by hand (construction, training, olympics, elections)
- lets you group identical, load-balanced VM's - similar to clustering.
- use when total control over application servers is needed with scalability
- centralized management allows you to manage, configure, and update a large set of VMs in minutes.
- scaling can be determined automatically or schedule based.

  

**When to use Containers / Kubernetes?**

- containers are great for splitting application components
- containers allow admins/devs to scale individual components up and down as needed.

  

example:

- webpages for Ecommerce
- traditionally webpages have front-end, back-end, and storage components
- the components can be on one server, or multiple servers
- can be broken down into 3 separate containers:
    
    - front end container
    - back end container
    - storage container

  

**When to use functions?**

- functions are best used for infrequent or event-driven computer processing
- applications that are event-driven running on VMs / platforms could be wasting money by sitting idle
- functions allow for portions of those applications that would be sitting idle to only run when needed, without a platform or infrastructure
- referred to as serverless computing

  

**When to use Azure Virtual Desktops?**

- cover RDS/VDI next semester in more detail
- centralized management of remote resources as needed
- platform / OS agnostic application deployment (no OS)
- secured access to remote resource (less data loss vulnerability)
- expanded on-prem VDI scalability / Hybrid VDI deployments
- things to note about Azure VDI
    
    - simplified management
    - performance management
    - multi-session win 10 deployments