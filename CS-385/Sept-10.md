### Quiz on Thursday next week during Recitation - REVIEW NOTES

## Continuation of Classes, Arrays, and For Loops
- This code continues on from Sept-8.md

        // Pass by reference, and using an iterator (which is an object that can be used essentially as if it were a pointer):
        void display_points(const vector<MyPoint> &points) {
            for (auto it = points.cbegin(); it != points.cend(); it++) {
                it->print_coords(); // same as (*it).print_coords();
            }
        }

        void display_points_v2(const vector<MyPoint> &points) {
            for (size_t i = 0; i < points.size(); i++) {
                points[i].print_coords();
            }
        }

## How to detect memory leaks

    valgrind --leak-check=yes ./mypoint

# Algorithms

## What is an algorithm?
- an algorithm is a sequence of unambiguous instructions for solving a problem, i.e for obtaining a required output for any legitimate input in a finite amount of time
- Interesting Points
    1. The nonambiguity requirement for each step of an algorithm cannot be compromised
    2. The range of inputs for which an algorithm works has to be specified carefully
    3. The same algorithm can be represented in several different ways
    4. There may exist several algorithms for solving the same problem

## Algorithm Design and Analysis Process
- As a rule, a good algorithm is the result of repeated affort and rework
- See slides for diagram
    1. Understand the problem
    2. Decide on: computational means, exact vs approximate solving, algorithm design technique
    3. Design an algorithm
    4. Prove correctness
    5. Analyze the algorithm
    6. Code the algorithm

## Interview Questions
- What subtle concepts are we trying to emphasize
    - Glove Selection
    - There are 22 gloves in a drawer: 5 pairs of red gloves, 4 pairs of yellow, and 2 pairs of green. You select gloves in the dark and can check them only after a selection has been made. What is the smallest number of gloves you need to select to get at least one matching pair in
        - the best case?
        - the worst case?
    - Sock selection
    - There are 22 socks in a drawer: 5 pairs of red socks, 4 pairs of yellow, and 2 pairs of green. You select sock in the dark and can check them only after a selection hass been made. What is the smallest number of sock you need to select to get at least one matching pair in
        - the best case?
        - the worst case?