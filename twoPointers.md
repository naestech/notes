> a **technique** that uses two pointers to traverse a data structure, often at different positions or speeds, to solve problems efficiently.

---

## **keywords**

pointer 1: the first position used in an operation.

pointer 2: the first position used in an operation.

increment: moving a pointer forward in the data structure.

---

## **how it works**

### **diagram**

<img width="377" alt="image (2)" src="https://github.com/user-attachments/assets/278df1ba-bf80-4b37-81fc-7c7e506ff47b">



---

### **code**

**initialization:**

```python
# initializing two pointers
pointer1 = 0  # starting at the beginning
pointer2 = len(arr) - 1  # starting at the end

```

**moving pointers:**

```python
# example of moving pointers inward
def move_pointers_inward(arr):
    pointer1 = 0
    pointer2 = len(arr) - 1

    while pointer1 < pointer2:
        print(f"pointer1: {arr[pointer1]}, pointer2: {arr[pointer2]}")
        pointer1 += 1
        pointer2 -= 1

```

### **examples**

**two-pointer use case:**

```python
# finding if a pair with a target sum exists
def has_pair_with_sum(arr, target):
    pointer1 = 0
    pointer2 = len(arr) - 1

    while pointer1 < pointer2:
        current_sum = arr[pointer1] + arr[pointer2]
        if current_sum == target:
            return True
        elif current_sum < target:
            pointer1 += 1
        else:
            pointer2 -= 1

    return False

```

**reversing an array:**

```python
# reverse an array using two pointers
def reverse_array(arr):
    pointer1 = 0
    pointer2 = len(arr) - 1

    while pointer1 < pointer2:
        arr[pointer1], arr[pointer2] = arr[pointer2], arr[pointer1]
        pointer1 += 1
        pointer2 -= 1

```

---

**putting it together:**

1. **initialization**: pointers are initialized to traverse from either ends or different positions based on the problem.
2. **operations**: pointers can be incremented, decremented, or moved conditionally.
3. **utilities**: efficient traversal and manipulation of data without auxiliary structures.

**main:**

```python
# example array
array = [1, 2, 3, 4, 5]

# move pointers inward
move_pointers_inward(array)
# outputs: pointer1: 1, pointer2: 5 ...

# check for a pair with target sum
print(has_pair_with_sum(array, 6))  # True (1 + 5)

# reverse the array
reverse_array(array)
print(array)  # [5, 4, 3, 2, 1]

```

---

## **runtime complexity**

**best and worst case:** O(n)

always linear since pointers always linearly traverse through the data structure.

---

## **use cases**

best for searching in sorted arrays, finding pairs or triplets, detecting cycles, or reversing arrays / linked lists

---

## **resources**

https://youtu.be/On03HWe2tZM?si=cU-3zePwnpxbAIwM
