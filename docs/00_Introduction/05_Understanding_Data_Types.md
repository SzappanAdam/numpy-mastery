# 📘 Lesson 05 — Understanding Data Types

> [!NOTE]
> **Difficulty:** 🟢 Beginner → 🟡 Intermediate  
> **Reading Time:** ~30 minutes  
> **Practice Time:** ~20 minutes  
> **Prerequisites:** Lesson 04 — Creating Your First Array

---

> *"Everything should be made as simple as possible, but not simpler."*  
> — Albert Einstein

---

# ✅ Before You Continue

Before starting this lesson, make sure you can:

- [ ] Import NumPy using `import numpy as np`
- [ ] Create an array with `np.array()`
- [ ] Explain what an `ndarray` is
- [ ] Use `type()`
- [ ] Read `dtype`, `shape`, `size`, and `ndim`

If any of these feel uncertain, consider reviewing Lesson 04 before continuing.

---

# 🎯 Learning Objectives

By the end of this lesson, you will be able to:

- Explain what a data type is.
- Understand why NumPy uses homogeneous arrays.
- Predict how NumPy chooses a data type.
- Recognize automatic type inference.
- Understand why data types affect performance.

---

# 🧠 Mental Model

Imagine a warehouse.

Every shelf is designed to store **exactly one type of box**.

One shelf stores only books.

Another stores only bottles.

Another stores only laptops.

Why?

Because if every object on a shelf has the same shape and size:

- storing them is easier,
- finding them is faster,
- moving them is more efficient.

Now imagine a shelf containing:

- one book,
- one bicycle,
- one coffee mug,
- one television,
- one pillow.

Everything has a different size.

Everything requires different handling.

Everything becomes slower.

NumPy arrays work exactly like the organized warehouse.

Every element is expected to have the same underlying data type.

That design decision is one of the main reasons NumPy is so fast.

---

# 📖 What Is a Data Type?

Every value stored inside a computer has a representation.

The computer cannot store an abstract idea such as:

```
42
```

Instead, it stores bits in memory.

To interpret those bits correctly, the computer must know **what kind of value they represent**.

That description is called a **data type**.

A data type answers questions like:

- Is this an integer?
- Is it a floating-point number?
- Is it text?
- Is it a Boolean value?
- How many bytes does it occupy?

Without knowing the data type, the computer would not know how to interpret the raw bits stored in memory.

---

# 🌍 Data Types in Everyday Python

Even before using NumPy, you've already encountered several Python data types.

For example:

```python
age = 25
```

The value `25` is an integer.

```python
temperature = 21.5
```

The value `21.5` is a floating-point number.

```python
name = "Alice"
```

The value `"Alice"` is a string.

```python
is_logged_in = True
```

The value `True` is a Boolean.

Python automatically keeps track of these types for you.

You rarely need to think about them.

NumPy, however, makes data types much more visible because they directly influence memory usage and computational performance.

---

# 🔬 Experiment Lab 01

Let's investigate.

Create the following program.

📂 **Example:** `examples/chapter_05/01_python_types.py`

```python
age = 25

temperature = 21.5

name = "Alice"

is_student = True

print(type(age))

print(type(temperature))

print(type(name))

print(type(is_student))
```

---

## 🧠 Prediction

Before running the code, answer:

Which four Python types do you expect to see?

Write your prediction first.

---

## ▶ Experiment

Run the program.

Expected output:

```text
<class 'int'>
<class 'float'>
<class 'str'>
<class 'bool'>
```

Excellent.

This confirms that Python already distinguishes different kinds of values.

NumPy builds upon this idea—but applies it to entire arrays.

---

# 💡 Did You Notice?

A single Python variable stores **one value**.

A NumPy array stores **many values**.

If NumPy wants to process millions of elements efficiently, it needs all of them to follow the same rules.

That is why homogeneous data types are so important.

---

# 🧠 Think Before You Continue

Imagine an array containing:

```text
1
2
3
4
5
```

Now imagine another array containing:

```text
1
"hello"
True
3.14
None
```

Which one do you think is easier for the computer to process quickly?

Why?

Don't worry about giving a perfect answer yet.

We'll uncover the reason step by step throughout this chapter.

---

# 📌 Key Takeaways (So Far)

At this point, you should understand that:

- Every value has a data type.
- Data types tell the computer how to interpret memory.
- Python automatically tracks data types.
- NumPy relies heavily on data types for efficiency.
- Homogeneous arrays are a deliberate design choice.

---

> **Continue with Part 2**, where we'll discover how NumPy automatically chooses a data type for an array and what happens when different types are mixed together.