> a resizable **data structure** that stores elements in contiguous memory blocks.

known as lists in python, array list in java, vectors in c++, arrays in javascript

---

## **keywords**

index: position of an element.

element: a stored value.

size: current number of elements.

capacity: total memory currently allocated.

---

## **how it works**

### **diagram**

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/d61f2617-4cd7-47f3-8c1b-42b35e353d1e/34724ae9-9cc0-4505-bd46-8b9e7cd6bcb6/image.png)

---

### **code**

**initialization:**

```python
# creating a dynamic array
dynamic_array = []  # an empty list in python
```

**insertion:**

```python
# inserting an element at a specific index or appending to the end
def insert(arr, index, value):
    if index < len(arr):
        arr.insert(index, value)  # insert at index, shifting other elements
    else:
        arr.append(value)  # append at the end if index is out of bounds
```

**retrieval:**

```python
# retrieving an element at a specific index
def get(arr, index):
    return arr[index]  # return value at the given index
```

**deletion:**

```python
# delete an element by index
def delete(arr, index):
    if 0 <= index < len(arr):
        arr.pop(index)  # remove element at the given index
```

**display:**

```python
# display all elements in the dynamic array
def display(arr):
    print(arr)  # print the list
```

---

**putting it together:**

1. **initialization**: dynamic arrays are initialized without a fixed size.
2. **operations**: `insert`, `get`, and `delete` provide flexibility for modifying/accessing elements.
3. **utilities**: `display` helps visualize the array's current state.

**main:**

```python
# create a dynamic array
dynamic_array = [1, 2, 3, 4]

# insert value at index
insert(dynamic_array, 2, 10)  # insert 10 at index 2

# display the array
display(dynamic_array)  # [1, 2, 10, 3, 4]

# retrieve value at index
print(get(dynamic_array, 2))  # 10

# delete element at index
delete(dynamic_array, 2)
display(dynamic_array)  # [1, 2, 3, 4]

```

---

## **runtime complexity**

**insertion, deletion:**

- **best case:** O(1)

if adding/deleting the last element.

- **worst case:** O(n)

if inserting/deleting an element in the middle or triggering resizing.

**retrieval:**

- O(1)

accessing by index is direct.

---

## **use cases**

best for storing data when the number of elements varies frequently and resizing needs to be handled efficiently.

---

## **resources**

https://www.youtube.com/watch?v=jzJlq35dQII
