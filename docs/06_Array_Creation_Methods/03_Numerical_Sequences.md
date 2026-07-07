# 📘 Lesson 06.03 — Numerical Sequences

> [!NOTE]
> **Difficulty:** 🟢 Beginner
>
> **Reading Time:** ~30 minutes
>
> **Practice Time:** ~20 minutes
>
> **Prerequisites:**
>
> - Lesson 06.01 — Creating Arrays from Existing Data
> - Lesson 06.02 — Filled Arrays

---

> *"Before NumPy can generate numbers, you need to understand what a numerical sequence really is."*

---

# ✅ Before You Continue

Before starting this lesson, make sure you can:

- [ ] Create arrays using `np.array()`
- [ ] Create arrays using `np.zeros()`
- [ ] Create arrays using `np.ones()`
- [ ] Explain what the `shape` of an array means

---

# 🎯 Learning Objectives

By the end of this lesson you will:

- Understand what a numerical sequence is.
- Learn the concepts of **start**, **stop**, and **step**.
- Recognize patterns in numerical data.
- Prepare for using `np.arange()` and `np.linspace()`.

---

# 🧠 Mental Model

Imagine you're climbing a staircase.

Every step moves you upward by the same distance.

```text
0

↓

1

↓

2

↓

3

↓

4

↓

5
```

This is a numerical sequence.

Every value follows a rule.

The rule here is simple:

> Add **1** every time.

A numerical sequence is simply a collection of values generated according to a predictable pattern.

---

# 📖 What Is a Numerical Sequence?

A **numerical sequence** is an ordered collection of numbers.

The numbers appear in a specific order because they follow a rule.

For example:

```text
1 2 3 4 5
```

Rule:

> Add **1**.

---

Another example:

```text
0 5 10 15 20
```

Rule:

> Add **5**.

---

Another example:

```text
10 8 6 4 2 0
```

Rule:

> Subtract **2**.

---

Notice something important.

The numbers themselves are less important than the rule that generates them.

---

# 🧠 Patterns Are Everywhere

Numerical sequences appear in far more places than mathematics.

For example:

### 📅 Calendar Days

```text
1

2

3

4

5
```

---

### ⏱ Seconds

```text
0

1

2

3

4
```

---

### 📈 Stock Prices (Simplified)

```text
100

105

110

115
```

---

### 🌡 Temperature Measurements

```text
20.0

20.5

21.0

21.5
```

---

### 🎮 Game Levels

```text
1

2

3

4

...
```

Whenever values follow a predictable progression,

you're looking at a sequence.

---

# 📖 The Four Building Blocks of a Sequence

Almost every sequence can be described using four ideas.

---

## 1️⃣ Start

Where does the sequence begin?

Example:

```text
10 11 12 13
```

Start:

```text
10
```

---

## 2️⃣ Stop

Where does the sequence end?

Example:

```text
10 11 12 13
```

Last value:

```text
13
```

In programming, however, things are often a little different.

Many functions define a **stop boundary**, not necessarily the final value that appears.

We'll see this shortly when we study `np.arange()`.

---

## 3️⃣ Step

How much do we move each time?

Example:

```text
2 4 6 8 10
```

Step:

```text
+2
```

Another example:

```text
20 15 10 5
```

Step:

```text
-5
```

Steps can be:

- positive,
- negative,
- or even decimal values.

---

## 4️⃣ Length

How many numbers does the sequence contain?

Example:

```text
0 2 4 6 8
```

Length:

```text
5
```

Sometimes we care about:

- the spacing,

sometimes about:

- the number of values.

This distinction is one of the biggest differences between `np.arange()` and `np.linspace()`.

---

# 🔬 Experiment Lab 01

Consider the sequence:

```text
5 10 15 20 25
```

Can you identify:

- Start?
- Stop?
- Step?
- Length?

Answer:

| Property | Value |
|----------|------:|
| Start | 5 |
| Last Value | 25 |
| Step | 5 |
| Length | 5 |

---

# 🧠 Brain Builder

Without writing any Python code, analyze these sequences.

### Sequence A

```text
3 6 9 12 15
```

---

### Sequence B

```text
100 90 80 70
```

---

### Sequence C

```text
0.0 0.5 1.0 1.5 2.0
```

For each sequence, determine:

- Start
- Last Value
- Step
- Length

If you can do this confidently,

you already understand the ideas behind most NumPy sequence-generation functions.

---

# 💡 Did You Notice?

At this point,

we haven't used NumPy at all.

That's intentional.

Understanding the underlying mathematical concepts first makes the NumPy functions much easier to learn.

Rather than memorizing function parameters,

you'll understand what those parameters represent.

---

# ⚠️ Common Misconception

Many beginners believe that generating a sequence simply means:

> "Create some consecutive numbers."

In reality,

a sequence is defined by its rule.

The numbers are merely the result of applying that rule repeatedly.

---

# 📌 Key Takeaways (So Far)

You have learned that:

- A numerical sequence follows a predictable rule.
- Every sequence has a beginning.
- Every sequence progresses using a step.
- Every sequence has a length.
- Understanding sequences is essential before learning `np.arange()` and `np.linspace()`.

---

# 📖 The Problem

Suppose you need the following numbers:

```text
0 1 2 3 4 5 6 7 8 9
```

One solution would be to type them manually.

```python
numbers = np.array([
    0, 1, 2, 3, 4,
    5, 6, 7, 8, 9
])
```

This works.

But imagine needing:

- the first 100 numbers,
- the first 10,000 numbers,
- the first 1,000,000 numbers.

Typing every value manually would be impossible.

We need a better solution.

---

# 🧠 Mental Model

Imagine asking a friend:

> "Please count from 0 to 9."

You wouldn't expect them to memorize a list.

Instead, they would follow a simple rule.

```text
Start at 0

↓

Say the current number

↓

Add 1

↓

Repeat
```

This is exactly what `np.arange()` does.

Instead of receiving every value individually,

it receives a rule for generating them.

---

# 📖 Meet `np.arange()`

The simplest form is:

```python
np.arange(stop)
```

Let's see it in action.

📂 **Example:** `examples/chapter_06/17_arange_stop.py`

```python
import numpy as np

arr = np.arange(10)

print(arr)
```

---

## 🧠 Prediction

Before running the program:

- How many numbers will be generated?
- What will the first number be?
- What will the last number be?

Think carefully before executing.

---

## ▶ Experiment

Expected output:

```text
[0 1 2 3 4 5 6 7 8 9]
```

Excellent.

Notice something surprising.

Although we wrote:

```python
10
```

the number **10** does **not** appear.

Why?

Let's investigate.

---

# 📖 Understanding the Stop Boundary

The argument:

```python
10
```

does **not** mean:

> "Generate numbers including 10."

Instead, it means:

> "Generate numbers until you reach 10."

The value:

```text
10
```

acts as a boundary.

It is **excluded** from the result.

You can think of it like a finish line.

When the sequence reaches the finish line,

it stops.

It does not cross it.

---

# 🧠 Visualizing the Boundary

```text
0   1   2   3   4   5   6   7   8   9 | 10
↑--------------------------------------↑
Generated values                    Stop boundary
```

Everything before the boundary appears.

The boundary itself does not.

---

# 🔬 Experiment Lab 02

Predict the output before running each example.

```python
np.arange(3)
```

---

```python
np.arange(5)
```

---

```python
np.arange(1)
```

Now verify your answers.

Expected outputs:

```text
[0 1 2]
```

---

```text
[0 1 2 3 4]
```

---

```text
[0]
```

Can you identify the pattern?

---

# 💡 Did You Notice?

Whenever you call:

```python
np.arange(n)
```

NumPy always begins at:

```text
0
```

The only thing you specify is where the sequence should stop.

This makes the one-argument form perfect for creating index values.

For example:

```python
for i in np.arange(5):
    print(i)
```

Output:

```text
0
1
2
3
4
```

Although Python programmers would normally write:

```python
for i in range(5):
```

this example illustrates that `np.arange()` follows the same basic idea: a start value (defaulting to `0`), a stop boundary, and a step (defaulting to `1`).

---

# ⚠️ Common Misconception

Many beginners expect:

```python
np.arange(10)
```

to produce:

```text
0 1 2 3 4 5 6 7 8 9 10
```

This is incorrect.

The stop value is **exclusive**.

This design matches many parts of Python,

including:

- slicing,
- `range()`,
- indexing conventions.

Learning this rule now will make many future topics easier.

---

# 🧠 Brain Builder

Suppose NumPy included the stop value.

Imagine:

```python
np.arange(10)
```

returned:

```text
0 1 2 3 4 5 6 7 8 9 10
```

How many elements would the array contain?

Would that match the value passed to the function?

Can you see why an exclusive stop boundary often leads to more predictable code?

---

# 📌 Key Takeaways (So Far)

You now know that:

- `np.arange(stop)` generates a sequence starting at `0`.
- The stop value is **not included**.
- The stop argument defines a boundary, not the final element.
- This behavior is consistent with Python's `range()` and slicing rules.

---

# 📖 Beyond the Simplest Form

In the previous lesson, we learned that:

```python
np.arange(10)
```

creates:

```text
[0 1 2 3 4 5 6 7 8 9]
```

This works because NumPy assumes two default values:

- **Start:** `0`
- **Step:** `1`

Only the stop boundary was specified.

But what if we want the sequence to begin somewhere else?

Or skip numbers?

For that, NumPy provides a more general form.

---

# 📖 The General Syntax

```python
np.arange(start, stop, step)
```

Each argument has a specific purpose.

| Parameter | Meaning |
|-----------|---------|
| `start` | First value in the sequence |
| `stop` | Stop boundary (excluded) |
| `step` | Amount added after each value |

Think of these as the three instructions NumPy follows.

---

# 🧠 Mental Model

Imagine you're walking along a number line.

First, decide where to stand.

```text
Start
```

Next, decide how far each step should be.

```text
Step
```

Finally, decide where the invisible wall is.

```text
Stop boundary
```

You keep walking until the next step would cross the wall.

Then you stop.

---

# 🔬 Experiment Lab 03 — Choosing the Starting Point

📂 **Example:** `examples/chapter_06/18_arange_start_stop.py`

```python
import numpy as np

arr = np.arange(5, 10)

print(arr)
```

---

## 🧠 Prediction

Before running the code:

- What will the first value be?
- Will `10` appear?
- How many elements do you expect?

---

## ▶ Experiment

Expected output:

```text
[5 6 7 8 9]
```

Notice:

The sequence begins at:

```text
5
```

but still stops **before** `10`.

The stop boundary rule has not changed.

---

# 📖 Understanding the Result

Let's analyze the sequence.

```text
5 6 7 8 9
```

| Property | Value |
|----------|------:|
| Start | 5 |
| Stop Boundary | 10 |
| Step | 1 |

NumPy repeatedly adds:

```text
+1
```

until the next value would reach the stop boundary.

---

# 🔬 Experiment Lab 04 — Changing the Step Size

Now let's skip every other number.

📂 **Example:** `examples/chapter_06/19_arange_step.py`

```python
import numpy as np

arr = np.arange(0, 10, 2)

print(arr)
```

Expected output:

```text
[0 2 4 6 8]
```

Let's examine what happened.

Instead of adding:

```text
+1
```

NumPy now adds:

```text
+2
```

after every value.

---

# 🧠 Visualizing the Steps

```text
0

↓

2

↓

4

↓

6

↓

8

↓

10 ✖
```

The next value would be:

```text
10
```

But that's the stop boundary.

So it is not included.

---

# 🔬 Experiment Lab 05 — Larger Steps

Predict the output.

```python
np.arange(10, 31, 5)
```

Run the program.

Expected output:

```text
[10 15 20 25 30]
```

Notice something interesting.

The value:

```text
30
```

appears.

Why?

Because it is **before** the stop boundary:

```text
31
```

The stop boundary itself remains excluded.

---

# 💡 Did You Notice?

Changing the step changes:

- how many numbers are generated,
- how quickly the sequence grows.

It does **not** change the meaning of the stop boundary.

That rule is always the same.

---

# ⚠️ Common Misconception

Some beginners believe that:

```python
np.arange(0, 10, 2)
```

means:

> "Generate five numbers."

It doesn't.

It means:

> "Start at 0.
>
> Add 2 repeatedly.
>
> Stop before reaching 10."

The number of elements is simply the result of those rules.

---

# 💻 Mini Challenge

Predict each output before running the code.

```python
np.arange(2, 8)
```

---

```python
np.arange(2, 12, 3)
```

---

```python
np.arange(100, 106)
```

---

```python
np.arange(-5, 6)
```

For each sequence, identify:

- Start
- Stop Boundary
- Step
- Length

---

# 🧠 Brain Builder

Imagine NumPy asked for the arguments in a different order:

```python
np.arange(step, start, stop)
```

Would that feel natural?

Why do you think the designers chose:

```python
(start, stop, step)
```

instead?

Think about how humans usually describe a journey.

We naturally answer:

1. Where do we begin?
2. Where do we stop?
3. How fast do we move?

The function signature mirrors that way of thinking.

---

# 📌 Key Takeaways (So Far)

You now know that:

- `np.arange(start, stop)` changes where the sequence begins.
- `step` controls the spacing between values.
- The stop boundary is always excluded.
- The number of generated values depends on all three parameters working together.

---

> **Continue with Part 4**, where we'll generate descending sequences using negative step values and explore edge cases.