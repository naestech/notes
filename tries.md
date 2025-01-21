> a trie (pronounced try) is a tree-like **data structure** used for storing strings in a way that facilitates efficient prefix-based searching.
> 

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
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end_of_word = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

```

**insertion:**

```python

def insert(self, word):
    node = self.root
    for char in word:
        if char not in node.children:
            node.children[char] = TrieNode()
        node = node.children[char]
    node.is_end_of_word = True

```

**retrieval:**

```python

def search(self, word):
    node = self.root
    for char in word:
        if char not in node.children:
            return False
        node = node.children[char]
    return node.is_end_of_word

```

**deletion:**

```python
def delete(self, word):
    def _delete(node, word, depth):
        if not node:
            return False
        if depth == len(word):
            if not node.is_end_of_word:
                return False
            node.is_end_of_word = False
            return len(node.children) == 0
        char = word[depth]
        if _delete(node.children[char], word, depth + 1):
            del node.children[char]
            return len(node.children) == 0
        return False
    _delete(self.root, word, 0)

```

**display:**

```python

def display(self, node=None, word=''):
    if node is None:
        node = self.root
    if node.is_end_of_word:
        print(word)
    for char, child in node.children.items():
        self.display(child, word + char)

```

---

**putting it together:**

1. initialize the Trie.
2. insert words.
3. search for prefixes or exact matches.
4. delete words if necessary.
5. display all stored words.

**main:**

```python
trie = Trie()
trie.insert("apple")
trie.insert("app")
print(trie.search("apple"))  # True
trie.delete("app")
trie.display()

```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best & worst case:** O(k)

where k is equal to the length of the word

---

## **use cases**

best for autocomplete, dictionary implementations, and prefix-based searching.

---

## **resources**

https://www.youtube.com/watch?v=zIjfhVPRZCg