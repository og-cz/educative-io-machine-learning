# Labeled Data

## **🔥 Chapter Goals**

* Understand what *class labels* are
* Learn how to *separate PCA-transformed data by class*

---

# **A. What Are Class Labels?**

In machine learning, **class labels = the category each data point belongs to.**

They are the **answers** your model tries to predict.

Examples:

* Email → **spam (1)** or **not spam (0)**
* Tumor → **malignant (0)** or **benign (1)**
* Handwritten digit → **0–9**

In scikit-learn datasets:

* `X` = data (features)
* `y` = labels (class IDs)

Example from the breast cancer dataset:

```python
from sklearn.datasets import load_breast_cancer
bc = load_breast_cancer()

print(bc.data.shape)   # (569, 30)
print(bc.target.shape) # (569,)
print(bc.target_names) # ['malignant', 'benign']
```

So:

* **569 samples**
* **30 features**
* **2 classes** ("malignant", "benign")

To separate each class:

```python
malignant = bc.data[bc.target == 0]
benign = bc.data[bc.target == 1]
```

---

# **B. Helper Function: `get_label_info`**

Goal: Return

1. the label name (e.g. `"benign"`) and
2. all PCA rows belonging to that class.

### **Logic**

* `label_name` → get the string name for the class index
* `label_data` → filter rows where `labels == class_label`

### ✔️ Final Code

```python
def get_label_info(component_data, labels, class_label, label_names):
    label_name = label_names[class_label]
    label_data = component_data[labels == class_label]
    return label_name, label_data
```

---

# **C. Main Function: `separate_data`**

Goal: Loop through all classes and gather their PCA data.

### Steps:

1. Create an empty list → `separated_data`
2. Loop through each class index
3. Call `get_label_info`
4. Append the result
5. Return the final list

### ✔️ Final Code

```python
def separate_data(component_data, labels, label_names):
    separated_data = []

    for class_label in range(len(label_names)):
        separated_data.append(
            get_label_info(component_data, labels, class_label, label_names)
        )

    return separated_data
```

---

# **D. How It Works With PCA**

We reduce the breast cancer dataset to 2 PCA components:

```python
from sklearn.decomposition import PCA

pca_obj = PCA(n_components=2)
component_data = pca_obj.fit_transform(bc.data)

labels = bc.target
label_names = bc.target_names

separated_data = separate_data(component_data, labels, label_names)
```

Now `separated_data` contains:

* all malignant PCA coordinates
* all benign PCA coordinates

Perfect for plotting.

---

# **E. Plotting the Two Classes**

```python
import matplotlib.pyplot as plt

for label_name, label_data in separated_data:
    col1 = label_data[:, 0]
    col2 = label_data[:, 1]
    plt.scatter(col1, col2, label=label_name)

plt.legend()
plt.title("Breast Cancer Dataset PCA Plot")
plt.show()
```

This creates a 2D scatterplot showing how PCA separates malignant vs benign samples.
