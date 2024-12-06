> a queue is a linear data structure that follows the **first-in, first-out (FIFO)** principle

---

## **keywords**

enqueue: adding a value to the end of the queue

dequeue: removing a value from the front of the queue

---
<!-- 
## **how it works**

### **diagram**

add diagram here
-->
---

### **code**

**initialization:**

```python
class Queue:
    def __init__(self):
        self.queue = []
```

**insertion:**

```python
    def enqueue(self, item):
        self.queue.append(item)  # add item to the rear

```

**retrieval:**

```python
    def front(self):
        if not self.is_empty():
            return self.queue[0]  # return the front element
        else:
            return "queue is empty"

```

**deletion:**

```python

    def dequeue(self):
        if not self.is_empty():
            return self.queue.pop(0)  # remove and return the front element
        else:
            return "queue is empty"
```

**display:**

```python
    def display(self):
        print("queue:", self.queue)

```

---

**putting it together:**

1. initialize a queue
2. enqueue elements
3. dequeue an element
4. display the queue

**main:**

```python
if __name__ == "__main__":
    q = Queue()
    q.enqueue(10)
    q.enqueue(20)
    q.enqueue(30)
    q.display()
    
    print("dequeued:", q.dequeue())
    print("front:", q.front())
    q.display()
```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(1)

enqueueing in an array-based queue

**worst case:** O(n)

dequeueing in an array-based queue due to shifting elements

---

## **use cases**

best for managing tasks in order

---

## **resources**

https://youtu.be/nqXaPZi99JI
