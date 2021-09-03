# Pointers
- see CS-382 notes taken on September 3 for further detail, they are pretty much the same thing aside from specific syntax

    int main() {
        int x; // type: integer
        x = 5;
        int *z; // pinter to integer
        z = '&'x; // stores the address of x into z
        x = 7;
        or
        // if z == &x, then *z == x
        z* = 7; // same as x = 7;
        return 0;
    }

- always make sure that you know what your pointers are pointing to
    - doing so can crash your program or return garbage that processes with the program
    - only change the address of the pointer to an address that is already being used by something that you declared
- gdb
    - gnu debugger
    - (gdb ./<'programName>)
    - run and any program specific arguments to run debugger
        - the debugger will tell you which lines it hits that have a problem
    - type q to quit