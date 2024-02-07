**Intro to USB**

USB was developed by Compaq, Intel, Microsoft and NEC, Hewlett-Packard, Lucent and Philips.

Was developed to find one connector - not a bunch like there was at the time.

Was designed to replace legacy connections, and be hot-pluggable

  

**Data Speed**

Three speeds (now there are 6?)

  

|   |   |
|---|---|
|**Low Speed**|**1.5Mbit/s**|
|**Full Speed**|**12Mbit/s**|
|**High Speed**|**480Mbit/s**|

  

|   |   |
|---|---|
|**USB 3.2 Gen 1 (SuperSpeed)**|**5Gbit/s**|
|**USB 3.2 Gen 2 (SuperSpeed 10Gbit/s)**|**10Gbit/s**|
|**USB 3.2 Gen 2 x 2 (SuperSpeed 20Gbit/s)**|**20Gbit/s**|

  

**Architecture:**

USB is based on "tiered star topology" - single host controller and (theoretically) up to **127 "slave" devices** #important

- Most hubs would run out of power way before 127, (7 bits, 0 is special and can't be used)

  

**Host is the Master**

All communications on this bus are initiated by the host

- The devices cannot intercommunicate with each other on the hub
- A device cannot initiate a transfer - must be prompted by user
- The only exception is when a device has been put into 'suspend' mode by the host (low power mode)

  

**USB Electrical Characteristics**

Contains 4 wires

- D+, D- (twisted pair for data, low speed may not be twisted) - (pins 1 and 2)
- VBUS - 5v power supply (pin 4)
- GND - ground wire (pin 3)
  

**Power distribution**

- A device (or hub) can only consume current from its upstream port.
- A "self-powered" device is one that provides its own power and does not draw power from the bus #important
- A "Bus-powered" device is one that needs extra power, it can pull **100mA or 500mA** if permitted by host. #important
- In "suspended" mode, must reduce its current consumption to 0.5mA (it needs this for getting woken up)

  
  

**Device Powering**

- Up to 5v is an attractive feature - this is usually what they use.
- Voltage can drop to 4.35V (?)
- No device is permitted to take more than 100mA before it has been **configured** by the host.
- The device must reduce its current consumption to 2.5mA whenever it is "suspended"
- The device may draw up to 500mA after it has been configured as a high power device
- A "self-powered" hub can provide 500mA
- Devices that draw more than 500mA need to be self-powered (using a Y splitter USB is not permitted and can easily damage ports.) #important

  

**Hot-Pluggable devices**

- If you pull a plug out while current is being drawn, it can cause an arc ("flyback") and cause damage / data loss.
- To be able to plug a device in and out of a running system rules have to be followed:

  

- Minimum of 1 micro F capacitor on VBUS and ground #important
- When you plug your device in with any capacitance between VBUS and ground will cause a dip in voltage across the other ports in the hub so:
- Maximum of 10 micro F capacitor on VBUS and ground #important
  

  

**USB Data Flow****￼**at any point in time only the host OR one device can be transmitting at a time

Works like a hub - blasts data to everything but only gets accepted by the destination

  

**Transceiver**

- At the end of the data link between host and device is a transceiver circuit
- Typical upstream end transceiver is located nearer to the host. The upstream end has two 15K pull-down resistors
- The equivalent downstream end transceiver are found in end devices
- individual receivers on each line are able to detect single ended signals (Single Ended Zero - SE0)
  

**Speed Identification**

- The device end of the link, a 1.5K ohm resistor pulls one of the lines up to a 3.3V supply from VBUS
- **D- for low speed devices**, and **D+ for a high speed device**
- High speed device will initially present itself as a full speed device with the pull-up resistor on D+

  
  

Three things to remember:

Version 1 - low speed - 1.5K resistor **connected to D-** #important

Version 1.2 - full speed - 1.5K resistor **connected to D+** #important

Version 3 - high speed - 45 ohm resistor on **each end of both D+ and D-** #important