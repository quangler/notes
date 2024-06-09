Data can be stored in either:

Analog - (hard drives, CDs)

Or Digital - (SSD, NVME, RAM)

  

Digital or Analog **data** can be converted into Digital **signal.** There are two ways of doing it:

Line Coding: necessary for all communications, stored as a series of 1s and 0s. Discreet signal

Block Coding: optional

  

**Line Coding:**

Three types:

- **Uni-Polar Encoding (unipolar-non-return-to-zero)** - use a single voltage level to represent data.

Uses a binary system: 1 = high voltage, 0 = no voltage

  
  
  
  
  
  
  
  

- **Polar Encoding** - uses multiple voltage levels to represent binary values

Available in 4 types:

- **Polar Non-Return to Zero (Polar NRZ)** - two voltage levels to represent binary

Usually negative and positive, NOT ZERO.

**NRZ-L** - _1 is positive and 0 is negative_

**NRZ-I** - _swaps every time it sees a 1_

  
  
  
  
  
  
  
  
  

- **Return to Zero (RZ)** - uses THREE voltage levels. (signal is self-clocking)

+ = 1, - = 0, 0 = none

Goes to value then returns to zero before moving on

  
  
  
  
  
  
  
  
  
  
  

- **Manchester** - combination of RZ and NRZ-L, bit time is divided into two halves.

Left side positive is 0, right side positive is 1

0 is low to high, 1 is high to low

  
  
  
  
  
  
  
  
  
  
  
  
  

- **Differential Manchester** - combination of RZ and NRZ-I, also transits in the middle, but changes phase only when a 1 is encountered.

Left side positive is 0 OR 1 if previous bit was a 1. Right side positive is 1.

  

1 starts **low to high**, then **swaps** to **high to low** each 1

0 is always **high to low**

  
  
  
  
  
  
  
  
  
  
  
  
  

- **Bipolar Encoding** - uses THREE voltage levels.

Zero voltage represents 0

1 bit is represented by alternating positive and negative

![Exported image](Notes/!%20Images/!%20Pre%20Grad/AC%20Power.md/Exported%20image%2020240207094509-0.png)

On test, have to identify if it is digital to digital or not

![Exported image](Notes/!%20Images/!%20Pre%20Grad/AC%20Power.md/Exported%20image%2020240207094509-1.png)

**NRZ-L vs NRZ-I**

![Exported image](Notes/!%20Images/!%20Pre%20Grad/AC%20Power.md/Exported%20image%2020240207094509-2.png)

**Return to Zero (RZ)**

![Exported image](Notes/!%20Images/!%20Pre%20Grad/AC%20Power.md/Exported%20image%2020240207094509-3.png)

**Manchester**

![Exported image](Notes/!%20Images/!%20Pre%20Grad/AC%20Power.md/Exported%20image%2020240207094509-4.png)

**Differential Manchester**

![Exported image](Notes/!%20Images/!%20Pre%20Grad/AC%20Power.md/Exported%20image%2020240207094509-5.png)

**Bipolar Encoding**