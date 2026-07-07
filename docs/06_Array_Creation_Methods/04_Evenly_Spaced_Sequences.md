# 📘 Lesson 06.04 — Evenly Spaced Sequences with `np.linspace()`

> [!NOTE]
> **Difficulty:** 🟢 Beginner → 🟡 Intermediate
>
> **Reading Time:** ~30 minutes
>
> **Practice Time:** ~25 minutes
>
> **Prerequisites:**
>
> - Lesson 06.03 — Numerical Sequences with `np.arange()`

---

> *"Sometimes you don't care about the distance between values. You care about how many values you have."*

---

# ✅ Before You Continue

Before starting this lesson, make sure you understand:

- [ ] What `np.arange()` does.
- [ ] The meaning of start, stop, and step.
- [ ] Why the stop boundary is exclusive.
- [ ] Why floating-point steps may introduce precision issues.

---

# 🎯 Learning Objectives

By the end of this lesson you will:

- Understand why `np.linspace()` exists.
- Learn when `np.arange()` is not the best choice.
- Understand the concept of evenly spaced samples.
- Prepare for using `np.linspace()` in scientific computing.

---

# 🧠 Mental Model

Imagine you're organizing seats in a theater.

You don't say:

> "Place each chair exactly 83 centimeters apart."

Instead, you say:

> "I need exactly 20 chairs to fit between these two walls."

The spacing is calculated automatically.

That is exactly how `np.linspace()` thinks.

---

# 📖 The Limitation of `np.arange()`

Suppose you want numbers between:

```text
0
```

and

```text
100
```

You could write:

```python
np.arange(0, 100, 5)
```

But here's the problem.

How many numbers will this produce?

You need to calculate it yourself.

Sometimes that's easy.

Sometimes it isn't.

Especially when using decimal values.

---

# 🧠 A Different Question

Instead of asking:

> "How large should each step be?"

Imagine asking:

> "I need exactly 50 measurements."

Now the spacing is no longer your concern.

The computer can calculate it automatically.

This is the philosophy behind `np.linspace()`.

---

# 🌍 Real-World Example — Measuring Temperature

Imagine you're recording the temperature during one hour.

You want:

- the first measurement at the beginning,
- the last measurement exactly one hour later,
- **100 measurements in total**.

Do you really care about the exact spacing in minutes?

Not necessarily.

What matters is:

> I want exactly **100 samples**.

This is a perfect job for `np.linspace()`.

---

# 🌍 Another Example — Plotting a Graph

Suppose you want to draw the curve:

```text
y = sin(x)
```

between:

```text
0
```

and

```text
2π
```

Should you choose:

```text
Step = 0.03742...
```

Probably not.

Instead you simply decide:

> "Generate 1000 evenly spaced points."

Again,

this is exactly what `np.linspace()` was designed for.

---

# 💡 Did You Notice?

The most important change is not the function.

It is the question you ask.

With `np.arange()`:

> **How far should I move each time?**

With `np.linspace()`:

> **How many points do I want?**

The computer solves the rest.

---

# ⚠️ Common Misconception

Many beginners think:

> "`np.linspace()` is just another version of `np.arange()`."

It isn't.

The two functions solve different problems.

Sometimes they produce similar results.

But their design philosophy is fundamentally different.

---

# 🧠 Brain Builder

Imagine two engineers.

Engineer A says:

> "Move forward by exactly 2 centimeters each time."

Engineer B says:

> "Place exactly 51 equally spaced markers between these two points."

Both may create similar-looking results.

But are they describing the same process?

Think carefully before moving on.

---

# 📌 Key Takeaways (So Far)

You now know that:

- `np.arange()` focuses on the **step size**.
- `np.linspace()` focuses on the **number of samples**.
- Both generate sequences.
- They answer different questions.
- Choosing the right function depends on the problem you're solving.

---

---

# 📖 Meet `np.linspace()`

The general syntax is:

```python
np.linspace(start, stop, num)
```

Unlike `np.arange()`,

the third argument does **not** represent the step size.

Instead,

it represents:

> **The total number of values to generate.**

This is the key idea of `np.linspace()`.

---

# 🧠 Mental Model

Imagine you're building a bridge.

You know:

- where the bridge begins,
- where the bridge ends.

Now you decide:

> "I want exactly five support pillars."

You do **not** calculate where each pillar should stand.

Instead,

you let the engineer distribute them evenly.

This is exactly how `np.linspace()` works.

---

# 🔬 Experiment Lab 01 — Your First `linspace`

📂 **Example:** `examples/chapter_06/24_linspace_first.py`

```python
import numpy as np

arr = np.linspace(0, 10, 6)

print(arr)
```

---

## 🧠 Prediction

Before running the program:

- How many numbers will be generated?
- Will `10` appear?
- Will the spacing be equal?

Take a moment to think before executing.

---

## ▶ Experiment

Expected output:

```text
[ 0.  2.  4.  6.  8. 10.]
```

Interesting.

Unlike `np.arange()`,

the value:

```text
10
```

**is included.**

This is one of the biggest differences between the two functions.

---

# 📖 Breaking Down the Arguments

Let's examine each parameter.

```python
np.linspace(0, 10, 6)
```

| Argument | Meaning |
|----------|---------|
| `0` | Start value |
| `10` | Final value |
| `6` | Total number of samples |

Notice that we never specified a step size.

NumPy calculated it automatically.

---

# 🧠 Visualizing the Samples

```text
0 ---- 2 ---- 4 ---- 6 ---- 8 ---- 10
```

There are:

```text
6 samples
```

distributed evenly across the interval.

---

# 🔬 Experiment Lab 02 — Fewer Samples

📂 **Example:** `examples/chapter_06/25_linspace_three.py`

```python
import numpy as np

arr = np.linspace(0, 10, 3)

print(arr)
```

Expected output:

```text
[ 0.  5. 10.]
```

Again,

NumPy automatically chooses the spacing.

This time,

each interval is:

```text
5
```

instead of:

```text
2
```

because we requested fewer samples.

---

# 📖 The Computer Does the Math

Suppose you ask for:

```python
np.linspace(0, 1, 11)
```

NumPy reasons like this:

```text
Start = 0

Stop = 1

Need 11 values
```

There are:

```text
10 intervals
```

between:

```text
11 points
```

Therefore,

each interval must be:

```text
0.1
```

You never had to calculate that yourself.

---

# 💡 Did You Notice?

With `np.arange()`,

you choose:

```text
Step
```

and the number of generated values is determined automatically.

With `np.linspace()`,

you choose:

```text
Number of values
```

and the step is calculated automatically.

The responsibility shifts from the programmer to NumPy.

---

# ⚠️ Common Misconception

Many beginners think the third argument means:

```python
np.linspace(start, stop, step)
```

This is incorrect.

The third argument is **not** the step.

It is the **number of samples**.

For example:

```python
np.linspace(0, 100, 5)
```

does **not** mean:

```text
Step = 5
```

It means:

> Generate exactly **five values** between `0` and `100`.

---

# 💻 Mini Challenge

Predict the output.

```python
np.linspace(0, 20, 5)
```

---

```python
np.linspace(-1, 1, 5)
```

---

```python
np.linspace(100, 200, 3)
```

For each example, answer:

- What is the first value?
- What is the last value?
- How many samples were requested?
- What is the spacing?

---

# 🧠 Brain Builder

Suppose you need exactly:

```text
365
```

daily measurements across one year.

Would it be easier to think in terms of:

- the distance between measurements,

or

- the total number of measurements?

This is why scientists often prefer `np.linspace()`.

---

# 📌 Key Takeaways (So Far)

You now know that:

- `np.linspace()` generates evenly spaced values.
- The third argument specifies the **number of samples**.
- The start and stop values are both included by default.
- NumPy computes the spacing automatically.
- This is fundamentally different from `np.arange()`.

---

> **Continue with Part 3**, where we'll explore the `endpoint` parameter and learn how to include or exclude the final value.