# **NumPy Statistical Analysis**

Learn how to apply basic statistical metrics to NumPy arrays.

---

## **Chapter Goals:**

- Learn about basic statistical analysis in NumPy
- Write code to obtain statistics for NumPy arrays

---

## **A. Analysis**

NumPy provides quick ways to inspect data arrays.

You can find **minimum** and **maximum** values:

```python
arr = np.array([[0, 72, 3],
                [1, 3, -60],
                [-3, -2, 4]])

print(arr.min())             # Overall minimum
print(arr.max())             # Overall maximum

print(repr(arr.min(axis=0))) # Minimum per column
print(repr(arr.max(axis=-1)))# Maximum per row
```

**Output:**

```
-60
72
array([ -3,  -2, -60])
array([72,  3,  4])
```

> **Tip:** `axis=0` → column-wise, `axis=1` → row-wise, `axis=-1` → last dimension

---

## **B. Statistical Metrics**

NumPy provides **mean, variance, median**:

```python
arr = np.array([[0, 72, 3],
                [1, 3, -60],
                [-3, -2, 4]])

print(np.mean(arr))                   # Mean of all elements
print(np.var(arr))                    # Variance of all elements
print(np.median(arr))                 # Median of all elements
print(repr(np.median(arr, axis=-1))) # Median per row
```

**Output:**

```
2.0
977.3333333333334
1.0
array([ 3.,  1., -2.])
```

> Use the `axis` argument to apply functions **row-wise** or **column-wise**.

---

# **Time to Code!**

### **1. Get overall minimum and maximum**

```python
def get_min_max(data):
    overall_min = data.min()
    overall_max = data.max()
    return overall_min, overall_max
```

---

### **2. Get minimums across each column**

```python
def col_min(data):
    return data.min(axis=0)
```

---

### **3. Compute mean, median, and variance**

```python
def basic_stats(data):
    mean = np.mean(data)
    median = np.median(data)
    var = np.var(data)
    return mean, median, var
```
