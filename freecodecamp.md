# [data structures easy to advanced course - full tutorial from a google engineer](https://youtu.be/RBSGKlAvoiM?si=cHE7PzdV2_CMle7z) 
## [github repo](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbm5ST2Fqcms1UkJvajY2SlpVVEFCalVyUnl0Z3xBQ3Jtc0tsTDJ1cm5vakVndl9ILTlHZWMxM1FqU0xCQXlNS1JjR3ppNGZhR05IdklrX1RFT1I0MEZPTzZJTUUxWW8zdnlRZzh1Qmt6NjQ2N002X20wRTNIMEtOZjJNOWFjTUVRV1dXS0RwS1VOb3F1OTd0dV9Jcw&q=https%3A%2F%2Fgithub.com%2Fwilliamfiset%2Fdata-structures&v=RBSGKlAvoiM) 

### **data structures**

- **definition**: a data structure is a way of organizing data so it can be used efficiently. it helps access, query, or update data quickly and easily.
---
- **importance**:
  - essential for creating fast, powerful algorithms.
  - helps manage and organize data naturally.
  - cleaner code, easier to understand.
  - programmers who excel often know which data structure to use for a task. this can be the difference between an average product and an outstanding one.
---
- **abstract data types (adt)**: an abstraction of a data structure that defines the interface but not the implementation.
  - **example analogy**: transportation is the abstract data type, and the actual data structure is the specific mode of transportation (e.g., walking, biking, etc.).
  - adts specify what methods should exist (e.g., add, remove) but not how these methods are implemented.
---
  - **examples**:
    - **list**: implemented as dynamic arrays or linked lists.
    - **queue**: could be implemented using stacks.
    - **map**: can have various implementations like hash maps or trees.

### **big-o notation**

- **definition**: big-o notation describes the time and space complexity of an algorithm, focusing on the worst-case scenario.
---
- **why it's used**: to measure how much time or space an algorithm will need, especially for large inputs.
  - if an algorithm takes too long or uses too much space, it’s not practical.
---
- **big-o considers**:
  - **worst-case time**: the longest time an algorithm could take to complete given the worst possible input.
  - **worst-case space**: the maximum amount of space required for the algorithm to run with a particular input.
  - **input size (n)**: usually refers to the number of elements processed by the algorithm.
---
- **common time complexities**:
  - **o(1)**: constant time, doesn't depend on input size.
  - **o(log n)**: logarithmic time, halves the input at each step (e.g., binary search).
  - **o(n)**: linear time, proportional to input size.
  - **o(n²)**: quadratic time, often caused by nested loops.
  - **o(2ⁿ)**: exponential time, doubles with each additional element (e.g., subset finding).
  - **o(n!)**: factorial time, considers every permutation of the input (e.g., finding all permutations).
---
  - **examples**:
    - **binary search**: logarithmic time, o(log n).
    - **merge sort**: linearithmic time, o(n log n).
    - **subset finding**: exponential time, o(2ⁿ).
    - **permutations**: factorial time, o(n!).
    - **iterating over an n×m array**: o(n*m).

### **big-o properties**

- **focus on large input sizes**: big-o notation is concerned with what happens when input size (n) becomes arbitrarily large (n → ∞).
---
- **ignore constants**: constants are ignored because they become insignificant as input size grows.
  - **example**: f(n) = 7log(n)³ + 15n² + 2n³ + 8 → big-o notation simplifies this to o(n³), since n³ dominates the behavior of the function as n grows.
---
- **comparing terms**: for big-o, only the largest term matters because it has the most significant impact on performance as input size increases.

### **examples of big-o**

1. **constant time (o(1))**:
   - operations that do not depend on input size (e.g., adding two numbers, or executing a loop that runs a fixed number of times).
---
2. **linear time (o(n))**:
   - operations proportional to the input size (e.g., iterating through an array).
---
3. **quadratic time (o(n²))**:
   - nested loops where each loop runs n times (e.g., basic sorting algorithms like bubble sort).
---
4. **logarithmic time (o(log n))**:
   - algorithms like binary search that repeatedly cut the problem size in half.
---
5. **linearithmic time (o(n log n))**:
   - algorithms like merge sort, which recursively divide and merge arrays.

### **advanced big-o examples**

1. **binary search**:
   - starts with two pointers at the beginning and end of a sorted array.
   - checks the midpoint; if not found, discards half the array.
   - runs in o(log n).
---
2. **multiplying loops**:
   - multiply nested loops to calculate time complexity.
   - example: outer loop runs n times, inner loop runs 3n + 2n → total time complexity: o(n²).
---
3. **other classic examples**:
   - **subset finding**: o(2ⁿ).
   - **permutations**: o(n!).
   - **merge sort**: o(n log n).
   - **iterating over n×m grid**: o(n * m).

---

### **arrays**

- **definition**: arrays are one of the most used data structures.
---
- **operations**:
  - **access**: o(1) (constant time) when accessing elements by index.
  - **searching**: o(n) (linear time) in unsorted arrays, o(log n) (logarithmic time) in sorted arrays with binary search.
  - **insertion**: o(n) (linear time) for inserting elements in the middle of the array (due to shifting).
  - **deletion**: o(n) (linear time) if elements need to be shifted.

## **overview**

- arrays form a core **building block** for all data structures.
---
- with just arrays and pointers, we can construct almost any data structure.

## **static array**

- **definition**: a static array is a **fixed-length** container with **indexable** elements, typically indexed from `0` to `n-1`.
---
- **contiguous memory**: static arrays are stored as continuous blocks of memory, no gaps or holes (i.e., no "swiss cheese" memory).

## **uses of static arrays**

- **everywhere**: it's hard to write a program without using arrays.
---
- **common uses**:
  - **temporary storage**: store objects.
  - **buffers**: used for input/output streams when handling large files.
  - **lookup tables**: due to their indexability.
  - **workaround**: used when a language allows only one return value (return a reference to an array).
  - **dynamic programming**: used in techniques like **tabulation** to cache subproblems (e.g., **knapsack** or **coin change problems**).

## **time complexity**

- **access time**: constant (`o(1)`) due to indexability.
---
- **searching**: worst-case linear (`o(n)`) if element doesn't exist (requires traversal).
---
- **insertions/deletions**: 
  - **static arrays**: no insertions/deletions since the array is fixed in size.
---
  - **dynamic arrays**:
    - **insertion**: linear (`o(n)`) due to shifting/copying elements.
    - **deletion**: linear (`o(n)`) for similar reasons.
    - **appending**: usually constant (`o(1)`), because resizing happens rarely.

## **dynamic arrays**

- **definition**: a dynamic array can **grow and shrink** in size as needed, unlike static arrays.
---
- **operations**: performs all the same operations as static arrays but with the flexibility to change size.
---
- **growth mechanism**:
  - when capacity is exceeded, the array **doubles** in size.
  - elements are copied to the new larger static array, and the new element is added.
---
- **example**: start with a dynamic array of size 2, add elements until capacity is exceeded, then double the size.

## **indexing and iteration**

- **indexing**: done using square brackets (`array[i]`), with zero-based indexing.
---
  - common confusion because **math** uses one-based indexing while **computer science** uses zero-based.
---
- **iteration**: arrays can be iterated over using `for-each` loops in some languages, hiding the explicit indexing.

## **example static array**

- **array `a`**: `[44, 12, -5, 17, 60, 39, 100]`.
---
  - **indexing**: `a[0] = 44`, `a[1] = 12`, etc.
---
  - accessing an index out of bounds (e.g., `a[9]`) throws an exception unless you're using **c**, where behavior can be undefined.

## **advanced example: dynamic array operations**

- start with array `a = [34, 4]`.
---
- **add** `-7` → array becomes `[34, 4, -7]`.
---
- **remove** `4` → array becomes `[34, -7]`.
---
- **resize**: when capacity is reached, the dynamic array resizes by doubling the internal static array.
