# Computer Architecture and Organization
### Intro to Computer Organization

### This Week: Intro to computer organization
- compiling C Programs and Dynamic Allocations
- Evaluating the Performance of Processors

### Header File
- header files include function declarations:
    - stdio.h
    - stdlib.h
    - ...
- preprocessor will insert the header file into the C file

### A Quick digression about the compiler
- compilation occurs in two steps: preprocessing and compiling
- in preprocessing, source code is expanded into a larger form that is simpler for the compiler to understand. any line that states with # is a ling that is interpreted by the preprocessor
    - include files are pasted in (#include)
    - macros are expanded (#define)
    - comments are stripped out (/* */, //)
    - continued lines are joined ('\')
- The compiler then converts the resulting text into binary code the CPU can run directly

        #include <headerfile.h> 

- header files are formatted for each function:
    - datatype functionname(datatype);

- compile and generate object files for each source file

        gcc -c main.c utils.c

- link object files and generat executable

        gcc main.o utils.o -o a.out

### Memory Layout
- stack ;
    - runtime stack
    - e.g. local variables
- heap:
    - dynamically allocated as needed
- data:
    - statically allocated data
    - e.g globabl vars, static vars, string constants
- text/shared libraries:
    - executable machine instructions
    - read-only
- when defining an array, the space allocated is determined at the compilation stage, and will be stored in Stack when running
- sometimes we don't know how large the space is to allocate at compilation stage until run-time;
- in C we use the malloc function:

        int arr_len;
        scanf("%d", &arrlen);
        int* dynamic_array = \
            (int*)malloc(sizeof(int) * arr_len);
        free(dynamic_array);
    
    - malloc function returns void*, so we need to explicitly convert it back to int*
    - malloc function will allocate the space in the heap area during runtime
    - calcuclate how many bytes for the data type. Warning: its not used for calculating an array's size

    - use free function to "delete" the allocated space

            free(dynamic_array);
### Technology trends
- electronics technology continues to evolve
    - increased capacity and performance
    - reduced cost

### Silicone Wafers
- silicone ingots are sliced into wafers
- after a series of 20-40 steps the wafers are patterned
- each die on the wafer is tested
- the wafer is broken up into each die and the dies that failed the test are removed

### Dies per Wafer
- How many dies are on a 20-cm diagonal wafer if the die size is 1.5 x 1.5 cm?

        wafer area = pi * r^2
                   = 3.14 * (20/2)^2
                   = 314
        die area  = 1.5 * 1.5
                  = 2.25
        #dies = (wafer area/die area)
              = 139

### Die Yields

    yield = 1/(1 + (defects per area * die area))^2

- assuming wafer yield is 100%
- defects per sq cm is 0.03
- what are the die yields of the 1x1 cm and 1.5x1.5 cm dies?

### Die Costs

    cost per die = cost per wafer/(dies per wafer * yield)

- if the cost of a wafer is $5000, what is the cost of a 1x1 cm and 1.5x1.5 cm in the previous examples?
- for 1x1 the cost:
    - 5000/(314 * 0.94) = $16.94
- for 1.5x1.5 the cost:
    - 5000/(139 * 0.87) = $41.35
- 1.5x1.5 costs 41.35/16.94 = 2.44 times more

### Integrated Circuit Cost
- nonlinear relation to area and defect rate:
    - wafer cost and area are fixed
    - defect rate determined by manufacturing process
    - die area determined by architecture and circuit design
    - note that the above formula has ignored all the wasted non-squares around the perimeter of the wafer