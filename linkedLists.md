> a linked list is a linear **data structure** where nodes are linked using pointers to data and a reference.
> 

---

## **keywords**

node: an element of the linked list containing data and a pointer/reference.
head: the first node in the linked list.
tail: the last node in the linked list. 
pointer: a reference that connects nodes.

singly linked list: each node only points to the next element.
doubly linked list: each node points to the next and previous elements.

---

<!-- 
## **how it works**
### **diagram**
add image.png here
---
-->


### **code**

**initialization:**

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None
```

**insertion:**

```python
def insert_at_end(self, data):
    new_node = Node(data)
    if not self.head:  # if the list is empty
        self.head = new_node
        return
    current = self.head
    while current.next:  # traverse to the end
        current = current.next
    current.next = new_node

```

**retrieval:**

```python

def find(self, value):
    current = self.head
    while current:
        if current.data == value:
            return current
        current = current.next
    return None
```

**deletion:**

```python

def delete(self, value):
    if not self.head:  # if the list is empty
        return
    if self.head.data == value:  # if the head is the node to be deleted
        self.head = self.head.next
        return
    current = self.head
    while current.next:
        if current.next.data == value:  # check the next node
            current.next = current.next.next
            return
        current = current.next
```

**display:**

```python
def display(self):
    elements = []
    current = self.head
    while current:
        elements.append(current.data)
        current = current.next
    print(" -> ".join(map(str, elements)))

```

---

**putting it together:**

1. initialize the linked list.
2. insert nodes into the linked list.
3. find, delete, and display nodes as needed.

**main:**

```python
if __name__ == "__main__":
    ll = LinkedList()
    ll.insert_at_end(10)
    ll.insert_at_end(20)
    ll.insert_at_end(30)
    ll.display()  # 10 -> 20 -> 30
    ll.delete(20)
    ll.display()  # 10 -> 30
    print(ll.find(30))  # 1

```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(1)

inserting at the head or retrieving the head

**worst case:** O(n)

traversing to the end for insertion or searching

---

## **use cases**

best for situations where frequent insertions or deletions are required and memory allocation needs to be dynamic.

---

## **resources**

https://youtu.be/N6dOwBde7-M
