# **Data Imputation**

Learn what to do when your dataset has **missing values**, and how to fill (impute) them using scikit-learn.

---

## **Chapter Goals**

* Understand what *data imputation* is
* Learn the **four imputation strategies** provided by `SimpleImputer`
* See examples of mean, median, most-frequent, and constant-value imputation
* Learn about other (more advanced) imputation techniques

---

# **A. What Is Data Imputation?**

In real-world datasets, missing values are extremely common.

Examples:

* A survey participant skips a question
* A sensor fails to record a reading
* Data logs were corrupted or incomplete

When this happens, you have two choices:

1. **Drop** the data (only if too many values are missing)
2. **Impute** the missing values  replace them with reasonable estimates

Data imputation lets you fill missing values with something statistically meaningful.

### ✔ In NumPy arrays

Missing values are represented using:

```python
np.nan
```

### ✔ scikit-learn’s tool for imputation

scikit-learn provides `SimpleImputer`, which supports **four** imputation strategies.

---

# **B. SimpleImputer (4 Imputation Methods)**

`SimpleImputer` can fill missing values using:

1. **Mean** of the column (default)
2. **Median**
3. **Most frequent value**
4. **A constant value** you choose

---

## **1. Mean Imputation (default)**

```python
from sklearn.impute import SimpleImputer
imp_mean = SimpleImputer()
transformed = imp_mean.fit_transform(data)
```

### Input

```
array([[ 1.,  2., nan,  2.],
       [ 5., nan,  1.,  2.],
       [ 4., nan,  3., nan],
       [ 5.,  6.,  8.,  1.],
       [nan,  7., nan,  0.]])
```

### Output (nan replaced with column means)

```
array([[1.  , 2.  , 4.  , 2.  ],
       [5.  , 5.  , 1.  , 2.  ],
       [4.  , 5.  , 3.  , 1.25],
       [5.  , 6.  , 8.  , 1.  ],
       [3.75, 7.  , 4.  , 0.  ]])
```

---

## **2. Median Imputation**

```python
imp_median = SimpleImputer(strategy='median')
transformed = imp_median.fit_transform(data)
```

### Output

```
array([[1. , 2. , 3. , 2. ],
       [5. , 6. , 1. , 2. ],
       [4. , 6. , 3. , 1.5],
       [5. , 6. , 8. , 1. ],
       [4.5, 7. , 3. , 0. ]])
```

Median is **robust to outliers** (similar to RobustScaler).

---

## **3. Most Frequent Imputation**

```python
imp_frequent = SimpleImputer(strategy='most_frequent')
transformed = imp_frequent.fit_transform(data)
```

### Output

```
array([[1., 2., 1., 2.],
       [5., 2., 1., 2.],
       [4., 2., 3., 2.],
       [5., 6., 8., 1.],
       [5., 7., 1., 0.]])
```

Useful for **categorical data**.

---

## **4. Constant Value Imputation**

```python
imp_constant = SimpleImputer(strategy='constant', fill_value=-1)
transformed = imp_constant.fit_transform(data)
```

### Output

```
array([[ 1.,  2., -1.,  2.],
       [ 5., -1.,  1.,  2.],
       [ 4., -1.,  3., -1.],
       [ 5.,  6.,  8.,  1.],
       [-1.,  7., -1.,  0.]])
```

Common constant values:

* `0`
* `-1`
* `"Unknown"` (in string datasets)

---

# **C. Other Imputation Methods (Beyond SimpleImputer)**

`SimpleImputer` only supports the basic four methods.

More advanced techniques include:

### **kNN Imputation**

* Uses the **k-nearest neighbors** to “estimate” missing values
* Useful when similar rows have similar values

### **MICE (Multiple Imputation by Chained Equations)**

* Builds a model for each feature
* Iteratively predicts missing values
* Useful for large datasets with many missing values

These are helpful for:

* Open-source datasets
* Medical datasets
* Survey data
* Scenarios with **complex patterns of missingness**

Industry datasets often don’t need these because they’re usually well-cleaned.
