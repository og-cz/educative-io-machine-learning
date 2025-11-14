# **Introduction**

This section gives an overview of **industry data science** and the **scikit-learn API**.
You’ll learn what data preprocessing is, why it matters, and how scikit-learn provides powerful tools to prepare data for machine learning.

---

## **A. ML Engineering vs. Data Science**

In industry, **machine learning engineers (MLEs)** and **data scientists (DS)** often work with similar tools and tasks. However, their main goals differ.

---

### **ML Engineers**

ML engineers focus on:

* Analyzing raw data for meaningful trends
* Building **efficient input pipelines**
* Preparing data for **model training**
* Using libraries like:

  * **NumPy** → numerical computing
  * **pandas** → data manipulation
  * **TensorFlow / PyTorch** → deep learning models

Their work is typically on **large datasets** and **production pipelines**.

---

### **Data Scientists**

Data scientists usually:

* Work with **smaller datasets**
* Aim to extract **quick insights**
* Use **traditional machine learning models**
* Focus on statistics, inference, and experimentation

One of their core tools is **scikit-learn**, a library designed for:

* Data preprocessing
* Feature engineering
* Classical ML models (SVM, logistic regression, decision trees, etc.)
* Evaluation and quick experimentation

You import it in Python using:

```python
import sklearn
```

---

### **Why scikit-learn?**

Scikit-learn provides:

* Clean and consistent API
* Tools for scaling, encoding, splitting, imputing, and transforming data
* Quick model experimentation
* Easy integration with NumPy and pandas

It is one of the **core libraries in industry-level data science**.

