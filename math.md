> math problems involve numerical operations, properties, and relationships to solve equations, optimize results, or identify patterns.
> 

---

## **keywords**

arithmetic: basic operations like addition, subtraction, multiplication, and division.

algebra: working with variables, equations, and expressions to solve for unknowns.

geometry: studying shapes, sizes, and properties of figures in space.

number theory: understanding integers, divisors, primes, and modular arithmetic.

combinatorics: counting arrangements, combinations, and permutations.

calculus: focusing on limits, derivatives, and integrals to study change and motion.

optimization: finding the maximum or minimum value of a function.

---

## **how it works**

### **diagram**

image.png

---

### **code**

**initialization:**

```python
import math  # for advanced math functions like sqrt, sin, etc.

```

**insertion:**

```python

def arithmetic_operations(a, b):
    return a + b, a - b, a * b, a / b if b != 0 else float('inf')

```

**algebra example:**

```python
def solve_linear(a, b):
    # Solves ax + b = 0 for x
    if a == 0:
        return "No solution" if b != 0 else "Infinite solutions"
    return -b / a

```

**geometry example:**

```python

def circle_area(radius):
    return math.pi * radius ** 2
```

**number theory example (gcd and lcm):**

```python

def gcd_lcm(a, b):
    gcd = math.gcd(a, b)
    lcm = abs(a * b) // gcd
    return gcd, lcm

```

**number theory example (gcd and lcm):**

```python

def gcd_lcm(a, b):
    gcd = math.gcd(a, b)
    lcm = abs(a * b) // gcd
    return gcd, lcm

```

**combinatorics example (factorial):**

```python
def factorial(n):
    return math.factorial(n)
```

**calculus example (approx derivative):**

```python
def derivative(f, x, h=1e-7):
    return (f(x + h) - f(x - h)) / (2 * h)

```

**display:**

```jsx
def display_result(result):
    print("Result:", result)
```

---

**putting it together:**

1. define the math operation (e.g., arithmetic, algebra, geometry, etc.).
2. write or use a function to compute the result.
3. display the result using the `display_result` function.

**main:**

```python
if __name__ == "__main__":
    # arithmetic example
    a, b = 10, 5
    results = arithmetic_operations(a, b)
    display_result(results)

    # algebra example
    x = solve_linear(2, -4)
    display_result(f"Solution for 2x - 4 = 0: {x}")

    # geometry example
    area = circle_area(5)
    display_result(f"Area of circle with radius 5: {area}")

```

---

## **runtime complexity**

**varies by operation:**

- arithmetic: O(1)
- algebra (solving linear equations): O(1)
- geometry (circle area): O(1)
- combinatorics (factorial): O(n)
- calculus (approx derivative): O(1) per evaluation

---

## **use cases**

best for problems involving:

- numerical calculations (e.g., finding sums, products, or averages).
- solving equations (e.g., algebraic or linear systems).
- geometric computations (e.g., area, perimeter, distance).
- optimization (e.g., minimizing cost or maximizing value).

---

## **resources**

[Math cheatsheet for coding interviews | Tech Interview Handbook](https://www.techinterviewhandbook.org/algorithms/math/)