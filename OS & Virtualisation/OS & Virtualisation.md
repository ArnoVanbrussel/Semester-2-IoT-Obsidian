
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
### 5.2.10 Inter-Process Communication
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
### 5.2.11 Multi Processing
- More than one execution unit
- in ISA:
	- SIMD: Single instruction Multiple Data
		- (Vector instructions eg: MMX)
- Master / Slave arbitration
	- For example: coprocessor
- Tightly coupled:
	- SMP: Symmetric multi processing
	- UMA: Uniform Memory access
	- NUMA: Non-uniform Memory access (local memory)
- Superscalar architectures, multiple pipelines; eg Hyper-threading
### 5.2.12 Process Forking
![[Pasted image 20240504163755.png]]
## 5.3 OS Process Management
- Done by OS Components
	- **OS Kernel**
- Process tree: System Process Table
- Process states / Process Control Block
	- PCB
- Process scheduling
- Creation and cleanup of processes
	- Terminated
	- Orphaned
	- Zombie
### 5.3.1 Process States
![[Pasted image 20240504164340.png]]
- Running 
- Ready
- Waiting 
- Terminated
### 5.3.2 Process Control Block (PCB)
![[Pasted image 20240504164409.png]]
- Contains:
	- Process state
	- Program counter
	- CPU registers
	- CPU scheduling information
	- Memory management information
	- I/O status information
### 5.3.3 System Process Table
![[Pasted image 20240504164433.png]]
- Hierarchical representation
	- Organizes processes:
		- Parent-child associations
- Stores essential process information
### 5.3.4 Context Switching
![[Pasted image 20240504164449.png]]
- Saves and restores process state
- Involves:
	- Storing current state
	- Loading new state
	- Updating data structures
### 5.3.5 Process Sceduler
![[Pasted image 20240504164549.png]]
- Determines process execution order
- Utilizes scheduling algorithms:
	- Round-robin
	- Priority-based
	- Multi-level feedback queues
# 6 Memory Management
## 6.1 Addressable Memory
- 16-bit
	- 65,536 bytes (64 Kilobytes)
- 32-bit
	- 4,294,967,296 bytes (4 Gigabytes)
- 63-bit
	- 18,446,744,073,709,551,616 (16 Exabytes)
- Physical limit imposed by width of address bus
- Practical limit also imposed by address operand of ISA instructions
## 6.2 Memory limits
- “8 bits” 8080 / 6800 / Z80 : 
	- 16 bit addresses, 16 bit bus: 64kb
- Intel 8086 / 8088 : 
	- 16 bit addresses, 20 bit bus: 1MB
- 80286 : 
	- 16 bit addresses, 24 bit bus: 16MB
- 80386SX: 
	- 32 bit addresses, 24 bit bus: 16MB
- 386DX-Pentium P54C: 
	- 32 bit addresses, 32 bit bus: 4GB
- P6 / Pentium PRO: 
	- 32 bit addresses, 36 bit bus: 64GB /w PAE
- 64 bit CPU’s: 
	- 64bit addresses; 40-52 bit bus: 1TB-4PB
## 6.3 Conventional Memory
- Original IBM/Comat PC using 8088 CPU had 20 address lines
- Total possible address space was thus 1MB
- First 640kb is named base memory and is usable for applications
- Upper 384kb is called UMA – Upper memory Area
- UMA is reserved for ROM BIOS, Peripherals, etc.
![[Pasted image 20240504165348.png]]
## 6.4 Real Mode
- x86 Original instruction set
- Operates on ‘real’ = physical addresses
- Unlimited direct access to all memory locations by all software
- 20 Bit “segmented” address space. (as 16bit operands are used)
	- A20 wrap-around logic still present in today’s systems
## 6.5 More (and less) Memory
- We want to be able to address more memory for applications
- We want the possibility to have less physical memory in the system than what could theoretically be addressed
- We may not want to be limited in the application by a shortage of physical memory
## 6.6 Back to Hardware
- We need extra hardware support 
- Extra address lines for physical RAM and a way to utilize these
- ISA Extensions
- Move to 32 bit, but also allow for better multitasking 
- Address more memory and allocate it in a dynamic way
	- …to multiple concurrently running processes
## 6.7 Protected mode
- Protected virtual address mode
- Segmentation
- Virtual memory
- Paging
- Hardware privilege levels
- Virtual 8086
- Protected mode NEEDS an OS to manage everything
### 6.7.1 Virtual Memory
- Hardware MMU:
	- **Memory Management Unit**
- Translates virtual to physical addresses
![[Pasted image 20240504165707.png]]
- Allows for process isolation
- Allows for memory protection
- Allows to address more memory than is physically available
### 6.7.2 Paging
![[Pasted image 20240504165836.png]]
- Virtual memory divides physical memory into fixed-size blocks called pages.
- When a process requests memory, the operating system allocates virtual memory space for it.
- Pages of the process's memory are loaded into physical memory as needed, typically using demand paging.
- If there is insufficient physical memory available, the operating system swaps pages between RAM and disk storage.
- This swapping process allows the system to free up physical memory by moving less frequently used pages to disk storage, enabling the system to execute processes as if it has more memory than is physically available.
### 6.7.3 Paging and Cache
![[Pasted image 20240504165949.png]]
### 6.7.4 Memory Paging
- OS & MMU: PTBR + PTLR
	- Page Table Base Register
	- Page Table Length Register
- Per Process Page Table (PT)
![[Pasted image 20240504170111.png]]
### 6.7.5 Swapping
- Swap pages to secondary storage
![[Pasted image 20240504170146.png]]
### 6.7.6 Page Faults
- When requested page is not available
- Handled by OS => IRQ generated by MMU
- Types:
	- Soft / Minor page faults
	- Hard / Major page faults
	- Invalid page faults => Access violation or exception
#### 6.7.6.1 Soft page faults
- Happens often in case of shared libraries / code
- Page is in memory but not mapped in MMU
	- OS should solve this; load TLB
		- **Translation Lookaside Buffer**
			- hardware cache used by the MMU to store frequently accessed virtual-to-physical address translations
#### 6.7.6.2 Copy-on-Write (COW)
![[Pasted image 20240504170515.png]]
- Memory management technique
	- Initially, multiple processes share the same memory segment.
	- If a process attempts to modify the shared memory, a copy is created for that process
	- This optimizes memory usage by deferring the copy operation until necessary, reducing overhead
#### 6.7.6.3 Swapping is not always bad
- With simple memory management systems, it could have proven beneficial to tweak swapping methods in specific cases
- Advanced algorithms in modern OS' optimize paging and swapping
	- Do not intervene
## 6.8 Addressable memory VS Physical memory
- 3 cases:
	- Larger address space than physical RAM
	- Address space is equal to physical RAM
	- More physical memory than is addressable
- In x86 systems; Address space is usually larger than RAM
### 6.8.1 Segmentation
- Variable size segments
- Segment table
### 6.8.2 Paging vs Segmentation
- Paging:
	- Program divided into fixed-size pages
	- Operating system is in charge
	- Faster than segmentation
	- Invisible to user
- Segmentation
	- Program divided into variable-size segments
	- User/Compiler is in charge
### 6.8.3 Memory Holes
- IRQ Vector tables at 0x0000
- Conventional memory / UMA
- 15-16MB for ISA expansion cards
- PCI Memory hole for shared memory above 3,5GB – 4GB
- Memory remapping & PAE can be used (Physical Address Extension)
### 6.8.4 Protection Rings
- "Protected" mode implements privilege rings
- Ring 0 can do anything
- Ring 3 should not be able to cause instability
![[Pasted image 20240504173507.png]]
### 6.8.5 Operating system kernel
- All this is managed by the OS
- More specifically the Kernel of the OS
![[Pasted image 20240504173540.png]]
# 7 Kernels
## 7.1 Operating Systems
> An operating system (OS) is system software that manages computer hardware and software resources, and provides common services for computer programs.

### 7.1.1 Main parts of OS'
- The system software, managing the hardware
	- Process management
	- Memory management
	- Disk & Filesystem access
	- Device access
	- ...
- Shared routines for application software
- Tools for managing the system
- A User Interface (GUI/CLI)
## 7.2 Kernels
- Hardware management
- Process management
- Memory management
- Storage management
- Device management
### 7.2.1 Kernel Oversimplified 
![[Pasted image 20240504173811.png|400]]
![[Pasted image 20240504173820.png|400]]
### 7.2.2 Kernel SCI
- System Call Interface
![[Pasted image 20240504173914.png]]
### 7.2.3 Example (OpenGL)
![[Pasted image 20240504173959.png]]
![[Pasted image 20240504174044.png]]
### 7.2.4 Kernels are complex
- Lot of code
- Lot of possible problems
- Not everything is used
	- At all times
	- In all cases
### 7.2.5 Monolithic kernel vs Microkernel
![[Pasted image 20240504174131.png]]
#### 7.2.5.1 Monolithic Kernel
- HW Protection Rings
- Context Switching between rings
	- 0: Kernel mode
	- 3: User mode
- Lot of code in ring 0
#### 7.2.5.2 Microkernel
- Low level memory management
- Low level process management
- Basic inter-process communication
- Small, efficient, smallest possible codebase
	- less problems and less security concerns
### 7.2.6 Windows NT Kernel
![[Pasted image 20240504174345.png]]
## 7.3 HAL - Hardware Abstraction Layer
- Same kernel on different architectures
- ISA / MMU / Architecture specific code is in the HAL
- Provides unified interface to kernel
![[Pasted image 20240504174457.png]]
![[Pasted image 20240504174506.png]]
## 7.4 Addressing Monolithic Kernel Problems
- Clearly Linux and Windows are not microkernels
- Monolithic architecture is proving problematic
	- Bulk
	- Security
	- Stability
- Architecture can not easily change
- Mach 3 kernel is a microkernel
- XNU is a hybrid kernel
- **Loadable Kernel Modules (LKMs)**:
- **Userspace Drivers**:
	- Used to run driver functionalities in user space for enhanced stability and security. This approach isolates driver code from the kernel, reducing the risk of system crashes due to faulty drivers.
- **Kernel-Mode Drivers**:
	- **Windows**: 
		- Utilizes kernel-mode drivers to extend kernel functionality. These drivers are loaded and unloaded dynamically and play a crucial role in hardware interaction and system stability.
	- **BSD**: 
		- Employs Kernel Loadable Modules (KLs) for similar purposes, providing a way to extend kernel functionality without rebuilding the kernel.
	- **macOS**: 
		- Relies on Kernel Extensions (kext) to add functionality to the kernel. Kexts are dynamically loaded and unloaded and are commonly used for device drivers and other low-level system tasks.
- **Linux modprobe / lsmod**:
	- **modprobe**: Command used to load, unload, and manage kernel modules in Linux systems.
	- **lsmod**: Command used to list currently loaded modules in the Linux kernel.
## 7.5 Rest of the OS?
- With Linux:
	- Linux Kernel
	- GNU Tools / Shell CLI
	- GCC StdLibs
	- Xwindows / KDE / GNOME
	- ...
		- All packed together = **Linux Distribution** = OS
# 8 Linux OS
> Herhaling Linux

# 9 Storage, Disks & Filesystems
## 9.1 Storage
- Persistent ('Disk')
- Non-persistent (RAM)
## 9.2 Tired Storage
- Fast, expensive & small <=> Slower, larger, cheaper
![[Pasted image 20240504203909.png]]
- Hot storage
- Cold storage
- Multiple tiers possible: warm, cool, ...
- Probability of access need
- Value of the data
- Size of the data
- Increased amounts of data are generated; Data avalanche
![[Pasted image 20240504205607.png]]
### 9.2.1 Application Metrics
- Scalability
- Manageability
- Security
- Reliability
- Availability
- Capacity
- Performance
### 9.2.2 Technological Metrics
- Size
- Speed
- Storage interface
- Cost (price/GB)
- Power (usage cost)
- Distance
- Reliability
## 9.3 Nearline Storage
- **Online storage:**
	- Immediately available for I/O
- **Nearline storage:**
	- Not immediately available but can be made online quickly without human intervention
- **Offline storage:**
	- Not immediately available and requires some human intervention to become online
## 9.4 Storage Topology / Interfaces
- **DAS:**
	- Direct Attached Storage
- **NAS:**
	- Network Attached Storage
- **SAN:**
	- Storage Area Network
![[Pasted image 20240504211839.png]]
### 9.4.1 SAS vs SATA
- SATA: Serial ATA
	- Advanced Technology Attachment
	- IDE interface (PATA): Integrated Drive Electronics
- SAS: Serial Attached SCSI
	- Small Computer System Interface
### 9.4.2 HBA
- Host Bus Adapter
- Interface between computer bus and storage device
- SATA / SAS / FC / ...
### 9.4.3 Storage Types: File, Block, Object
![[Pasted image 20240504212420.png]]
- Block storage
	- Address items in storage using:
		- Logical numbers of data segments of fixed size (blocks)
- File storage
	- Addressing items in storage using:
		- Logical file and path names
- Object storage
	- Addressing items in storage using:
		- Logical object references or metadata
#### 9.4.3.1 Block Devices
- Hard disks
- CHS mapping
	- Cylinder
	- Head
	- Sector
- Drive geometry (physical or virtual)
- Original scheme limits:
	- 24 bits 1023/255/63
	- 512 bytes /sector
- Logical Block Addressing
	- 48-bit logical addresses
	- 64-bit LBA
- Geometry is not useful for OS and makes no sense for an SSD
=> LBA
### 9.4.4 DAS
- Direct attached storage
	- Built-in
	- External
- 1-1 connection between storage device and host
- HBA (Host Bus Adapter) Interface
- E.g.:
	- Classical computer disk interface
	- SATA / ATA
	- Nvme
	- PCIe NVME
	- SAS (SCSI)
- Can be in external exclosure
- Can be removable media (tape / optical)
- Also
	- USB hard drive / sticks
	- Firewire / Thunderbolt enclosures
### 9.4.5 NAS
- Network Attached Storage
- File storage
- E.g.:
	- SMB, FTP, NFS, ...
- Shared Storage possible
### 9.4.6 SAN
- Storage Area Network
- Block storage
- Shared storage possible
- SAN Fabric
	- Fiber Channel (FC)
	- iSCSI
	- Speed
	- Efficiency (overhead)
	- Cost
#### 9.4.6.1 iSCSI
- Based on ethernet infrastructure
- Scalable and flexible
- Compatible with existing technologies
- High latency and protocol overhead
- Lower performance (relative)
- Cheaper
- Terminology
	- iSCSI Target
	- iSCSI Initiator
- LUN (block storage)
![[Pasted image 20240504213129.png]]
#### 9.4.6.2 Fiber Channel
- Specific interconnect for SAN fabric
- Low latency
- High performance
- Reliable
- Expensive
- FCoE: Fiber Channel over Ethernet
	- May be useful in migration scenario
#### 9.4.6.3 SAN Fabric Redundancy
- Redundant controllers
- Redundant connections on each controller
- Redundant fabrics
![[Pasted image 20240504213341.png]]
### 9.4.7 Converged Network Adapter
![[Pasted image 20240504213357.png]]
## 9.5 RAID
- Redundant Array of Independent Disks
- Any combination of the following:
	- Redundancy
	- Capacity expansion
	- Speed enhancement
### 9.5.1 Hardware / Software RAID
- System sees a single block device
- Combination performed by RAID controller
- What if HBA fails?
### 9.5.2 RAID functions
- Hot swap
- Hot spare
- LUN's
	- Logical Unit Number
	- Logical disks in an array
### 9.5.3 Standard RAID Levels
- Striping (RAID 0)
- Mirroring (RAID 1)
![[Pasted image 20240504213736.png|350]]![[Pasted image 20240504213748.png|350]]
- RAID 5:
	- With parity
	- Capacity: n-1
![[Pasted image 20240504213824.png]]
- RAID 6
	- Double parity
	- Capacity: n-2
![[Pasted image 20240504213920.png]]
- Nested RAID Levels
	- RAID 10
![[Pasted image 20240504213950.png]]
- RAID 50
![[Pasted image 20240504214012.png]]
- RAID 60
![[Pasted image 20240504214035.png]]
### 9.5.4 Non-RAID Levels
- JBOD: Just a Bunch of Disks
- Spanned volumes
### 9.5.5 Recovery of RAID arrays
- TLER of disks (Time limited error recovery)
- MFBT of disks
- Disk error rate
- Resyncing & initialisation
- Recovery time depends on array size
- Number of operations during recovery depends on disk size
- Unused space also needs 'recovering'
![[Pasted image 20240504214515.png]]
### 9.5.6 Bit rot / Data degradation
- RAID with single parity does NOT protect against data degradation
- Hard disk error rate is not zero
- Likelihood depend on data volume
	- URE error rate specs:
		- 1 in 10e14 for consumer drives
		- 1 in 10e15 for enterprise drives
### 9.5.7 Performance
- IOPS (I/O operations per second)
- NCQ (Native Command Queuing)
- Disk buffers
- Read-Ahead
- Hybrid drives with flash
![[Pasted image 20240504215446.png]]
## 9.6 Storage Clusters 
![[Pasted image 20240504215508.png]]
## 9.7 Storage Virtualization
- Add extra layer of abstraction
- Implement RAID / HBA functions in software
- Example: vSAN
![[Pasted image 20240504215541.png]]
# 10 Filesystems
## 10.1 Filesystems - Intro
- Group of letters = word
- Group of words = sentence
- Group of sentences = book
- Group of books = library
	- Books are ordered/sorted according to system
		- Dewey Decimal System
- Computers work with 0s and 1s
	- 1 character in ASCII or ISO-8859 = 8 bits = 1 byte
	- 1 unicode character in UTF-8 encoding:
		- 8-32 bits = 1-4 bytes
- Gets stored on block devices
	- hdd, ssd, ram disk, usb-stick
- System needs to organize this all
	- Disk = blocks
	- Collection of blocks = sector (mostly 512 bytes)
	- Collection of sectors = partition
	- Partition not usable for an OS => filesystem needed

> A file system is the methods and data structures that an operating system uses to keep track of files on a disk or partition; that is, the way the files are organized on the disk

E.g.: fat, ntfs, ext2/3/4, btrfs, ...

## 10.2 Filesystem objectives
- Store data in a reliable and consistent way
- Across different applications and even system
- Make it easy to retrieve said data
- Make it possible or modify or add data
- Manage the available storage space (free space)
- Do this in performant way
- Do this in efficient way
## 10.3 Filesystem paths and structure
- Flat filesystem
- Directory sturcture
- Path separator (`/ or \)
- File extension separator ( . )
![[Pasted image 20240505145921.png]]
- Present file structure to application in uniform way
- Application doesn't need to know what filesystem is used
![[Pasted image 20240505145956.png]]
- Filesystem metadata
	- Name
	- Size
	- Creation date
	- Modification time
	- Others:
		- ownership
		- security
		- properties
## 10.4 Filesystem Fragmentation
- Can cause performance problems with mechanical disks
- Larger seek times
- slow sustained I/O speeds
- not enough continuous free space for new data
![[Pasted image 20240505150109.png]]
## 10.5 Fragmentation solutions
- defragment as a maintenance task
- do background defragmentation
- techniques in filesystem to reduce fragmentation
	- needs large enough free space (ntfs)
- do not care about fragmentation as media is random-access
## 10.6 Filesystem limitations
- naming
	- character limits
	- case sensitivity
- path depth
- max file size
- max # of files in folder
## 10.7 Design limitation examples
- FAT filesystem
	- max vol.: 20TB (fat32)
	- 260 char limit for path+file names
	- 4GB max file size
	- 65536 files in single dir
	- no ACL's
- NTFS:
	- max vol.: 256TB
	- max file size: 256TB
	- max # files in volume: 4.294.967.295
	- max # files in single dir: idem
	- max file name + path length = 65535 char
		- soft limit: 255 (configureable)
## 10.8 Filesystem implementation: FAT
- FAT = File Allocation Table
	- 12; 16; 32
![[Pasted image 20240505150616.png]]
![[Pasted image 20240505150626.png]]
## 10.9 Filesystem implementation: NTFS
- $MFT (Master File Table)
![[Pasted image 20240505150652.png]]
![[Pasted image 20240505150658.png]]
## 10.10 Filesystem Features
### 10.10.1 Journaling
- What?
	- Keeping track of changes that have not yet been committed to disk in a sort of diary
- Why?
	- Bring filesystem online faster after system crash or power failure
- FSCK-type fixing of an FS would take long for larger filesystems
#### 10.10.1.1 Journaling Filesystems
- NTFS
- EXT3/4
#### 10.10.1.2 Non-Journaling Filesystems
- exFAT
- EXT2
### 10.10.2 Metadata
- Imperative for filesystem housekeeping
- Usable for application
	- Alternate data streams (ADS)
	- Data / Resource Fork
#### 10.10.2.1 Inodes
> An inode is a data structure on a filesystem on Linux that stores all the information about a file except its name and its actual data
- Metadata: data about file
## 10.11 Softlinks, hardlinks and inodes
![[Pasted image 20240505174907.png]]
### 10.11.1 Filesystem links
- Soft links or Symbolic links
- Hard links
	- Hard linking only possible within a filesystem

- Supported by:
	- EXT2/3/4
	- NTFS
![[Pasted image 20240505175008.png]]
## 10.12 Security (ACL's)
- Base ACL
	- Owner/group/other
- Extended ACL
	- Multiple UID/GID entries in ACL
- File ownership/group membership
![[Pasted image 20240505175057.png]]
## 10.13 Quota
- Limit amount of disk space
- Usable for different users/entities
## 10.14 Next-gen Filesystems
### 10.14.1 Support for large datasets
- Store larger files
- store more files
- on larger media
- Still in an efficient and performant way
### 10.14.2 Expandability / Scalability
- Storage migration is a problem
- Easily grow storage as need arises
- No need for full investment up front
- Not pinned down to initial sizing
### 10.14.3 Integrity
- Prevent bit-rot
- Detect faults
- recover from faults
### 10.14.4 Multi disk support
- Data redundancy
- Smart allocation of disks to data type and  use
- Integrated support for tiered storage
### 10.14.5 Snapshots
- Literally: photo
	- capture situation at certain point in time
- Storage snapshot:
	- 'photo' of situation
	- status of filesystem at certain point in time
### 10.14.6 Do we still need backups
- YES
### 10.14.7 Encryption
- Full disk encryption
- Careful of free space
- Contents not distinguishable from random data
- May be supported by disk controller (SED)
	- Self Encrypting Drive
### 10.14.8 Deduplication
- Works on block-level
- Store multiple copies of a same block just once
- Enormous gains when
	- multiple copies of same data exist
	- Example: multiple vm's
### 10.14.9 Data compression
- On the fly compression
- May improve performance if disk operation is slower than compression
### 10.14.10 Storage Overcommitment
- Have more "available" space than is actually backed by storage devices
- Count on deduplication or compression
- Add storage later when needed
- Not all provisioned storage will get used by all consumers
### 10.14.11 Shared storage filesystem
- Simultaneous access from different systems
- Need arbitration (locking)
- Examples:
	- VMFS
	- GFS (Global File System)
## 10.15 Noteworthy Filesystems
- FAT
- NTFS
- EXT2
- EXT3/4
- UDF (cd-rom/worm)
- HFS+ / APFS
### 10.15.1 OpenZFS
- Features:
	- Long term storage
	- checksum of all data and metadata
	- native RAID levels
	- All data gets written through copy-on-write
	- Snapshots
	- transparant compression
	- huge storage possibilliets
- 128 bits system
- Up to 256 quadrillion zettabytes
### 10.15.2 BtrFS
- Copy-on-write
- B+ tree filesystems
- Pooled storage (multiple devices)
- sub volumes
- snapshots
- deduplication
- compression
- dynamic resizing
### 10.15.3 ReFS
- Microsoft next-gen FS
- Not bootable
- B+ tree for metadata and files
- allocation-on-write
- resilience / integrity checking
- redundancy
- extemely large data pools
### 10.15.4 B+ Trees
- Binary search tree
- O log(n) for each operation
![[Pasted image 20240505180446.png]]
### 10.15.5 Windows Storage spaces
![[Pasted image 20240505180506.png]]
### 10.15.6 S3D: Storage spaces Direct
![[Pasted image 20240505180525.png]]
### 10.15.7 JFFS2
Also Yaffs/ F2FS
NAND Flash filesystem
JFFS(2): for RAW flash media
F²FS: for nand media with flash translation layer
### 10.15.8 NAND flash
- No mechanical delays
	- constant seek time for any block
- Wear leveling
- Block erasure
# 11 OS Virtualisation
## 11.1 Virtualisation
- What is virtualisation
- What is "the cloud"
- are these related?
### 11.1.1 Mainframes
- Mainframes have been virtualising for a long time
	- E.g.: IBM Z-System (LPAR)
![[Pasted image 20240505180816.png]]
### 11.1.2 Virtualisation
- Virtualisation <=> Emulation
- On desktop systems
	- Cross platform operations
	- Testing and development
- On Server systems:
	- Reducing TCO
	- Isolating Services and applications
	- Management and operations
### 11.1.3 Datacenter Virtualisation
- Redundancy
- Scalability
- Flexibility
- Upgradability
- Manageability
- Reduction of TCO (Total cost of ownership)
	- Increase utilisation of hardware
	- Decrease number of servers
	- Increase computing density (reduce floorspace)
	- Decrease power usage for same workload
	- Decrease power usage for same workload
	- Decrease cooling requirements
### 11.1.4 Virtualised desktops
- Not the same as virtualisation on desktop computers
- VDI = Virtual Desktop Infrastructure
- Run client OS on virtualisation platform
- Connect to it with PC or thin client
- Manageability
- Security
### 11.1.5 Container Virtualisation
- Run containers instead of full OS
- Provide application isolation
- Consistent resources
- Development/deployment
### 11.1.6 Abstract Computers
- Platforms that do not necessarily exist
- Made as abstraction layer
	- JVM (Java Virtual Machine)
	- .NET framework
- JVM implemented on any architecture can run java software
### 11.1.7 Virtualisation technology
- Hypervisors
- Supervisor software runs system software above application
	- Functionality of kernel
- Hypervisor runs system above os kernel
	- Manages resource sharing between simultaneously running kernel+OS
#### 11.1.7.1 Hypervisors
- 2 types
	- Type 1: Bare-metal hypervisor
	- Type 2: Hosted Hypervisor
![[Pasted image 20240505181605.png|350]]![[Pasted image 20240505181610.png|350]]
#### 11.1.7.2 hardware assisted Virtualisation
- we had protection levels implemented in CPU
- Now we need a protection level above ring 0
- 2 solutions for type 1 hypervisor
	- Trick OS and run guest OS in ring 1, hypervisor in ring 0
	- Modify CPU architecture and introduce increased protection levelµ
#### 11.1.7.3 Protection rings
- Run OS in ring 1
- Hypervisor in ring 0
- Use binary translation to trick guest OS
- Only possible for x86 OS (32bit)
- Hardware virtualisation extensions
![[Pasted image 20240505181909.png]]
#### 11.1.7.4 Nested virtualisation
- hypervisor in virtualised environment?
- pass hardware virtualisation to virtual CPU in guest hypervisor
![[Pasted image 20240505181950.png]]
#### 11.1.7.5 VMware ESXi
- Type 1
- Hypervisor needs to manage hardware
- Needs drivers to interface with hardware and provide virtual hardware to guest OS
- VMware HCL
#### 11.1.7.6 Microsoft HyperV
![[Pasted image 20240505182050.png]]
#### 11.1.7.7 HyperV driver model
- Hardware drivers in primary partition
- Regular windows drivers
![[Pasted image 20240505182122.png]]
## 11.2 Application Abstraction Layers
### 11.2.1 Abstraction Layers
![[Pasted image 20240505182558.png]]
#### 11.2.1.1 Hardware
- Computing device
- Functions set in stone
- Desktop calculator
#### 11.2.1.2 Application
- Application software runs on hardware
- Machine code
- Programmable calculator
#### 11.2.1.3 System Firmware
- Compiler toolchains
- stdlib
- Enhanced portability
- Firmware for hardware initialisation and some functional abstraction
- BIOS
#### 11.2.1.4 Operating System
- Provides
	- Operational API's
	- Hardware initialisation
	- Application loading
- DOS-era type computer
- Single tasking
#### 11.2.1.5 OS lib's
- Multitasking OS
- run multiple applications
- Provides shared libs for applications
- Printing
#### 11.2.1.6 Application Frameworks
- Crossplatform development
- Abstraction of OS API's
- Consistent UX/UI
### 11.2.2 Containerisation 
- Run multiple OS root filesystems under single kernel
- Share kernel for multiple 'rest of the OS' + application
![[Pasted image 20240505182808.png]]
![[Pasted image 20240505182837.png]]
![[Pasted image 20240505182851.png]]
![[Pasted image 20240505182900.png]]
![[Pasted image 20240505182914.png]]
# 12 Virtualised Hardware