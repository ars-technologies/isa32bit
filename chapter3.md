## Chapter 3 - Software interface and API set

### I. Considerations

The software interface and API has to cover and work on the most popular computer operating systems, and the most popular application processors.

<b>The aim is for the ISA32bit API to work on:
- Windows - x86 64bit
- Mac OS - x86 64bit, and Apple silicon m1,2 arm 64bit
- Linux - x86 64bit, and arm 64bit
- Android - arm 32bit, arm 64bit </b>

Originally the ISA and other similar parallel interfaces were set to be part of the processor address/data space. Peripherals mounted on these interfaces became part of the processor address/data space.

<b>The aim is for the ISA32bit API to have its own address/data space which can also be tied to the processor address/data space</b>

Application processors have 2 modes exposed to computer operating systems - User mode and Kernel mode.

Windows and Linux (including Android) operating systems do not allow direct access to hardware in User mode - from an application program. Building and loading kernel drivers/modules faces many obstacles on both Windows and Linux.

Mac OS allows User level to hardware but this may change at any time in the future.

<b>The aim is for the ISA32bit API to work on - User level.</b>

ISA, PCI (and related) interfaces have 2 address/data spaces - i/o (input/output) and memory. I/O space is present only on x86 compatible processors and not present on arm or other processors.

A feature of the i/o space is FIFO access - read from or write to a single address of a sequence of data. 

<b>The aim is for the ISA32bit API to have and serve both - i/o and memory spaces.</b>

Application processors have MMU (memory management unit) which provides to software one or more virtual addresses for a single physical memory space (as on address lines) address.

Software developers have to use API provided by the operating system to get the virtual addresses for every physical memory addresses range.

<b>The aim is for the ISA32bit API to access directly the memory space with a physical address.</b>


### II. API set

As a minimum the ISA32bit API set is covering 8/16/32 bit read/write to i/o and memory spaces:

<b>uint8_t in8(uint16_t adr);  
uint16_t in16(uint16_t adr);  
uint32_t in32(uint16_t adr); </b>  
    read from i/o space  
    parameter:  adr - i/o space address (can be also 32 bit)  
    returns: 8/16/32bit data  

<b>uint8_t rd8(uint32_t adr);  
uint16_t rd16(uint32_t adr);  
uint32_t rd32(uint32_t adr);</b>  
    read from memory space  
    parameter:  adr - physical memory space address   
    returns: 8/16/32bit data   

<b>void out8(uint16_t adr, uint8_t dt);  
void out16(uint16_t adr, uint16_t dt);  
void out32(uint16_t adr, uint32_t dt);</b>  
    write to i/o space  
    parameters:  adr - i/o space address (can be also 32 bit)  
                 dt - 8/16/32bit data  
  returns: none       

<b>void wr8(uint32_t adr, uint8_t dt);  
void wr16(uint32_t adr, uint16_t dt);  
void wr32(uint32_t adr, uint32_t dt);</b>  
    write to memory space  
    parameters:  adr - physical memory space address   
                 dt - 8/16/32bit data  
  returns: none       

As a minimum the API set provides a single function to get the status of the IRQ and DMA channels:  

<b>uint32_t GetIrqDma();</b>  
    Gets the current level of the IRQ and DRQ lines of the ISA bus  
    parameters: none   
    returns: IRQ and DRQ levels, 1 bit per channel     


   ## Appendix
### [1. Host hardware implementation](appendix1.md)    
### [2. Sample software and libraries to build on: Windows, Mac OS, Linux](appendix2.md)


        Join our project - Become a contributor and/or implementer and/or user of ISA32bit
          
        You are welcome to contact us and/or share about our project 

Contributors: Paul Arssov / paul@arstech.com 

    
