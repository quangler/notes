**Dynamic Memory**

  

Startup RAM - ram assigned to vm during startup

  

Minimum RAM - minimum amount of RAM that the host will try to assign to a VM. Hyper-V can reallocate RAM away from VMs until minimum RAM value is met

  

Maximum RAM - max amount of RAM that the host provides a VM

  

Memory Buffer - the % of memory that Hyper-V should allocate to the VM as a buffer in case the VM demands for more memory

  

Memory Weight - priority set for this VM compared to other VMs

  

**CPU Settings**

  

Virtual machine reserve % - amount of CPU's power reserved for this VM, and therefore always available.

  

Virtual machine limit % - maximum amount of processor power that the VM can use. In times of CPU contention, the VM may not get a full 100%.

  

Relative Weight - when there contention for your CPU resources, the weight value determines the importance of a VM getting shares of CPU time. VM with a weight of 200 would get twice as many CPU cycles as a VM with a weight of 100.

  

**Virtual Hard Drives**

  

Fixed Size - creates a file that is a solid size of drive, wont change

Dynamically Expanding - created small, expands as it data is changed

Differencing - linked clone