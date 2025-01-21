> recursion is a **technique** where a function calls itself with modified arguments until a base condition is met.
> 

---

<!-- 
## **how it works**
### **diagram**
image.png
---
-->

---

### **code**

**initialization:**

```python
def recursive_function(input):
    if base_case(input):
        return base_result

```

---

**putting it together:**

1. define a base case.
2. break the problem into smaller parts.
3. solve each part recursively.
4. combine results and return.

**main:**

```python
def recursive_function(input):
    if base_case(input):
        return base_result
    subproblem = divide_problem(input)
    result = recursive_function(subproblem)
    return combine_results(result)

```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(log(n))

recursion with binary search

**worst case:** O(n!)

recursion with different permutations

---

## **use cases**

best for divide-and-conquer problems like merge sort, fibonacci sequence, and tree traversals.

---

## **resources**

https://www.youtube.com/watch?v=ivl5-snqul8