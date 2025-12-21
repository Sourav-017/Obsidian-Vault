 [[Numpy]]

`np.vstack` **vertically stacks arrays** — it joins them **row-wise**.

Think of it as putting arrays **on top of each other**.

---

# ✅ **Basic example**

`import numpy as np  a = np.array([1, 2, 3]) b = np.array([4, 5, 6])  np.vstack((a, b))`

**Output:**

`array([     [1, 2, 3],     [4, 5, 6] ])`

It turns 1D arrays into rows and stacks them vertically.

---

# ✅ **Stacking 2D arrays**

`A = np.array([[1, 2],               [3, 4]])  B = np.array([[5, 6]])  np.vstack((A, B))`

**Output:**

`array([     [1, 2],     [3, 4],     [5, 6] ])`

---

# ✅ **When to use `vstack`**

Use it when:

- You have samples and want to append more samples vertically
    
- You want to combine multiple `(n, d)` arrays into one big dataset
    
- You want to stack features or points row-by-row