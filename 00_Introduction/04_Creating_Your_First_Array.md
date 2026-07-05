# 📘 Lesson 04 — Creating Your First Array

> [!NOTE]
> **Difficulty:** 🟢 Beginner  
> **Reading Time:** ~25 minutes  
> **Practice Time:** ~20 minutes  
> **Prerequisites:** Lesson 03 — Installing NumPy

---

> *"The journey of a thousand miles begins with a single step."*  
> — Lao Tzu

---

# 🎯 Learning Objectives

By the end of this lesson, you will be able to:

- Import the NumPy library.
- Understand the purpose of the `np` alias.
- Create your first NumPy array.
- Recognize that a NumPy array is different from a Python list.
- Explain each part of the code used to create an array.

---

# 🧠 Mental Model

Imagine a bookshelf.

Each shelf holds books of exactly the same size.

Every book has its own position.

Because every book is identical in size, finding the 100th book is easy.

You simply count to the correct position.

Now imagine another bookshelf.

Some books are tiny.

Others are enormous.

Some aren't books at all—they're boxes.

Finding the 100th item suddenly becomes much more complicated.

This is the key difference between Python lists and NumPy arrays.

NumPy assumes every element has the same type and size.

That assumption allows it to organize memory much more efficiently.

---

# 📖 Before We Write Any Code

This is the first programming lesson of the course.

If you're excited to finally write some NumPy code...

...great!

But before typing anything, let's understand **what we're trying to create**.

So far we've learned:

- What NumPy is.
- Why NumPy exists.
- How to install it.

Now we're finally ready to create the most important object in the entire library:

> **The ndarray.**

Everything else in NumPy revolves around this data structure.

---

# 🤔 What Is an Array?

An **array** is an ordered collection of values.

Each value occupies a specific position.

For example:

```text
Index

 0   1   2   3

 ▼   ▼   ▼   ▼

+---+---+---+---+
|10 |20 |30 |40 |
+---+---+---+---+
```

Each value can be accessed by its position (called its **index**).

If you've worked with Python lists before, this idea should already feel familiar.

However, NumPy arrays are **not** Python lists.

Although they may look similar at first glance, they behave very differently behind the scenes.

We'll spend much of this course exploring those differences.

---

# 🚀 Your First NumPy Program

Create a new Python file named:

```text
first_array.py
```

Then write the following code:

```python
import numpy as np

numbers = np.array([1, 2, 3, 4, 5])

print(numbers)
```

Save the file.

Run it.

If everything is set up correctly, you should see:

```text
[1 2 3 4 5]
```

Congratulations!

You have just created your first NumPy array.

Although this program is very small, it introduces one of the most important objects in scientific Python.

---

# 🔍 Code Dissection

Let's examine every line carefully.

```python
import numpy as np
```

This line imports the NumPy library.

The keyword:

```python
import
```

tells Python to load another module.

The word:

```python
numpy
```

is the name of the library.

Finally:

```python
as np
```

creates a shorter nickname (called an **alias**) for the library.

Instead of writing:

```python
numpy.array(...)
```

we can simply write:

```python
np.array(...)
```

This convention is used in almost every NumPy project you'll encounter.

---

# 💡 Did You Notice?

Why isn't the output printed like a Python list?

Python list:

```python
[1, 2, 3, 4, 5]
```

NumPy array:

```python
[1 2 3 4 5]
```

Notice that the commas are missing.

This small visual difference is one of the easiest ways to recognize a NumPy array when printed.

Internally, however, the differences are much deeper than formatting.

We'll uncover them gradually throughout the course.

---

# 🧠 Think Before You Continue

Before reading further, try answering this question.

If we remove the line:

```python
import numpy as np
```

what do you think will happen?

Will the program still run?

Why or why not?

Take a moment to think before testing it.

Learning to predict program behavior is one of the most valuable programming skills you can develop.

---

# 📌 Key Takeaways (So Far)

You have learned that:

- NumPy must be imported before use.
- `np` is simply an alias for the NumPy module.
- `np.array()` creates a NumPy array.
- Arrays and Python lists may look similar, but they are different objects.
- Understanding the `ndarray` is the foundation of learning NumPy.

---

# 🔬 Experiment Lab 01

Before we continue, let's perform our first real NumPy experiment.

Create the following program:

```python
import numpy as np

numbers = np.array([1, 2, 3, 4, 5])

print(numbers)
print(type(numbers))
```

Before running it...

## 🧠 Prediction

What do you think `type(numbers)` will display?

Take a moment to think.

Don't run the code just yet.

Try making a prediction first.

---

## ▶ Experiment

Run the program.

You should see something similar to:

```text
[1 2 3 4 5]
<class 'numpy.ndarray'>
```

Interesting...

The object is **not** a Python list.

Instead, Python tells us that its type is:

```text
numpy.ndarray
```

This confirms something very important.

`np.array()` does **not** return a list.

It returns a completely different object.

---

# 📖 What Is `ndarray`?

You will see this word constantly throughout the course.

Let's break it down.

```
nd
```

stands for

> **n-dimensional**

and

```
array
```

means

> **array**

So,

```
ndarray
```

literally means:

> **N-dimensional array**

The letter **N** simply means:

> "Any number."

An ndarray may contain:

- one dimension
- two dimensions
- three dimensions

or even many more.

For now, our example

```python
np.array([1,2,3,4,5])
```

is a **one-dimensional array**.

We'll learn about additional dimensions later.

---

# 🔍 Code Dissection

Let's inspect this line carefully.

```python
numbers = np.array([1, 2, 3, 4, 5])
```

Every part has a purpose.

| Code | Meaning |
|------|---------|
| `numbers` | Variable name |
| `=` | Assign the result |
| `np` | Alias of the NumPy module |
| `array()` | Function that creates an ndarray |
| `[1,2,3,4,5]` | A Python list used as the input |

Notice something subtle.

The list is only the **input**.

The result is an ndarray.

These are different objects.

---

# 🧠 Mental Model

Imagine pouring water into a bottle.

The water changes containers.

The bottle is **not** the water.

Likewise,

```python
[1,2,3]
```

is simply the data you provide.

NumPy then places that data inside a brand-new container:

```
ndarray
```

The input list is one thing.

The resulting array is another.

This distinction is easy to overlook when you're beginning, but it becomes extremely important later.

---

# 👀 Did You Notice?

Suppose we write:

```python
numbers = np.array([1, 2, 3])
```

The variable

```python
numbers
```

does **not** store the numbers directly.

Instead, it stores a **reference** to the ndarray object created by NumPy.

For now, you can simply think of a reference as:

> "The variable knows where the object is."

We'll study Python objects and references in much greater detail later.

---

# 🧪 Experiment Lab 02

Let's compare two objects.

```python
import numpy as np

python_list = [1, 2, 3]

numpy_array = np.array([1, 2, 3])

print(type(python_list))

print(type(numpy_array))
```

Before running the code...

## 🧠 Prediction

Will both objects have the same type?

Or different types?

Why?

---

## ▶ Experiment

Run the code.

Expected output:

```text
<class 'list'>
<class 'numpy.ndarray'>
```

Excellent.

Even though both objects contain the same values...

they are completely different data structures.

---

# ⚠️ Common Misconception

Many beginners say:

> "A NumPy array is basically a list."

Not quite.

A better way to think about it is:

> A NumPy array can often be **created from** a Python list, but once created, it becomes an entirely different object with different behavior, different capabilities, and different performance characteristics.

This distinction will become clearer with every lesson.

---

# 💡 Toolbox

> [!TIP]
>
> The built-in Python function
>
> ```python
> type()
> ```
>
> is one of the simplest debugging tools you have.
>
> Whenever you're unsure what kind of object you're working with, use:
>
> ```python
> print(type(variable))
> ```
>
> It can save you a lot of confusion.

---

# 📌 Key Takeaways (So Far)

You now know that:

- `np.array()` returns an `ndarray`.
- `ndarray` stands for *n-dimensional array*.
- A Python list and a NumPy array are different object types.
- Python lists are commonly used as input when creating arrays.
- The `type()` function allows you to inspect the type of any Python object.

---

> **Continue with Part 3**, where we'll inspect an array more closely using its attributes, introduce `dtype`, `shape`, and `ndim`, and start thinking like NumPy.