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

# 📖 Meet `np.ones()`

So far, we've created arrays filled with zeros.

```python
import numpy as np

arr = np.zeros(5)

print(arr)
```

Output:

```text
[0. 0. 0. 0. 0.]
```

But what if every element should start with the value **1** instead?

NumPy provides another function for exactly this purpose:

```python
np.ones()
```

The overall idea is identical to `np.zeros()`.

The only difference is the initial value.

---

# 🧠 Mental Model

Imagine you're preparing answer sheets for an exam.

One approach is to start with every checkbox empty:

```
☐ ☐ ☐ ☐ ☐
```

Another is to start with every checkbox already selected:

```
☑ ☑ ☑ ☑ ☑
```

The structure is the same.

Only the initial state changes.

This is exactly the relationship between:

- `np.zeros()`
- `np.ones()`

---

# 🔬 Experiment Lab 05 — Your First One Array

📂 **Example:** `examples/chapter_06/10_ones_1d.py`

```python
import numpy as np

arr = np.ones(5)

print(arr)

print(arr.dtype)
```

---

## 🧠 Prediction

Before running the code:

- How many elements will the array contain?
- Which value will every element have?
- Which data type do you expect?

---

## ▶ Experiment

Run the program.

Expected output:

```text
[1. 1. 1. 1. 1.]

float64
```

Notice something familiar.

Just like `np.zeros()`,

`np.ones()` also creates a floating-point array by default.

---

# 📖 The Similarity Is Intentional

Compare the two functions.

```python
np.zeros(5)
```

↓

```text
[0. 0. 0. 0. 0.]
```

---

```python
np.ones(5)
```

↓

```text
[1. 1. 1. 1. 1.]
```

Everything is the same except the initial value.

This consistency is one of NumPy's strengths.

Once you learn one creation function,

the others become much easier to understand.

---

# 🔬 Experiment Lab 06 — A Two-Dimensional Array of Ones

📂 **Example:** `examples/chapter_06/11_ones_2d.py`

```python
import numpy as np

arr = np.ones((2, 4))

print(arr)
```

Expected output:

```text
[[1. 1. 1. 1.]
 [1. 1. 1. 1.]]
```

Inspect it.

```python
print(arr.shape)

print(arr.ndim)

print(arr.size)

print(arr.dtype)
```

Expected output:

```text
(2, 4)

2

8

float64
```

Everything we've already learned still applies.

Only the initial value changed.

---

# 🔬 Experiment Lab 07 — Integer Ones

Just like `np.zeros()`,

`np.ones()` also supports the `dtype` parameter.

📂 **Example:** `examples/chapter_06/12_ones_integer.py`

```python
import numpy as np

arr = np.ones(6, dtype=int)

print(arr)

print(arr.dtype)
```

Expected output:

```text
[1 1 1 1 1 1]

int64
```

(On some systems, `int32`.)

Again,

the platform may differ,

but the behavior remains the same.

---

# 💡 Did You Notice?

Both functions follow exactly the same pattern.

```python
np.zeros(shape, dtype=...)
```

---

```python
np.ones(shape, dtype=...)
```

Once you understand one,

you almost automatically understand the other.

This kind of API consistency is one of the reasons NumPy is pleasant to work with.

---

# ⚠️ Common Misconception

Some beginners assume that:

```python
np.ones()
```

creates an array suitable only for mathematical calculations involving the number one.

Not at all.

Very often,

arrays of ones are used as:

- masks,
- weights,
- counters,
- initialization values,
- placeholders,
- or starting points for later computations.

The value **1** is simply a convenient default.

---

# 💻 Mini Challenge

Predict the output.

```python
np.ones(4)

np.ones((3, 2))

np.ones(5, dtype=int)

np.ones((2, 2), dtype=bool)
```

For each example,

predict:

- the values,
- the shape,
- the data type.

Then verify your answers.

---

# 🧠 Brain Builder

Suppose NumPy did not provide `np.ones()`.

Could you still create an array of ones?

Certainly.

For example:

```python
np.zeros(5) + 1
```

would work.

So why do you think NumPy includes a dedicated function anyway?

Consider:

- readability,
- performance,
- programmer intent.

We'll revisit this design philosophy many times throughout the course.

---

# 📌 Key Takeaways (So Far)

You now know that:

- `np.ones()` creates arrays filled with ones.
- It follows the same API as `np.zeros()`.
- The default `dtype` is `float64`.
- You can override the data type using `dtype`.
- Consistent APIs make NumPy easier to learn and use.

---

> **Continue with Part 4**, where we'll introduce `np.full()` and `np.empty()`, compare all filled-array creation functions, and finish this lesson with exercises and a summary.