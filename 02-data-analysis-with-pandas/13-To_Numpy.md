# To Numpy

In this chapter, you’ll learn how to **convert pandas DataFrames** into **NumPy arrays** - a key step when preparing data for machine learning models.

---

## 🎯 Chapter Goals

* Learn how to convert a DataFrame to a NumPy matrix
* Practice modifying a real MLB dataset and converting it to NumPy data

---

## 🅐 Why Machine Learning Uses NumPy

A **DataFrame** is excellent for organizing and analyzing data in Python.
However, most **machine learning frameworks** (like TensorFlow or scikit-learn) expect input data as **NumPy arrays**, not DataFrames.

That means we need to convert the DataFrame into **purely numerical data**.
Even **categorical features** (like team names or countries) must be turned into **numbers**, because models can’t interpret text directly.

🧠 **Key idea:**
Machine learning = numeric input only → we must convert all categorical data into numeric form before conversion.

---

## 🅑 Indicator (Dummy) Features

When converting a DataFrame, categorical columns must be replaced by *indicator features*.
An indicator (or *dummy variable*) represents each possible category with a `1` (present) or `0` (absent).

---

### 🧩 Example

```python
# predefined non-indicator DataFrame
print('{}\n'.format(df))

# predefined indicator DataFrame
print('{}\n'.format(indicator_df))
```

**Output:**

```
    color
r1    red
r2   blue
r3  green
r4    red
r5    red
r6   blue

    blue  red  green
r1     0    1      0
r2     1    0      0
r3     0    0      1
r4     0    1      0
r5     0    1      0
r6     1    0      0
```

🧠 **Explanation:**

* Each category (`red`, `blue`, `green`) becomes a new column.
* Each row has a `1` in the column matching its category.
* This creates numeric, machine-readable data while preserving category meaning.

---

## 🅒 Converting to Indicators with `get_dummies()`

pandas provides a built-in helper for this task:
[`pd.get_dummies()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.get_dummies.html)

It automatically converts all categorical features in a DataFrame into indicator columns.

---

### 🧩 Example

```python
# predefined df
print('{}\n'.format(df))

converted = pd.get_dummies(df)
print('{}\n'.format(converted.columns))

print('{}\n'.format(converted[['teamID_BOS', 'teamID_PIT']]))
print('{}\n'.format(converted[['lgID_AL', 'lgID_NL']]))
```

**Output:**

```
          lgID teamID
playerID             
bettsmo01   AL    BOS
martest01   NL    PIT
pedrodu01   AL    BOS
polangr01   NL    PIT
```

```
Index(['lgID_AL', 'lgID_NL', 'teamID_BOS', 'teamID_PIT'], dtype='object')

           teamID_BOS  teamID_PIT
playerID                         
bettsmo01           1           0
martest01           0           1
pedrodu01           1           0
polangr01           0           1
```

🧠 **Explanation:**

* Each category becomes a column.
* Column names show their origin (e.g. `teamID_BOS` came from `teamID`).
* This preserves readability while ensuring all data is numeric.

---

## 🅓 Converting to a NumPy Array

Once your DataFrame contains only numeric data (after applying `get_dummies()`), you can easily convert it to a NumPy array.

Use the [`values`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.values.html) attribute:

---

### 🧩 Example

```python
# predefined indicator df
print('{}\n'.format(df))

n_matrix = df.values
print(repr(n_matrix))
```

**Output:**

```
           HR  teamID_BOS  teamID_PIT
playerID                             
bettsmo01  24           1           0
martest01   7           0           1
pedrodu01   7           1           0
polangr01  11           0           1
```

```
array([[24,  1,  0],
       [ 7,  0,  1],
       [ 7,  1,  0],
       [11,  0,  1]])
```

🧠 **Explanation:**
Each **row** and **column** in the array corresponds to the same position in the original DataFrame.
This matrix can now be passed directly into a machine learning model.

---

## 🧩 Time to Code! (Practice Task)

Let’s apply what you’ve learned to convert a DataFrame into a NumPy array.

---

### 1️⃣ Filter for the Current Century

Keep only rows where `yearID ≥ 2000`.

```python
df = df[df['yearID'] > 2000]
```

**Output:**

```
    playerID  yearID teamID    HR  RBI
0   cruzne02    2017    SEA   NaN  119
2   cruzne02    2016    SEA  43.0  105
3  pedrodu01    2015    BOS  12.0   42
4  troutmi01    2017    LAA  33.0   72
```

---

### 2️⃣ Remove Missing Values

Drop rows that contain any `NaN` values using `dropna()`:

```python
df = df.dropna()
```

**Output:**

```
     HR  RBI   playerID teamID  yearID
1   7.0   62  pedrodu01    BOS    1917
2  43.0  105   cruzne02    SEA    2016
3  12.0   42  pedrodu01    BOS    2015
4  33.0   72  troutmi01    LAA    2017
5  15.0   74  pedrodu01    BOS    1916
```

---

### 3️⃣ Convert Categorical Columns to Indicators

Use `pd.get_dummies()` to replace all categorical features:

```python
df = pd.get_dummies(df)
```

---

### 4️⃣ Convert to NumPy Matrix

```python
matrix = df.values
```

**Output:**

```
   HR  RBI  yearID  playerID_cruzne02  playerID_pedrodu01  playerID_troutmi01  teamID_BOS  teamID_LAA  teamID_SEA
0  22  119    2017                  1                   0                   0           0           0           1
1   7   62    1917                  0                   1                   0           1           0           0
2  43  105    2016                  1                   0                   0           0           0           1
3  12   42    2015                  0                   1                   0           1           0           0
4  33   72    2017                  0                   0                   1           0           1           0
5  15   74    1916                  0                   1                   0           1           0           0
```

```
array([[  22,  119, 2017,    1,    0,    0,    0,    0,    1],
       [   7,   62, 1917,    0,    1,    0,    1,    0,    0],
       [  43,  105, 2016,    1,    0,    0,    0,    0,    1],
       [  12,   42, 2015,    0,    1,    0,    1,    0,    0],
       [  33,   72, 2017,    0,    0,    1,    0,    1,    0],
       [  15,   74, 1916,    0,    1,    0,    1,    0,    0]])
```

---

## 🧠 Summary

| Step | Function                  | Description                                       |
| ---- | ------------------------- | ------------------------------------------------- |
| 1    | `df[df['yearID'] > 2000]` | Filter DataFrame by condition                     |
| 2    | `df.dropna()`             | Remove rows with missing data                     |
| 3    | `pd.get_dummies(df)`      | Convert categorical features to indicator columns |
| 4    | `df.values`               | Convert to a NumPy matrix                         |

