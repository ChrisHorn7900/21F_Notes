# Machine Programming(1): Instruction Sets

## Today: Instruction Sets
- Turning C into Executable
- ARMv8 (& LEGv8) Instruction Sets Overview
- Registers and Arithmetic Operators
- Memory Operations
- Logical Operations
- Moving Constants
- Representing Instructions

## Turning C into Executable
- Assembler
    - Translates .s into .o
    - Binary encoding of each instruction
    - Nearly-complete image of executable code
    - Missing linkages between code in different files
- Linker
    - Resolves references between files
    - Combines with static run-time libraries
        - e.g., code for malloc, printf, etc...
    - Some libraries are dynamically linked
        - Linking occurs when program begins execution

## Assembly/Machine Code View
- Programmer-Visible State:
    - Components in the CPU that we, as programmers, can write a program to control or monitor
    - PC: Program counter
        - Address of next instruction
    - Register file
        - Heavily used program data
    - Condition codes
        - Store status information about most recent arithmetic or logical operation
        - Use for conditional branching
    - Memory:
        - Byte addressable array
        - Code and user data
        - Stack to support procedures

## Definitions
- **Architecture (also ISA: instruction set architecture):** The parts of a processor design that one needs to understand or write assembly/machine code
    - Examples: instruction set specification, registers
- **Microarchitecture:** Implementation of the architecture
    - Examples: cache sizes and core frequency
- **Code Forms:**
    - Machine Code: The byte-level programs that a processor executes
    - Assembly Code: A text representation of machine code

## Instruction Set
- The repertoire of instructions of a computer
- Different computers (or processors) have different instruction sets:
    - But with many aspects in common
- Early computers had very simple instruction sets
- Many modern computers also have simple instruction sets
- Example ISAs:
    - Intel: x86, IA32, Itanium, x86-64
    - ARM: Used in almost all mobile phones

## The ARMv8 Instruction Set
- A subset, called LEGv8, used as the example throughout the book
- Commercialized by ARM Holdings (www.arm.com)
- Large share of embedded core market
    - Applications in consumer electronics, network/storage equipment, cameras, printers, ...
- Typical of many modern ISAs:
    - See ARM Reference Data tear-out card

## Terminologies
- Opcode (verb) - what operation to perform
- Operands (noun) - what to operate upon
- Source Operands - where values come from
- Destination Operand - where to deposit data values

## Arithmetic Operations (Example)
- Add and subtract, three operands:
    - One destination and two sources
    - ADD a, b, c // a = b + c
- All arithmetic operations have this form
- **Design Principle 1: Simplicity favors regularity**
    - Regularity makes implementation simpler
    - Simplicity enables higher performance at lower cost
- **Only one arithmetic operation** per assembly instruction
    - There are some advanced cases
- In C/Java/... you can write a complex instruction
    - f = (g + h) - (i + j);
- You need more than one instruction to do the same in assembly

        ADD t0, g, h // temp t0 = g + h
        ADD t1, i, j // temp t1 = i + j
        SUB f, t0, t1 // f = t0 - t1

## Register Operands
- Arithmetic instructions use register operands
- LEGv8 has a 32 x 64-bit register file
    - Use for frequently accessed data
    - 64-bit data is called a "doubleword"
        - 31 x 64-bit general purpose registers X0 to X30
    - 32-bit data called a "word"
        - 31 x 32-bit general purpose sub-registers W0 to W30
- **Design Principle 2: Smaller is faster**
    - c.f. main memory: millions of locations

## Arithmetic Operations (Continued)
- C code:
    
        f = (g + h) - (i + j)
- Assume we store those numbers in registers X20 to X23, and we want to store the result in X19
- Compiled LEGv8 code:

        ADD X9, X20, X21
        ADD X10, X22, X23
        SUB X19, X9, X10

## Registers vs. Memory
- Registers are faster to access than memory
- Operating on memory data requires loads and stores
    - More instructions to be executed
- Compiler must use registers for variables as much as possible
    - Only spill to memory for less frequently used variables
    - Register optimization is important!

## Byte-Oriented Memory Organization
- Programs refer to data by address:
    - Conceptually, envision it as a very large array of bytes
        - In reality, it's not, but can think of it that way
    - An address is like an index into the array
        - and, a pointer variable stores an address

## Machine Words
- Any given computer has a "Word Size"
    - Nominal size of integer-valued data
    - and of addresses
- Until recently, most machines used 32 bits (4 bytes) as word size
    - Limits addresses to 4GB (2^32 bytes)
- Increasingly, machines have 64-bit word size
    - Potentially, could have 18 EB (exabytes) of addressable memory
    - That's 18.4x10^18
- Machines still support multiple data formats
    - Fractions or multiples of word size
    - Always integral number of bytes
