## ML engineering vs. data science

In industry, there is quite a bit of overlap between machine learning engineering and data science. Both jobs involve working with data, such as data analysis and data preprocessing.

The main task for machine learning engineers is to first analyze the data for viable trends, then create an efficient input pipeline for training a model. This process involves using libraries like [NumPy](http://www.numpy.org/) and [pandas](https://pandas.pydata.org/) for handling data, along with machine learning frameworks like TensorFlow for creating the model and input pipeline. For more information on ML engineering and the NumPy and pandas libraries, check out the previous two sections in this course.

While the NumPy and pandas libraries are also used in data science, this chapter covers one of the core libraries that is specific to industry-level data science: [scikit-learn](https://scikit-learn.org/stable/). Data scientists tend to work on smaller datasets than machine learning engineers, and their main goal is to analyze the data and quickly extract usable results. Therefore, they focus more on traditional data inference models (found in scikit-learn), rather than deep neural networks.

The scikit-learn library includes tools for data preprocessing and data mining. It is imported in Python via the statement `import sklearn`.

[Introduction](./01-Introduction.md)

### 1. Standardizing Data

[Standardizing Data](./02-Standardizing-Data.md)

- **What it is:** Converting features so they have mean = 0 and standard deviation = 1.
- **What you do:** Apply `StandardScaler` to remove scale differences between columns.

---

### 2. Data Range (Min–Max Scaling)

[Data Range](./03-Data-Range.md)

- **What it is:** Scaling values to a fixed range (usually 0–1).
- **What you do:** Use `MinMaxScaler` to transform all features into the same range.

---

### 3. Robust Scaling

[Robust Scaling](./04-Robust-Scaling.md)

- **What it is:** Scaling based on median and IQR to reduce the effect of outliers.
- **What you do:** Apply `RobustScaler` when your dataset contains extreme values.

---

### 4. Normalizing Data (L2)

[Normalizing Data](./05-Normalizing-Data.md)

- **What it is:** Scaling based on median and IQR to reduce the effect of outliers.
- **What you do:** Apply `RobustScaler` when your dataset contains extreme values.

---

### 5. Data Imputation

[Data Imputation](./06-Data-Imputation.md)

- **What it is:** Filling in missing values so models can use incomplete data.
- **What you do:** Use `SimpleImputer` to replace missing entries with mean, median, or constant values.

---

### 6. PCA (Principal Component Analysis)

[PCA](./07-PCA.md)

- **What it is:** A technique to reduce the number of features by finding the most important patterns.
- **What you do:** Use `PCA` to compress data into fewer uncorrelated components.

---

### 7. Labeled Data

[Labeled Data](./08-Labeled-Data.md)

- **What it is:** Data that includes categories (labels) for classification tasks.
- **What you do:** Separate PCA data by class, visualize labeled groups, and prepare for supervised learning.