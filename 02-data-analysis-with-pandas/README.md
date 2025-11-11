# Introduction

An overview of data analysis with pandas.

In this chapter, you'll use [pandas](https://en.wikipedia.org/wiki/Pandas_(software)) to analyze Major League Baseball (MLB) data. The data comes courtesy of [Sean Lahman](https://en.wikipedia.org/wiki/Sean_Lahman) and contains statistics for every player, manager, and team in MLB history. The full database can be found and downloaded [here](http://www.seanlahman.com/baseball-archive/statistics/).

## A. Data analysis

Before doing any task with a dataset, it is a good idea to perform preliminary [data analysis](https://en.wikipedia.org/wiki/Data_analysis) Data analysis allows us to understand the dataset, find potential outlier values, and figure out which features of the dataset are most important to our application.

## B. pandas

Since most machine learning frameworks (e.g. TensorFlow) are built on Python, it is beneficial to use a Python-based data analysis toolkit like pandas. pandas (all lowercase) is an excellent tool for processing and analyzing real world data, with utilities ranging from parsing multiple file formats to converting an entire data table into a NumPy matrix array.

In the following chapters we'll dive into the main data analysis functionalities of pandas. For a 
complete overview of the pandas toolkit, you can visit the [pandas website](https://pandas.pydata.org/pandas-docs/stable/).

## C. Matplotlib and pyplot

An essential part of data analysis is creating charts and plots to visualize the data. Similar to the saying, "a picture is worth a thousand words", data visualization can convey key data trends and correlations through a single figure.

The library we will use for data visualization in Python is [Matplotlib](https://en.wikipedia.org/wiki/Matplotlib). Specifically, we'll be using the [pyplot](https://matplotlib.org/api/pyplot_api.html) API of Matplotlib, which provides a variety of plotting tools from simple line plots to advanced visuals like heatmaps and 3-D plots. While we will only touch on the basic necessities for our data analysis (e.g. line plots, boxplots, etc.), a full overview of Matplotlib can be found at its [website](https://matplotlib.org/index.html).

### **1. Series**

[Series](./01-Introduction.md)

- **What it is:** A one-dimensional labeled array, like a column in a spreadsheet.
- **What you do:** Create, access, modify, and label individual data columns.

---

### **2. DataFrame**

[DataFrame](./02-Series.md)

- **What it is:** A two-dimensional table with labeled rows and columns (like an Excel sheet).
- **What you do:** Create tables, rename columns, access data by labels, and manipulate entire datasets.

---

### **3. Combining**

[Combining](./03-DataFrame.md)

- **What it is:** Joining or merging multiple DataFrames together.
- **What you do:** Use `concat`, `merge`, or `join` to stack or align data from different sources.

---

### **4. Indexing**

[Indexing](./04-Combining.md)

- **What it is:** Selecting and labeling specific rows or columns.
- **What you do:** Use `.loc` and `.iloc` to access data by labels or position.

---

### **5. File I/O**

[File I/O](./05-Indexing.md)

- **What it is:** Reading and writing data files.
- **What you do:** Load data with `read_csv`, export with `to_csv`, and work with different file types.

---

### **6. Groupings**

[Groupings](./06-File_IO.md)

- **What it is:** Grouping data for summarization or analysis.
- **What you do:** Use `groupby` to calculate sums, means, counts, or other stats for each category.

---

### **7. Features**

[Features](./07-Groupings.md)
- **What it is:** Working with columns as features (variables) in your data.
- **What you do:** Add, remove, rename, or transform columns for analysis.

---

### **8. Filtering**

[Filtering](./08-Features.md)

- **What it is:** Selecting rows that match certain conditions.
- **What you do:** Use logical comparisons to keep, drop, or modify data that meets rules (e.g. `df[df['age'] > 30]`).

---

### **9. Sorting**

[Sorting](./09-Filtering.md)
- **What it is:** Arranging data by values or labels.
- **What you do:** Sort by one or multiple columns with `sort_values` or `sort_index`.

---

### **10. Metrics**

[Metrics](./10-Sorting.md)

- **What it is:** Getting quick statistics or summaries from data.
- **What you do:** Use `describe()`, `mean()`, `min()`, `max()`, and more to understand your dataset.

---

### **11. Plotting**

[Plotting](./11-Metrics.md)

- **What it is:** Visualizing your data with charts.
- **What you do:** Use `df.plot()` with Matplotlib to make line, bar, or box plots and add labels or titles.

---

### **12. To NumPy**

[To NumPy](./12-Plotting.md)
- **What it is:** Converting Pandas data to NumPy arrays.
- **What you do:** Use `.to_numpy()` to move data between Pandas and NumPy for numerical analysis.