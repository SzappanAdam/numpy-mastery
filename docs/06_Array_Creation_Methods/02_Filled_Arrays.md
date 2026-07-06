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

# 📖 Controlling the Data Type

In the previous lesson, we discovered that:

```python
import numpy as np

arr = np.zeros(5)

print(arr.dtype)
```

produces:

```text
float64
```

This is the default behavior.

However, NumPy also allows you to explicitly choose the data type.

You can do this using the `dtype` parameter.

---

# 🔬 Experiment Lab 03 — Integer Zero Arrays

📂 **Example:** `examples/chapter_06/08_zeros_integer.py`

```python
import numpy as np

arr = np.zeros(5, dtype=int)

print(arr)

print(arr.dtype)
```

---

## 🧠 Prediction

Before running the program, answer these questions.

- Will the values still be zeros?
- Will they look different?
- What data type do you expect?

Think first.

Then execute the code.

---

## ▶ Experiment

Expected output:

```text
[0 0 0 0 0]

int64
```

On some systems you may instead see:

```text
int32
```

Both are perfectly normal.

The exact integer type depends on your platform.

The important observation is that the array now stores integers instead of floating-point numbers.

---

# 📖 The `dtype` Parameter

The general syntax is:

```python
np.zeros(shape, dtype=...)
```

The first argument specifies:

> **How large should the array be?**

The `dtype` argument specifies:

> **What kind of values should the array store?**

These two concepts are completely independent.

For example:

```python
np.zeros(10)
```

creates:

- 10 elements
- floating-point numbers

Whereas:

```python
np.zeros(10, dtype=int)
```

creates:

- 10 elements
- integer numbers

The shape stays the same.

Only the representation changes.

---

# 🔬 Experiment Lab 04 — Boolean Arrays

Let's try another data type.

📂 **Example:** `examples/chapter_06/09_zeros_boolean.py`

```python
import numpy as np

arr = np.zeros(6, dtype=bool)

print(arr)

print(arr.dtype)
```

Run the program.

Expected output:

```text
[False False False False False False]

bool
```

Interesting.

Even though we called:

```python
zeros()
```

the array contains:

```text
False
```

instead of:

```text
0
```

Why?

Because every data type has its own representation of "zero".

For Boolean values:

```text
0

↓

False
```

---

# 💡 Did You Notice?

The function name:

```python
zeros()
```

does not necessarily mean:

> "Fill the array with the digit 0."

Instead, it means:

> **Fill the array with the zero value of the chosen data type.**

Examples:

| Data Type | Zero Value |
|-----------|------------|
| `float` | `0.0` |
| `int` | `0` |
| `bool` | `False` |

This idea appears throughout NumPy.

The values displayed depend on the chosen `dtype`.

---

# ⚠️ Common Misconception

Many beginners think that:

```python
np.zeros()
```

always creates floating-point arrays.

Not quite.

It creates floating-point arrays **by default**.

But the data type is completely under your control.

Whenever necessary, simply specify:

```python
dtype=...
```

---

# 💻 Mini Challenge

Predict the output before running each example.

```python
np.zeros(3)

np.zeros(3, dtype=int)

np.zeros(3, dtype=bool)

np.zeros((2, 2), dtype=int)
```

Pay attention to both:

- the values,
- and the reported `dtype`.

---

# 🧠 Brain Builder

Imagine you're writing software that stores:

- the number of visitors to a website,
- whether a sensor is active,
- the measured temperature.

Would you choose the same data type for all three?

Why or why not?

Think about what kind of information each array is meant to represent.

---

# 📌 Key Takeaways (So Far)

You now know that:

- `dtype` controls how values are stored.
- `np.zeros()` uses `float64` by default.
- You can explicitly request integers or Booleans.
- The shape and the data type are independent concepts.
- Every data type has its own representation of "zero".

---

> **Continue with Part 3**, where we'll explore `np.ones()` and discover that creating arrays filled with ones is just as simple.