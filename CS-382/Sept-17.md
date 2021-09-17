## Logical Operations
- Instructions for bitwise manipulations

        Operation       C       Java        LEGv8
        Shift left      <<      <<          LSL
        Shift right     >>      >>          LSR
        Bit-by-bit AND  &       &           AND, ANDI
        Bit-by-bit OR   |       |           OR, ORI
        Bit-by-bit XOR  ~       ~           EOR, EORI

    - Useful for extracting and inserting groups of bits in a word 
    - Shifting left by *i* bits gives the identical result as multiplying by 2^i
        - LSL by 6 is the same as multiplying by 2^6 or 64

## Shift Operations

    opcode: 11 bits
    Rm: 5 bits
    shamt: 6 bits
    Rn: 5 bits
    Rd: 5 bits

- shamt: how many positions to shift
- Shift left logical:
    - Shift left and fill with 0 bits
    - LSL by *i* bits multiplies by 2^i
- Shift right logical:
    - Shift right and fill with 0 bits
    - LSR by *i* bits divides by 2^i (unsigned only)

## AND Operations
- Useful to mask bits in a word
    - Select some bits, clear others to 0

            AND X9, X10, X11

## OR Operations
- Useful to include bits in a word
    - Set some bits to 1, leave others unchanged

            OR X9, X10, X11

## EOR Operations
- Differencing operation

        EOR X9, X10, X12 // X9 = X10 ^ X12

## Moving Constants
- Most constants are small
    - 12-bit immediate is sufficient
- For the occasional 32-bit constant
    - MOVZ: move wide with zeroes
    - MOVK: move wide with keep
- Use with flexible second operand (shift)

## Stored Program Computers
- Instructions represented in binary, just like data
- Instructions and data stored in memory
- Programs can operate on programs
    - e.g. compilers, linkers
- Binary compatibility allows compiled programs to work on different computers
    - Standardized ISAs

## Represented Instructions
- Instructions are encoded in binary
    - Called machine code
- LEGv8 instructions:
    - Encoded as 32-bit instruction words
    - Small number of formats encoding operation code (opcode), register numbers, ...
    - Regularity!

## LEGv8 R-format Instructions
- Instruction fields:
    - opcode: operation code
    - Rm: the second register source operand
    - shamt: shift amount
    - Rn: the first register source operand
    - Rd: the register destination

## LEGv8 D-format Instructions
- Load/store instructions:
    - Rn: base register
    - Address: constant offset from contents of base register (+/- 32 doublewords)
    - Rt: destination (load) or source (store) register number
- Design Principle 3: Good design demands good compromises
    - Different formats complicates decoding, but allow 32-bit instructions uniformly
    - Keep formats as similar as possible

## LEGv8 I-format Instructions
- Immediate instructions
    - Rn: source register
    - Rd: destination register
- Immediate field is **zero-extended**
            