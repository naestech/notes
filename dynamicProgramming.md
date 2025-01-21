> dynamic programming, abbreviated as dp, is a **technique** for solving problems by breaking them down into smaller overlapping subproblems and storing their results to avoid redundant computation.
> 

---

## **keywords**

dp table: a data structure, usually an array, to store results of subproblems.

state: representation of a subproblem. 

example: `dp[i]`is the result of subproblem `i`

transition: the relationship between the current state and previous states.

example: `dp[i] = dp[i-1] + cost[i]`

recursion: solving a problem by solving its subproblems recursively.

memoization: storing results of recursive calls to avoid recalculating.

tabulation: solving dynamic programming iteratively, filling up a dp table.

---
<!-- 
## **how it works**
### **diagram**
image.png
---
-->

1d dynamic programming handles single-variable subproblems, while 2d dynamic programming handles two-variable subproblems.

---

### **code**

**1d programming: fibonacci sequence**

**initialization:**

```python
def fibonacci(n):
    if n <= 1:
        return n
    dp = [0] * (n + 1)
    dp[1] = 1
    return dp

```

**transition:**

```python

    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]
    return dp[n]

```

---

**2d programming: longest common subsequence**

**initialization:**

```python
def lcs(text1, text2):
    m, n = len(text1), len(text2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    return dp

```

**transition:**

```python
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if text1[i - 1] == text2[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
            else:
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
    return dp[m][n]

```

---

**putting it together:**

1. define the problem and decide the dp state.
2. initialize the dp array/table.
3. set up the transition formula.
4. compute the dp values iteratively or recursively.
5. return the final dp value (often `dp[n]` or `dp[m][n]`).

---

## **runtime complexity**

**1d dynamic programming:**

**space and time complexity:** O(n)

**2d dynamic programming:**

**space and time complexity:** O(m*n)

---

## **use cases**

1d dynamic programming is best for fibonacci sequence, minimum cost to climb stairs, and longest increasing subsequence.

2d dynamic programming is best for longest common subsequence, edit distances, and grid-based pathfinding problems.

---

## **resources**

https://www.youtube.com/watch?v=vYquumk4nWw