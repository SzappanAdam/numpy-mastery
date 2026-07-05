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

# 🔬 Experiment Lab 02 — NumPy Makes Decisions

So far, we've seen that Python automatically knows the type of a single value.

But what happens when we ask NumPy to create an array?

Consider this example.

📂 **Example:** `examples/chapter_05/02_type_inference.py`

```python
import numpy as np

numbers = np.array([1, 2, 3, 4, 5])

print(numbers)
print(numbers.dtype)
```

---

## 🧠 Prediction

Before running the program, ask yourself:

- How does NumPy know which data type to use?
- Did we explicitly tell NumPy to create an integer array?

Look carefully.

There is no `dtype=` parameter anywhere.

So how did NumPy decide?

---

## ▶ Experiment

Run the code.

Expected output (may vary slightly depending on your platform):

```text
[1 2 3 4 5]
int64
```

On some systems you may see:

```text
int32
```

Both results are correct.

The exact integer type depends on your operating system, Python build, and hardware architecture.

The important observation is this:

> **NumPy chose the data type automatically.**

This process is called **type inference**.

---

# 📖 What Is Type Inference?

Type inference means:

> **NumPy examines the input data and automatically chooses an appropriate data type.**

In our example:

```python
np.array([1, 2, 3, 4, 5])
```

every value is an integer.

Therefore, NumPy creates an integer array.

Notice that we never had to write:

```python
dtype=int
```

NumPy inferred it for us.

This makes array creation simple while still producing efficient arrays.

---

# 🧠 Mental Model

Imagine a librarian receiving a stack of books.

If every book is a novel, they all go on the fiction shelf.

If every book is a cookbook, they all go in the cooking section.

The librarian doesn't need to ask where each individual book belongs.

The collection itself provides enough information.

NumPy behaves similarly.

It looks at the values you provide and chooses a data type that can represent all of them safely.

---

# 🔬 Experiment Lab 03 — Floating-Point Numbers

Let's try a different input.

📂 **Example:** `examples/chapter_05/03_float_inference.py`

```python
import numpy as np

numbers = np.array([1.5, 2.5, 3.5])

print(numbers)
print(numbers.dtype)
```

---

## 🧠 Prediction

Before running the code:

Will NumPy still create an integer array?

Or something else?

Why?

---

## ▶ Experiment

Run the program.

Expected output:

```text
[1.5 2.5 3.5]

float64
```

Again, the exact floating-point type may differ depending on your platform.

The key observation is that NumPy detected floating-point values and selected an appropriate floating-point data type.

---

# 🔍 Observation

Compare the two arrays.

```python
np.array([1, 2, 3])
```

↓

Integer array

---

```python
np.array([1.5, 2.5, 3.5])
```

↓

Floating-point array

Nothing in the code explicitly told NumPy which type to use.

The values themselves determined the result.

---

# 💡 Did You Notice?

The values stored inside an array influence its `dtype`.

Changing the input changes the inferred data type.

However, NumPy always attempts to choose **one data type for the entire array**.

This is a very important design rule.

We'll soon see what happens when different kinds of values are mixed together.

---

# ⚠️ Common Misconception

Many beginners think that NumPy stores the type of each element individually.

That is **not** how homogeneous arrays work.

Instead:

- the **array** has a data type,
- every element follows that same data type.

This consistency allows NumPy to organize memory efficiently and perform fast numerical operations.

---

# 💻 Mini Challenge

Predict the `dtype` for each array before running the code.

```python
np.array([10, 20, 30])

np.array([0.5, 1.5, 2.5])

np.array([1000, 2000, 3000])

np.array([-1, -2, -3])
```

Then run the examples and compare your predictions.

Did NumPy behave as you expected?

---

# 🧠 Brain Builder

Think about the following question.

If NumPy allowed every element in an array to have a completely different type...

- Would it still know exactly how much memory each element occupies?
- Could it quickly jump to the millionth element?
- Would mathematical operations still be as efficient?

Don't worry if you can't answer completely yet.

We'll return to this question when discussing memory layout later in the course.

---

# 📌 Key Takeaways (So Far)

You now know that:

- NumPy automatically chooses a suitable data type.
- This process is called **type inference**.
- The input values determine the inferred type.
- Arrays are designed to use a single data type for all elements.
- This design is essential for NumPy's performance.

---

> **Continue with Part 3**, where we'll intentionally mix different kinds of values inside one array and discover how NumPy resolves type conflicts.