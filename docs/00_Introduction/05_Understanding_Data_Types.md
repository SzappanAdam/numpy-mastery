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

# 🔬 Experiment Lab 04 — Mixing Data Types

Until now, every array we've created contained values of the same type.

For example:

```python
np.array([1, 2, 3])
```

contains only integers.

And:

```python
np.array([1.5, 2.5, 3.5])
```

contains only floating-point numbers.

But what happens if we mix different kinds of values together?

Let's find out.

---

## 📂 Example: `examples/chapter_05/04_mixed_integer_float.py`

```python
import numpy as np

numbers = np.array([1, 2, 3.5])

print(numbers)
print(numbers.dtype)
```

---

## 🧠 Prediction

Before running the program, think carefully.

Possible outcomes:

- The array becomes an integer array.
- The array becomes a floating-point array.
- NumPy raises an error.

Which one seems most reasonable?

Why?

Take a moment before executing the code.

---

## ▶ Experiment

Run the program.

Expected output:

```text
[1.  2.  3.5]

float64
```

Notice something interesting.

The integers:

```text
1
2
```

became:

```text
1.0
2.0
```

NumPy automatically converted them.

---

# 📖 Why Did This Happen?

Remember one of NumPy's fundamental rules:

> **An array should use a single data type for all of its elements.**

Our input contained:

- integers
- floating-point numbers

NumPy had to choose **one** data type.

Could it safely convert:

```text
3.5
```

into an integer?

No.

That would lose information.

However, it **can** safely convert:

```text
1
```

into:

```text
1.0
```

without changing its value.

Therefore, NumPy chooses the floating-point type.

---

# 🧠 Mental Model

Imagine you own a set of containers.

One container is designed for marbles.

Another is designed for tennis balls.

Now imagine you receive:

- two marbles,
- one tennis ball.

If you must place everything into **one kind of container**, which would you choose?

The larger container.

Every marble fits inside a tennis-ball container.

But a tennis ball cannot fit into a marble container.

NumPy follows the same logic.

It chooses the type capable of storing **all** values without losing information.

---

# 📖 Safe Conversion

This kind of automatic conversion is called **safe conversion** (or *safe casting*).

A safe conversion preserves the value.

For example:

```text
1
```

↓

```text
1.0
```

No information is lost.

But this conversion:

```text
3.5
```

↓

```text
3
```

would discard the decimal part.

That is **not** considered safe.

NumPy avoids unsafe conversions when inferring a data type.

---

# 🔬 Experiment Lab 05 — Mixing Integers and Booleans

Let's try something different.

📂 **Example:** `examples/chapter_05/05_integer_boolean.py`

```python
import numpy as np

values = np.array([True, False, 1, 0])

print(values)

print(values.dtype)
```

---

## 🧠 Prediction

What do you expect?

Will NumPy create:

- a Boolean array?
- an integer array?
- something else?

Think first.

Then run the code.

---

## ▶ Experiment

Expected output:

```text
[1 0 1 0]

int64
```

(On some systems, `int32`.)

Why?

Because in Python:

```python
True == 1

False == 0
```

Booleans can safely be represented as integers.

NumPy therefore promotes the array to an integer type.

---

# 👀 Did You Notice?

NumPy is not simply asking:

> "Which type appears most often?"

Instead, it asks a more important question:

> **"Which type can represent every value safely?"**

This is a subtle but extremely important distinction.

---

# ⚠️ Common Misconception

Many beginners think:

> "NumPy converts values randomly."

It doesn't.

NumPy follows well-defined promotion rules.

Whenever possible, it selects a type that can represent every element without losing information.

Later in the course, we'll study these promotion rules in much greater detail.

---

# 💻 Mini Challenge

Without running the code, predict the `dtype` for each array.

```python
np.array([5, 10.0])

np.array([True, 7])

np.array([False, 12.5])

np.array([0, 1, True])
```

Write down your predictions.

Then run the examples and compare the results.

Can you identify the pattern?

---

# 🧠 Brain Builder

Imagine NumPy always chose the **smallest** data type instead of the safest one.

What problems could occur?

Would mathematical calculations still be reliable?

Could values change unexpectedly?

Think about this before continuing.

---

# 📌 Key Takeaways (So Far)

You have learned that:

- NumPy can automatically convert compatible values.
- Arrays still use a single data type internally.
- NumPy prefers safe conversions over unsafe ones.
- Integers may become floating-point numbers.
- Booleans may become integers.
- Data type selection follows consistent promotion rules.

---

# 🔬 Experiment Lab 06 — What About Strings?

So far, we've mixed:

- integers,
- floating-point numbers,
- Booleans.

Now let's introduce something completely different:

**text**.

📂 **Example:** `examples/chapter_05/06_strings.py`

```python
import numpy as np

values = np.array([1, 2, "three"])

print(values)
print(values.dtype)
```

---

## 🧠 Prediction

Before running the program, think carefully.

Possible outcomes:

- NumPy raises an error.
- NumPy keeps integers and strings separate.
- NumPy converts everything to a single common type.

Which outcome do you expect?

Why?

---

## ▶ Experiment

Run the program.

You will see output similar to:

```text
['1' '2' 'three']

<U21
```

Your exact output may differ.

For example:

```text
<U5
```

or

```text
<U32
```

The important observation is **not the number**.

The important observation is that the array now stores **strings**.

The integers were converted into their textual representation.

---

# 📖 What Does `<U21` Mean?

This output may look confusing.

Let's break it down.

```
<
```

Represents the byte order (endianness) on your system.

For now, you don't need to worry about it.

```
U
```

Means:

> **Unicode string**

The number:

```
21
```

indicates the maximum number of Unicode characters allocated for each element in this particular array.

The exact value depends on the input data and your NumPy version.

For beginners, the key takeaway is simply:

> This is a string array.

We'll study NumPy's string data types in much greater detail later.

---

# 🧠 Mental Model

Imagine labeling storage boxes.

One box says:

```
Books
```

Another says:

```
Electronics
```

If someone hands you a printed label that says:

```
Laptop
```

it's easy to place it with the other labels.

Likewise, numbers can be converted into text:

```
1
```

↓

```
"1"
```

Once everything becomes text, every element follows the same rules.

---

# 📖 Explicitly Choosing a Data Type

Until now, NumPy has chosen the data type automatically.

But what if you want to make the decision yourself?

You can do that using the `dtype` parameter.

📂 **Example:** `examples/chapter_05/07_explicit_dtype.py`

```python
import numpy as np

numbers = np.array([1, 2, 3], dtype=float)

print(numbers)

print(numbers.dtype)
```

Output:

```text
[1. 2. 3.]

float64
```

Even though the input contained integers...

the resulting array stores floating-point numbers.

This is because we explicitly requested a floating-point data type.

---

# 💡 Function Reference — `np.array()`

## Purpose

Create a new NumPy array from an input sequence.

---

## Syntax

```python
np.array(object, dtype=None)
```

---

## Parameters

| Parameter | Description |
|-----------|-------------|
| `object` | Input data (list, tuple, another array, etc.) |
| `dtype` | Optional data type for the resulting array |

---

## Returns

An `ndarray`.

---

## Common Examples

```python
np.array([1, 2, 3])

np.array([1.5, 2.5])

np.array([True, False])

np.array(["A", "B"])

np.array([1, 2, 3], dtype=float)
```

---

## Common Mistakes

❌ Assuming every element can keep its own type.

❌ Assuming `dtype` always becomes `int64`.

❌ Forgetting that `dtype` can be specified explicitly.

---

# 🧠 Brain Builder

Suppose NumPy allowed every element to use an independent data type.

Ask yourself:

- Would arrays still have predictable memory layouts?
- Could vectorized operations remain as fast?
- Would indexing still be efficient?

Keep these questions in mind.

In future chapters, we'll answer them by exploring how arrays are stored in memory.

---

# 📌 Chapter Summary

Congratulations!

You have completed one of the most important conceptual chapters in this course.

You now understand that:

- every value has a data type,
- NumPy arrays are homogeneous,
- NumPy automatically infers a common data type,
- values may be converted to fit that common type,
- you can override the inferred type using the `dtype` parameter.

These ideas explain why NumPy arrays are both efficient and predictable.

---

# 💻 Practice Exercises

## Exercise 1

Create an integer array and print its `dtype`.

---

## Exercise 2

Create a floating-point array without using `dtype=`.

Verify the inferred type.

---

## Exercise 3

Create an integer array using:

```python
dtype=float
```

Inspect the result.

---

## Exercise 4

Create an array containing:

```python
[True, 5, 10]
```

Predict the resulting `dtype` before running the program.

---

## Exercise 5

Create an array containing:

```python
[1, "hello", 3]
```

Inspect the inferred type.

---

# ✅ Knowledge Check

Before continuing, make sure you can answer the following questions.

- What is a data type?
- Why does NumPy prefer homogeneous arrays?
- What is type inference?
- Why are integers sometimes converted into floating-point numbers?
- Why does `np.array([1, 2, 3], dtype=float)` produce floating-point values?
- Why might different computers display different integer types (`int32` vs `int64`)?

If you can confidently answer these questions, you're ready for the next lesson.

---

# 🚀 Looking Ahead

In the next chapter, we'll discover that `np.array()` is only **one** way to create arrays.

NumPy provides many specialized creation functions, including:

- `np.zeros()`
- `np.ones()`
- `np.empty()`
- `np.arange()`
- `np.linspace()`
- `np.full()`

Learning when to use each of these functions is one of the keys to writing clean and efficient NumPy code.