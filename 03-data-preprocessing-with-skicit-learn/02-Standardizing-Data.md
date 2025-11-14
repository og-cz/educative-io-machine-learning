# **Standardizing Data**

In this section, you’ll learn what **data standardization** is and how to apply it using **NumPy** and **scikit-learn**.

---

## **A. Standard Data Format**

Real-world data can vary widely:

* 100m sprint times: **9.5 – 10.5 seconds**
* Pizza calories: **1500 – 3000 calories**
* Weight: **kg vs. lbs** (same concept, different scales)

Because features can exist on **different scales**, it becomes difficult to compare or interpret them directly.

### **Why Standardize?**

Data scientists often convert data to a **standardized format**:

* Mean = **0**
* Standard deviation = **1**

This transformation is called **data standardization**.

### **Standardization Formula**

For a given value ( x ):

[
z = \frac{x - \mu}{\sigma}
]

Where:

* ( \mu ) = mean of the feature
* ( \sigma ) = standard deviation
* ( z ) = standardized value

A standardized value tells you **how many standard deviations** the original value is from the mean.

---

## **B. NumPy and scikit-learn**

Most scikit-learn functions use **NumPy arrays** as input.

* **Rows** → individual data observations
* **Columns** → features (just like spreadsheet columns)

The preprocessing module is:

```python
from sklearn.preprocessing import scale
```

The function `scale()` performs standardization across a chosen axis.

---

### **Example: Standardizing Pizza Data**

```python
# predefined pizza data
print('{}\n'.format(repr(pizza_data)))

from sklearn.preprocessing import scale

# Standardizing each column (default axis=0)
col_standardized = scale(pizza_data)
print('{}\n'.format(repr(col_standardized)))

# Column means
col_means = col_standardized.mean(axis=0).round(decimals=3)
print('{}\n'.format(repr(col_means)))

# Column standard deviations
col_stds = col_standardized.std(axis=0)
print('{}\n'.format(repr(col_stds)))
```

### **Output**

```
array([[2100,   10,  800],
       [2500,   11,  850],
       [1800,   10,  760],
       [2000,   12,  800],
       [2300,   11,  810]])

array([[-0.16552118, -1.06904497, -0.1393466 ],
       [ 1.4896906 ,  0.26726124,  1.60248593],
       [-1.40693001, -1.06904497, -1.53281263],
       [-0.57932412,  1.60356745, -0.1393466 ],
       [ 0.66208471,  0.26726124,  0.2090199 ]])

array([ 0., -0.,  0.])
array([1., 1., 1.])
```

* The last two arrays being **very close to `[0, 0, 0]`** and **`[1, 1, 1]`** confirms the standardization was successful.
* If they were far from 0 or 1, the scaling would be incorrect.

---

### **Why Standardize by Column?**

Usually, we standardize **each feature independently**.

Example:
A pizza with weight value “1.6” in the standardized data means:

> The pizza’s weight is **1.6 standard deviations above the mean weight**.

---

### **Standardizing Across Rows**

Sometimes you want to standardize within each observation (across rows):

```python
scale(data, axis=1)
```

Example use case: analyzing a **single student's test scores** relative to *their* average.

---

# **Time to Code!**

Write a function that standardizes a NumPy array using `scale`.

### ✔️ **Expected Implementation**

```python
def standardize_data(data):
  scaled_data = scale(data)
  return scaled_data
```

### **Example Output**

```
array([[-0.02978671, -0.11884522, -0.02068678, -0.08362497],
       [-0.93993628, -0.89015859, -1.03020176, -0.84697085],
       [-0.66523659, -0.65404225, -0.56681784, -0.72689397],
       [ 1.63495958,  1.66304607,  1.61770638,  1.65748979]])
```
