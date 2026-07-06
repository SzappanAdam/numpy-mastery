# 📘 Lesson 06.02 — Filled Arrays

> [!NOTE]
> **Difficulty:** 🟢 Beginner
>
> **Reading Time:** ~25 minutes
>
> **Practice Time:** ~20 minutes
>
> **Prerequisites:**
>
> - Lesson 06.01 — Creating Arrays from Existing Data

---

> *"Sometimes the most useful data is the data you haven't filled in yet."*

---

# ✅ Before You Continue

Before starting this lesson, make sure you can:

- [ ] Create arrays using `np.array()`
- [ ] Read `shape`
- [ ] Read `dtype`
- [ ] Explain what an `ndarray` is

---

# 🎯 Learning Objectives

By the end of this lesson you will:

- Understand why NumPy can create arrays from scratch.
- Learn when `np.zeros()` is useful.
- Create one-dimensional and two-dimensional zero-filled arrays.
- Inspect their properties.
- Understand why zero-initialized arrays are common in scientific computing.

---

# 🧠 Mental Model

Imagine buying a brand-new notebook.

Every page is blank.

Nothing has been written yet.

That doesn't make the notebook useless.

In fact, its emptiness is exactly what makes it useful.

A zero-filled NumPy array is very similar.

Instead of containing meaningful values immediately, it provides a clean structure that can be filled later.

---

# 📖 Why Create an Empty Dataset?

Until now, every array started with existing data.

For example:

```python
scores = [95, 88, 91]

arr = np.array(scores)
```

But in many real-world programs, the data does not exist yet.

Imagine you're writing a simulation.

Perhaps you'll calculate one million values.

Where should those values be stored?

You first create the array.

Then you gradually fill it.

This is one of the reasons functions like `np.zeros()` exist.

---

# 🔬 Experiment Lab 01 — Your First Zero Array

📂 **Example:** `examples/chapter_06/06_zeros_1d.py`

```python
import numpy as np

arr = np.zeros(5)

print(arr)
```

---

## 🧠 Prediction

Before running the code:

- How many elements will the array contain?
- What value will each element have?
- What do you expect the `dtype` to be?

Think before executing.

---

## ▶ Experiment

Run the program.

Expected output:

```text
[0. 0. 0. 0. 0.]
```

Notice something surprising.

The values are displayed as:

```text
0.
```

instead of:

```text
0
```

Why?

Let's investigate.

---

# 📖 Why Are They Floating-Point Numbers?

Inspect the array.

```python
import numpy as np

arr = np.zeros(5)

print(arr.dtype)
```

Expected output:

```text
float64
```

By default, `np.zeros()` creates an array of floating-point numbers.

This design is intentional.

Many numerical calculations involve decimal values, so floating-point numbers are a sensible default.

If you need integers instead, you can specify the desired data type explicitly.

We'll do that shortly.

---

# 🔬 Experiment Lab 02 — A Two-Dimensional Zero Array

Creating larger arrays is just as easy.

📂 **Example:** `examples/chapter_06/07_zeros_2d.py`

```python
import numpy as np

arr = np.zeros((3, 4))

print(arr)
```

Run the program.

Expected output:

```text
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]
```

Let's inspect it.

```python
print(arr.shape)

print(arr.ndim)

print(arr.size)
```

Expected output:

```text
(3, 4)

2

12
```

---

# 🧠 Understanding the Shape

Notice the argument:

```python
(3, 4)
```

This is a tuple.

It tells NumPy:

- Create 3 rows.
- Create 4 columns.

A useful way to read it is:

> `(rows, columns)`

As we progress to higher dimensions later in the course, this pattern will continue.

---

# 💡 Did You Notice?

With `np.array()`, the **data** determines the shape.

With `np.zeros()`, **you** determine the shape.

This is an important shift.

You're no longer describing the values.

You're describing the structure first.

---

# 📌 Key Takeaways (So Far)

You have learned that:

- `np.zeros()` creates arrays from scratch.
- The argument specifies the desired shape.
- The default data type is `float64`.
- Zero-filled arrays are useful when data will be computed later.

---

> **Continue with Part 2**, where we'll customize the data type using `dtype=` and learn why integer zero arrays are sometimes preferable.