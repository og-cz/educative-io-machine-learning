# Plotting

In this chapter, you’ll learn how to **visualize data in pandas** using the **pyplot** API from **Matplotlib**.
Plotting helps you see trends, patterns, and relationships in your data - turning numbers into insights.

---

## 🎯 Chapter Goals

* Learn how to create different plots from DataFrames using the **`plot()`** function.
* Learn how to display and customize these plots using **Matplotlib’s pyplot API**.

---

## 🅐 Basics of Plotting

The main function for creating plots from DataFrames is [`plot()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.plot.html).
It works together with **`matplotlib.pyplot.show()`** to display the result.

Before anything else, we import pyplot:

```python
import matplotlib.pyplot as plt
```

---

### 🧩 Example: Creating a Simple Line Plot

```python
# predefined df
print('{}\n'.format(df))

df.plot(kind='line', x='yearID', y='HR')
plt.show()
```

**Output (DataFrame):**

```
   yearID  HR
0    2000  49
1    2001  73
2    2002  46
3    2003  45
4    2004  45
5    2005   5
6    2006  26
7    2007  28
```

🧠 **Explanation:**

* `df.plot()` creates the line plot.
* `plt.show()` displays it in a new window or output cell.

You can also save the figure using `plt.savefig()`:

```python
df.plot(kind='line', x='yearID', y='HR')
plt.show()
plt.savefig('output/hr_plot.png')  # Save to PNG
```

---

### 🖊 Adding Titles and Labels

By default, plots have no titles or axis labels.
You can set them using pyplot functions:

```python
df.plot(kind='line', x='yearID', y='HR')
plt.title('Home Runs per Year')
plt.xlabel('Year')
plt.ylabel('HR Count')
plt.show()
```

🧠 **Explanation:**

* `plt.title()` adds a chart title.
* `plt.xlabel()` and `plt.ylabel()` label the axes.

---

## 🅑 Other Plot Types

`DataFrame.plot()` can create various plots by setting the `kind` parameter.
Here are some examples:

---

### 📊 Bar Plot

```python
df.plot(kind='bar', y='HR')
plt.ylabel('Frequency')
plt.show()
```

🧠 **Explanation:**
Shows the *HR* values as vertical bars.
Useful for comparing categories or years.

---

### 📦 Box Plot

```python
df.plot(kind='box', y='HR')
plt.show()
```

🧠 **Explanation:**
Displays the data’s spread (median, quartiles, and outliers).
The circles on the plot represent **outlier values**.

📘 *For all available plot kinds*, check the
[pandas plot documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.plot.html#pandas.DataFrame.plot).

---

## 🅒 Plotting Multiple Features

You can visualize multiple columns (features) on the same figure to compare trends.

```python
# gca = get current axis
ax = plt.gca()

df.plot(kind='line', x='yearID', y='H', ax=ax)
df.plot(kind='line', x='yearID', y='BB', color='red', ax=ax)
plt.show()
```

🧠 **Explanation:**

* `plt.gca()` allows both plots to share the same axes.
* Both `H` (Hits) and `BB` (Walks) are plotted together for easy comparison.
* The `color` argument changes the line color.

---

### 🧩 Boxplot for Multiple Columns

```python
df.plot(kind='box')
plt.show()
```

🧠 **Explanation:**
Shows how each column (e.g., *H*, *BB*) varies.
This helps identify outliers and compare distributions.

---

## 🧠 Summary

| Concept    | Function                       |
| ---------- | ------------------------------ |
| Line plot  | `df.plot(kind='line')`         |
| Bar plot   | `df.plot(kind='bar')`          |
| Box plot   | `df.plot(kind='box')`          |
| Show plot  | `plt.show()`                   |
| Save plot  | `plt.savefig()`                |
| Set title  | `plt.title()`                  |
| Label axes | `plt.xlabel()`, `plt.ylabel()` |

