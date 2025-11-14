# **Robust Scaling**

Understand what outliers are, how they distort your data, and how to fix the issue using **RobustScaler** from scikit-learn.

---

## **Chapter Goals**

* Learn **what outliers are**
* Understand **why normal scaling fails** with outliers
* Learn how to apply **Robust Scaling** using scikit-learn

---

# **A. What Are Data Outliers?**

An **outlier** is a data point that is *far outside* the normal range of your dataset.

Example:
If your watermelon weights are:

```
5, 4, 6, 7, 20
```

The **20** is an outlier  it's much bigger than the others.

Outliers matter because:

* They **pull the mean** upward
* They **stretch the min/max**
* They **ruin standardized and ranged scaling**

### ✔ Why standard scaling fails

Standard scaling uses:

* **Mean**
* **Standard deviation**

Both are easily pulled by extreme values.

### ✔ Why min-max scaling fails

Min-max uses:

* **Minimum value**
* **Maximum value**

If an outlier becomes the new max/min, scaling becomes distorted.

---

# **Using IQR to Ignore Outliers**

To avoid getting affected by outliers, we use the **median** and **IQR** instead of mean and min/max.

### **IQR Formula**

```
IQR = Q3 – Q1
```

Where:

* **Q1** = 25th percentile
* **Q3** = 75th percentile

The IQR captures the **middle 50% of the data**  the “normal” region.

### **Why median & IQR are better**

* They don’t move much when outliers appear
* They focus only on the central region of the data

### **Classic Outlier Detection Rule (Tukey's Rule)**

Anything:

* **Below Q1 − 1.5 × IQR** → outlier
* **Above Q3 + 1.5 × IQR** → outlier

This rule helps detect abnormal points, but robust scaling simply *reduces* their influence instead of removing them.

---

# **B. Robust Scaling with scikit-learn**

scikit-learn provides a transformer called **RobustScaler**, which scales each feature as:

```
(value − median) / IQR
```

Meaning:

* Centered around the **median**
* Scaled based on the **middle 50% of the data**
* Outliers no longer dominate the scaling

### **Example Code**

```python
# predefined data
print('{}\n'.format(repr(data)))

from sklearn.preprocessing import RobustScaler
robust_scaler = RobustScaler()
transformed = robust_scaler.fit_transform(data)
print('{}\n'.format(repr(transformed)))
```

### **Output**

```
array([[ 1.2,  2.3],
       [ 2.1,  4.2],
       [-1.9,  3.1],
       [-2.5,  2.5],
       [ 0.8,  3. ],
       [ 6.3,  2.1],
       [-1.5,  2.7],
       [ 1.4,  2.9],
       [ 1.8,  3.2]])

array([[ 0.        , -1.        ],
       [ 0.27272727,  2.16666667],
       [-0.93939394,  0.33333333],
       [-1.12121212, -0.66666667],
       [-0.12121212,  0.16666667],
       [ 1.54545455, -1.33333333],
       [-0.81818182, -0.33333333],
       [ 0.06060606,  0.        ],
       [ 0.18181818,  0.5       ]])
```

Notice how extreme values no longer dominate the scaling.

---

# **Time to Code!**

Your task:
Complete the function below to apply robust scaling to a NumPy array.

Steps:

1. Create a `RobustScaler` object
2. Apply `.fit_transform(data)`
3. Return the scaled array

### **Solution**

```python
def robust_scaling(data):
  robust_sclaler = RobustScaler()
  scaled_data = robust_sclaler.fit_transform(data)
  return scaled_data
```

### **Output**

```
array([[ 0.28360414,  0.25738077,  0.25482625,  0.2901354 ],
       [-0.52880355, -0.48448145, -0.68725869, -0.39845261],
       [-0.28360414, -0.25738077, -0.25482625, -0.2901354 ],
       [ 1.76957164,  1.97123391,  1.78378378,  1.86073501]])
```
