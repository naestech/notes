> intervals are a technique that uses ranges represented as `[start, end]`, where `start` is the beginning and `end` is the endpoint of the range.
> 

---

## **keywords**

merge: combining overlapping intervals into a single interval.

overlap: when two intervals share any part of their ranges.

union: the result of merging all overlapping intervals.

disjoint: intervals that have no overlap.

intersection: the range that two overlapping intervals share.

---

## **how it works**

### **diagram**

image.png

---

### **code**

**initialization:**

```python
intervals = []  # list to store intervals
```

**insertion:**

```python

def insert_interval(intervals, new_interval):
    result = []
    for interval in intervals:
        if interval[1] < new_interval[0]:
            result.append(interval)
        elif new_interval[1] < interval[0]:
            result.append(new_interval)
            new_interval = interval
        else:  # overlapping intervals, merge them
            new_interval[0] = min(new_interval[0], interval[0])
            new_interval[1] = max(new_interval[1], interval[1])
    result.append(new_interval)
    return result

```

**retrieval:**

```python

def find_overlapping_intervals(intervals, target):
    return [interval for interval in intervals if not (interval[1] < target[0] or interval[0] > target[1])]

```

**deletion:**

```python

def delete_interval(intervals, to_delete):
    result = []
    for interval in intervals:
        if interval[1] <= to_delete[0] or interval[0] >= to_delete[1]:
            result.append(interval)
        else:
            if interval[0] < to_delete[0]:
                result.append([interval[0], to_delete[0]])
            if interval[1] > to_delete[1]:
                result.append([to_delete[1], interval[1]])
    return result

```

**display:**

```python

def display_intervals(intervals):
    return ', '.join(f"[{start}, {end}]" for start, end in intervals)

```

---

**putting it together:**

1. initialize the intervals list.
2. perform operations like insertion, retrieval, deletion, or displaying intervals.
3. use helper functions to handle overlapping or merging logic.

**main:**

```python
if __name__ == "__main__":
    intervals = [[1, 3], [6, 9]]
    new_interval = [2, 5]
    intervals = insert_interval(intervals, new_interval)
    print("After insertion:", display_intervals(intervals))

    target = [4, 7]
    overlaps = find_overlapping_intervals(intervals, target)
    print("Overlapping intervals:", display_intervals(overlaps))

    to_delete = [2, 6]
    intervals = delete_interval(intervals, to_delete)
    print("After deletion:", display_intervals(intervals))

```

---

## **runtime complexity**

**insertion, retrieval, deletion:**

**best and worst case:** O(n)

most operations require iterating through the intervals list, so runtime depends on the number of intervals.

---

## **use cases**

best for problems involving scheduling such as meeting rooms and time intervals, merging ranges such as combining intervals on a number line, or range queries and overlaps.

---

## **resources**

[Interval cheatsheet for coding interviews | Tech Interview Handbook](https://www.techinterviewhandbook.org/algorithms/interval/)