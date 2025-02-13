# Data Structures and Algorithms Flashcards

## Table of Contents
1. Algorithms
   - Binary Search
   - Sorting Algorithms
2. Data Structures
   - Arrays
   - Dynamic Arrays
   - Graphs
   - Hash Maps
   - Heap
   - Linked List
   - Queue
   - Stack
   - Trees
   - Tries
3. Techniques
   - Sliding Window
   - Two Pointers
   - Recursion
   - Backtracking
   - Dynamic Programming
   - Greedy Algorithm
   - Intervals
   - Bit Manipulation

## ALGORITHMS

### Binary Search

#### Concept Cards
Q: What is binary search?
A: A search algorithm that finds a target value in a sorted array by repeatedly dividing the search range in half.

Q: What is the key requirement for binary search?
A: The input array must be sorted.

Q: What is the time complexity of binary search?
A: O(log n), because we divide the search space in half in each step.

#### Implementation Cards
Q: Write pseudocode for binary search
A: 
``` python
function binarySearch(array, target):
    left = 0
    right = length(array) - 1
    
    while left <= right:
        mid = left + (right - left) / 2
        
        if array[mid] == target:
            return mid
        else if array[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
            
    return -1
```

Q: Implement binary search in Python
A: 
``` python
def binary_search(arr: list[int], target: int) -> int:
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = left + (right - left) // 2
        
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
            
    return -1
```

Q: How would you modify binary search to find the leftmost occurrence?
A: 
```python
def binary_search_leftmost(arr: list[int], target: int) -> int:
    left, right = 0, len(arr) - 1
    result = -1
    
    while left <= right:
        mid = left + (right - left) // 2
        
        if arr[mid] == target:
            result = mid  # Save the position
            right = mid - 1  # Continue searching left
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
            
    return result
```

### Sorting Algorithms

#### Quick Sort
Q: What is QuickSort?
A: A divide-and-conquer sorting algorithm that picks a 'pivot' element and partitions the array around it.

Q: What is the average time complexity of QuickSort?
A: O(n log n)

Q: Implement QuickSort in Python
A: 
```python
def quicksort(arr: list[int]) -> list[int]:
    if len(arr) <= 1:
        return arr
        
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quicksort(left) + middle + quicksort(right)
```

#### Merge Sort
Q: What is MergeSort?
A: A divide-and-conquer algorithm that divides array into two halves, recursively sorts them, and merges.

Q: What is the time complexity of MergeSort?
A: O(n log n) in all cases

Q: Implement MergeSort in Python
A: 
```python
def mergesort(arr: list[int]) -> list[int]:
    if len(arr) <= 1:
        return arr
        
    mid = len(arr) // 2
    left = mergesort(arr[:mid])
    right = mergesort(arr[mid:])
    
    return merge(left, right)
    
def merge(left: list[int], right: list[int]) -> list[int]:
    result = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
            
    result.extend(left[i:])
    result.extend(right[j:])
    return result
```

## DATA STRUCTURES

### Hash Map

#### Concept Cards
Q: What is a hash map?
A: A data structure that implements an associative array abstract data type, using a hash function to map keys to values.

Q: What is the average time complexity for operations?
A: O(1) for insert, delete, and lookup

Q: What causes collisions in a hash map?
A: When two different keys hash to the same index

#### Implementation Cards
Q: Write pseudocode for a basic hash map
A: 
```
class HashMap:
    function init(size):
        create array of size
        initialize count = 0
        
    function hash(key):
        return hash_function(key) % size
        
    function put(key, value):
        index = hash(key)
        store (key,value) at index (handle collisions)
        
    function get(key):
        index = hash(key)
        return value at index (handle collisions)
        
    function remove(key):
        index = hash(key)
        remove value at index (handle collisions)
```

Q: Implement a basic hash map in Python
A: 
```python
class HashMap:
    def __init__(self, size=1000):
        self.size = size
        self.map = [[] for _ in range(self.size)]
    
    def _get_hash(self, key: str) -> int:
        return hash(key) % self.size
    
    def put(self, key: str, value: any) -> None:
        hash_key = self._get_hash(key)
        bucket = self.map[hash_key]
        
        for i, (k, v) in enumerate(bucket):
            if k == key:
                bucket[i] = (key, value)
                return
        bucket.append((key, value))
    
    def get(self, key: str) -> any:
        hash_key = self._get_hash(key)
        bucket = self.map[hash_key]
        
        for k, v in bucket:
            if k == key:
                return v
        return None
    
    def remove(self, key: str) -> None:
        hash_key = self._get_hash(key)
        bucket = self.map[hash_key]
        
        for i, (k, v) in enumerate(bucket):
            if k == key:
                del bucket[i]
                return
```

### Linked List

#### Concept Cards
Q: What is a linked list?
A: A sequential data structure where each element points to the next element in the sequence.

Q: What are the advantages of linked lists over arrays?
A: Dynamic size, efficient insertion/deletion at beginning

Q: What is the time complexity of operations?
A: Access O(n), Insert/Delete at beginning O(1), Insert/Delete at position O(n)

#### Implementation Cards
Q: Write pseudocode for a singly linked list
A: 
```
class Node:
    value
    next = null

class LinkedList:
    function init():
        head = null
        
    function insert_front(value):
        new_node = Node(value)
        new_node.next = head
        head = new_node
        
    function delete_front():
        if head is null: return
        head = head.next
        
    function search(value):
        current = head
        while current is not null:
            if current.value == value: return current
            current = current.next
        return null
```

Q: Implement a singly linked list in Python
A: 
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class LinkedList:
    def __init__(self):
        self.head = None
    
    def insert_front(self, val: int) -> None:
        new_node = ListNode(val)
        new_node.next = self.head
        self.head = new_node
    
    def delete_front(self) -> None:
        if not self.head:
            return
        self.head = self.head.next
    
    def search(self, val: int) -> ListNode:
        current = self.head
        while current:
            if current.val == val:
                return current
            current = current.next
        return None
    
    def insert_after(self, node: ListNode, val: int) -> None:
        if not node:
            return
        new_node = ListNode(val)
        new_node.next = node.next
        node.next = new_node
```

### Queue

#### Concept Cards
Q: What is a queue?
A: A linear data structure that follows First-In-First-Out (FIFO) principle.

Q: What are the main operations of a queue?
A: enqueue (add to back) and dequeue (remove from front)

Q: What is the time complexity of queue operations?
A: O(1) for both enqueue and dequeue

#### Implementation Cards
Q: Write pseudocode for a queue
A: 
```
class Queue:
    function init():
        items = empty list
        
    function enqueue(value):
        add value to end of items
        
    function dequeue():
        if items is empty: return null
        return remove and return first item
        
    function peek():
        if items is empty: return null
        return first item
```

Q: Implement a queue in Python
A: 
```python
class Queue:
    def __init__(self):
        self.items = []
    
    def enqueue(self, val: any) -> None:
        self.items.append(val)
    
    def dequeue(self) -> any:
        if not self.is_empty():
            return self.items.pop(0)
        return None
    
    def peek(self) -> any:
        if not self.is_empty():
            return self.items[0]
        return None
    
    def is_empty(self) -> bool:
        return len(self.items) == 0
```

Q: Implement a queue using two stacks in Python
A: 
```python
class QueueUsingStacks:
    def __init__(self):
        self.stack1 = []  # for enqueue
        self.stack2 = []  # for dequeue
    
    def enqueue(self, val: any) -> None:
        self.stack1.append(val)
    
    def dequeue(self) -> any:
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        return self.stack2.pop() if self.stack2 else None
```

### Stack

#### Concept Cards
Q: What is a stack?
A: A linear data structure that follows Last-In-First-Out (LIFO) principle.

Q: What are the main operations of a stack?
A: push (add to top) and pop (remove from top)

Q: What is the time complexity of stack operations?
A: O(1) for both push and pop

#### Implementation Cards
Q: Write pseudocode for a stack
A: 
```python
class Stack:
    function init():
        items = empty list
        
    function push(value):
        add value to end of items
        
    function pop():
        if items is empty: return null
        return remove and return last item
        
    function peek():
        if items is empty: return null
        return last item
```

Q: Implement a stack in Python
A: 
```python
class Stack:
    def __init__(self):
        self.items = []
    
    def push(self, val: any) -> None:
        self.items.append(val)
    
    def pop(self) -> any:
        if not self.is_empty():
            return self.items.pop()
        return None
    
    def peek(self) -> any:
        if not self.is_empty():
            return self.items[-1]
        return None
    
    def is_empty(self) -> bool:
        return len(self.items) == 0
```

### Binary Tree

#### Concept Cards
Q: What is a binary tree?
A: A tree data structure where each node has at most two children, referred to as left and right child.

Q: What is a binary search tree (BST)?
A: A binary tree where for each node, all left subtree values are less than the node's value, and all right subtree values are greater.

Q: What is the time complexity of BST operations?
A: Average: O(log n) for search, insert, delete. Worst case: O(n) if tree is unbalanced

#### Implementation Cards
Q: Write pseudocode for a binary tree node
A: 
```python
class TreeNode:
    value
    left = null
    right = null
```

Q: Implement a binary search tree in Python
A: 
```python
class TreeNode:
    def __init__(self, val=0):
        self.val = val
        self.left = None
        self.right = None

class BST:
    def __init__(self):
        self.root = None
    
    def insert(self, val: int) -> None:
        if not self.root:
            self.root = TreeNode(val)
            return
        
        def _insert(node, val):
            if val < node.val:
                if not node.left:
                    node.left = TreeNode(val)
                else:
                    _insert(node.left, val)
            else:
                if not node.right:
                    node.right = TreeNode(val)
                else:
                    _insert(node.right, val)
        
        _insert(self.root, val)
    
    def search(self, val: int) -> TreeNode:
        def _search(node, val):
            if not node or node.val == val:
                return node
            if val < node.val:
                return _search(node.left, val)
            return _search(node.right, val)
        
        return _search(self.root, val)
```

Q: Implement common tree traversals in Python
A: 
```python
def inorder(root: TreeNode) -> list[int]:
    result = []
    def _inorder(node):
        if node:
            _inorder(node.left)
            result.append(node.val)
            _inorder(node.right)
    _inorder(root)
    return result

def preorder(root: TreeNode) -> list[int]:
    result = []
    def _preorder(node):
        if node:
            result.append(node.val)
            _preorder(node.left)
            _preorder(node.right)
    _preorder(root)
    return result

def postorder(root: TreeNode) -> list[int]:
    result = []
    def _postorder(node):
        if node:
            _postorder(node.left)
            _postorder(node.right)
            result.append(node.val)
    _postorder(root)
    return result
```

### Trie (Prefix Tree)

#### Concept Cards
Q: What is a trie?
A: A tree-like data structure used to store strings, where each node represents a character and paths from root to leaf form complete strings.

Q: What are common use cases for tries?
A: Autocomplete, spell checkers, IP routing tables

Q: What is the time complexity of trie operations?
A: O(m) where m is the length of the string for insert and search

#### Implementation Cards
Q: Implement a trie in Python
A: 
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def insert(self, word: str) -> None:
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end = True
    
    def search(self, word: str) -> bool:
        node = self.root
        for char in word:
            if char not in node.children:
                return False
            node = node.children[char]
        return node.is_end
    
    def starts_with(self, prefix: str) -> bool:
        node = self.root
        for char in prefix:
            if char not in node.children:
                return False
            node = node.children[char]
        return True
```

### Heap (Priority Queue)

#### Concept Cards
Q: What is a heap?
A: A complete binary tree where each node's value follows the heap property (either min-heap or max-heap).

Q: What is the heap property?
A: In a max-heap, parent's value is greater than children. In a min-heap, parent's value is less than children.

Q: What are the time complexities of heap operations?
A: Insert: O(log n), Remove top: O(log n), Get top: O(1)

#### Implementation Cards
Q: Implement a min heap in Python
A: 
```python
class MinHeap:
    def __init__(self):
        self.heap = []
    
    def parent(self, i: int) -> int:
        return (i - 1) // 2
    
    def left_child(self, i: int) -> int:
        return 2 * i + 1
    
    def right_child(self, i: int) -> int:
        return 2 * i + 2
    
    def insert(self, val: int) -> None:
        self.heap.append(val)
        self._sift_up(len(self.heap) - 1)
    
    def extract_min(self) -> int:
        if not self.heap:
            return None
        
        min_val = self.heap[0]
        last_val = self.heap.pop()
        
        if self.heap:
            self.heap[0] = last_val
            self._sift_down(0)
            
        return min_val
    
    def _sift_up(self, i: int) -> None:
        parent = self.parent(i)
        if i > 0 and self.heap[i] < self.heap[parent]:
            self.heap[i], self.heap[parent] = self.heap[parent], self.heap[i]
            self._sift_up(parent)
    
    def _sift_down(self, i: int) -> None:
        min_idx = i
        left = self.left_child(i)
        right = self.right_child(i)
        
        if left < len(self.heap) and self.heap[left] < self.heap[min_idx]:
            min_idx = left
            
        if right < len(self.heap) and self.heap[right] < self.heap[min_idx]:
            min_idx = right
            
        if min_idx != i:
            self.heap[i], self.heap[min_idx] = self.heap[min_idx], self.heap[i]
            self._sift_down(min_idx)
```

## TECHNIQUES

### Sliding Window

#### Concept Cards
Q: What is the sliding window technique?
A: A method to perform operations on arrays/strings using a window that slides through the data.

Q: When should you use sliding window?
A: For problems involving contiguous sequences in arrays/strings where you need to find subsets of data.

Q: What are common sliding window patterns?
A: Fixed-size window, variable-size window with conditions

#### Implementation Cards
Q: Implement fixed-size sliding window template in Python
A: 
```python
def fixed_sliding_window(arr: list[int], k: int) -> list[int]:
    if not arr or k <= 0:
        return []
    
    result = []
    window_sum = sum(arr[:k])  # Initial window
    result.append(window_sum)
    
    for i in range(k, len(arr)):
        # Remove first element of previous window
        # Add last element of current window
        window_sum = window_sum - arr[i-k] + arr[i]
        result.append(window_sum)
    
    return result
```

Q: Implement variable-size sliding window template in Python
A: 
```python
def variable_sliding_window(arr: list[int], target: int) -> int:
    window_sum = 0
    window_start = 0
    min_length = float('inf')
    
    for window_end in range(len(arr)):
        window_sum += arr[window_end]
        
        while window_sum >= target:
            min_length = min(min_length, window_end - window_start + 1)
            window_sum -= arr[window_start]
            window_start += 1
    
    return min_length if min_length != float('inf') else 0
```

### Two Pointers

#### Concept Cards
Q: What is the two pointers technique?
A: A method using two pointers to solve array problems, often moving towards each other or in the same direction.

Q: When should you use two pointers?
A: For problems involving searching pairs in sorted arrays, or when you need to track two positions in an array.

#### Implementation Cards
Q: Implement two pointers template for pair sum in Python
A: 
```python
def find_pair_sum(arr: list[int], target: int) -> tuple[int, int]:
    left, right = 0, len(arr) - 1
    
    while left < right:
        current_sum = arr[left] + arr[right]
        if current_sum == target:
            return (left, right)
        elif current_sum < target:
            left += 1
        else:
            right -= 1
    
    return (-1, -1)  # No pair found
```

### Dynamic Programming

#### Concept Cards
Q: What is dynamic programming?
A: A method to solve complex problems by breaking them down into simpler subproblems and storing the results for future use.

Q: What are the key components of DP?
A: 1. Optimal substructure 2. Overlapping subproblems 3. State and transition function

#### Implementation Cards
Q: Implement fibonacci using DP in Python
A: 
```python
def fib_dp(n: int) -> int:
    if n <= 1:
        return n
    
    dp = [0] * (n + 1)
    dp[1] = 1
    
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    
    return dp[n]
```

Q: Implement 0/1 knapsack using DP in Python
A: 
```python
def knapsack(values: list[int], weights: list[int], capacity: int) -> int:
    n = len(values)
    dp = [[0] * (capacity + 1) for _ in range(n + 1)]
    
    for i in range(1, n + 1):
        for w in range(capacity + 1):
            if weights[i-1] <= w:
                dp[i][w] = max(
                    values[i-1] + dp[i-1][w-weights[i-1]],
                    dp[i-1][w]
                )
            else:
                dp[i][w] = dp[i-1][w]
    
    return dp[n][capacity]
```

### Backtracking

#### Concept Cards
Q: What is backtracking?
A: An algorithmic technique that considers searching every possible combination in a systematic way.

Q: When should you use backtracking?
A: For problems that require finding all (or some) solutions to a computational problem, particularly constraint satisfaction.

#### Implementation Cards
Q: Implement N-Queens using backtracking in Python
A: 
```python
def solve_n_queens(n: int) -> list[list[str]]:
    def create_board():
        return [['.' * n for _ in range(n)]]
    
    def can_place(row: int, col: int, queens: set) -> bool:
        for prev_row, prev_col in queens:
            if prev_col == col:
                return False
            if abs(prev_row - row) == abs(prev_col - col):
                return False
        return True
    
    def backtrack(row: int, queens: set) -> list[list[str]]:
        if row == n:
            board = create_board()
            for r, c in queens:
                board[r] = board[r][:c] + 'Q' + board[r][c+
                ...
```
            

### Greedy Algorithms

#### Concept Cards
Q: What is a greedy algorithm?
A: An algorithmic paradigm that makes the locally optimal choice at each step, hoping to find a global optimum.

Q: When should you use greedy algorithms?
A: When local optimal choices lead to global optimal solution, like in activity selection or Huffman coding.

Q: What are common examples of greedy problems?
A: Minimum spanning tree, activity selection, coin change with unlimited coins.

#### Implementation Cards
Q: Implement activity selection in Python
A: 
```python
def activity_selection(start: list[int], finish: list[int]) -> list[int]:
    activities = sorted(zip(start, finish), key=lambda x: x[1])
    selected = [0]  # First activity is always selected
    last_finish = activities[0][1]
    
    for i in range(1, len(activities)):
        if activities[i][0] >= last_finish:
            selected.append(i)
            last_finish = activities[i][1]
    
    return selected
```

### Intervals

#### Concept Cards
Q: What are interval problems?
A: Problems involving ranges or periods with start and end points.

Q: What are common interval operations?
A: Merging overlapping intervals, finding intersections, checking for overlaps.

#### Implementation Cards
Q: Implement merge intervals in Python
A: 
```python
def merge_intervals(intervals: list[list[int]]) -> list[list[int]]:
    if not intervals:
        return []
        
    # Sort by start time
    intervals.sort(key=lambda x: x[0])
    
    result = [intervals[0]]
    
    for interval in intervals[1:]:
        if interval[0] <= result[-1][1]:
            result[-1][1] = max(result[-1][1], interval[1])
        else:
            result.append(interval)
    
    return result
```

Q: Implement interval intersection in Python
A: 
```python
def interval_intersection(A: list[list[int]], B: list[list[int]]) -> list[list[int]]:
    result = []
    i = j = 0
    
    while i < len(A) and j < len(B):
        start = max(A[i][0], B[j][0])
        end = min(A[i][1], B[j][1])
        
        if start <= end:
            result.append([start, end])
            
        if A[i][1] < B[j][1]:
            i += 1
        else:
            j += 1
            
    return result
```

### Bit Manipulation

#### Concept Cards
Q: What is bit manipulation?
A: Technique of manipulating individual bits in integers using bitwise operations.

Q: What are common bit operations?
A: AND (&), OR (|), XOR (^), NOT (~), Left Shift (<<), Right Shift (>>)

Q: What are common bit manipulation tricks?
A: Check if power of 2, count set bits, find single number in pairs

#### Implementation Cards
Q: Implement check if power of 2 in Python
A: 
```python
def is_power_of_two(n: int) -> bool:
    return n > 0 and (n & (n - 1)) == 0
```

Q: Implement count set bits in Python
A: 
```python
def count_set_bits(n: int) -> int:
    count = 0
    while n:
        count += n & 1
        n >>= 1
    return count
```

Q: Implement single number in Python
A: 
```python
def find_single_number(nums: list[int]) -> int:
    result = 0
    for num in nums:
        result ^= num
    return result
```

### Math

#### Concept Cards
Q: What are common mathematical concepts in coding interviews?
A: Prime numbers, GCD/LCM, factorials, combinations/permutations

Q: What is the prime factorization of a number?
A: Breaking down a number into its prime factors

#### Implementation Cards
Q: Implement prime number check in Python
A: 
```python
def is_prime(n: int) -> bool:
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True
```

Q: Implement GCD using Euclidean algorithm in Python
A: 
```python
def gcd(a: int, b: int) -> int:
    while b:
        a, b = b, a % b
    return a
```

### Common Patterns and Tips

#### Interview Strategy Cards
Q: What is the general approach to solving coding problems?
A: 1. Understand the problem
   2. Find edge cases
   3. Design solution
   4. Write code
   5. Test code
   6. Optimize if needed

Q: What are common optimization techniques?
A: 1. Hash maps for O(1) lookup
   2. Two pointers to avoid nested loops
   3. Sliding window for subarrays
   4. Binary search for sorted arrays
   5. Dynamic programming for overlapping subproblems

Q: What are common space-time tradeoffs?
A: 1. Using extra space to reduce time complexity
   2. Memoization vs tabulation in DP
   3. Preprocessing vs on-the-fly computation

#### Common Pitfalls Cards
Q: What are common mistakes to avoid?
A: 1. Not handling edge cases
   2. Not validating input
   3. Off-by-one errors
   4. Integer overflow
   5. Not considering time/space complexity

Q: What should you communicate during interviews?
A: 1. Your thought process
   2. Alternative approaches
   3. Time and space complexity
   4. Tradeoffs in your solution
   5. Test cases and edge cases

### System Design Considerations

#### Scaling Cards
Q: How do these data structures scale?
A: 1. Arrays: Poor for large insertions/deletions
   2. Hash Maps: Good for distributed systems with proper hashing
   3. Trees: Good for balanced data distribution
   4. Tries: Excellent for string-based lookups at scale

Q: What are important factors in scaling?
A: 1. Memory usage
   2. CPU efficiency
   3. I/O operations
   4. Network bandwidth
   5. Concurrent access patterns

#### Implementation Trade-offs Cards
Q: What are common implementation trade-offs?
A: 1. Array vs Linked List: Random access vs Sequential access
   2. Hash Table vs BST: Average vs Worst case complexity
   3. BFS vs DFS: Memory vs Depth exploration
   4. Iteration vs Recursion: Space vs Clarity