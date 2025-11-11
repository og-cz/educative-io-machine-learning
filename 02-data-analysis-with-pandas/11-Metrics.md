# Metrics

Use pandas to get summary statistics for your data.

## Chapter Goals:

* Understand the common metrics used to summarize numeric data
* Learn how to describe categorical data using frequency counts

---

## A. Numeric Metrics

When working with numeric data, we often want to calculate summary values - like the average (mean), minimum, maximum, or standard deviation.
These **metrics** help us understand the shape and spread of our data before doing deeper analysis.

Instead of calculating each metric separately, pandas provides a built-in method called [`describe()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.describe.html).
It gives you an instant overview of the numeric columns in your DataFrame.

Here’s what `describe()` shows by default:

| Metric    | Description                         |
| --------- | ----------------------------------- |
| **count** | Number of rows (non-missing values) |
| **mean**  | Average value                       |
| **std**   | Standard deviation (spread of data) |
| **min**   | Smallest value                      |
| **25%**   | 25th percentile (lower quartile)    |
| **50%**   | 50th percentile (median)            |
| **75%**   | 75th percentile (upper quartile)    |
| **max**   | Largest value                       |

Example:

```python
# df is predefined
print(df)

metrics1 = df.describe()
print(metrics1)

hr_rbi = df[['HR', 'RBI']]
metrics2 = hr_rbi.describe()
print(metrics2)
```

**Output:**

```
    playerID  yearID teamID  HR  RBI
0   cruzne02    2017    SEA  39  119
1  pedrodu01    2017    BOS   7   62
2   cruzne02    2016    SEA  43  105
3  pedrodu01    2015    BOS  12   42
4  troutmi01    2017    LAA  33   72
5  pedrodu01    2016    BOS  15   74
```

Using `describe()` on the whole DataFrame includes **all numeric columns** (`yearID`, `HR`, and `RBI` in this case).
If you only want to summarize specific columns, select them first like we did with `hr_rbi`.

---

### Custom Percentiles

By default, `describe()` shows the 25th, 50th, and 75th percentiles.
But you can change which percentiles appear by using the `percentiles` keyword argument.

```python
metrics1 = hr_rbi.describe(percentiles=[.5])
metrics2 = hr_rbi.describe(percentiles=[.1])
metrics3 = hr_rbi.describe(percentiles=[.2, .8])
```

**Explanation:**

* `.5` → 50% (median)
* `.1` → 10%
* `.2` and `.8` → 20% and 80%

`describe()` always includes the **50th percentile (median)**, and replaces the default 25% and 75% with whatever you specify.

---

## B. Categorical Features

For **categorical features** (non-numeric data like names, teams, or years), we don’t calculate mean or standard deviation.
Instead, we count how often each category appears - called **frequency counts**.

You can use [`value_counts()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.value_counts.html) for this.

Example:

```python
p_ids = df['playerID']
print(p_ids.value_counts())          # Regular counts
print(p_ids.value_counts(normalize=True))  # Proportions
print(p_ids.value_counts(ascending=True))  # Sort ascending
```

**Output:**

```
pedrodu01    3
cruzne02     2
troutmi01    1
```

* `normalize=True` → shows **proportion** instead of count
* `ascending=True` → sorts smallest to largest

If you just want to see the **unique categories** (without their frequencies), use [`unique()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.unique.html):

```python
print(df['playerID'].unique())
print(df['teamID'].unique())
```

Output:

```
array(['cruzne02', 'pedrodu01', 'troutmi01'], dtype=object)
array(['SEA', 'BOS', 'LAA'], dtype=object)
```

Even numeric columns can be treated as categorical - for example, `yearID` can represent different seasons.

```python
y_ids = df['yearID']
print(y_ids.unique())
print(y_ids.value_counts())
```

---

## 🧠 Time to Code!

You’ll now get metrics from an MLB player DataFrame named `player_df`.

---

### 1️⃣ Describe all numeric data

Set `summary_all` to `player_df.describe()`.

```python
# CODE HERE
summary_all = player_df.describe()
```

---

### 2️⃣ Describe a single column

We’ll focus on the `'HR'` (home runs) column.
Set `hr_df` to that column, and get its default summary and custom percentiles.

```python
# CODE HERE
hr_df = player_df['HR']
summary_hr = hr_df.describe()
low_high_10 = hr_df.describe(percentiles=[.1, .9])
```

---

### 3️⃣ Treat HR as a categorical feature

Finally, get the frequency counts for each unique home run value.

```python
# CODE HERE
hr_counts = hr_df.value_counts()
```

