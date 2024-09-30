## [data structures easy to advanced course - full tutorial from a google engineer](https://youtu.be/RBSGKlAvoiM?si=cHE7PzdV2_CMle7z)

### **data structures**

- **definition**: a data structure is a way of organizing data so it can be used efficiently. it helps access, query, or update data quickly and easily.
- **importance**:
  - essential for creating fast, powerful algorithms.
  - helps manage and organize data naturally.
  - cleaner code, easier to understand.
  - programmers who excel often know which data structure to use for a task. this can be the difference between an average product and an outstanding one.
- **abstract data types (adt)**: an abstraction of a data structure that defines the interface but not the implementation.
  - **example analogy**: transportation is the abstract data type, and the actual data structure is the specific mode of transportation (e.g., walking, biking, etc.).
  - adts specify what methods should exist (e.g., add, remove) but not how these methods are implemented.
  - **examples**:
    - **list**: implemented as dynamic arrays or linked lists.
    - **queue**: could be implemented using stacks.
    - **map**: can have various implementations like hash maps or trees.

### **big-o notation**

- **definition**: big-o notation describes the time and space complexity of an algorithm, focusing on the worst-case scenario.
- **why it's used**: to measure how much time or space an algorithm will need, especially for large inputs.
  - if an algorithm takes too long or uses too much space, it’s not practical.
- **big-o considers**:
  - **worst-case time**: the longest time an algorithm could take to complete given the worst possible input.
  - **worst-case space**: the maximum amount of space required for the algorithm to run with a particular input.
  - **input size (n)**: usually refers to the number of elements processed by the algorithm.
- **common time complexities**:
  - **O(1)**: constant time, doesn't depend on input size.
  - **O(log n)**: logarithmic time, halves the input at each step (e.g., binary search).
  - **O(n)**: linear time, proportional to input size.
  - **O(n²)**: quadratic time, often caused by nested loops.
  - **O(2ⁿ)**: exponential time, doubles with each additional element (e.g., subset finding).
  - **O(n!)**: factorial time, considers every permutation of the input (e.g., finding all permutations).
  - **examples**:
    - **binary search**: logarithmic time, O(log n).
    - **merge sort**: linearithmic time, O(n log n).
    - **subset finding**: exponential time, O(2ⁿ).
    - **permutations**: factorial time, O(n!).
    - **iterating over an n×m array**: O(n*m).

### **big-o properties**

- **focus on large input sizes**: big-o notation is concerned with what happens when input size (n) becomes arbitrarily large (n → ∞).
- **ignore constants**: constants are ignored because they become insignificant as input size grows.
  - **example**: f(n) = 7log(n)³ + 15n² + 2n³ + 8 → big-o notation simplifies this to O(n³), since n³ dominates the behavior of the function as n grows.
- **comparing terms**: for big-o, only the largest term matters because it has the most significant impact on performance as input size increases.

### **examples of big-o**

1. **constant time (O(1))**:
   - operations that do not depend on input size (e.g., adding two numbers, or executing a loop that runs a fixed number of times).
2. **linear time (O(n))**:
   - operations proportional to the input size (e.g., iterating through an array).
3. **quadratic time (O(n²))**:
   - nested loops where each loop runs n times (e.g., basic sorting algorithms like bubble sort).
4. **logarithmic time (O(log n))**:
   - algorithms like binary search that repeatedly cut the problem size in half.
5. **linearithmic time (O(n log n))**:
   - algorithms like merge sort, which recursively divide and merge arrays.

### **advanced big-o examples**

1. **binary search**:
   - starts with two pointers at the beginning and end of a sorted array.
   - checks the midpoint; if not found, discards half the array.
   - runs in O(log n).
2. **multiplying loops**:
   - multiply nested loops to calculate time complexity.
   - example: outer loop runs n times, inner loop runs 3n + 2n → total time complexity: O(n²).

3. **other classic examples**:
   - **subset finding**: O(2ⁿ).
   - **permutations**: O(n!).
   - **merge sort**: O(n log n).
   - **iterating over n×m grid**: O(n * m).

### **arrays**

- **definition**: arrays are one of the most used data structures.
- **operations**:
  - **access**: O(1) (constant time) when accessing elements by index.
  - **searching**: O(n) (linear time) in unsorted arrays, O(log n) (logarithmic time) in sorted arrays with binary search.
  - **insertion**: O(n) (linear time) for inserting elements in the middle of the array (due to shifting).
  - **deletion**: O(n) (linear time) if elements need to be shifted.
