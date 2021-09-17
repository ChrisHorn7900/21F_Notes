- Suppose we have a string of lowercase characters "abca". We want to determine if all the characters are unique.
- Obvious solution: loop over each character one by one and check whether it appears anywhere in the rest of the string or not:

        int main() {
            string s;
            cin >> s;
            size_t n = s.length();
            for (size_t i = 0; i < n; i++){
                for (size_t j = i + 1; j++){
                    if (s[i] == s[j]){
                        cout << "Not unique" << endl;
                        return 0;
                    }
                }
            }
            cout << "unique" << endl;
            return 0;
        }

- Run time = O(n^2) so not very fast

- we can use an unordered map in C++, which is a hash table, to keep track of which characters we have already seen (using characters as the keys and booleans as the values). The run time is then O(n) but the overhead of computing the hash function for keys that are single characters will be high so the linear term in the run time will have a high constant in practice.
- Alternatively, we can use an array of booleans to keep track of which characters we have already seen (using the character - 'a' as the index). Now there is no need to compute any hash function and array look-ups are done in Θ(1) running time. So the overall algorithm is still O(n) (with a small constant for the linear term) but we use more memory for the array than strictly necessary: each array element needs to be addressable in memory so a bool uses a whole byte of memory rather than a single bit. So we are using 8 times more memory than we actually need to.

# Bitwise and Bitshifting Operations

## Bitshifting:
- << means left shift
- ">>" means right shift
- Let's use only 8 bits for brevity, and start with unsigned integers
- Left shift:
    - unsigned int a = 11; a << 1;
    - 00001011 (11)
    - << 1 ==
    - 00010110 (22)
    - so a << 1 == 22.
- Shifting all the bits of an unsigned integer to the left by 1 position is equivalent to integer multiplication by 2. The old leftmost bit is lost, the new rightmost bit is zero.
- You can obiously shift by more than one position at a time: if the variable a is 11 then a << 3 == 88 (shifting to the left by 3 positions is equivalent to multiplying by 2^3). Shifting by a negative number of positions is undefined.

- Right shift:
    - unsigned int a = 11; a >> 1;
    - 00001101 (11)
    - '>> 1 ==
    - 00000110 (5)
    - so a >> 1 = 5.
- Shifting all the bits of an unsigned integer to the right by 1 is dividing an integer by 2. The old rightmost bit is lost, the new leftmost bit is 0.
- Things are slightly more complicated for signed integers, in the case when integers are negative. Technically speaking, shifting a negative integer 
- -5 << 1 == -10
- still works like multiplying by 2. the process is just more complicated with 2's complicated


- Back to checking whether a string is made of unique characters:
- Take the string 'aba'
- We'll start with the first (leftmost) character 'a'

        unsigned int vector = 0
        unsigned int setter;

- Each bit (from right to left) in the vector variable indicates whether the corresponding character has already been seen or not. This requires only 26 bits of memory for lowercase characters, which can all fit inside a single unsigned integer. Here we use 8 bits only for brevity

        hgfedcba
        00000000 (vector)

- The setter variable is used to represent the current character that we want to check:

        setter = 1 << ('a' - 'a');
        00000001 (setter)

- To determine if a character has been seen before, we'll bitwise AND the vector and setter:

        00000000 (vector)
        & 00000001
        '----------
        00000000
- A zero value implies the character 'a' has not been seen before. If the character has been seen before then we get back the value of setter, which is non-zero
- To set the vector for the next iteration, we must bitwise OR the vector and the setter and store the result back in the vector

          00000000 (vector)
         |00000001 (setter)
          00000001 (-> vector)

- Take the character 'b' from the string "aba":
- setter = 1 << ('b' - 'a');

        00000001 (vector)
        &00000010 (setter)
        00000000

- Then we update the vecotr:

        00000001 (vector)
        |00000010 (setter)
        00000011 (-> vector)

- Take the second 'a' from the string "aba":

        setter = 1 << ('a' - 'a');
        00000011 (vector)
        &00000001 (setter)
        00000001

- The result is the same as setter and is non-zero, therefore 'a' has been seen already