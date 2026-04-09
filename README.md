# ISA32bit
                              
      Extending the standard 16bit ISA bus interface to 32bit address/data bus and more... 

               # Chapter 1 - What is proposed 


## I. Introduction

ISA bus has been around since the first IBM PC and compatible computers - for good 40+ years.

Large number of peripheral were created and plugged/used on computers which have ISA bus slots.

While the computer systems did evolve and the ISA bus slots disappeared, the ISA bus peripherals are still used on old computer systems or together with USB2ISA line of products of ARS Technologies.

This project space is a proposal for extending the ISA bus interace.

But why?

Currently the computer interfaces swinged heavily towards serial interfaces which run on single or tens of gigabits/s of clock speed. 

It is challenging creating new hardware for these interfaces - requiring a custom chip or a phy + fpga combination.

However, in many cases there is no actual need of the gigabits/s speed. And, many interface chips have parallel data and address busses.

Tbis proposal extend the capabilities of the original ISA interface, while using the same 98 pin connector/interface.

ISA32bit interface is intended for new designs which have low to moderate data throughtput - kbit/s to 10s of mbit/s.




## II. Original ISA bus and the proposed ISA32bit bus

The original ISA interface is described in multiple places, here are:
- [the wikipedia link](http://en.wikipedia.org/wiki/ISA_bus)
- [the techfest link](http://wearcam.org/ece385/lecture6/isa.htm)

The original ISA interface has the following capabilities:
- 8/16bit I/O and memory data bus
- 16bit I/O address bus, 24bit memory address bus
- IRQ channels and 8/16bit DMA channels
- minimum of 250ns read/write data cycle
- 8MHz system clock, 14.3MHz oscilator clock
- 5V logic level
- 98 pin connector/interface

The extended ISA32bit interface proposes the following capabilities:
- compatible mode to handle original ISA peripherals
- 8/16/32bit I/O and memory data bus
- 16/32bit I/O address bus, 32bit memory address bus
- IRQ channels and 8/16/32bit DMA channels
- minimum of 66ns read/write data cycle
- 15/30MHz (up to 120MHz)) system and oscilator clock
- 5V and 3.3V logic levels
- same 98 pin connector/interface

How does the proposed ISA32bit compare with the [EISA](https://en.wikipedia.org/wiki/Extended_Industry_Standard_Architecture) and 32bit [PCI](https://en.wikipedia.org/wiki/Peripheral_Component_Interconnect) interfaces?

While the EISA interface requires a very high pin count connector - of 98pins + 100pins, the ISA32bit interface uses the original 98pin ISA connector.

In the same way as the PCI interface the proposed ISA32bit interface uses partially multiplexed address/data bus. But while the PCI inteface is synchronous/clocked, the ISA32bit is still asynchronous.

## III. 2 sides

There are 2 sides of the ISA interface - <b>host</b> side and <b>peripheral</b> side.

Traditionally the host side was provided by the motherboard but long ago ISA inteface was removed from motherboards.

The appendinx will show 2 implementations of the host side of ISA32bit interface - hardware and software emulation through USB3 and WiFi interfaces. <br><br>

The peripheral side of the ISA interface had a wide variety of boards providing video, audio, network, disk controller, serial/parallel ports, data aquisition, etc. functionality.

There are sample schematics for  peripheral card implementation of the ISA32bit interface.




   ## Next:
### [Chapter 2 - Timing diagrams and hardware interface](chapter2)
### [Chapter 3 - Software interface and API set](chapter3)


   ## Appendix
1. Host hardware implementation    
2. Sample software and libraries to build on: Windows (x86/64), Mac OS (x86/64, arm-m1,2/64), Linux (x86/64, arm/64) 


        Join our project - Become a contributor and/or implementer and/or user of ISA32bit

Contributors: Paul Arssov / paul@arstech.com 
