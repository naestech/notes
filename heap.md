> a heap is a specialized binary tree-based **data structure**
> 

---

## **keywords**

max-heap: every parent node is greater than or equal to its child nodes.
min-heap: every parent node is less than or equal to its child nodes.

heap property: the rule that defines whether the heap is a max-heap or min-heap.

priority queue: a data structure where elements are dequeued based on priority of highest or lowest value.

---

<!-- 
## **how it works**
### **diagram**
image.png
---
-->

---

### **code**

**initialization:**

```python
class Heap:
    def __init__(self):
        self.heap = []
```

**insertion:**

```python

    def insert(self, val):
        self.heap.append(val)
        self._heapify_up(len(self.heap) - 1)
    
    def _heapify_up(self, index):
        parent = (index - 1) // 2
        while index > 0 and self.heap[index] < self.heap[parent]:
            self.heap[index], self.heap[parent] = self.heap[parent], self.heap[index]
            index = parent
            parent = (index - 1) // 2

```

**retrieval:**

```python
    def peek(self):
        return self.heap[0] if self.heap else None

```

**deletion:**

```python

    def remove(self):
        if len(self.heap) == 0:
            return None
        if len(self.heap) == 1:
            return self.heap.pop()
        
        root = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._heapify_down(0)
        return root
    
    def _heapify_down(self, index):
        smallest = index
        left = 2 * index + 1
        right = 2 * index + 2
        
        if left < len(self.heap) and self.heap[left] < self.heap[smallest]:
            smallest = left
        if right < len(self.heap) and self.heap[right] < self.heap[smallest]:
            smallest = right
        if smallest != index:
            self.heap[index], self.heap[smallest] = self.heap[smallest], self.heap[index]
            self._heapify_down(smallest)

```

**display:**

```python

    def display(self):
        return self.heap
```

---

**putting it together:**

1. initialize a heap.
2. insert elements into the heap.
3. retrieve the minimum (or maximum) value from the heap.
4. delete elements from the heap.
5. display the heap.

**main:**

```python
if __name__ == "__main__":
    h = Heap()
    h.insert(10)
    h.insert(20)
    h.insert(15)
    h.insert(5)
    h.display()  # prints [5, 10, 15, 20]
    print(h.peek())  # prints 5
    h.remove()  
    h.display()  # prints [10, 20, 15]

```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(1)
retrieval of the root.

**worst case:** O(log(n))

insertion or deleting an element.

---

## **use cases**

best for scheduling tasks where priority matters or finding the k largest or smallest elements in a collection.

---

## **resources**

https://youtu.be/0wPlzMU-k00