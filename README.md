# 🚀 RISC-V Journey

> Exploring Computer Architecture through RISC-V Assembly.

This repository documents my journey of learning and experimenting
with the RISC-V Instruction Set Architecture (ISA).

Instead of only studying the theory, I am trying to understand
how instructions, registers, memory and control flow work by
implementing and testing small programs using the Venus Simulator.

## 🎯 Objectives

- Understand the fundamentals of RISC-V architecture
- Learn RISC-V assembly language
- Explore registers and instruction formats
- Understand memory operations and control flow
- Implement small assembly programs
- Experiment with the Venus Simulator
- Document observations and learnings

  # What Are Processors?

A processor is a hardware component that executes instructions
and performs operations on data.

## Basic Capabilities

- Arithmetic
- Logic
- Comparison
- Memory Access
- Decision Making
- Input/Output

## What a Processor Cannot Do Directly

A processor does not directly understand human language.
Software and other systems translate human-level tasks into
instructions that the processor can execute.

## What is RISC-V?

RISC-V is an Instruction Set Architecture (ISA) based on
Reduced Instruction Set Computer (RISC) principles.

## Why RISC-V?

- Open standard
- Modular design
- Simple instruction structure
- Useful for education and research

# 🗃️ RISC-V Registers

Registers are small and fast storage locations inside the processor.
They are used to hold data and intermediate results while instructions
are being executed.

## General-Purpose Registers

RISC-V provides **32 general-purpose registers**, named:

`x0` to `x31`

Each register can store a value that can be used by instructions.

---

## 🔹 The Special `x0` Register

The `x0` register is special because it **always contains 0**.

Any value written to `x0` is ignored.

### Example

```asm
add x5, x3, x0
x5 = x3 + 0
x5 = x3

**so, x0 can be useful for copying values.**
### Instruction Execution Cycle

**A processor repeatedly follows these basic steps:

1. FETCH
2. DECODE
3. EXECUTE
4. WRITEBACK
5. REPEAT**



