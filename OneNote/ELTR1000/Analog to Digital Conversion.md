> [!caution] This page contained a drawing which was not converted.   

What is a signal - voltage that is changing over time

- analog can vary **infinitely**
- digital is on or off (think binary)

  

analog signal - like the real world, infinite gradient

- a time vs voltage graph would be **smooth** and **continuous**

  

digital signal - computers, set amount of data; can increase detail but will **never be** infinite

- a time vs voltage graph would be choppy based on how many bits it has
- uses a binary system (0s and 1s) so it cannot take on fractional values

(may look like a digital graph but it is made up of a ton of little steps)

  
  
  

**Digital to Analog Conversion (DAC)**

DAC - Inputs a binary number and outputs an analog voltage/current signal

- weighted resistor DAC (r/2nr DAC)
- ladder DAC (?)

  

Operational Amplifier / op-amp #important

- **takes a small voltage and increases it** #important
- **takes two inputs and compares them** #important
- has 2 digital inputs (positive and negative), then needs power
  
  

  
  
 ![Exported image](Exported%20image%2020240207094508-0.png)   
  

V1 = most significant bit

Vout = - (V1 + V2/2 + V3/4 …) - FORMULA FOR DAC - OUTPUT IN ANALOG

  
  
  
  

Vn / 2n-1 is general formula

  
  

**FLASH OPERATION:**

![Exported image](Exported%20image%2020240207094508-1.png)  

**SERIES CIRCUIT**

![Exported image](Exported%20image%2020240207094508-2.png)  
  
  
  
  

  

The weird looking guys are **XOR gates**

ONLY ACTIVATE IF IT IS **(1 - 0) OR (0 - 1)**

![Exported image](Exported%20image%2020240207094508-3.png)

**Operational Amp**

If you connect the positive to a ground, it is an amplifier

  

If you connect the positive to a positive, it is a comparator (HOW IT WORKS HERE)

**POSITIVE > NEGATIVE, OUTPUT = 1**

![Exported image](Exported%20image%2020240207094508-4.png)

**Diodes**, allow only one way power

![Exported image](Exported%20image%2020240207094508-5.png)

**If V****ref** **= 8V**

  

8v from ground

  
  

7v from ground

  

6v from ground

  

5v from ground

  
  

4v from ground

  

3v from ground

  

2v from ground

  

1v from ground

  

![Exported image](Exported%20image%2020240207094508-6.png)

Example: