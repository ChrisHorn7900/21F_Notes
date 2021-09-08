# Computer Architecture and Organization
### Intro to Computer Organization

### This Week: Intro to computer organization
- compiling C Programs and Dynamic Allocations

### Header File
- header files include function declarations:
    - stdio.h
    - stdlib.h
    - ...
- preprocessor 

### A Quick digression about the compiler
- compilation occurs in two steps: preprocessing and compiling
- in preprocessing, source code is expanded into a larger form that is simpler for the compiler to understand. any line that states with # is a ling that is interpreted by the preprocessor
    - include files are pasted in (#include)
    - macros are expanded (#define)
    - comments are stripped out (/* */, //)
    - continued lines are joined ('\')

include "headerfile.h"

- header files are formatted for each function:
    - datatype functionname(datatype);

gcc -c main.c utils.c
gcc main.o utils.o utils.h -o main.out
./main.out

### Memory Layout
- when defining an array, the space allocated is determined at the cimpilation stage, and will be stored in Stack when running
- sometimes we don't know how large the space is to allocate at compilation stage until run-time;
- in C we use tjhe malloc function:
    int arr_len;
    scanf("%d", &arrlen);
    int* dynamic_array = \
        (int*)malloc(sizeof(int) * arr_len);
    free(dynamic_array);
    
    - malloc function will allocate the space in the heap area during runtime
    - calcuclate how many bytes for the data type. Warning: its not used for

    - use free function to "delete" the allocated space
### Technology trends
- electronics technology continues to evolve
    - increased capacity and performance
    - reduced cost
