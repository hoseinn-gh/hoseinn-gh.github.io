---
title: "32-bit RISC-V Von Neumann Processor"
excerpt: "A RISC-V core supporting the full RV32IM instruction set, with a two-pass assembler written from scratch."
collection: portfolio
---

A 32-bit RISC-V processor built in Logisim Evolution, together with the
toolchain needed to run programs on it. The processor supports the full RV32IM
instruction set, the base 32-bit integer instructions plus the multiply and
divide extension.

## Architecture

The core uses a Von Neumann organization, meaning instructions and data share a
single memory rather than living in separate instruction and data memories. This
is closer to how real systems are organized, but it introduces a structural
hazard: the processor may need to fetch an instruction and access data in the
same cycle, and there is only one memory port to do it with. The design resolves
this by splitting each cycle into two phases, so fetch and data access never
contend for the port.

Execution can be stepped one instruction at a time, which makes it possible to
watch register and memory state change and to trace exactly where a program
diverges from expectation.

## Toolchain

Hardware alone is not enough to run anything, so the project includes a two-pass
assembler written in C++. The first pass walks the source to resolve label
addresses, and the second emits machine code, expanding pseudo-instructions and
handling assembler directives along the way. The output is a memory image that
loads directly into the processor's RAM.

Writing the assembler alongside the processor meant both sides of the
hardware-software boundary had to agree exactly on instruction encoding, which
turned out to be a useful way to find bugs in the decoder.

[Source on GitHub](https://github.com/hoseinn-gh/von_neumann_risc_V)
