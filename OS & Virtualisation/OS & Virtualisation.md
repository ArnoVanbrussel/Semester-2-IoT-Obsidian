
# 1 Introduction
- Theory heavy module
- General overview of computer systems
- Overview of evolution and technologies
- OS, virtualisatie en computersystemen = complex
- Moeilijk inzicht hebben zonder overzicht waar alles vandaan komt
- Bedoeling:
	- Snappen van oude concepten omdat die hetzelfde bleven
	- Alles van [ENIAC]([[https://nl.wikipedia.org/wiki/ENIAC]])  tot Cloud
### 1.1.1 Objectives
- Deeper understanding of operation principles of computing systems
- Understanding of concepts used in modern architects
	- concepten = theorie
- Knowledge and understanding of terms used in modern architecture
- Ability to make well-founded technological choices
	- bv.: IoT sensor genereert enorm veel data, hoe verwerken, hoe opslaan, etc.

> Extremely general overview so a lot of details will not be treated

### 1.1.2 Content
- Hardware architecture of computer systems
- Software architecture of computer systems
- Principles of code execution on computer systems
- Core operating systems concepts
- Core virtualization concepts
- Core storage concepts
- Next-gen systems; the software defined datacenter

> Quite literally:
> From the first vacuum tube computer to modern cloud infrastructure
### 1.1.3 Classes
- Emphasis on conceptual knowledge
- Labs to deepen understanding of concepts
### 1.1.4 Exam
- Theoretical exam
- Practical exam task with case
- Tasks during the semester
	- (presented on practical exam)

# 2 From Logic Gates to Computing
## 2.1 Digital Logic
### 2.1.1 Binary Units
- Bit: 1/0
	- Binary Digit
- Byte: 8 bits
- Nibble: 4 bits
- Word: depends...
	- 16 bits
	- Double word or Long word: 32 bits
	- Very long word: 64 bits
	- May depend on architecture and context
### 2.1.2 MSB / LSB:
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

### 2.1.3 Base conversions
- Decimal (base 10)
- Binary (base 2)
- Hexadecimal (base 16)
	- (1 byte = 2 nibbles)
	- Handig: 2 tekens = 1 byte
- Octal (base 8)
	- Minder courant

![[Pasted image 20240212090339.png]]

### 2.1.4 Basic logical operations (exhaustive list):
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
### 2.1.5 Arithmetic operations in digital logic
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

### 2.1.6 Multiple operations
- Multiple functions can be implemented in digital logic
- One can select the function to perform on the input data
- This is called an arithmetic logic unit or [ALU](https://nl.wikipedia.org/wiki/Arithmetic_logic_unit)
- The [opcode](https://nl.wikipedia.org/wiki/Opcode) decides the performed operation
![[Pasted image 20240212095622.png]]

### 2.1.7 Multiplexers (MUX)
- Logic that selects a value from several inputs
![[Pasted image 20240212095838.png]]
![[Pasted image 20240212095808.png]]

### 2.1.8 Memory elements in digital logic
- Providing feedback in gate circuits can create memory elements
- Flip Flop circuit
	- SR Latch (2 NOR Gates)
	- SR Flip Flop (Clocked latch)
	- D Flip Flop (Data Flip Flop)![[Pasted image 20240212100444.png]]
	- Combining multiple flipflops to store a byte on information is a **register**
### 2.1.9 Larger memories
- Stacking multiple storage cells
- Use an address decoder (this is a demultiplexer) to select the wanted location
- This is RAM
- [Static RAM](https://en.wikipedia.org/wiki/Static_random-access_memory#:~:text=Static%20random%2Daccess%20memory%20(static,lost%20when%20power%20is%20removed.) or [SRAM](https://en.wikipedia.org/wiki/Static_random-access_memory#:~:text=Static%20random%2Daccess%20memory%20(static,lost%20when%20power%20is%20removed.) (as contents do not need refreshing)
	- Is used for cache storage
### 2.1.10 Combinational logic
- Output dependent solely on current input state
### 2.1.11 Sequential logic
- Output dependent on previous state(s) too
- Needs memory elements
### 2.1.12 Large scale integration
- Single logic function discretely implemented using germanium transistors
![[Pasted image 20240212101335.png]]
- Integrated circuits
	- Single IC contains 4 logic gates
![[Pasted image 20240212101353.png]]
- Large scale integration (LSI)
	- Whole functional blocks integrated into a single IC
	- 4000-10000 transistors in a single package
	- Examples: 1k RAM, ALU, ...
### 2.1.13 Very-large-scale integration
- VLSI = +1M transistors
- Transistor count in excess of 5,3 trillion
- Further; ULSI (Ultra-Large-Scale), SoC (System on Chip), 3D IC, ...
### 2.1.14 The digital computer
> We may want to automate some sequences of operations
# 3 Computer architecture
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

### 3.1.1 CPU - Central processing unit
- Contains
	- ALU
	- Control logic
	- Register
![[Pasted image 20240214085604.png|300]]![[Pasted image 20240214085612.png|400]]
> We need somewhere to store the instructions. A memory for the program: "program" or "instruction memory". Should this be RAM? ROM? Should it be the same as general memory.

#### 3.1.1.1 [Harvard Architecture](https://en.wikipedia.org/wiki/Harvard_architecture) **EXAMEN**
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
#### 3.1.1.2 [Von Neumann Architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture) **EXAMEN**
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

#### 3.1.1.3 [Instruction Set Architecture](https://en.wikipedia.org/wiki/Instruction_set_architecture)
- What instructions are supported by a CPU?
- **ISA** "Instruction Set Architecture"
- Set of supported opcodes

> Example x86: [https://en.wikipedia.org/wiki/X86_instruction_listings](https://en.wikipedia.org/wiki/X86_instruction_listings)

- [CISC](https://en.wikipedia.org/wiki/Complex_instruction_set_computer): Complex Instruction Set Computer
- [RISC](https://en.wikipedia.org/wiki/Reduced_instruction_set_computer): Reduced Instruction Set Computer
- [Turing complete systems](https://en.wikipedia.org/wiki/Turing_completeness):
	- Any Turing complete machine can perform any task of another Turing machine. (given infinite memory and time) (This will be revisited later)

##### 3.1.1.3.1 Example: [Z80 CPU]([https://en.wikipedia.org/wiki/Zilog_Z80](https://en.wikipedia.org/wiki/Zilog_Z80))
![[Pasted image 20240214094849.png]]![[Pasted image 20240214094912.png]]![[Pasted image 20240214094930.png]]

- 2 distinct use cases
	- Exact use scenario is known at time of design
		- Machine controller
		- Dedicated computer system
	- Use case is unknown at time of design
		- PC, Laptop
		- Universal computer system

#### 3.1.1.4 Dedicated computer system
- Specifications are known
- Functions
- Estimation of required instruction and RAM size
- Peripherals
- Can be optimized for the task at hand
- Usually smaller footprint devices
- Often completely self contained (RAM+ROM+Peripherals+...)
- **MCU or Micro Controller Unit**
#### 3.1.1.5 Universal computer system
- Unknown what tasks will be performed
- Must be expandable
	- MPU
- Does need external support components
- Differences are fading; see SoC systems later
#### 3.1.1.6 Input and output devices
- Interfaces to the computer system can be:
	- Memory mapped I/O
	- PIO- Programmed Input/Output:
		- CPU controls I/O operations
	- DMA - Direct Memory Access:
		- Devices access system RAM
	- Integrated peripherals
		- Needs specific instructions in ISA
#### 3.1.1.7 Software and portability
- There are a lot of flexibilities in system design
- The 'program' currently is specific to the utilized:
	- ISA
	- CPU implementation
	- System architecture
	- Present devices and configuration
# 4 Software Basic System Operations
## 4.1 We have a working "computer"
- Computer system with CPU and memory
- I/O devices
- All built from the simplest logic elements
- Now we need to tell it what to do => List of instructions => Software
## 4.2 Software
- List of instructions the CPU can execute
- Machine instruction = OPCODE + OPERAND
![[Pasted image 20240219090053.png]]
## 4.3 OPCODE and Operands
- OPCODE is a specific instruction from the ISA
- Operates on operands (most literals or memory address locations)
![[Pasted image 20240219090134.png]]
## 4.4 Getting to a known state
- RESET
- Set PC to 0
- RUN/STOP
- Begin execution from PC, increment PC after each execution cycle
- ROM
- Start of program at lowest Addresses of RAM (or Instruction memory)
- Diode matrix (Decoder + soldered diode array)
- (E)EPROM
![[Pasted image 20240219102434.png|350]]![[Pasted image 20240219102444.png|250]]
## 4.5 Current Technology
- Reset button
- BIOS/UEFI
	- is (flash) EEPROM and 'bootstraps' the system
### 4.5.1 Monitor Software
- Check state
- Read and write memory addresses
- Load data into memory
- Can be used to load different "programs"
- Very specific to exact architecture
- Machine and vendor specific
### 4.5.2 Software Development
- Opcode -> Machine code, ISA specific
- Assembler -> mnemonics, translates to instructions, ISA independent
- High level programming languages
	- Early successfull examples: COBOL / Fortran / BASIC
	- Provides hardware abstraction
	- "Describes" the program flow
	- needs to be compiled
![[Pasted image 20240504145212.png]]![[Pasted image 20240504151149.png]]
#### 4.5.2.1 Assembler code
- Closest to machine code
- uses mnemonics for instructions
- can contain macros and labels
- do a level of pre- and post-processing
#### 4.5.2.2 Compilers
- Translate one language to another
- C => Assembler
- Assembler => Object file (machine code)
#### 4.5.2.3 Linkers
- Links object files in an executable file
- Static linking
- Dynamic linking (library!)
![[Pasted image 20240504151834.png]]
#### 4.5.2.4 Portability
- Machine code is not portable
	- Dependent on exact system architecture
	- Dependent on exact ISA
- High-level source code is portable to a degree
	- Compiler for specific architecture
	- Provides reusable software components
	- Results in libraries that can be linked against
#### 4.5.2.5 Optimalisation
- Compilers generate "sub optimal" code
- Higher level languages are easier and more practical
- Large business projects => high level programming language
- Timing critical software components => Code in assembler
- These days optimising compilers generate more efficient bytecode than most low-level programmers
- So no longer holds in all cases, but does in some
## 4.6 Extra abstraction through AI?
![[Pasted image 20240504152456.png]]
## 4.7 Problem: Interaction with devices
- Put something on the screen (if available)
- Read data from "disk" (if available) 
### 4.7.1 Solution part 1: Standard compiler library
- Standard library eg C 'stdlib'
- Implements certain standard functions, eg printf, scanf, ...
- Is shipped with compiler
- Source code can #include <stdlib.h>
- Platform specific implementation details are handled
- Source code does not need to be modified
- Software does need to be recompiled
- Dynamic linking of software libraries is possible to save on storage
### 4.7.2 Solution Part 2: Function blocks
- Implement standard functions in code blocks in known/reserved program memory locations
- Have user software 'call' these functions
## 4.8 IRQ - Interrupt Requests
- Code flow is always sequenced
- We may want to 'interrupt' the normal sequence of operations
- Hardware IRQ
	- When an event happens
	- Has hardware interface and connections to the CPU control logic
- Software IRQ
	- Triggered by a software condition
- When an IRQ happens
	- IVT (IRQ Vector Table) is consulted
	- Execution i handed to the ISR (Interrupt Service Routine)
![[Pasted image 20240504155941.png|700]]
![[Pasted image 20240504155958.png|700]]
- 2 types of interrupts
	- Maskable and Non-maskable (NMI)
		- Masking = disable some interrupts
		- Often done using a bit pattern that is AND-ed to the IRQ's
		- NMI cannot be disabled
### 4.8.1 Using interrupts to provide basic I/O services
- Usable as "OS Entry Point" on x86
- Concept of SVC (SuperVisor Call) on /360 Mainframes
- Example INT21 DOS Function dispatcher:
![[Pasted image 20240504160159.png]]
## 4.9 Basic 'operation' of a computer system
- Get the system to a known and initialized state
- Provide a way to load/start different programs
- Provide a unified way for software to run
- Provide tools for basic system maintenance
=> Operating System
## 4.10 Operating system
![[Pasted image 20240504160328.png]]
### 4.10.1 Disk operations
- Software needs to be loaded
- Data needs to be saved
- Data needs to be read
- Storage operations are an important part of computing
- A way to organise, find and retreive data: 
	- File System
### 4.10.2 Disk Operating System: DOS
- Provides system initialization
- Basic abstracted functions using INT21 function dispatcher
- Filesystem (FAT)
- Way to interact (command Shell)
- Load and execute software
# 5 Tasks and Processes
## 5.1 Multitasking
- Seemingly concurrent execution of multiple tasks over a certain period of time
### 5.1.1 Cooperative Multitasking
![[Pasted image 20240504160944.png]]
- Each task executes to the end OR to a certain point at own discretion
- A Scheduler ("Task of tasks") decides what task is next
- Problem: If a task keeps busy then the whole system halts
- Problem: No reliable way of ensuring all tasks get (equal) share
### 5.1.2 Preemptive Multitasking
![[Pasted image 20240504161606.png]]![[Pasted image 20240504161625.png]]
- Time slice
	- IRQ for scheduler, smallest allocatable timer
- Affinity and priority can be selected by scheduler
- Context switching by scheduler
### 5.1.3 Processes
- The concept of running multiple applications as separate tasks works
- This system can be further implemented by separating an application in multiple processes
- Processes can run independent from each other
### 5.1.4 Thread
- Even further parallelism
- Thread is a segment of a process
- Process context switching is heavy, thread is lightweight
- Processes take a lot of resources for starting and terminating
- Threads take less recourses for starting and terminating
### 5.1.5 Fiber
- Fibers are even lighter
- Multiple fibers can run in a single thread
- Switching between fibers is not preemptive
- Fiber must "yield" execution
- Fibres are thus a form of cooperative multitasking
- Fibres are not part of most mainstream OS'
	- But are implemented in user-space libraries
## 5.2 Problems with multithreading
### 5.2.1 Synchronisation Problems
![[Pasted image 20240504162152.png]]
### 5.2.2 Race Conditions
![[Pasted image 20240504162234.png|350]]![[Pasted image 20240504162300.png|350]]
### 5.2.3 Shared Resources
- For example, access to specific hardware, I/O or logical resource
	- Only one process can use a specific resource at a time
	- The rest must wait
### 5.2.4 Dining philosophers problem
![[Pasted image 20240504162549.png]]
### 5.2.5 Deadlock
![[Pasted image 20240504162601.png]]
### 5.2.6 Semaphore
- Variable used to show use of a resource
- Synchronisation primitive
![[Pasted image 20240504162642.png]]
### 5.2.7 Mutex (or lock)
- **Mutual Exclusion:** 
	- Ensures that only one thread can access a shared resource at a time, preventing data corruption or inconsistency.
- **Separate Read and Write Locks:** 
	- Provides the flexibility to allow concurrent read access while ensuring exclusive write access.
- **Lock Holder Tracking (PID):** 
	- Maintains information about the thread currently holding the lock, aiding debugging and monitoring.
- **Thread-Specific Release:** 
	- Ensures that only the thread that acquired the lock can release it, maintaining control over resource access.
- **Reentrant Mutex:** 
	- Allows a thread to acquire the same lock multiple times without causing a deadlock, enhancing flexibility in programming concurrency.

### 5.2.8 Memory Protection
- **Segmentation:** 
	- Divides the memory into logical segments, each with its own set of permissions, preventing unauthorized access to memory regions.
- **Paged Virtual Memory:** 
	- Utilizes a mapping mechanism where physical memory is divided into fixed-size pages, allowing non-contiguous allocation of virtual memory, enhancing memory utilization and security.
### 5.2.9 Communication between processes
- **Inter Process Communication (IPC):** 
	- Facilitates communication and data exchange between processes
- **Message Queues:** 
	- Provides a mechanism for processes to communicate by sending and receiving messages through a shared queue, enabling asynchronous communication and synchronization between processes.
### Inter-Process Communication
- **Using File/Storage:** 
	- Processes can communicate by reading from and writing to shared files or storage locations, facilitating data exchange between them.
- **Signal / System Function:** 
	- Processes can send signals to each other using system functions like `kill` in Unix-like systems, allowing for communication and synchronization between processes.
- **Sockets (Networking):** 
	- Processes on different systems can communicate over a network using sockets, enabling data exchange and collaboration over the internet or local network.
- **Domain Socket (Filesystem Inode):** 
	- Provides a form of inter-process communication within the same system, utilizing special file types that facilitate communication between processes through the filesystem's inode structure.
- **Shared Memory:** 
	- Allows multiple processes to share a region of memory, enabling fast communication and data exchange by directly accessing shared memory segments.
- **Named Pipe (as Stdin/Stdout):** 
	- Also known as FIFO (First In, First Out), named pipes provide a mechanism for inter-process communication through special files in the file system, resembling standard input and output streams.
- **Message Queue:** 
	- Processes can exchange messages through message queues, allowing for asynchronous communication and synchronization between them.
	- ![[Pasted image 20240504163424.png]]
	- ![[Pasted image 20240504163447.png]]
	- ![[Pasted image 20240504163459.png]]
