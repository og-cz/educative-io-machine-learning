# **Saving and Loading NumPy Data**

Learn how to save and reload NumPy arrays for later use.

---

## **Chapter Goals:**

- Learn how to save and load data in NumPy
- Write code to save NumPy data to a file

---

## **A. Saving**

After manipulating data in NumPy, you can save it using `np.save`.

```python
arr = np.array([1, 2, 3])

# Saves to 'arr.npy'
np.save('arr.npy', arr)

# np.save appends '.npy' automatically if missing
np.save('arr', arr)
```

- First argument → file name/path
- Second argument → data to save
- Overwrites existing file if it already exists

---

## **B. Loading**

To load previously saved data, use `np.load`.

```python
arr = np.array([1, 2, 3])
np.save('arr.npy', arr)

load_arr = np.load('arr.npy')
print(repr(load_arr))
```

**Output:**

```
array([1, 2, 3])
```

> `np.load` returns the data exactly as saved. The file name must include the ".npy" extension if it wasn’t appended.

---

# **Time to Code!**

Generate random points and save them to a file.

```python
def save_points(save_file):
    points = np.random.uniform(-2.5, 2.5, size=(100, 2))
    np.save(save_file, points)
```

- `points` → 100 random (x, y) points in range [-2.5, 2.5)
- Save to `save_file` using `np.save`
