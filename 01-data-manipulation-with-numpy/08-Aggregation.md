# **NumPy Aggregation Techniques**

Learn how to combine and summarize NumPy arrays.

---

## **Chapter Goals:**

- Learn how to aggregate data in NumPy
- Write code to obtain sums and concatenations of NumPy arrays

---

## **A. Summation**

NumPy provides `np.sum` to calculate totals:

```python
arr = np.array([[0, 72, 3],
                [1, 3, -60],
                [-3, -2, 4]])

print(np.sum(arr))             # Overall sum
print(repr(np.sum(arr, axis=0))) # Sum per column
print(repr(np.sum(arr, axis=1))) # Sum per row
```

**Output:**

```
18
array([ -2,  73, -53])
array([ 75, -56,  -1])
```

Cumulative sums are calculated using `np.cumsum`:

```python
print(repr(np.cumsum(arr)))          # Flattened cumulative sum
print(repr(np.cumsum(arr, axis=0)))  # Column-wise cumulative sum
print(repr(np.cumsum(arr, axis=1)))  # Row-wise cumulative sum
```

**Output:**

```
array([ 0, 72, 75, 76, 79, 19, 16, 14, 18])
array([[  0,  72,   3],
       [  1,  75, -57],
       [ -2,  73, -53]])
array([[  0,  72,  75],
       [  1,   4, -56],
       [ -3,  -5,  -1]])
```

> `axis=0` → down columns, `axis=1` → across rows

---

## **B. Concatenation**

Combine multiple arrays using `np.concatenate`:

```python
arr1 = np.array([[0, 72, 3],
                 [1, 3, -60],
                 [-3, -2, 4]])
arr2 = np.array([[-15, 6, 1],
                 [8, 9, -4],
                 [5, -21, 18]])

print(repr(np.concatenate([arr1, arr2])))         # Vertical concatenation
print(repr(np.concatenate([arr1, arr2], axis=1))) # Horizontal concatenation
```

**Output:**

```
array([[  0,  72,   3],
       [  1,   3, -60],
       [ -3,  -2,   4],
       [-15,   6,   1],
       [  8,   9,  -4],
       [  5, -21,  18]])
array([[  0,  72,   3, -15,   6,   1],
       [  1,   3, -60,   8,   9,  -4],
       [ -3,  -2,   4,   5, -21,  18]])
```

> `axis=0` → vertical stacking (rows), `axis=1` → horizontal stacking (columns)

---

# **Time to Code!**

### **1. Get overall and column sums**

```python
def get_sums(data):
    total_sum = np.sum(data)
    col_sum = np.sum(data, axis=0)
    return total_sum, col_sum
```

---

### **2. Get cumulative sums per row**

```python
def get_cumsum(data):
    row_cumsum = np.cumsum(data, axis=1)
    return row_cumsum
```

---

### **3. Concatenate two arrays**

```python
def concat_arrays(data1, data2):
    col_concat = np.concatenate([data1, data2])
    row_concat = np.concatenate([data1, data2], axis=1)
    return col_concat, row_concat
```
