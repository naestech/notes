> an **algorithmic approach** that maintains a window which "slides" over the entire input data, optimizing the solution by avoiding repeated work.

---

## **keywords**

sliding window: the process of moving the window across the data.

dynamic window: a window whose size changes depending on the problem constraints.

window size: the length of the current subarray or substring being considered.

left pointer: the starting position of the window.

right pointer: the ending position of the window.

---

## **how it works**

### **diagram**
<img width="563" alt="image (1)" src="https://github.com/user-attachments/assets/5038f13e-453e-46ba-9f61-b14e05c5da4b">


---

### **code**

**initialization:**

```python
# Initialize pointers and the result variable
left = 0
right = 0
result = 0
window = []
```

**insertion:**

```python
# Expand the window by moving the right pointer
window.append(data[right])  # Add the new element at the right end
right += 1
```

**retrieval:**

```python
# Retrieve the current window sum or value
current_window = window[left:right]
result = sum(current_window)  # Or any other operation depending on the problem
```

**deletion:**

```python
# Shrink the window by moving the left pointer
window.pop(0)  # Remove the element at the left end
left += 1
```

**display:**

```python
# Display the current window or the result
print(f"Current window: {window}, Result: {result}")
```

---

**putting it together:**

1. start with two pointers (`left` and `right`) at the beginning of the array or string.
2. expand the window by moving the `right` pointer until a condition is met.
3. if the condition is violated, move the `left` pointer to shrink the window, and continue the process.
4. continue sliding the window until all possible subarrays or substrings are considered.

**main:**

```python
def sliding_window(data, target_sum):
    left = 0
    right = 0
    current_sum = 0
    result = []

    while right < len(data):
        # Add the current element to the window sum
        current_sum += data[right]

        # While the window sum exceeds the target, shrink the window from the left
        while current_sum > target_sum:
            current_sum -= data[left]
            left += 1

        # If the sum matches the target, record the window
        if current_sum == target_sum:
            result.append(data[left:right+1])

        # Move the right pointer to expand the window
        right += 1

    return result
```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(1)

the window expands or shrinks with constant time complexity as it adds or removes a single element.

**worst case:** O(n)

the window can traverse the entire array, and each element might be added and removed from the window only once, resulting in linear time complexity.

---

## **use cases**

best for finding subarrays or substrings that meet certain criteria, or solving problems evaluating all contiguous subarrays or substrings of a given size or under certain conditions.

---

## **resources**

https://www.youtube.com/watch?v=p-ss2JNynmw
