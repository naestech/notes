> a **data structure** that maps keys to a values using a hashing function.

---

a **hash function** is an **algorithm** that transforms input data into a fixed-length string.

$$
\text{index} = \text{hash}(\text{key}) \bmod \text{tableSize}
$$

a **load factor** is the ratio (usually ≥ 0.7) that determines when the hash table should resize.

$$
\text{loadFactor} = \text{keys} \div \text{buckets}
$$

---

## keywords

bucket: storage unit for key-value pairs at an index.

collision: happens when two or more keys hash to the same index.

hash: a fixed-length string.

index: hash table location.

key: input data.

modulus (%): division remainder.

---

## how it works

### diagram

![IMG_4287C0837D6B-1.jpeg](https://prod-files-secure.s3.us-west-2.amazonaws.com/d61f2617-4cd7-47f3-8c1b-42b35e353d1e/a3b175ea-f61e-4d35-8e0d-55a21a6db41f/IMG_4287C0837D6B-1.jpeg)

---

### code

**initialization:**

```python
class hashTable:
    def __init__(self, size):
        self.size = size
        self.table = [[] for _ in range(size)]  # create buckets

```

**hash function:**

```python
    def hash_function(self, key):
        return key % self.size  # simple hash: key modulo table size

```

**insertion:**

```python
    def insert(self, key, value):
        index = self.hash_function(key)  # calculate index
        # check for existing key and update value if found
        for pair in self.table[index]:
            if pair[0] == key:
                pair[1] = value
                return
        # if key is new, append it to the bucket
        self.table[index].append([key, value])

```

**retrieval:**

```python
    def get(self, key):
        index = self.hash_function(key)  # calculate index
        for pair in self.table[index]:
            if pair[0] == key:
                return pair[1]  # return the value for the key
        return None  # key not found

```

**deletion:**

```python
    def delete(self, key):
        index = self.hash_function(key)  # calculate index
        for i, pair in enumerate(self.table[index]):
            if pair[0] == key:
                del self.table[index][i]  # remove the pair
                return True  # success
        return False  # key not found

```

**display:**

```python
    def display(self):
        print("hash table:")
        for i, bucket in enumerate(self.table):
            print(f"{i:02} -> {bucket}")

```

**load factor:**

```python
    def load_factor(self):
        num_elements = sum(len(bucket) for bucket in self.table)
        return num_elements / self.size

```

**resizing:**

```python
    def resize(self):
        new_size = self.size * 2
        new_table = [[] for _ in range(new_size)]
        for bucket in self.table:
            for key, value in bucket:
                new_index = key % new_size
                new_table[new_index].append([key, value])
        self.size = new_size
        self.table = new_table

```

---

**putting it together:**

1. **initialization**: `__init__` sets up the table and bucket size.
2. **operations**: `insert`, `get`, and `delete` let you modify and access the table.
3. **utilities**: `display` and `load_factor` help debug and monitor performance.
4. **resizing**: ensures the table remains efficient at high load factors.

**main:**

```python
# create the hash table
hash_table = hashTable(5)

# insert keys and values
hash_table.insert(111, "espresso")
hash_table.insert(222, "cappuccino")
hash_table.insert(333, "macchiato")
hash_table.insert(444, "latte")
hash_table.insert(3333, "sandwich")  # collision with 333

# display the hash table
hash_table.display()

# retrieve some values
print("\\nretrieving values:")
print("key 111:", hash_table.get(111))
print("key 333:", hash_table.get(333))
print("key 3333:", hash_table.get(3333))  # demonstrates collision handling
print("key 999 (not in table):", hash_table.get(999))

# delete a key and display again
print("\\nremoving key 333:")
hash_table.delete(333)
hash_table.display()

# check load factor and resize if necessary
print("\\nload factor before resize:", hash_table.load_factor())
if hash_table.load_factor() > 0.7:
    print("resizing hash table...")
    hash_table.resize()
    hash_table.display()

```

---

## runtime complexity

**insertion, retrieval, deletion:**

**best case:** O(1)

if no keys collide, the function computes the hash, finds an empty bucket, then inserts/prints/deletes the key-value pair.

**worst case:** O(n)

if all keys collide, the function traverses the bucket (like a linked list) to check for duplicate keys, then inserts/prints/deletes the key-value pair.

---

## use cases

best for fast key-value lookups when order doesn’t matter

---

## resources

https://www.youtube.com/watch?v=FsfRsGFHuv4
