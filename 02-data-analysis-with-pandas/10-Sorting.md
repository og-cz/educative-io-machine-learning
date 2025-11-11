# Sorting

Sorting is an essential skill in data analysis. It allows us to organize datasets for easier reading, comparison, and pattern detection.

---

## **Chapter Goals**

* Learn how to sort a DataFrame by its features
* Practice sorting MLB player statistics by different columns

---

## **A. Sorting by a Single Feature**

Large datasets are easier to understand when organized.
In pandas, we use the [`DataFrame.sort_values()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.sort_values.html) method to sort data by one or more columns.

**Syntax:**

```python
df.sort_values(by, ascending=True)
```

* **`by`** → the column name(s) to sort by (string or list)
* **`ascending`** → `True` for ascending (default), `False` for descending

---

### **Example: Sorting a DataFrame**

```python
# Example DataFrame
df = pd.DataFrame({
  'playerID': ['pedrodu01', 'pedrodu01', 'troutmi01', 'cruzne02', 'cruzne02', 'troutmi01'],
  'yearID': [2016, 2017, 2017, 2016, 2017, 2016],
  'teamID': ['BOS', 'BOS', 'LAA', 'SEA', 'SEA', 'LAA'],
  'HR': [15, 7, 33, 43, 39, 29]
})

print(df, '\n')

# Sort by 'yearID' ascending
sort1 = df.sort_values('yearID')
print(sort1, '\n')

# Sort by 'playerID' descending
sort2 = df.sort_values('playerID', ascending=False)
print(sort2)
```

**Explanation:**

* Sorting by `'yearID'` arranges rows from 2016 → 2017.
* Sorting by `'playerID'` (descending) reverses alphabetical order (Z → A).

---

## **B. Sorting by Multiple Features**

You can sort by **more than one column** by passing a list to the `by` argument.
Each additional column acts as a **tiebreaker** for the previous one.

---

### **Example: Multiple Columns**

```python
# Sort by 'yearID' first, then 'playerID'
sort1 = df.sort_values(['yearID', 'playerID'])
print(sort1, '\n')

# Sort by 'yearID' (ascending) and 'HR' (descending)
sort2 = df.sort_values(['yearID', 'HR'], ascending=[True, False])
print(sort2)
```

**Explanation:**

* The **first column** (`yearID`) determines the main order.
* The **second column** (`playerID` or `HR`) breaks ties.
* The `ascending` argument can take a list to specify sort order per column.

Example:

```python
ascending=[True, False]
```

→ sort `'yearID'` ascending, but `'HR'` descending.

---

✅ **Key Notes**

* You can sort alphabetically, numerically, or by date.
* Sorting doesn’t modify the original DataFrame unless you use `inplace=True`.
* For descending order, always use `ascending=False`.

---

## **🧩 Time to Code! Practice Section**

Let’s practice sorting using the MLB statistics DataFrame `yearly_stats_df`.

---

### **1. Sort by Year**

Sort by `'yearID'` in ascending order.

```python
# CODE HERE
by_year = yearly_stats_df.sort_values('yearID')

print(by_year)
```

**Output (excerpt):**

```
   yearID teamID     H    AB   HR   2B   3B        BA
1    2015    CLE  1395  4395  669  169  169  0.317406
3    2015    DET  1515  5515  689  289  289  0.274705
...
```

---

### **2. Sort by Home Runs (Descending)**

Sort `'HR'` in descending order to find players with the highest home runs.

```python
# CODE HERE
best_hr = yearly_stats_df.sort_values('HR', ascending=False)

print(best_hr)
```

**Output (excerpt):**

```
   yearID teamID     H    AB   HR   2B   3B        BA
2    2016    BOS  1598  4598  878  278  278  0.347542
0    2017    CLE  1449  3449  818  218  118  0.420122
...
```

---

### **3. Sort by Home Runs (Descending), Then Strikeouts (Ascending)**

Use multiple columns and different sort directions.

```python
# CODE HERE
best_hr_so = yearly_stats_df.sort_values(['HR', 'SO'], ascending=[False, True])

print(best_hr_so)
```

**Explanation:**

* `'HR'`: highest first
* `'SO'`: lowest first (to break ties between players with equal HR)

