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

