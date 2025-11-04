# NumPy Random Numbers & Distributions – Lecture Summary

### **A. Random Integers**

- Use `np.random.randint` to generate pseudo-random integers.
- Syntax:

```python
np.random.randint(low, high=None, size=None)
```

- If `high=None`, `low` is the upper exclusive bound (lower bound = 0).
- If `high` is specified, integers are drawn from `[low, high)`.
- `size` specifies the output shape.

```python
np.random.randint(5)                # Single integer in [0, 5)
np.random.randint(-3, high=14, size=(2,2))  # 2x2 array
```

---

### **B. Utility Functions**

- **`np.random.seed(seed)`** – Sets a seed for reproducibility.
- **`np.random.shuffle(array)`** – Shuffles array in-place (only first dimension for multi-D arrays).

```python
np.random.seed(1)
np.random.randint(10)            # Reproducible
np.random.shuffle(np.array([1,2,3,4]))
```

---

### **C. Random Distributions**

#### **1. Uniform Distribution**

- Numbers drawn **equally likely** from a range `[low, high)`.
- Default range: `[0.0, 1.0)`.

```python
np.random.uniform(low=-2.5, high=1.5, size=5)
```

#### **2. Normal (Gaussian) Distribution**

- Numbers distributed **around a mean** (`loc`) with standard deviation (`scale`).

```python
np.random.normal(loc=2.0, scale=3.5, size=(10,5))
```

---

### **D. Custom Sampling**

- Use `np.random.choice` to sample from a custom array.
- `p` defines the probability for each element (must sum to 1).

```python
choices = ['a', 'b', 'c', 'd']
np.random.choice(choices, p=[0.5, 0.1, 0.2, 0.2])
```

---

# **Time to Code!**

### **1. Generate random integers**

**Question:**
Generate a single random integer from `[0, 5)` and assign it to `random1`.
Then generate a 3x5 array of integers from `[3, 10)` and assign it to `random_arr`.

**Answer:**

```python
random1 = np.random.randint(5)
random_arr = np.random.randint(3, high=10, size=(3,5))
```

**Explanation:**
`np.random.randint(5)` generates one integer in `[0, 5)`.
`np.random.randint(3, high=10, size=(3,5))` creates a 3x5 array of integers in `[3, 10)`.

---

### **2. Generate a uniform random array**

**Question:**
Create an array `random_uniform` of 5 numbers sampled uniformly from `[-2.5, 1.5]`.

**Answer:**

```python
random_uniform = np.random.uniform(low=-2.5, high=1.5, size=5)
```

**Explanation:**
`np.random.uniform` draws numbers where **every number in the range is equally likely**.

---

### **3. Generate a normal distribution array**

**Question:**
Create a 10x5 array `random_norm` sampled from a normal distribution with mean 2.0 and standard deviation 3.5.

**Answer:**

```python
random_norm = np.random.normal(loc=2.0, scale=3.5, size=(10,5))
```

**Explanation:**
`np.random.normal(loc, scale, size)` produces numbers **around the mean**, with most numbers close to `loc`.

---

### **4. Sample from a custom distribution**

**Question:**
Create a list `choices = ['a', 'b', 'c', 'd']` and randomly pick one value with probability `[0.5, 0.1, 0.2, 0.2]`.

**Answer:**

```python
choices = ['a', 'b', 'c', 'd']
choice = np.random.choice(choices, p=[0.5, 0.1, 0.2, 0.2])
```

**Explanation:**
`np.random.choice` selects elements from a list, optionally weighted with `p`. Probabilities must sum to 1.

---

### **5. Shuffle an array in-place**

**Question:**
Create an array `arr` containing integers 1 to 5, then shuffle it randomly in-place.

**Answer:**

```python
arr = np.array([1,2,3,4,5])
np.random.shuffle(arr)
```

**Explanation:**
`np.random.shuffle` reorders elements **in-place**. Multi-dimensional arrays shuffle only the first axis.
