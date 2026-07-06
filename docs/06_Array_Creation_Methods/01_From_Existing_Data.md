# 📘 Lesson 06.01 — Creating Arrays from Existing Data

> [!NOTE]
> **Difficulty:** 🟢 Beginner
>
> **Reading Time:** ~25 minutes
>
> **Practice Time:** ~20 minutes
>
> **Prerequisites:**
>
> - Lesson 04 — Creating Your First Array
> - Lesson 05 — Understanding Data Types

---

> *"Good programmers don't create data.
>
> They transform it."*

---

# ✅ Before You Continue

Before starting this lesson, make sure you can:

- [ ] Create a NumPy array using `np.array()`
- [ ] Explain what an `ndarray` is
- [ ] Read the `dtype` of an array
- [ ] Explain type inference

---

# 🎯 Learning Objectives

By the end of this lesson you will:

- Understand why existing data often needs to become a NumPy array.
- Learn the role of `np.array()`.
- Recognize common input types.
- Understand what happens during array creation.
- Begin thinking in terms of data transformation rather than data creation.

---

# 🧠 Mental Model

Imagine you're moving into a new house.

You already own:

- books,
- clothes,
- dishes,
- furniture.

You don't buy everything again.

You simply move your belongings into the new house.

NumPy works in much the same way.

Most of the time, your data already exists.

Perhaps it comes from:

- a Python list,
- a tuple,
- a CSV file,
- a database,
- a web API,
- another library.

Your task is not to create data from nothing.

Your task is to transform existing data into a structure that NumPy can process efficiently.

---

# 📖 Data Rarely Starts as a NumPy Array

When beginners first learn NumPy, it often looks like this:

```python
arr = np.array([1, 2, 3])
```

This is useful for learning.

However...

Real-world programs rarely begin with numbers typed directly into the source code.

Instead, data usually comes from somewhere else.

For example:

```text
CSV File
        │
        ▼
Python List
        │
        ▼
NumPy Array
        │
        ▼
Calculations
```

Or perhaps:

```text
Database

↓

Python Objects

↓

NumPy Array

↓

Machine Learning Model
```

The array is often just one step in a larger pipeline.

---

# 🔬 Experiment Lab 01

Let's start with something familiar.

📂 **Example:** `examples/chapter_06/01_list_to_array.py`

```python
import numpy as np

numbers = [10, 20, 30, 40, 50]

array = np.array(numbers)

print(array)
print(type(array))
```

---

## 🧠 Prediction

Before running the code:

- Is `numbers` still a Python list?
- What type is `array`?
- Did the original list change?

Think carefully before executing the program.

---

## ▶ Experiment

Run the code.

Expected output:

```text
[10 20 30 40 50]

<class 'numpy.ndarray'>
```

Notice something important.

The original list still exists.

NumPy simply used it as the input to create a new array.

---

# 📖 The Input and the Result

Let's look at the code again.

```python
numbers = [10, 20, 30, 40, 50]

array = np.array(numbers)
```

Two different objects now exist.

The first:

```python
numbers
```

is still a Python list.

The second:

```python
array
```

is a NumPy array.

They may contain similar values.

They are **not** the same object.

This distinction becomes especially important when we discuss copying and shared memory in later chapters.

---

# 💡 Did You Notice?

The variable name doesn't matter.

This works just as well:

```python
data = [1, 2, 3]

values = np.array(data)
```

Or:

```python
scores = [95, 88, 91]

results = np.array(scores)
```

What matters is the object being passed to `np.array()`.

The names themselves are simply labels chosen by the programmer.

---

# 📌 Key Takeaways (So Far)

You have learned that:

- Most real-world data already exists before NumPy sees it.
- `np.array()` transforms existing data into an `ndarray`.
- The original Python object remains unchanged.
- The resulting array is a new object.

---

> **Continue with Part 2**, where we'll discover that `np.array()` accepts much more than just Python lists.