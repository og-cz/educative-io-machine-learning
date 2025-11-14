# **Principal Component Analysis (PCA)**

Learn what PCA is and why it’s a powerful preprocessing tool.

---

## **Chapter Goals**

* Understand **why PCA is used**
* Learn how PCA performs **dimensionality reduction**
* Learn how to apply PCA using scikit-learn
* See practical examples and code

---

# **A. Dimensionality Reduction (Why PCA Exists)**

Real datasets often have **many correlated features**.

Example (basketball stats):

* **Total points**
* **Points per game**

These two columns almost tell the **same story**, meaning they are **redundant**.

When a dataset contains correlated numeric features, we can use:

### **Principal Component Analysis (PCA)**

→ A method to reduce the number of columns **while keeping most of the information**.

PCA extracts **principal components**, which are:

* Uncorrelated
* Latent variables (hidden patterns)
* Sorted by importance (PC1 explains the most variance, then PC2, etc.)

Using fewer components makes machine learning models:

* Faster
* Simpler
* Less prone to overfitting

---

# **SHORT SUMMARY: WHY PCA IS BETTER THAN RANGE/SCALING**

| What You Do | What You Get                                                     |
| ----------- | ---------------------------------------------------------------- |
| **Range**   | Only min/max info, no relationships                              |
| **Scaling** | Makes values comparable but keeps redundancy                     |
| **PCA**     | Removes correlation + keeps important patterns + reduces columns |

PCA does **compression with intelligence**.

---

# **B. PCA in scikit-learn**

PCA in sklearn uses the `PCA` transformer.

### **`n_components` = how many new PCA features you want**

Example:

* If your original data has **5 columns**, PCA can produce up to **5 components**
  (but usually only **m − 1** meaningful)

### Each PCA component captures:

* **PC1** → biggest pattern
* **PC2** → second biggest
* **PC3** → third biggest
* etc.

---

## **Code Example**

```python
# predefined data
print('{}\n'.format(repr(data)))

from sklearn.decomposition import PCA
pca_obj = PCA() # default: m - 1 components
pc = pca_obj.fit_transform(data).round(3)
print('{}\n'.format(repr(pc)))

pca_obj = PCA(n_components=3)
pc = pca_obj.fit_transform(data).round(3)
print('{}\n'.format(repr(pc)))

pca_obj = PCA(n_components=2)
pc = pca_obj.fit_transform(data).round(3)
print('{}\n'.format(repr(pc)))
```

### **Output**

```
array([[ 1.5,  3. ,  9. , -0.5,  1. ],
       [ 2.2,  4.3,  3.5,  0.6,  2.7],
       [ 3. ,  6.1,  1.1,  1.2,  4.2],
       [ 8. , 16. ,  7.7, -1. ,  7.1]])
```

### PCA with default (4 components)

```
array([[-4.8600e+00,  4.6300e+00, -4.7000e-02,  0.0000e+00],
       [-3.7990e+00, -1.3180e+00,  1.2700e-01,  0.0000e+00],
       [-1.8630e+00, -4.2260e+00, -8.9000e-02,  0.0000e+00],
       [ 1.0522e+01,  9.1400e-01,  9.0000e-03,  0.0000e+00]])
```

Last column is **all zeros** → meaning only **3 real patterns** exist in the data.

### PCA with 3 components

```
array([[-4.8600e+00,  4.6300e+00, -4.7000e-02],
       [-3.7990e+00, -1.3180e+00,  1.2700e-01],
       [-1.8630e+00, -4.2260e+00, -8.9000e-02],
       [ 1.0522e+01,  9.1400e-01,  9.0000e-03]])
```

### PCA with 2 components

```
array([[-4.86 ,  4.63 ],
       [-3.799, -1.318],
       [-1.863, -4.226],
       [10.522,  0.914]])
```

---

# **C. Why PCA Works: Intuition**

Imagine 3 columns:

* `height_cm`
* `height_inches`
* `height_feet`

These contain the **exact same information**, just in different units.

PCA detects that:

* They are 100% correlated
* They do not add new information

Therefore PCA compresses these 3 columns into **one**:

```
[cm, inches, feet]  →  [PC1 (height)]
```

✔ You reduce **3 → 1**
✔ No information lost (just redundancy removed)

That single PCA component becomes the “true height dimension”.

---

# **Time to Code!**

Complete the function using PCA:

### **Goal**

* Create a PCA object with `n_components`
* Apply `fit_transform`
* Return the transformed data

### **Solution**

```python
def pca_data(data, n_components):
  from sklearn.decomposition import PCA
  
  pca_obj = PCA(n_components)
  component_data = pca_obj.fit_transform(data)
  return component_data
```

### **Expected Output**

```
array([[-119.81884272,   -5.56005586,   -3.17269264,    5.29159311],
     [-168.89015548,   10.11620863,  -30.78188677,    1.2967759 ],
     [-169.31170747,   14.0805323 ,  -16.75362821,  -10.27839889],
     ...,
     [-138.38716306,    0.9380922 ,  -37.28518133,    8.07369031],
     [-137.50517338,    4.2518251 ,  -35.98834188,    7.01643434],
     [-139.19033295,    1.00906423,  -29.77243231,    1.67685973]])
```

