# **Data Normalization**

Learn what L2 normalization is, why it matters, and how to apply it using scikit-learn.

---

## **Chapter Goals**

* Understand **why we normalize rows instead of columns**
* Learn how to apply **L2 normalization** using scikit-learn’s `Normalizer`

---

# **A. What Is L2 Normalization?**

Up to now, all scaling methods changed the **features** (columns).
But sometimes, we need to scale **each data point** (each row).

This is especially important in:

* **Clustering**
* **Cosine similarity calculations**
* **Text vectorization (TF-IDF)**
* **Recommendation systems**

Why?
Because in those tasks, the **direction** of a vector matters more than its **magnitude**.

### ✔ What L2 Normalization Does

For each row:

```
Divide each value by the row’s L2 norm.
```

### ✔ What is the L2 norm?

For a row:

```
[a, b, c, d]
```

Its L2 norm =

```
sqrt(a² + b² + c² + d²)
```

So normalized value becomes:

```
value / sqrt(sum_of_squares)
```

This makes the entire row a **unit vector** (length = 1).

---

# **B. Why Use L2 Normalization?**

Because many algorithms measure **angles**, not raw size.

Example: cosine similarity (used in clustering) compares the **direction** of vectors:

* Same direction → **more similar**
* Different direction → **less similar**

To measure angles correctly, all vectors must have **equal length**, and L2 normalization ensures that.

---

# **C. L2 Normalization With scikit-learn**

scikit-learn provides a transformer called **Normalizer**, which normalizes each **row** using L2 norm by default.

### **Example Code**

```python
# predefined data
print('{}\n'.format(repr(data)))

from sklearn.preprocessing import Normalizer
normalizer = Normalizer()
transformed = normalizer.fit_transform(data)
print('{}\n'.format(repr(transformed)))
```

### **Output**

```
array([[4, 1, 2, 2],
       [3, 4, 0, 0],
       [7, 5, 9, 2]])

array([[0.8       , 0.2       , 0.4       , 0.4       ],
       [0.6       , 0.8       , 0.        , 0.        ],
       [0.55513611, 0.39652579, 0.71374643, 0.15861032]])
```

Each row is now scaled so its total vector length = **1**.

---

# **D. Understanding Cosine Similarity**

Cosine similarity measures how **similar the direction** of two vectors is.
It ignores the size and only looks at angle.

### Meaning of values:

| Value            | Interpretation                               |
| ---------------- | -------------------------------------------- |
| **Close to 1.0** | Highly similar direction                     |
| **Around 0.5**   | Moderately similar                           |
| **Close to 0.0** | Not similar                                  |
| **< 0**          | Opposite direction (rare with positive data) |

L2 normalization ensures vectors are properly scaled before applying cosine similarity.

---

# **Time to Code!**

Your task:
Complete the function that performs **L2 normalization** on a NumPy array.

Steps:

1. Create a `Normalizer` object
2. Apply `.fit_transform(data)`
3. Return the normalized array

### **Solution**

```python
def normalize_data(data):
  normalizer = Normalizer()
  norm_data = normalizer.fit_transform(data)
  return norm_data
```

### **Output**

```
array([[0.86792607, 0.39056673, 0.0433963 , 0.30377413],
       [0.85891432, 0.39128319, 0.03721962, 0.32829614],
       [0.87204702, 0.39638501, 0.04742464, 0.28313215],
       [0.84484854, 0.42789936, 0.0419055 , 0.31839756]])
```

The rows are now perfectly normalized.
