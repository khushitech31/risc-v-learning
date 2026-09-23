Table of Contents
1. Introduction: The Digital World Around Us
2. What Are Processors?
3. Binary and Data Representation
4. Registers: The Processor's Workspace
5. Memory System Architecture
6. Processor Execution Models
7. RISC-V Instruction Set Architecture (ISA)
8. Control Flow and Program Structure
9. Advanced RISC-V Features and Extensions
10. Practical RISC-V Programming
11. Development Tools and Resources
12. Future of RISC-V and Career Opportunities
13. Conclusion

1. Introduction: The Digital World Around Us
After reading this chapter, I understood that processors are everywhere - smartphones, laptops, cars, home appliances. Every smart device has a processor inside.

Technology Hierarchy - I understood this as a 10-floor building:
Floor 10: Applications (Instagram, WhatsApp, Games)
Floor 9: Programming Languages (Python, Java)
Floor 8: Operating Systems (Android, Linux)
Floor 7: Software Libraries
Floor 6: Compilers
Floor 5: Assembly Language -> RISC-V defines this level
Floor 4: Processor Architecture -> RISC-V ISA
Floor 3: Digital Logic Design
Floor 2: Transistors
Floor 1: Silicon Manufacturing

RISC-V defines Floor 4 and 5, which is the interface between hardware and software.

2. What Are Processors?
Processor is often called the brain, but I learned it is more like a very fast simple calculator.

What a Processor CAN do: Arithmetic, Logic (AND, OR), Comparison, Memory Access, Decision Making, I/O

What it CANNOT do directly: Understand human language, See or hear, Learn or adapt - all need software.

Instruction Cycle: Fetch -> Decode -> Execute -> Memory Access -> Write Back

Performance: Clock Speed (GHz) _ IPC (Instructions Per Cycle). CPU Time = (Instruction Count _ CPI) / Clock Rate

3. Binary and Data Representation
Why Binary? Because transistors have only two stable states - ON (1) and OFF (0).

Number Systems: Binary (base-2), Hexadecimal (base-16). 1 Hex digit = 4 binary bits.

Signed vs Unsigned: Unsigned is only positive. Signed uses 2's complement for negative numbers. -1 is all 1s (0xFFFFFFFF).

4. Registers: The Processor's Workspace
Registers are fastest memory inside CPU. RV32 has 32 registers (x0 to x31).
Register	ABI Name	Usage
x0	zero	Always 0
x1	ra	Return Address
x2	sp	Stack Pointer
x3	gp	Global Pointer
x4	tp	Thread Pointer
x5-x7	t0-t2	Temporary caller-saved
x8	s0/fp	Saved / Frame Pointer
x9	s1	Saved
x10-x11	a0-a1	Args and Return values
x12-x17	a2-a7	Args 3-8
x18-x27	s2-s11	Saved callee-saved
x28-x31	t3-t6	Temporary
Calling Convention: Callee-saved registers must be saved in Prologue and restored in Epilogue.

5. Memory System Architecture
Memory Hierarchy Trade-off: Fast memory is expensive and small, slow memory is cheap and large.

Registers (0.1 ns) > L1 Cache (1-2 ns) > L2 Cache (5-10 ns) > L3 Cache (20-50 ns) > Main Memory (50-100 ns) > SSD (0.1 ms)

Virtual Memory: Each program thinks it has full 0x00000000 to 0xFFFFFFFF, but MMU translates virtual address to physical using Page Table and TLB.

Cache-friendly code (row-major) is 10x-100x faster than cache-unfriendly.

6. Processor Execution Models
1. In-Order Execution: Executes exactly in program order. Simple, low power, but stalls on memory wait.
2. Out-of-Order Execution: Executes when data is ready. High performance but complex hardware (Reorder Buffer, Register Renaming).
3. Specialized: VLIW (compiler packs multiple ops), Dataflow, Vector Processors (one instruction on 1000 elements - important for AI/ML).

7. RISC-V ISA Deep Dive
RISC-V is Load/Store Architecture - cannot operate directly on memory. Must load to register, compute, store back.

Why 32-bit Fixed Width? Simple to decode, predictable fetch, easy pipelining.

Formats:
R-Type: add x1, x2, x3 - [funct7 | rs2 | rs1 | funct3 | rd | opcode]
I-Type: addi x1, x2, 10, lw x1, 0(x2)
S-Type: sw x1, 0(x2)
B-Type: beq x1, x2, label
U-Type: lui x1, 0x12345
J-Type: jal x1, label

8. Control Flow and Program Structure
Branches: beq, bne, blt, bge, bltu, bgeu
Jumps: jal, jalr

Loops are made with labels and branches. Triple nested loop 100x100 = 1M iterations * 20 instructions = 20M instructions.

9. Advanced RISC-V Features and Extensions
Modular ISA: Base is RV32I (47 instructions), add extensions as needed.
Extension	Purpose
I	Base Integer (required)
M	Multiply/Divide - MUL, DIV, REM
A	Atomic - LR.W, SC.W, AMO - for multi-core sync
F	Single Float 32-bit
D	Double Float 64-bit
C	Compressed 16-bit - saves 30% code size
V	Vector - for AI/ML
Zicsr	CSR
Zifencei	Fence
M is separate because Multiply needs large hardware and is slow.

Atomic: lr.w (Load-Reserved) and sc.w (Store-Conditional) used to build locks.

10. Practical RISC-V Programming
Data Structures in assembly: Dynamic Array (base, size, capacity), Linked List, Stack using sp.

Algorithms: Bubble Sort, Quick Sort in assembly.

Pseudo-instructions: li, mv, ret, nop - converted by assembler.

11. Development Tools and Resources
Online: Venus (venus.cs61c.org), RARS
Local: riscv-gnu-toolchain, Spike (spike pk http://a.out), GDB
Visual: Ripes - pipeline visualizer

Essential Repos:
riscv-isa-sim, TheThirdOne/rars, mortbopet/Ripes, ucb-bar/riscv-sodor, chipsalliance/rocket-chip, riscv-boom/riscv-boom, lowRISC/ibex, riscv-pk, mit-pdos/xv6-riscv, riscv-tests

12-Week Plan: Week1-2 Hello World, Week3-4 Calculator, Week5-6 Arrays, Week7-8 Sorting, Week9-10 File I/O, Week11-12 Interrupts & Shell.

12. Future and Career
Industry Adoption:
Now: Embedded/IoT, Storage - Production
2024-2025: Network Infra
2025-2027: Automotive
2025-2028: Data Center/Server
2027-2030: Mobile

Career:
Hardware: Processor Design Engineer ($120k-$250k+), SoC Integration - Verilog/VHDL - Companies SiFive, Ventana
Software: Embedded, Compiler Developer (GCC/LLVM), OS Developer
Emerging: Verification Engineer, Security, AI Accelerator

Advantage: No license fees, no vendor lock-in, open, customizable.

13. Conclusion
What I accomplished:
1. Mastered Fundamentals: binary, registers, memory
2. Learned ISA: instruction types, addressing modes
3. Explored Advanced: OoO, VLIW, Vector, extensions
4. Gained Practical Skills: assembly, debugging
5. Built Dev Environment
6. Understood Industry Context

RISC-V is future - Democratization, Innovation, Collaboration, Sustainability.

Reference: RISC-V Architecture Tutorial by Nikhil Kumar Rajput
Author (Khushi Kumari)
