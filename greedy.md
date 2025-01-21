> greedy's algorithm is a **technique** to solving optimization problems by breaking it down to pieces and making the optimal choice at each step.
> 

---

## **keywords**

greedy choice property: the ability to make decisions locally without reconsidering past choices.

optimal substructure: a problem's global optimal solution can be constructed from optimal solutions to its subproblems

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
def initialize_greedy():
    # setup data structures or inputs for the greedy algorithm
    items = []  # example input
    return items
```

**insertion:**

```python

def add_item(items, item):
    # add an item to the input list
    items.append(item)
    return items
```

**retrieval:**

```python

def retrieve_solution(items):
    # apply greedy algorithm to find a solution
    solution = []
    for item in sorted(items):
        if is_valid_choice(solution, item):
            solution.append(item)
    return solution
```

**deletion:**

```python
def delete_item(items, item):
    # remove an item from the input list
    if item in items:
        items.remove(item)
    return items
```

**display:**

```python
def display_solution(solution):
    # print or return the solution
    print("Optimal solution:", solution)
```

---

**putting it together:**

1. initialize the input data.
2. insert items or data into the algorithm's input.
3. run the greedy algorithm to retrieve the solution.
4. optionally delete or modify items and rerun as needed.
5. display the final solution.

**main:**

```python
def main():
    items = initialize_greedy()
    items = add_item(items, 10)
    items = add_item(items, 20)
    items = add_item(items, 15)

    solution = retrieve_solution(items)
    display_solution(solution)

main()
```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(n log n)

due to sorting or other greedy operations.

**worst case:** O(n^2)

if sorting or decision-making involves pairwise comparisons.

---

## **use cases**

best for interval scheduling, fractional knapsack, minimum spanning tree using prim's or kruskal's algorithms, or huffman coding.

---

## **resources**

https://www.youtube.com/watch?v=HzeK7g8cD0Y