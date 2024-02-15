# Week 1
## Introduction
- Theory heavy module
- General overview of computer systems
- Overview of evolution and technologies
- OS, virtualisatie en computersystemen = complex
- Moeilijk inzicht hebben zonder overzicht waar alles vandaan komt
- Bedoeling:
	- Snappen van oude concepten omdat die hetzelfde bleven
	- Alles van [ENIAC]([[https://nl.wikipedia.org/wiki/ENIAC]])  -> Cloud
### Objectives
- Deeper understanding of operation principles of computing systems
- Understanding of concepts used in modern architects
	- concepten = theorie
- Knowledge and understanding of terms used in modern architecture
- Ability to make well-founded technological choices
	- bv.: IoT sensor genereert enorm veel data, hoe verwerken, hoe opslaan, etc.

> Extremely general overview so a lot of details will not be treated

### Content
- Hardware architecture of computer systems
- Software architecture of computer systems
- Principles of code execution on computer systems
- Core operating systems concepts
- Core virtualization concepts
- Core storage concepts
- Next-gen systems; the software defined datacenter

> Quite literally:
> From the first vacuum tube computer to modern cloud infrastructure
### Classes
- Emphasis on conceptual knowledge
- Labs to deepen understanding of concepts
### Exam
- Theoretical exam
- Practical exam task with case
- Tasks during the semester
	- (presented on practical exam)

## Basic digital Logic
### Binary Units
- Bit: 1/0
	- Binary Digit
- Byte: 8 bits
- Nibble: 4 bits
- Word: depends...
	- 16 bits
	- Double word or Long word: 32 bits
	- Very long word: 64 bits
	- may depend on architecture and context
### MSB / LSB:
- Least & Most significant bit
	- Bit die minst of meest gaat veranderen
	- Meestal LSB rechts en MSB links
		- Hoeft niet!!!
		- [Endianness](https://nl.wikipedia.org/wiki/Endianness)
			- Big endian vs Little endian
				- Big endian: MSB links, LSB rechts
				- Little endian: LSB links, MSB rechts
			- Mixed endian

![[Pasted image 20240212085801.png]]

> 32-bit vs. 64-bit systeem:
> 	Woord = 32-bit vs. woord = 64-bit

### Base conversions
- Decimal (base 10)
- Binary (base 2)
- Hexadecimal (base 16)
	- (1 byte = 2 nibbles)
	- Handig: 2 tekens = 1 byte
- Octal (base 8)
	- Minder courant

![[Pasted image 20240212090339.png]]

### Digital logic
- Basic logical operations (exhaustive list):
	- NOT
		- Flip bit 0->1, 1->0
	- AND
		- Only 1 when both 1
	- OR
		- 1 when either 1
	- XOR
		- Only 1 when only 1 is 1
	- NOR
		- OR but flipped, so only 1 when both 0
	- NAND
		- AND but flipped, so only 0 when both 1
![[Pasted image 20240212090855.png]]
![[Pasted image 20240212091433.png]]

- More complex functions can be built form these elements
- A lot of design tools exist for design, calculation and simulation for educational use for example: [logiJS](https://logijs.com/)
- Universal gates:
	- NAND & NOR
	- Any function can be implemented using the NAND or the NOR gate
	- Can build an entire computer using only these

### Arithmetic operations in digital logic
- Arithmetic operations can be implemented in digital logic
- Overdracht van bit bij cijferen: carry bit
- Addition:
	- Half-adder
	- Adds 2 single binary bits
		- 1 light: 0 or 1
		- 1 light is Carry bit 0 or 1![[Pasted image 20240212092906.png]]
	- Full-adder
		- A full adder is a digital circuit that performs addition of three binary digits: two inputs (A and B) and a carry input (C-in). It produces a sum output (S) and a carry output (C-out). The full adder is a fundamental building block in digital circuit design, and multiple full adders can be combined to create more complex arithmetic circuits.![[Pasted image 20240212093822.png]]
	- Calculator with full adders (4-bit): ![[Pasted image 20240212094411.png]]

- Subtraction:
	- Is just adding with a negative number
	- 2's complement notation:
	- ![[Pasted image 20240212094819.png]]![[Pasted image 20240212095223.png]]

- Multiplication
	- Is just adding something multiple times
	- And in a similar way, all operation can be implemented

### Multiple operations
- Multiple functions can be implemented in digital logic
- One can select the function to perform on the input data
- This is called an arithmetic logic unit or [ALU](https://nl.wikipedia.org/wiki/Arithmetic_logic_unit)
- The [opcode](https://nl.wikipedia.org/wiki/Opcode) decides the performed operation
![[Pasted image 20240212095622.png]]

### Multiplexers (MUX)
- Logic that selects a value from several inputs
![[Pasted image 20240212095838.png]]
![[Pasted image 20240212095808.png]]

### Memory elements in digital logic
- Providing feedback in gate circuits can create memory elements
- Flip Flop circuit
	- SR Latch (2 NOR Gates)
	- SR Flip Flop (Clocked latch)
	- D Flip Flop (Data Flip Flop)![[Pasted image 20240212100444.png]]
	- Combining multiple flipflops to store a byte on information is a **register**
### Larger memories
- Stacking multiple storage cells
- Use an address decoder (this is a demultiplexer) to select the wanted location
- This is RAM
- [Static RAM](https://en.wikipedia.org/wiki/Static_random-access_memory#:~:text=Static%20random%2Daccess%20memory%20(static,lost%20when%20power%20is%20removed.) or [SRAM](https://en.wikipedia.org/wiki/Static_random-access_memory#:~:text=Static%20random%2Daccess%20memory%20(static,lost%20when%20power%20is%20removed.) (as contents do not need refreshing)
	- Is used for cache storage

### Combinational logic
- Output dependent solely on current input state
### Sequential logic
- Output dependent on previous state(s) too
- Needs memory elements
### Large scale integration
- Single logic function discretely implemented using germanium transistors
![[Pasted image 20240212101335.png]]
- Integrated circuits
	- Single IC contains 4 logic gates
![[Pasted image 20240212101353.png]]
- Large scale integration (LSI)
	- Whole functional blocks integrated into a single IC
	- 4000-10000 transistors in a single package
	- Examples: 1k RAM, ALU, ...
### Very-large-scale integration
- VLSI = +1M transistors
- Transistor count in excess of 5,3 trillion
- Further; ULSI (Ultra-Large-Scale), SoC (System on Chip), 3D IC, ...
### The digital computer
> We may want to automate some sequences of operations

# Week 1 - Labo
## Computer architecture
- Components we already have:
	- ALU
	- Registers / Memory
- Programming / Automation
	- Execute a sequence of instructions automatically
	- We need a clock
		- [Frequentie](https://nl.wikipedia.org/wiki/Kloksnelheid#:~:text=Een%20kloksnelheid%20van%201%20Hz,per%20seconde%20hun%20bewerkingen%20uit.) (Hertz)
		- Synchronize all operations
		- Go to next instruction cycle
	- We need to keep track of the current instruction
	- We need somewhere to store the instructions

> We need to keep track of the current instruction. We use a special purpose register "PC"; the Program Counter.

### CPU - Central processing unit
- Contains
	- ALU
	- Control logic
	- Register
![[Pasted image 20240214085604.png|300]]![[Pasted image 20240214085612.png|400]]
> We need somewhere to store the instructions. A memory for the program: "program" or "instruction memory". Should this be RAM? ROM? Should it be the same as general memory.

#### [Harvard Architecture](https://en.wikipedia.org/wiki/Harvard_architecture) **EXAMEN**
- Separate memory for instructions and data
- **Pro's:**
	- Snellere instructie-uitvoering
		- Harvard-architectuur maakt gelijktijdige toegang tot instructies en gegevens mogelijk, wat kan leiden tot snellere instructie-uitvoering.
	- Betere prestaties voor specifieke toepassingen
		- In bepaalde toepassingen, zoals ingebedde systemen, kan de Harvard-architectuur efficiënter zijn vanwege de gelijktijdige toegang tot instructies en gegevens.
	- Verhoogde parallelle verwerking
		- Harvard-architectuur maakt het gemakkelijker om parallelle verwerking te implementeren vanwege de afzonderlijke gegevens- en instructiebussen.
- **Con's:**
	- Complexiteit van ontwerp
		- Implementatie van Harvard-architectuur kan complexer zijn vanwege de noodzaak van afzonderlijke bussen voor instructies en gegevens.
	- Kosten
		- De extra hardware die nodig is voor afzonderlijke bussen kan leiden tot hogere kosten.
![[Pasted image 20240214090027.png|350]]![[Pasted image 20240214090233.png|350]]
#### [Von Neumann Architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture) **EXAMEN**
- Same memory is used for instructions and data
- Groot voordeel: Self Modifying Code
- **Pro's:**
	- Eenvoudig ontwerp
		- Von Neumann-architectuur heeft een eenvoudiger ontwerp met één gemeenschappelijke bus voor zowel instructies als gegevens.
	- Kost-efficiëntie
		- Omdat het ontwerp minder complex is, kunnen systemen gebaseerd op de Von Neumann-architectuur vaak kost effectiever zijn.
	- Flexibiliteit
		- De architectuur is flexibeler en gemakkelijker aan te passen aan verschillende toepassingen.
- **Con's:**
	- Langzamere instructie-uitvoering
		- Omdat instructies en gegevens dezelfde bus delen, kan dit leiden tot langzamere instructie-uitvoering in vergelijking met Harvard-architectuur.
	- Beperkte parallelle verwerking
		- Von Neumann-architectuur heeft beperktere mogelijkheden voor parallelle verwerking in vergelijking met Harvard-architectuur.
![[Pasted image 20240214090043.png|350]]![[Pasted image 20240214090240.png|350]]
> Funny old computer: [Altair 8800](https://nl.wikipedia.org/wiki/Altair_8800)/ [Altair 8800](https://oldcomputers.net/altair-8800.html)
> Fun example: NES
> 	Cartridge: Instruction memory
> 		(ROM - Read only memory, basically I-RAM)

#### [Instruction Set Architecture](https://en.wikipedia.org/wiki/Instruction_set_architecture)
- What instructions are supported by a CPU?
- **ISA** "Instruction Set Architecture"
- Set of supported opcodes

> Example x86: [https://en.wikipedia.org/wiki/X86_instruction_listings](https://en.wikipedia.org/wiki/X86_instruction_listings)

- [CISC](https://en.wikipedia.org/wiki/Complex_instruction_set_computer): Complex Instruction Set Computer
- [RISC](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer): Reduced Instruction Set Computer
- [Turing complete systems](https://en.wikipedia.org/wiki/Turing_completeness):
	- Any Turing complete machine can perform any task of another Turing machine. (given infinite memory and time) (This will be revisited later)

##### Example: [Z80 CPU]([https://en.wikipedia.org/wiki/Zilog_Z80](https://en.wikipedia.org/wiki/Zilog_Z80))
![[Pasted image 20240214094849.png]]![[Pasted image 20240214094912.png]]![[Pasted image 20240214094930.png]]

- 2 distinct use cases
	- Exact use scenario is known at time of design
		- Machine controller
		- Dedicated computer system
	- Use case is unknown at time of design
		- PC, Laptop
		- Universal computer system

#### Dedicated computer system
- Specifications are known
- Functions
- Estimation of required instruction and RAM size
- Peripherals
- Can be optimized for the task at hand
- Usually smaller footprint devices
- Often completely self contained (RAM+ROM+Peripherals+...)
- **MCU or Micro Controller Unit**
#### Universal computer system
- **MPU or Micro Processor Unit**
- Does need external support components
- Differences are fading; see SoC systems later
- Must be expandable
#### Input and output devices
- Interfaces to the computer system can be:
	- Memory mapped I/O
	- PIO- Programmed Input/Output:
		- CPU controls I/O operations
	- DMA - Direct Memory Access:
		- Devices access system RAM
	- Integrated peripherals
		- Needs specific instructions in ISA
#### Software and portability
- There are a lot of flexibilities in system design
- The 'program' currently is specific to the utilized:
	- ISA
	- CPU implementation
	- System architecture
	- Present devices and configuration