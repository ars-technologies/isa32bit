	Host <-> Peripheral interaction
	
1. Basics

This chapter deals with access by software. We will look separately for DMA (direct memory access) type of access.

This chapter will look at the interaction between an ISA32bit host and both standard ISA card and ISA32bit capable peripheral card.

The standard ISA interface has 8 and 16 bit data sizes and the ISA32bit interface has 8, 16 and 32 bit data sizes   

The standard ISA interface has 24 bit memory address space and 16 bit I/O address space. The ISA32bit interface has has 32 bit memory address space and 32 bit I/O address space.  

The ISA32bit host has one or more ISA connectors allowing mounting of 1 or more ISA cards.

The ISA32bit host samples the level on the MEMCS16 pin. If high then one or more of the mounted ISA cards are standard ISA cards. If low then all ISA cards are ISA32bit enabled or there is a mix of ISA32bit enabled and standard ISA cards.  


2. ISA32bit host interacting with standard ISA card

The 8 and 16bit data access are handled in the same way as for standard ISA card - 8 and 16 bit data access, 24 bit memory and 16bit I/O address space. 

A0-15 lines remain address only lines - no multiplexing with data. D8-15 lines remain data only lines - no multiplexing with A24-31 .

If software makes 32 bit data memory/io read/write access command it is converted to 2 16 bit commands.

If software makes memory/io read/write access command to 32 bit address space it is converted to 24 bit memory address space and 16 bit I/O address space - high bytes are zero. 


3. ISA32bit host interacting with ISA32bit card

The 8 and 16 bit data access are handled in the same way as for standard ISA card - 8 and 16 bit data access. 

A0-15 lines remain address only lines - no multiplexing with data. However D8-15 lines are multiplexed with A24-31 ., This allows 32 bit memory and I/O address space. 

The 32 bit data access is handled with A0-15 lines remain address during BALE signal high and then lines are multiplexed with D16-31 data. 

D8-15 lines are multiplexed with A24-31 - allowing 32 bit memory and I/O address space. 
