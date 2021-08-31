# CS-382 Computer Architecture and Organization
- Professor Shudong Hao

## This week: overview and C
- overview, logistics, and linux basics
- C basics
- C pointers

## Classes of Computers
- personal computers
    - general purpose, variety of software
    - subject to cost/performance tradeoff
- server computers
    - network based
    - high capacity, performance, reliability
    - range from small servers to building size
- supercomputers
    - high-end scientific and engineering calculations
    - highest capability byt represent a small fraction of computers on the market
- embedded computers
    - hidden as components of systems
    - stringent power/performance/cost constraints

## The Post PC Era
- personal mobile device (PMD)
    - battery operated
    - connects to the internet
    - hundreds of dollars
    - smart phones, tablets, electronic glasses
- cloud computing
    - warehouse scale computers (WSC)
    - software as a service (SaaS)
    - portion of software run on a PMD and a portion run in the cloud
    - Amazon and Google

## What you will learn
- How programs are translated into the machine language
    - and how the hardware executes them
- the hardware/software interface
- what determines program performance
    - and how it can be improved
- how hardware designers improve performance
- what is parallel processing

## Eight Great Ideas
### design for Moore's Law
### use Abstraction to simplify
### make the Common Case Fast
### performance via Parallelism
### performance via Pipelining
### performance via Prediction
### Hierarchy of memories
### Dependability via redundancy

## Basic Microcomputer design
- clock synchronizes CPU functions
- Control Unit (CU) coordinates sequence of execution steps
- ALU performs arithmetic and logic operations
- the memory storage unit holds instructions and data for a running program
- a bus is a group of wires that transfer data from one part to another (data, address, control)

## Abstractions for Computers
- Level 5 - High-level language
- Level 4 - Assembly language
- Level 3 - Operating System
- Level 2 - Instruction Set Architecture
- Level 1 - Microarchitecture
- Level 0 - Digital logic

## Below Your Program
- application software: written in high-level language
- system software
    - compiler: translates HLL code to machine code
    - operating system: service code
        - handling input/output
        - managing memory and storage
        - scheduling tasks and sharing resources
- hardware: processor, memory, I/O controllers

## Levels of Programming
- high-level language:
    - level of abstraction closer to problem domain
    - provides for productivity and protability
- assembly language
    - textual representation of instructions
- hardware representation
    - binary digits (bits)
    - encoded instructions and data

## Abstractions
- abstraction helps us deal with complexity
    - hide lower-level detail
- instruction set architecture (ISA)
    - the hardware/software interface
- application binary interface
    - the ISA plus system software interface
- implementation
    - the detail underlying and interface

# C Programming
- Brian Kernhighan and Dennis Ritchie
    - the C Programming Language, second edition, prentice hall, 1988
    - still the best book about C, from the originators
