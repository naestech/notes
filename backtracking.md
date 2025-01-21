> backtracking is a **technique** that uses a trial-and-error method to solve problems incrementally
> 

---

<!-- 
## **how it works**
### **diagram**
image.png
---
-->

---

**putting it together:**

1. start with an empty state.
2. try all possible candidates.
3. if the state is valid, recurse further.
4. if it fails, backtrack and try the next option.

**main:**

```python
def is_valid(state, candidate):
    """
    Checks if the candidate can be added to the current state.
    This function ensures that the solution constraints are not violated.
    """
    return True  # Replace with problem-specific validation logic

def backtrack(state, candidates):
    """
    Explores all possible solutions by trying candidates.
    If a solution is found, it is added to the result.
    """
    if is_solution(state):  # Base case: stop when we reach a solution
        result.append(state[:])  # Add a copy of the solution to the results
        return

    for candidate in candidates:  # Try all possible candidates
        if is_valid(state, candidate):  # Only proceed with valid candidates
            state.append(candidate)  # Make a choice
            backtrack(state, candidates)  # Recurse with updated state
            state.pop()  # Undo the choice (backtrack)

def is_solution(state):
    """
    Determines if the current state is a complete solution.
    Replace with problem-specific logic.
    """
    return False  # Replace with solution-checking logic

# Usage
result = []  # This will hold all valid solutions
initial_state = []  # Start with an empty state
candidates = []  # Define the possible candidates (e.g., numbers, positions)
backtrack(initial_state, candidates)

# Print or process the results
for solution in result:
    print(solution)

```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(1)

backtracking with simple constraints

**worst case:** O(k^2)

backtracking where k is the branching factor, and n is the depth of recursion.

---

## **use cases**

best for solving constraint-satisfaction problems like sudoku.

---

## **resources**

https://www.youtube.com/watch?v=vqnZ9RhhkmY