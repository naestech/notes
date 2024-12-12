> a non-linear **data structure** where nodes are organized in a hierarchy
> 

---

## **keywords**

subtree: a tree within a tree. this can be found by looking at a parent and its children.

root: the topmost node.

parent: a node with a node attached below it.

child: a node with a node attached above it.

branch: a node with a node attached above and below it.

leaf: a node with no nodes attached below it.

child: a node with a node attached above it.

sibling: a node that shares the same parent node.

size: the number of nodes in a tree.

depth: the number of of edges from the root to a node.

height: the number of edges in the longest path from a node to a leaf.

---
<!-- 
## **how it works**
### **diagram**
image.png
---
-->

### **code**

**initialization:**

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.children = []

class Tree:
    def __init__(self):
        self.root = None
```

**insertion:**

```python
def insert(self, parent_value, value):
    if not self.root:
        self.root = Node(parent_value)
        self.root.children.append(Node(value))
    else:
        parent = self.find(self.root, parent_value)
        if parent:
            parent.children.append(Node(value))
    # Helper method to find a node
def find(self, node, value):
    if node.value == value:
        return node
    for child in node.children:
        result = self.find(child, value)
        if result:
            return result
    return None

```

**retrieval:**

```python

def retrieve(self, value):
    return self.find(self.root, value)

```

**deletion:**

```python
def delete(self, value):
    if not self.root:
        return
    if self.root.value == value:
        self.root = None  # Clear the entire tree if the root is deleted
        return
    self._delete(self.root, value)

def _delete(self, node, value):
    for child in node.children:
        if child.value == value:
            node.children.remove(child)
            return
        self._delete(child, value)

```

**display:**

```python

def display(self, node=None, level=0):
    if not node:
        node = self.root
    print(" " * level * 4 + str(node.value))
    for child in node.children:
        self.display(child, level + 1)

```

---

**putting it together:**

1. create a tree.
2. add nodes to the tree.
3. retrieve or delete nodes.
4. display the structure.

**main:**

```python
tree = Tree()
tree.insert(None, "A")  # Insert root
tree.insert("A", "B")
tree.insert("A", "C")
tree.insert("B", "D")
tree.insert("C", "E")
tree.display()

node = tree.retrieve("C")
print(f"Retrieved node: {node.value}")

tree.delete("B")
tree.display()

```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best case:** O(1)

if the node is the root.

**worst case:** O(n)

if the node is a leaf.

---

## **use cases**

best for hierarchal data, such as file systems, game development, html document parsing.

---

## **resources**

https://www.youtube.com/watch?v=Etpc_-br5rI
