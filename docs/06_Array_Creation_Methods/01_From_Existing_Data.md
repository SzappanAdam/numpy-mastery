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

# 📖 `np.array()` Accepts More Than Lists

In the previous lesson, we created an array from a Python list.

```python
numbers = [10, 20, 30]

arr = np.array(numbers)
```

It worked exactly as expected.

But here's an important question:

> **Does `np.array()` only work with lists?**

The answer is:

> **No.**

In fact, `np.array()` can create arrays from many different kinds of Python objects.

As long as NumPy can understand the structure of the input, it can usually convert it into an `ndarray`.

---

# 🧠 Mental Model

Imagine a translator.

The translator doesn't care whether the original text came from:

- a book,
- a newspaper,
- a handwritten note,
- or an email.

As long as the language is understandable, the translator can translate it.

`np.array()` works similarly.

It doesn't specifically require a list.

It simply needs an input that can be interpreted as a sequence of values.

---

# 🔬 Experiment Lab 02 — Creating an Array from a Tuple

Python has another built-in collection type called a **tuple**.

It looks very similar to a list.

The main visual difference is that tuples use parentheses instead of square brackets.

📂 **Example:** `examples/chapter_06/02_tuple_to_array.py`

```python
import numpy as np

numbers = (10, 20, 30, 40)

arr = np.array(numbers)

print(arr)

print(type(arr))
```

---

## 🧠 Prediction

Before running the program:

- Will NumPy accept the tuple?
- Will the result still be an `ndarray`?
- Will the output look different?

Write down your prediction.

---

## ▶ Experiment

Run the program.

Expected output:

```text
[10 20 30 40]

<class 'numpy.ndarray'>
```

Excellent.

Even though the input was a tuple...

the result is still a NumPy array.

---

# 📖 Lists vs Tuples

Let's compare them.

| Feature | List | Tuple |
|----------|------|-------|
| Syntax | `[ ]` | `( )` |
| Mutable | ✅ Yes | ❌ No |
| Can be used with `np.array()` | ✅ Yes | ✅ Yes |

For the purpose of creating NumPy arrays:

both work perfectly.

---

# 🔬 Experiment Lab 03 — Creating an Array from a `range`

Another useful Python object is `range()`.

Instead of storing all numbers immediately,

`range()` represents a sequence.

📂 **Example:** `examples/chapter_06/03_range_to_array.py`

```python
import numpy as np

numbers = range(5)

arr = np.array(numbers)

print(arr)
```

---

## 🧠 Prediction

What do you think will happen?

Will NumPy understand the `range` object?

Or will it produce an error?

Think first.

Then run the code.

---

## ▶ Experiment

Expected output:

```text
[0 1 2 3 4]
```

Great!

NumPy successfully converted the sequence into an array.

---

# 💡 Did You Notice?

The input objects we've used so far are different:

```python
[1, 2, 3]
```

↓

List

---

```python
(1, 2, 3)
```

↓

Tuple

---

```python
range(3)
```

↓

Range object

Yet all three produce the same kind of result:

```python
ndarray
```

This tells us something important.

`np.array()` focuses on the **values**, not on the specific container they came from.

---

# ⚠️ Common Misconception

Many beginners assume that NumPy was designed specifically for Python lists.

That's not true.

Lists are simply one of many valid inputs.

NumPy is much more flexible than that.

As you'll see later in this course, arrays can also be created from:

- existing NumPy arrays,
- nested sequences,
- buffers,
- and many other data sources.

---

# 💻 Mini Challenge

Without looking at the answers, predict whether each of the following will work.

```python
np.array([1, 2, 3])

np.array((1, 2, 3))

np.array(range(3))
```

After making your predictions, run the code.

Did every example create an `ndarray`?

---

# 🧠 Brain Builder

Suppose NumPy only accepted Python lists.

How would that affect programs that read data from:

- files,
- databases,
- APIs,
- other scientific libraries?

Would programmers constantly need to convert everything into lists first?

Why might that be inconvenient?

---

# 📌 Key Takeaways (So Far)

You now know that:

- `np.array()` accepts many different kinds of input.
- Python lists are only one possible source.
- Tuples can also be converted into arrays.
- `range()` objects can be converted into arrays.
- NumPy focuses on the sequence of values rather than the specific Python container.

---

# 📖 Nested Data

So far, every array we've created has been one-dimensional.

For example:

```python
np.array([1, 2, 3, 4, 5])
```

Visually, this looks like a single row of values:

```text
[1 2 3 4 5]
```

But what if our data naturally contains **rows and columns**?

Imagine a classroom where each row represents one student's test scores.

Instead of storing everything in a single long list, we could organize the data into multiple rows.

This is where **nested sequences** become useful.

---

# 🧠 Mental Model

Imagine a bookshelf.

Previously, we had one shelf:

```text
[ Book ][ Book ][ Book ][ Book ]
```

Now imagine a bookcase with multiple shelves:

```text
Shelf 1 → [ Book ][ Book ][ Book ]

Shelf 2 → [ Book ][ Book ][ Book ]

Shelf 3 → [ Book ][ Book ][ Book ]
```

Each shelf contains several books.

Together, they form a larger structure.

Nested lists work exactly the same way.

Each inner list becomes one row of the array.

---

# 🔬 Experiment Lab 04 — Creating a Two-Dimensional Array

📂 **Example:** `examples/chapter_06/04_nested_lists.py`

```python
import numpy as np

matrix = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

print(matrix)
```

---

## 🧠 Prediction

Before running the code:

- Will NumPy accept this structure?
- How many dimensions will the resulting array have?
- How many rows do you expect?
- How many columns?

Write down your answers before running the program.

---

## ▶ Experiment

Run the program.

Expected output:

```text
[[1 2 3]
 [4 5 6]
 [7 8 9]]
```

Excellent.

Notice that the output now contains multiple rows.

Although it looks different, it is still an `ndarray`.

---

# 📖 What Happened?

Look carefully at the input.

```python
[
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

The outer list contains three inner lists.

Each inner list contains three values.

NumPy interprets this as:

- three rows,
- three columns.

The result is a **two-dimensional array**.

---

# 🔍 Inspecting the Array

Let's inspect the object we just created.

```python
import numpy as np

matrix = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

print(matrix.shape)
print(matrix.ndim)
print(matrix.size)
```

Expected output:

```text
(3, 3)

2

9
```

Let's interpret each value.

### `shape`

```text
(3, 3)
```

The array has:

- 3 rows
- 3 columns

---

### `ndim`

```text
2
```

The array has two dimensions.

---

### `size`

```text
9
```

There are nine elements in total.

---

# 💡 Did You Notice?

Previously, we saw shapes like:

```text
(5,)
```

Now we see:

```text
(3, 3)
```

This isn't a coincidence.

Every value in the shape tuple describes one dimension.

For a two-dimensional array:

```text
(rows, columns)
```

As we explore higher-dimensional arrays later in the course, the shape tuple will naturally grow to describe each additional dimension.

---

# ⚠️ Common Mistake

Beginners often confuse:

```text
shape = (3, 3)
```

with:

```text
size = 3
```

Remember:

- `shape` describes the layout.
- `size` counts **every element**.

In this example:

```text
3 × 3 = 9
```

So:

```python
matrix.size
```

returns:

```text
9
```

---

# 💻 Mini Challenge

Create the following arrays.

```python
np.array([
    [10, 20],
    [30, 40]
])

np.array([
    [1, 2, 3],
    [4, 5, 6]
])

np.array([
    [100],
    [200],
    [300]
])
```

For each array, inspect:

- `shape`
- `ndim`
- `size`
- `dtype`

Can you identify the relationship between the rows, columns, and total number of elements?

---

# 🧠 Brain Builder

Suppose every row had a different number of elements.

For example:

```python
[
    [1, 2, 3],
    [4, 5],
    [6, 7, 8]
]
```

Ask yourself:

- Is this still a proper rectangle?
- How many columns would the array have?
- Could NumPy store it efficiently?

We'll investigate this exact question in the next part.

---

# 📌 Key Takeaways (So Far)

You have learned that:

- Nested lists create multi-dimensional arrays.
- Each inner list becomes one row.
- `shape` now reports rows and columns.
- `ndim` increases as dimensions increase.
- `size` is still the total number of elements.

---

> **Continue with Part 4**, where we'll investigate irregular ("ragged") nested sequences, understand why NumPy prefers rectangular data, and conclude the lesson.