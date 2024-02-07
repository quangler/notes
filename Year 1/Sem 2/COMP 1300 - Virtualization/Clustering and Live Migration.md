IT Needs:

- always on and always available

- no single point of failure for business critical infrastructure

- redundancy - if a host (or node) fails, another host can pickup its job

  

**Windows Failover Clustering**

- a group of nodes (hosts) that work together as a single logical unit

- connected together via physical means as well as via software or at application layer

- if one or more node fails, another node in the cluster picks up the application, service, or role of the failed node

  

**How does it work?**

- constant queries the failover nodes to ensure they are healthy, alive, and working properly

- also called a "heartbeat"

  

**Prerequisites and Requirements**

- same version of windows server for all failover cluster nodes (not absolutely necessary but try to keep it the same)

- servers with the same or similar hardware configurations

- shared storage, via SAN with iSCSI and NFS targets

  

**Quorum**

- the number of failures that a cluster can support in order to keep working

- once the threshold is reached, the cluster stops working

  

- if you have two nodes, and one goes down, then comes back up later (assuming you don't have quorum setup) it can be reallllly bad

- causes "split-brain" - this can cause data corruption

- a quorum doesn't let this happen

  

Best practice is to use 3 nodes in a failover cluster (that way if one fails it's still working)

  

**Hyper-V Live Migration**

- windows failover clustering to live migrate VMs in Hyper-V

requirements for Hyper-V live migration without failover clustering:

- hosts have to be the same operating system

- both the source and destination servers must be in same domain

- source and destination Hyper-V hosts must be connected by a reliable network