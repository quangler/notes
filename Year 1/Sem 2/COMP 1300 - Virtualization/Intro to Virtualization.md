**Hardware Abstraction:**

- between hardware and software
- hides differences in hardware so kernal doesnt need to be changed

  

Hypervisor = HAL++:

Host - physical machine

Guest - virtual machine

  

**Virtualization vs Simulator/Emulator:**

  

Virtualization - logical computer running on physical computer (act like a normal computer)

  

Simulation/Emulator - imitation of actual process, hardware/software that enables one device (host) to behave like another (client)

  

Type 1 (bare metal):

hypervisor runs without underlying OS

  

{

multiple OS's

hypervisor

hardware

}

  

Type 2:

application that requires a host OS

  

{

multiple OS's

hypervisor

OS kernal

hardware abstraction layer (HAL)

hardware

}

  

**Why use Virtualization?**

- only have 1 physical server to worry about
- way faster to do stuff (gold images and whatnot)
- training is realistic and way cheaper (cant break anything)
- testing/sandbox
- safety/security
  

  

**Nested Virtualization:**

  

"Virtualize Intel VT-x/EPT or AMD-V/RVI" enable for hyper-v or ESXi (makes nesting work)