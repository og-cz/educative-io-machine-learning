# **Range Scaling (Min-Max Scaling)**

In this section, you’ll learn how to **compress data to a fixed range** using scikit-learn’s `MinMaxScaler`.

---

## **A. Range Scaling**

Besides standardizing data (mean 0, std 1), another common transformation is **range scaling**  compressing values into a fixed interval such as **[0, 1]**.

### **Why Scale to a Range?**

Scaling to **[0, 1]** allows data to be interpreted as:

* proportions
* percentages
* relative values between 0% and 100%

This is useful when comparing features with completely different units or magnitudes.

---

## **Step 1: Compute Proportion Within Original Range**

For a value ( x ):

[
x_{\text{prop}} = \frac{x - d_{\min}}{d_{\max} - d_{\min}}
]

Where:

* ( d_{\min} ) = minimum value of the data
* ( d_{\max} ) = maximum value of the data
* ( x_{\text{prop}} ) = how far x is between the min and max (0 → min, 1 → max)

⚠️ This only works if ( d_{\max} \neq d_{\min} ).

---

## **Step 2: Scale to a Target Range**

To convert the proportional value into a target range ([r_{\min}, r_{\max}]):

[
x_{\text{scale}} = x_{\text{prop}} \cdot (r_{\max} - r_{\min}) + r_{\min}
]

This maps values smoothly into any chosen interval.

---

## **B. Range Compression with scikit-learn**

Scikit-learn provides **transformers**, objects that learn from data and then transform it.

### **MinMaxScaler**

This transformer:

* computes the min & max of each feature
* scales values into a chosen range
* default range: **[0, 1]**

You use it via:

```python
from sklearn.preprocessing import MinMaxScaler
```

---

### **Example: Using MinMaxScaler**

```python
# predefined data
print('{}\n'.format(repr(data)))

from sklearn.preprocessing import MinMaxScaler
default_scaler = MinMaxScaler()  # default [0,1]
transformed = default_scaler.fit_transform(data)
print('{}\n'.format(repr(transformed)))

custom_scaler = MinMaxScaler(feature_range=(-2, 3))
transformed = custom_scaler.fit_transform(data)
print('{}\n'.format(repr(transformed)))
```

### **Output**

```
array([[ 1.2,  3.2],
       [-0.3, -1.2],
       [ 6.5, 10.1],
       [ 2.2, -8.4]])

array([[0.22058824, 0.62702703],
       [0.        , 0.38918919],
       [1.        , 1.        ],
       [0.36764706, 0.        ]])

array([[-0.89705882,  1.13513514],
       [-2.        , -0.05405405],
       [ 3.        ,  3.        ],
       [-0.16176471, -2.        ]])
```

---

### ⚠️ Important Note

After min-max scaling:

> **The values no longer represent real-world units.**
> They’re *purely mathematical*, used so algorithms can compare features fairly.

You cannot interpret “0.8” as 0.8 kg or 0.8 calories  it’s just a normalized value.

---

# **Fit vs. Transform**

Transformers have two key steps:

### **1. `fit(data)`**

Learns:

* min
* max
* (or in other transformers: mean, std, etc.)

### **2. `transform(new_data)`**

Uses the **learned information** to scale new values.

### **3. `fit_transform(data)`**

Shortcut for calling both on the same dataset.

---

## **Example Comparing Fit/Transform vs Fit_Transform**

```python
# predefined new_data
print('{}\n'.format(repr(new_data)))

from sklearn.preprocessing import MinMaxScaler
default_scaler = MinMaxScaler()
transformed = default_scaler.fit_transform(new_data)
print('{}\n'.format(repr(transformed)))

default_scaler = MinMaxScaler()  # new scaler
default_scaler.fit(data)         # fitted on DIFFERENT data
transformed = default_scaler.transform(new_data)
print('{}\n'.format(repr(transformed)))
```

### **Output**

```
array([[ 1.2, -0.5],
       [ 5.3,  2.3],
       [-3.3,  4.1]])

array([[0.52325581, 0.        ],
       [1.        , 0.60869565],
       [0.        , 1.        ]])

array([[ 0.22058824,  0.42702703],
       [ 0.82352941,  0.57837838],
       [-0.44117647,  0.67567568]])
```

---

## **Interpretation**

### **Case 1: `fit_transform(new_data)`**

* Uses ONLY `new_data` for min/max.
* Always maps values into the chosen range.
* Used for **visualization**, **toy problems**, or **self-contained datasets**.

### **Case 2: `fit(data)` + `transform(new_data)`**

* Learns scale from one dataset (`data`)
* Applies scaling to another (`new_data`)
* Values may fall outside [0,1]

This is how **real ML pipelines** handle new incoming data.

---

# **Time to Code!**

Complete the `ranged_data` function using `MinMaxScaler`.

### ✔️ Expected Solution

```python
def ranged_data(data, value_range):
  min_max_scaler = MinMaxScaler(feature_range=value_range)
  scaled_data = min_max_scaler.fit_transform(data)
  return scaled_data
```

### **Example Output**

```
array([[13.53470437, 13.02096178, 13.8125    , 13.04794521],
       [10.        , 10.        , 10.        , 10.        ],
       [11.06683805, 10.92478422, 11.75      , 10.47945205],
       [20.        , 20.        , 20.        , 20.        ]])
```

