# NumPy Arithmetic & Linear Algebra – Lecture Summary

### **A. Arithmetic**

**1. Element-wise arithmetic**

```python
arr = np.array([[1, 2], [3, 4]])
arr + 1      # Add 1 to each element
arr - 1.2    # Subtract 1.2 from each element
arr * 2      # Multiply each element by 2
arr / 2      # Divide each element by 2
arr // 2     # Integer division
arr**2       # Square each element
arr**0.5     # Square root each element
```

**Explanation:**

- Operations apply to all elements in the array at once.
- Efficient for modifying large datasets (e.g., converting Fahrenheit → Celsius).

```python
def f2c(temps):
    return (5/9)*(temps-32)
fahrenheits = np.array([32, -4, 14, -40])
celsius = f2c(fahrenheits)
```

- NumPy arithmetic **returns a new array**; original array is unchanged.

---

### **B. Non-linear functions**

**1. Exponentials and logarithms**

```python
arr = np.array([[1, 2], [3, 4]])
np.exp(arr)     # e^arr
np.exp2(arr)    # 2^arr

arr2 = np.array([[1, 10], [np.e, np.pi]])
np.log(arr2)    # Natural log
np.log10(arr2)  # Base 10 log
```

**Explanation:**

- Non-linear transformations like exponentials/logs can be applied element-wise.
- Constants: `np.e` and `np.pi`.

**2. General power**

```python
arr = np.array([[1, 2], [3, 4]])
np.power(3, arr)      # 3^arr
arr2 = np.array([[10.2, 4], [3, 5]])
np.power(arr2, arr)   # arr2^arr
```

- `np.power(base, exponent)` applies element-wise for arrays.

---

### **C. Matrix multiplication**

```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([-3, 0, 10])
np.matmul(arr1, arr2)  # Dot product for vectors

arr3 = np.array([[1, 2], [3, 4], [5, 6]])
arr4 = np.array([[-1, 0, 1], [3, 2, -4]])
np.matmul(arr3, arr4)  # Matrix multiplication
```

**Explanation:**

- `np.matmul(a, b)` performs matrix multiplication or dot product.
- Dimensions must align: second dim of `a` = first dim of `b`.

---

# **Time to Code!**

### **1. Create matrices**

```python
arr = np.array([[-0.5, 0.8,-0.1],
                [0.0,-1.2,1.3]])
arr2 = np.array([[1.2, 3.1], [1.2, 0.3], [1.5, 2.2]])
```

### **2. Perform arithmetic**

```python
multiplied = arr * np.pi          # Multiply each element by π
added = arr + multiplied          # Add original array
squared = added ** 2              # Square elements
```

### **3. Apply exponential & logarithm**

```python
exponential = np.exp(squared)     # e^squared
logged = np.log(arr2)             # Natural log
```

### **4. Matrix multiplication**

```python
matmul1 = np.matmul(logged, exponential)  # Shape (3, 3)
matmul2 = np.matmul(exponential, logged)  # Shape (2, 2)
```

**Explanation:**

- Operations applied element-wise for arithmetic, powers, exponentials, and logs.
- `np.matmul` combines arrays into new matrices, respecting dimensional rules.
