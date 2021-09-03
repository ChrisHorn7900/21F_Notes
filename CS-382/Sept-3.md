# Memory
- "real" memory
    - is complicated
    - it involves electronics, semiconductors, physics, etc.
    - its not terribly relevant at this point
- "virtual" memory
    - the notion of memory as used by programs
    - it involves logical concepts
    - its how you should think about memory (most of the time)

## Virtual Memory
- its a large aray of bytes
    - one byte is eight bits
    - an int is four consecutive bytes - so is a float
    - a char is one byte
- the array index of a byte is its address
    - the address of a larger item is the index of its first byte

## Memory Addressed in C
- you can get the memory address of any variable
- just use the operator **&**

# C Pointers
- what is a C pointer?
    - a variable that holds an address
    - works like variables holding object addresses in java
- pointers in C are "typed"
    - pointer to an int
    - pointer to a char
    - pointer to a float
    - pointer to whatever you can define

    int main() {
        int a = 4;
        int* ptr = "&"a;
        printf("%p\n", ptr);
        return 0;
    }

- an array name represents the pointer to the first element of te array

    int a[3];
    int* ptr = a;

    - the following are equivalent:
        - *(ptr + 2);
        - a[2];
    - the following are equivalent:
        - ptr + 2;
        - &a[2];

## Deferencing C Pointers
- deference pointers
    - accessing/ modifying the value pointed to by a pointer

        int main() {
            int a = 4;
            int* ptr = "&"a;
            printf("%d\n", a);
            printf("%d\n", *ptr);
            *ptr = *ptr + 1;
            printf("%d\n", a);
            printf("%d\n", *ptr);
            return 0;
        }