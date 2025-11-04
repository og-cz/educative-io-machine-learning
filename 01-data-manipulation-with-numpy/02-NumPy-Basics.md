# NumPy Basics

### **A. Ranged Data**

**1. `np.arange`**

```python
arr = np.arange(5)        # [0, 1, 2, 3, 4]
arr = np.arange(-1, 4)    # [-1, 0, 1, 2, 3]
arr = np.arange(-1.5, 4, 2)  # [-1.5, 0.5, 2.5]
```

**Explanation:**

- Creates 1D arrays with a start `m`, stop `n`, and step `s`.
- Similar to Python `range`, but returns a NumPy array.
- Upcasts mixed types automatically.

**2. `np.linspace`**

```python
arr = np.linspace(5, 11, num=4)                # [5., 7., 9., 11.]
arr = np.linspace(5, 11, num=4, endpoint=False)  # [5., 6.5, 8., 9.5]
arr = np.linspace(5, 11, num=4, dtype=np.int32)  # [5, 7, 9, 11]
```

**Explanation:**

- Splits a range `[start, stop]` into `num` evenly spaced points.
- Endpoints are included by default (`endpoint=True`).
- Can manually set data type with `dtype`.

---

### **B. Reshaping Data**

**1. `np.reshape`**

```python
arr = np.arange(8)
reshaped_arr = np.reshape(arr, (2, 4))
reshaped_arr2 = np.reshape(arr, (-1, 2, 2))
```

**Explanation:**

- Changes the shape of an array without altering data.
- `-1` can be used in one dimension to infer its size automatically.
- Total elements must match.

**2. Flattening**

```python
flattened = reshaped_arr.flatten()
```

**Explanation:**

- Converts any array into 1D.
- Useful for preparing data for processing or analysis.

---

### **C. Transposing**

**1. Basic transpose**

```python
arr = np.arange(8).reshape(4, 2)
transposed = np.transpose(arr)
```

**Explanation:**

- Swaps rows and columns.
- Shape changes from `(4, 2)` → `(2, 4)`.

**2. Transpose with axes permutation**

```python
arr = np.arange(24).reshape(3, 4, 2)
transposed = np.transpose(arr, axes=(1, 2, 0))
```

**Explanation:**

- Reorders axes according to `axes` tuple.
- Allows flexible rearrangement of multidimensional data.

---

### **D. Arrays of Zeros and Ones**

**1. `np.zeros` and `np.ones`**

```python
arr = np.zeros(4)            # [0., 0., 0., 0.]
arr2 = np.ones((2, 3))       # 2x3 array of 1s
arr3 = np.ones((2, 3), dtype=np.int32)  # int array
```

**2. `np.zeros_like` and `np.ones_like`**

```python
arr = np.array([[1, 2], [3, 4]])
zeros_like_arr = np.zeros_like(arr)  # same shape as arr, filled with 0
ones_like_arr = np.ones_like(arr)    # same shape as arr, filled with 1
```

**Explanation:**

- Useful for creating arrays with the same shape as existing arrays.
- Can specify `dtype` to change data type.

Here’s your **“Time to Code!” section** for the basic NumPy operations, formatted as questions with your answers included:

---

# **Time to Code!**

### **1. Create an initial array and reshape it**

**Question:**
Create an array `arr` of integers from 0 to 11, inclusive. Then reshape it into a 3D array with shape `(2, 3, 2)` and assign it to `reshaped`.

**Answer:**

```python
arr = np.arange(12)
reshaped = np.reshape(arr, (2, 3, 2))
```

**Explanation:**
`np.arange(12)` creates `[0, 1, ..., 11]`. `np.reshape` reorganizes it into 2 layers, each with 3 rows and 2 columns.

---

### **2. Flatten and transpose the reshaped array**

**Question:**
Create a flattened version of `reshaped` called `flattened`.
Then create a transposed version called `transposed` with axes permutation `(1, 2, 0)`.

**Answer:**

```python
flattened = reshaped.flatten()
transposed = np.transpose(reshaped, (1, 2, 0))
```

**Explanation:**
`flatten()` converts the 3D array back to 1D.
`np.transpose` with `(1, 2, 0)` reorders axes: first → third, second → first, third → second.

---

### **3. Create arrays of zeros and ones**

**Question:**

- Create a 1D array of 5 zeros called `zeros_arr`.
- Create an array of ones with the same shape as `transposed` called `ones_arr`.

**Answer:**

```python
zeros_arr = np.zeros(5)
ones_arr = np.ones_like(transposed)
```

**Explanation:**
`np.zeros(5)` creates `[0., 0., 0., 0., 0.]`.
`np.ones_like(transposed)` creates an array of ones with the same shape as `transposed`.

---

### **4. Create evenly spaced points**

**Question:**
Create an array `points` with 101 evenly spaced numbers between -3.5 and 1.5, inclusive.

**Answer:**

```python
points = np.linspace(-3.5, 1.5, num=101)
```

**Explanation:**
`np.linspace` splits the interval into 101 evenly spaced points. The choice of 101 ensures both endpoints are included and the spacing is consistent.
