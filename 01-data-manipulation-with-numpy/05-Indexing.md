# Indexing

Index into NumPy arrays to extract data and array slices.

---

## **Chapter Goals:**

- Learn about indexing arrays in NumPy
- Write code for indexing and slicing arrays

---

## **A. Array Accessing**

Accessing elements in NumPy arrays works exactly like Python lists.
For multi-dimensional arrays, you access elements the same way you would for lists of lists.

```python
arr = np.array([1, 2, 3, 4, 5])
print(arr[0])   # First element
print(arr[4])   # Last element

arr = np.array([[6, 3], [0, 2]])
print(repr(arr[0]))  # First row
```

**Output:**

```
1
5
array([6, 3])
```

✅ **Tip:**

- `arr[i]` → accesses the _i-th element_ (or row in 2D arrays).
- `arr[i][j]` → accesses the _j-th element inside the i-th row_.

---

## **B. Slicing (`start:stop`)**

You can slice NumPy arrays using the colon operator `:`.
This works the same as Python lists, and you can even use negative indexes to go backwards.

### **1D Array Example**

```python
arr = np.array([1, 2, 3, 4, 5])
print(repr(arr[:]))      # All elements
print(repr(arr[1:]))     # From 2nd element onward
print(repr(arr[2:4]))    # 3rd to 4th element
print(repr(arr[:-1]))    # Exclude last
print(repr(arr[-2:]))    # Last two elements
```

**Output:**

```
array([1, 2, 3, 4, 5])
array([2, 3, 4, 5])
array([3, 4])
array([1, 2, 3, 4])
array([4, 5])
```

---

### **2D Array Example**

You can use commas to separate row and column slices:
`data[row_slice, col_slice]`

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6],
                [7, 8, 9]])

print(repr(arr[:]))          # All rows, all cols
print(repr(arr[1:]))         # From 2nd row onward
print(repr(arr[:, -1]))      # Last column
print(repr(arr[:, 1:]))      # From 2nd column onward
print(repr(arr[0:1, 1:]))    # First row, 2nd to 3rd column
print(repr(arr[0, 1:]))      # Same as above but flattened
```

**Output:**

```
array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])
array([[4, 5, 6],
       [7, 8, 9]])
array([3, 6, 9])
array([[2, 3],
       [5, 6],
       [8, 9]])
array([[2, 3]])
array([2, 3])
```

✅ **Rule of thumb:**

- First slice → rows
- Second slice → columns
- `:` → select _all elements_ along that axis

---

## **C. Argmin and Argmax**

Use these to find the **indexes** of the smallest or largest values in an array.

- `np.argmin(array)` → index of the smallest value
- `np.argmax(array)` → index of the largest value

```python
arr = np.array([[-2, -1, -3],
                [4, 5, -6],
                [-3, 9, 1]])

print(np.argmin(arr[0]))  # smallest in first row
print(np.argmax(arr[2]))  # largest in third row
print(np.argmin(arr))     # smallest in entire array
```

**Output:**

```
2
1
5
```

---

### **Using the `axis` keyword**

- `axis=0` → looks **down the columns** (finds row index for each column)
- `axis=1` → looks **across rows** (finds column index for each row)
- `axis=-1` → same as `axis=1` for 2D arrays (last dimension)

```python
arr = np.array([[-2, -1, -3],
                [4, 5, -6],
                [-3, 9, 1]])

print(repr(np.argmin(arr, axis=0)))  # column-wise
print(repr(np.argmin(arr, axis=1)))  # row-wise
print(repr(np.argmax(arr, axis=-1))) # same as axis=1
```

**Output:**

```
array([2, 0, 1])
array([2, 2, 0])
array([1, 1, 1])
```

✅ **Summary:**

- `np.argmin(arr)` → single index of global minimum
- `np.argmin(arr, axis=0)` → minimum per column
- `np.argmin(arr, axis=1)` → minimum per row

---

# **Time to Code!**

### **1. Access a specific element directly**

**Question:**
Create a function `direct_index(data)` that returns the **third element of the second row** in the 2D NumPy array `data`.

**Answer:**

```python
def direct_index(data):
    elem = data[1][2]
    return elem
```

**Explanation:**
`data[1]` accesses the second row;
`data[1][2]` accesses the third element in that row.

---

### **2. Slice arrays using NumPy syntax**

**Question:**
Create a function `slice_data(data)` that returns two slices:

- `slice1`: all rows, skipping the **first element** in each row
- `slice2`: the **first four rows**, excluding the **last two columns**

Return both as `(slice1, slice2)`.

**Answer:**

```python
def slice_data(data):
    slice1 = data[:, 1:]
    slice2 = data[:4, :-2]
    return slice1, slice2
```

**Explanation:**

- `data[:, 1:]` → all rows, from column 1 to end.
- `data[:4, :-2]` → first four rows, all but last two columns.

---

### **3. Find indexes of minimum values**

**Question:**
Create a function `argmin_data(data)` that returns:

- `argmin_all`: index of the **overall minimum** element.
- `argmin1`: indexes of **each row’s minimum** element.

Return both as `(argmin_all, argmin1)`.

**Answer:**

```python
def argmin_data(data):
    argmin_all = np.argmin(data)
    argmin1 = np.argmin(data, axis=1)
    return argmin_all, argmin1
```

**Explanation:**

- `np.argmin(data)` → position of smallest element in the flattened array.
- `axis=1` → finds the column index of the smallest element in each row.

---

### **4. Find indexes of maximum values**

**Question:**
Create a function `argmax_data(data)` that returns the index of the **maximum element in each row** using `axis=-1`.

**Answer:**

```python
def argmax_data(data):
    argmax_neg1 = np.argmax(data, axis=-1)
    return argmax_neg1
```

**Explanation:**
`axis=-1` means the function scans along the last dimension (rows in this case).
