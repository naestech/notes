> definition
> 

---

## **keywords**

bitwise operators: operators used to manipulate bits (e.g., AND `&`, OR `|`, XOR `^`, NOT `~`).

shift operators: operations that shift bits left or right (`<<`, `>>`).

masking: using a binary mask to extract or modify specific bits.

bit count: counting the number of `1` bits in a binary representation.

toggle: flipping a bit from `0` to `1` or `1` to `0`.

set: ensuring a bit is `1`.

clear: ensuring a bit is `0`.

---

## **how it works**

### **diagram**

image.png

---

### **code**

**initialization:**

```python
# no specific initialization required for bit manipulation
```

**basic operation:**

```python

def basic_bitwise_ops(a, b):
    return {
        "AND": a & b,
        "OR": a | b,
        "XOR": a ^ b,
        "NOT a": ~a,
        "NOT b": ~b,
        "Left Shift a by 1": a << 1,
        "Right Shift b by 1": b >> 1,
    }
```

**check if power of two:**

```python

def is_power_of_two(x):
    return x > 0 and (x & (x - 1)) == 0

```

**count set bits (hamming weight):**

```python
def count_set_bits(x):
    count = 0
    while x:
        count += x & 1
        x >>= 1
    return count

```

**toggle a specific bit:**

```python

def toggle_bit(x, pos):
    return x ^ (1 << pos)

```

**set and clear bits:**

```python

def set_bit(x, pos):
    return x | (1 << pos)

def clear_bit(x, pos):
    return x & ~(1 << pos)

```

**display:**

```python
def display_binary(x):
    return f"{x} in binary: {bin(x)[2:]}"

```

---

**putting it together:**

1. identify the operation (e.g., AND, OR, toggle, etc.).
2. apply the corresponding bit manipulation function.
3. display results in binary and decimal as needed.

**main:**

```python
if __name__ == "__main__":
    a, b = 5, 3  # example inputs
    print("Basic Bitwise Operations:")
    for op, result in basic_bitwise_ops(a, b).items():
        print(f"{op}: {result} ({display_binary(result)})")

    num = 16
    print(f"\nIs {num} a power of two? {is_power_of_two(num)}")

    print(f"\nNumber of set bits in {num}: {count_set_bits(num)}")

    print(f"\nToggling bit 1 in {a}: {toggle_bit(a, 1)} ({display_binary(toggle_bit(a, 1))})")

```

---

## **runtime complexity**

**varies by operation:**

- basic bitwise operations: O(1)
- check power of two: O(1)
- count set bits: O(log n) (proportional to the number of bits in `n`)
- toggle/set/clear bit: O(1)

---

## **use cases**

best for problems involving:

- optimizing performance through low-level operations.
- subset generation (using bit masks).
- toggling or checking the state of binary flags.
- numerical properties (e.g., checking power of two).
- encoding and decoding binary data.

---

## **resources**

[How to Solve Bit Manipulation Interview Questions](https://interviewkickstart.com/blogs/interview-questions/bit-manipulation)