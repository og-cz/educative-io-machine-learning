### **A. Creating NumPy Arrays**

**Code:**

```python
import numpy as np

arr = np.array([[0, 1, 2], [3, 4, 5]], dtype=np.float32)
print(repr(arr))
```

**Explanation:**
Converts a Python list to a 2-D NumPy array. The `dtype` argument sets the data type. Mixed types in an array are automatically upcast to a common type (e.g., integers → floats if floats are present).

---

**Code (Upcasting example):**

```python
arr = np.array([0, 0.1, 2])
print(repr(arr))
```

**Explanation:**
Mixed `int` and `float` elements are upcast to `float` automatically.

---

### **B. Copying Arrays**

**Code:**

```python
a = np.array([0, 1])
b = np.array([9, 8])
c = a
c[0] = 5
d = b.copy()
d[0] = 6
```

**Explanation:**
Assigning an array (`c = a`) creates a reference, not a copy. Modifying `c` changes `a`. Using `.copy()` creates a new array (`d`) independent of `b`.

---

### **C. Casting Arrays**

**Code:**

```python
arr = np.array([0, 1, 2])
print(arr.dtype)
arr = arr.astype(np.float32)
print(arr.dtype)
```

**Explanation:**
`astype` converts an array to a new data type. Here, integers are converted to `float32`.

---

### **D. Using NaN**

**Code:**

```python
arr = np.array([np.nan, 1, 2])
print(repr(arr))
```

**Explanation:**
`np.nan` represents “Not a Number” and can only exist in float arrays or string arrays when combined with text.

---

### **E. Infinity**

**Code:**

```python
print(np.inf > 1000000)
arr = np.array([np.inf, 5])
arr2 = np.array([-np.inf, 1])
```

**Explanation:**
`np.inf` represents positive infinity, `-np.inf` represents negative infinity. They cannot be used with integer arrays.

---

### **Practice Arrays**

**Code (NaN array and copy):**

```python
arr = np.array([np.nan,2,3,4,5])
arr2 = arr.copy()
arr2[0] = 10
```

**Explanation:**
Creates a copy of `arr` to modify it independently.

---

**Code (Float arrays):**

```python
float_arr = np.array([1,5.4,3])
float_arr2 = arr2.astype(np.float32)
```

**Explanation:**
`float_arr` upcasts automatically due to mixed types. `float_arr2` is manually cast to `float32`.

---

**Code (2-D matrix):**

```python
matrix = np.array([[1,2,3],[4,5,6]], dtype=np.float32)
```

**Explanation:**
Creates a 2-D array (matrix) with a specified float type.

---

# **Time to Code!**

### **1. Create an array with NaN**

**Question:**
Create an array from the list `[np.nan, 2, 3, 4, 5]`.

**Answer:**

```python
arr = np.array([np.nan, 2, 3, 4, 5])
```

---

### **2. Copy an array and modify it**

**Question:**
Copy `arr` into `arr2` and change the first element of `arr2` to `10`.

**Answer:**

```python
arr2 = arr.copy()
arr2[0] = 10
```

---

### **3. Create float arrays**

**Question:**

- Create `float_arr` from the list `[1, 5.4, 3]` (automatic upcasting).
- Create `float_arr2` by manually casting `arr2` to `np.float32`.

**Answer:**

```python
float_arr = np.array([1, 5.4, 3])
float_arr2 = arr2.astype(np.float32)
```

---

### **4. Create a 2-D matrix**

**Question:**
Create a 2-D array (matrix) with first row `[1, 2, 3]` and second row `[4, 5, 6]`, with type `np.float32`.

**Answer:**

```python
matrix = np.array([[1, 2, 3], [4, 5, 6]], dtype=np.float32)
```
