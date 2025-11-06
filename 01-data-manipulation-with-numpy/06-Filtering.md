# **Filtering NumPy Data**

Filter NumPy data for specific values.

---

## **Chapter Goals:**

- Learn how to filter data in NumPy
- Write code for filtering NumPy arrays

---

## **A. Filtering Data**

Sometimes we only want values that meet a certain condition.

For example, if tracking baseball batting averages, we may want only values **above 0.300**.

In NumPy, we can apply **relation operations element-wise**:

```python
arr = np.array([[0, 2, 3],
                [1, 3, -6],
                [-3, -2, 1]])

print(repr(arr == 3))
print(repr(arr > 0))
print(repr(arr != 1))
print(repr(~(arr != 1)))  # Negation
```

**Output:**

```
array([[False, False,  True],
       [False,  True, False],
       [False, False, False]])
array([[False,  True,  True],
       [ True,  True, False],
       [False, False,  True]])
array([[ True,  True,  True],
       [False,  True,  True],
       [ True,  True, False]])
array([[False, False, False],
       [ True, False, False],
       [False, False,  True]])
```

> **Tip:** `np.nan` can’t be compared with `==` or `>`. Use `np.isnan(arr)` instead.

---

## **B. Filtering with `np.where`**

`np.where(condition)` returns the **indices of True elements**:

```python
arr = np.array([0, 3, 5, 3, 1])
print(repr(np.where(arr == 3)))

arr = np.array([[0, 2, 3],
                [1, 0, 0],
                [-3, 0, 0]])
x_ind, y_ind = np.where(arr != 0)
print(repr(x_ind))  # Row indices
print(repr(y_ind))  # Column indices
print(repr(arr[x_ind, y_ind]))
```

**Output:**

```
(array([1, 3]),)
array([0, 0, 1, 2])
array([1, 2, 0, 0])
array([ 2,  3,  1, -3])
```

`np.where` with 3 arguments works like a **vectorized if-else**:

```python
np_filter = np.array([[True, False], [False, True]])
positives = np.array([[1, 2], [3, 4]])
negatives = np.array([[-2, -5], [-1, -8]])

print(repr(np.where(np_filter, positives, negatives)))
```

**Output:**

```
array([[ 1, -5],
       [-1,  4]])
```

> You can also use **broadcasting** for constants:

```python
print(np.where(np_filter, positives, -1))
```

**Output:**

```
array([[ 1, -1],
       [-1,  4]])
```

---

## **C. Axis-wise Filtering**

`np.any` → logical OR
`np.all` → logical AND

```python
arr = np.array([[-2, -1, -3],
                [4, 5, -6],
                [3, 9, 1]])

print(np.any(arr > 0, axis=0))  # Column-wise
print(np.any(arr > 0, axis=1))  # Row-wise
print(np.all(arr > 0, axis=1))  # Row-wise AND
```

**Output:**

```
array([ True,  True,  True])
array([False,  True,  True])
array([False, False,  True])
```

Combine with `np.where` to **filter entire rows or columns**:

```python
has_positive = np.any(arr > 0, axis=1)
print(has_positive)
print(repr(arr[np.where(has_positive)]))
```

**Output:**

```
[False  True  True]
array([[ 4,  5, -6],
       [ 3,  9,  1]])
```

---

# **Time to Code!**

### **1. Get all positive values**

```python
def get_positives(data):
    positives = data > 0
    x_ind, y_ind = np.where(positives)
    return data[x_ind, y_ind]
```

---

### **2. Replace non-positive elements with zeros**

```python
def replace_zeros(data):
    zeros = np.zeros_like(data)
    zero_replace = np.where(data > 0, data, zeros)
    return zero_replace
```

---

### **3. Replace non-positive elements with -1**

```python
def replace_neg_one(data):
    neg_one_replace = np.where(data > 0, data, -1)
    return neg_one_replace
```

---

### **4. Filter using a “coin flip” boolean array**

```python
def coin_flip_filter(data):
    coin_flips = np.random.randint(2, size=data.shape)
    bool_coin_flips = coin_flips.astype(np.bool)
    one_replace = np.where(bool_coin_flips, data, 1)
    return one_replace
```
