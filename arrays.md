> a fixed size **data structure** that stores elements of the same data type in a contiguous block of memory.

---

## **keywords**

index: position of an element in the array.

element: a value stored in the array.

length: number of elements in the array.

---

## **how it works**

### **diagram**

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/d61f2617-4cd7-47f3-8c1b-42b35e353d1e/8f3a5c3a-1f1d-4d22-94ce-4c92ce42b6a9/image.png)

---

### **code**

**initialization:**

```python
# creating an array of fixed size
array = [0] * 5  # creates an array with 5 elements, all initialized to 0

```

**insertion:**

```python
# inserting an element at a specific index
def insert(arr, index, value):
    arr[index] = value  # assign value at the given index

```

**retrieval:**

```python
# retrieving an element at a specific index
def get(arr, index):
    return arr[index]  # return value at the given index

```

**deletion:**

```python
# delete an element by shifting elements
def delete(arr, index):
    for i in range(index, len(arr) - 1):
        arr[i] = arr[i + 1]
    arr[-1] = None  # clear the last element

```

**display:**

```python
# display all elements in the array
def display(arr):
    print(arr)  # print the array

```

---

**putting it together:**

1. **initialization**: arrays are initialized with fixed sizes.
2. **operations**: `insert`, `get`, and `delete` allow you to modify or access array elements.
3. **utilities**: `display` helps visualize the array’s contents.

**main:**

```python
# create an array
array = [1, 2, 3, 4, 5]

# insert value at index
insert(array, 2, 10)  # insert 10 at index 2

# display the array
display(array)  # [1, 2, 10, 4, 5]

# retrieve value at index
print(get(array, 2))  # 10

# delete element at index
delete(array, 2)
display(array)  # [1, 2, 4, 5, None]

```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(1)

if you're inserting an element at the end of the array or retrieving/deleting from a known index.

**worst case:** O(n)

if you need to shift elements, particularly for deletion or inserting at the beginning or middle.

---

## **use cases**

best for fast, indexed access of one data type to elements when the order matters or random access is frequent.

---

## **resources**

https://www.youtube.com/watch?v=eE9MnoS0lc0
