> a **search algorithm** that finds the position of a target value within a sorted data structure by disregarding half of the array during each step.
> 

---

## **keywords**

middle element: element at the center of the data structure that is being compared to the target element.
target element: element that the algorithm is searching for.

---

## **how it works**

### **diagram**
<img width="520" alt="binarysearch" src="https://github.com/user-attachments/assets/f2a48e27-117e-44cc-bd09-a152cfe064da">


---

### **code**

**initialization:**

```python
def binary_search(arr, target):
    left = 0
    right = len(arr) - 1
```

**insertion:**

```python

def binary_search(arr, target):
    left = 0
    right = len(arr) - 1
    while left <= right:
        mid = left + (right - left) // 2
        if arr[mid] == target:
            return mid  # target found
        elif arr[mid] < target:
            left = mid + 1  # search the right half
        else:
            right = mid - 1  # search the left half
    return -1  # target not found

```

---

**putting it together:**

1. initialize the array and target.
2. implement the retrieval logic to find the target index.
3. adjust as needed for insertion or other operations.

**main:**

```python
if __name__ == "__main__":
    sorted_array = [1, 3, 5, 7, 9, 11]
    target = 7
    index = binary_search(sorted_array, target)
    if index != -1:
        print(f"target found at index {index}")
    else:
        print("target not found")

```

---

## **runtime complexity**

**retrieval:**

**best case:** O(1) 
if the target value is in the center initially

**worst case:** O(log(n))

repeatedly having to split

---

## **use cases**

best for large static datasets for quickly sorting when adding or removing values are rare or handled seperatly.

---

## **resources**

https://youtu.be/xrMppTpoqdw?si=poaALREnXiGVZBjR
