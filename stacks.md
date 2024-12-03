> a stack is a last in, first out **data structure** that can only be removed or added from the top.
> 

---

## **keywords**

push: adding an element to the top of the stack.

pop: removing the top element from the stack.

peek: looking at the top element without removing it.

<!-- 
---
## **how it works**
### **diagram**
add image.png 
-->

---

### **code**

**initialization:**

```python
class Stack:
    def __init__(self):
        self.stack = []
```

**insertion:**

```python
    def push(self, value):
        self.stack.append(value)
```

**retrieval:**

```python
    def peek(self):
        if not self.is_empty():
            return self.stack[-1]
        return None  # or raise an exception
```

**deletion:**

```python

    def pop(self):
        if not self.is_empty():
            return self.stack.pop()
        return None  # or raise an exception
```

**display:**

```python
    def display(self):
        print(self.stack)
```

**check if empty**

```python
    def is_empty(self):
        return len(self.stack) == 0
```

---

**putting it together:**

1. create an instance of the `stack` class.
2. use `push` to add items.
3. use `pop` to remove items.
4. use `peek` to see the top item.
5. use `display` to visualize the stack.

**main:**

```python
if __name__ == "__main__":
    s = Stack()
    s.push(1)
    s.push(2)
    s.push(3)
    s.display()  # [1, 2, 3]
    print(s.peek())  # 3
    s.pop()  # remove 3
    s.display()  # [1, 2]
    print(s.is_empty())  # false
    s.pop()  # remove 2
    s.pop(). # remove 1
    print(s.is_empty())  # true
```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best and worst case:** O(1)

a stack is a linear data structure

---

## **use cases**

best for undo or redo operations in text editors, moving backward/forward through history, or other backtracking algorithms

---

## **resources**

https://youtu.be/KInG04mAjO0?si=lHFDloiYf48bTfRG
