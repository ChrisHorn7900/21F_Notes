## Understanding Performance
- Algorithm:
    - Determine number of operations executed
- Programming language, compiler, architecture:
    - Determine number of machine instructions executed per operation
- Processor and memory system:
    - Determine how fast instructions are executed
- I/O system (indluding OS):
    - Determine how fast I/O operations are executed

## Performance Response Time and Throughput
- Response time:
    - How long it takes to do a task
- Througput
    - Total work done per unit time
        - e.g. tasks/ transactions/ ... per hour
- How are response time and throughput affected by
    - Replacing the processor with a faster version?
    - Adding more processors?
- We'll focus on response time for now...

## Relative Performance
- Define Performance = 1 / Execution Time
- "X is *n* times faster than Y"

        Performance x / Performance y

        = execution time y / execution time x

        = *n*

- Example: time taken to run a program: 10s on A, 15s on B;

        Execution Time B / Execution Time A
        
        = 15s / 10s = 1.5

        So A is 1.5 times faster than B

## Measuring Execution Time
- Elapsed time:
    - Total response time, including all aspects
        - Processing, I/O, OS overhead, idle time
    - Determines system performance
- CPU time
    - Time spent processing a given job
        - Discounts I/O time, other job's shares
    - Comprises user CPU time and system CPU time
    - Different programs are affected differently by CPU and system performance

## Cpu Clocking
- Operation of digital hardware governed by a constant-rate clock:
- Clock period: duration of a clock cycle
    - e.g. 250ps = 0.25ns = 250x10^-12s
    - Picosecond is one trillionth of a second
- Clock frequency (rate): cycles per second
    - e.g. 4.0Ghz = 4000Mhz = 4.9x10^9Hz

## CPU Time
    CPU time = CPU clock cycles * Clock cycle time
             = CPU clock cycles * (1 / Clock cycle rate)
- Performance improved by
    - Reduced number of clock cycles
    - Increasing clock rate
    - Hardware designer must often trade off clock rate against cycle count

## CPU Time Example
- Computer A: 2Ghz clock, 10s CPU time
- Designer Computer B:
    - Aim for 6s CPU time
    - Can do faster clock, but causes 1.2 x clock cycles
- How fast must Computer B's clock be?

        Clock cycles A = CPU time A * Clock rate A
                       = 10s * 2GHz
                       = 2x10^10
        Clock rate B = Clock cycles B / CPU time B
                     = 1.2 * Clock cycles A / 6s
                     = 2.4x10^10 / 6s = 4GHz

## Instruction Count and CPI
- Instruction Count for a program
    - Determined by program, ISA and compiler
- Average Cycles Per Instruction (CPI):
    - Determined by CPU hardware
    - If different instructions have different CPI
    - Average CPI affected by instruction mix

## Instruction Count and CPI
    CPU time = CPU clock cycles * Clock cycle time
             = CPU clock cycles * 1 / Clock cycle rate
    Clock cycles = Instruction count * CPI
                 = Instruction count * CPI * Clock cycle time
                 = Instruction count * CPI / Clock rate

## CPI Example
- Computer A: Cycle Time = 250ps, CPI = 2.0
- Computer B: Cycle Time = 500ps, CPI = 1.2
- Same ISA (what does this mean?)
- Which is faster, and by how much?

        CPU time A = IC * CPI A * Clock cycle time A
                   = IC * 2.0 * 250ps = IC * 500ps

        CPU time B = IC * CPI B * Clock cycle time B
                   = IC * 1.2 * 500ps = IC * 600ps
        
        CPU time B / CPU time A = (IC * 600ps) / (IC * 500ps) = 1.2

## CPI in More Detail
- If different instruction classes take different numbers of cucles (assume *n* instruction classes):

        Clock cycles = Σ(CPIi * ICi) n times where i=1
- Weighted average CPI:

        CPI = Clock cycles / Instruction Count
            = Σ(CPI i * Instruction Count i / Instruction Count) n times where i=1

## Performance Summary
- Performance depends on:
    - Algorithm: affects IC, possibly CPI
    - Programming language: affects IC, CPI
    - Compiler: affects IC, CPI
    - Instruction set architecture: affects IC, CPI, and Clock Rate
    