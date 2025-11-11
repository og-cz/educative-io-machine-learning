# Introduction
An overview of data processing and the NumPy library.

In this chapter, you'll learn how to perform data processing and manipulation using NumPy.

# **A. Data processing**

When asked about Google's model for success, Peter Norvig, the director of research at Google, famously stated,

> "We don't have better algorithms than anyone else; we just have more data."
> 

Though probably an understatement (given the amount of talent employed at Google), the quote does provide a sense of just how vital data is to having successful outcomes.

People normally discuss the importance of data in the context of machine learning. No matter how sophisticated a machine learning model is, it will not perform well unless it has a reasonable amount of data to train on. On the other hand, given a large and diverse set of training data, a good deep learning model will significantly outperform non-deep-learning algorithms.

However, data is not just limited to machine learning. Companies use data to identify customer trends, political parties use data to determine which demographics they should target, sports teams use data to analyze players, etc.

[](https://www.educative.io/api/collection/6083138522447872/5629499534213120/page/5689792285114368/image/5643440998055936)

> Example baseball data used in sabermetrics. The concept was popularized by the 2011 film, Moneyball.
> 

The universal usage of data makes *data processing*, the act of converting raw data into a meaningful form, an essential skill to have.

# **B. NumPy**

Many scenarios involve mostly numeric datasets. For example, medical data contains many numeric metrics, such as height, weight, and blood pressure. Furthermore, the majority of neural networks use input data that is either numeric or has been converted to a numeric form.

When we deal with numeric data, the best Python library to use is [NumPy](http://www.numpy.org/). The NumPy library allows us to perform many operations on numeric data and convert the data to more usable forms.

```sql
import numpy as np  # import the NumPy library

# Initializing a NumPy array
arr = np.array([-1, 2, 5], dtype=np.float32)

# Print the representation of the array
print(repr(arr))

# OUTPUT:
# array([-1.,  2.,  5.], dtype=float32)
```

- we just converted the existing array of a datatype of float32
    - we used float 32 to save memory than float64 but it dependso the data and if you ahve no argument it np will choose the proper data type for you


### **1. NumPy Arrays**

[NumPy Arrays](/01-data-manipulation-with-numpy/01-NumPy-Arrays.md)

- What it is: Arrays are like lists but faster and smarter.
- What you do: Make arrays, see their shape (rows & columns), change their shape, flatten them, or rotate them.

---

### **2. NumPy Basics**

[NumPy Basics](/01-data-manipulation-with-numpy/02-NumPy-Basics.md)

- What it is: The simple stuff to get started with arrays.
- What you do: Access elements, pick parts of arrays (slices), do simple math on arrays, and play with 1D or 2D arrays.

---

### **3. Math**

[Math](/01-data-manipulation-with-numpy/03-Math.md)

- What it is: Doing math with arrays.
- What you do: Add, subtract, multiply, divide arrays. Use `sin`, `cos`, `exp`, etc. No loops needed—NumPy does it fast.

---

### **4. Random**

[**Random**](/01-data-manipulation-with-numpy/04-Random.md)

- What it is: Making random numbers.
- What you do: Create random numbers in a range, random choices, random normal or uniform numbers, or random points for testing.

---

### **5. Indexing**

[Indexing](/01-data-manipulation-with-numpy/05-Indexing.md)

- What it is: Picking certain elements from arrays.
- What you do: Get a single number, a row, a column, a block of numbers. Find positions of min and max numbers.

---

### **6. Filtering**

[Filtering](/01-data-manipulation-with-numpy/06-filtering.md)

- What it is: Picking elements based on a rule.
- What you do: Get only numbers bigger than 0, replace negative numbers, or flip values using true/false conditions.

---

### **7. Statistics**

[Statistics](/01-data-manipulation-with-numpy/07-statistics.md)

- What it is: Finding numbers that describe your array.
- What you do: Find the smallest, biggest, average, middle number, or variance of your array (how spread out numbers are).

---

### **8. Aggregation**

[Aggregation](/01-data-manipulation-with-numpy/08-aggregation.md)

- What it is: Combining or summarizing arrays.
- What you do: Add all numbers, get sums of rows or columns, cumulative sums (like running total), or join arrays together.

---

### **9. Saving and Loading Data**

[Saving Data](/01-data-manipulation-with-numpy/09-saving-loading-data.md)

- What it is: Keep your arrays for later.
- What you do: Save arrays to a file and load them again so you don’t have to recreate them every time.
