# 📘 Lesson 06.05 — Choosing Between `np.arange()` and `np.linspace()`

> [!NOTE]
> **Difficulty:** 🟢 Beginner → 🟡 Intermediate
>
> **Reading Time:** ~25 minutes
>
> **Practice Time:** ~20 minutes
>
> **Prerequisites:**
>
> - Lesson 06.03 — `np.arange()`
> - Lesson 06.04 — `np.linspace()`

---

> *"Good programmers know many functions. Great programmers know when to use them."*

---

# 🎯 Learning Objectives

By the end of this lesson you will:

- Understand how to choose between `np.arange()` and `np.linspace()`.
- Learn to identify the underlying problem before writing code.
- Develop a practical decision-making process.
- Avoid common beginner mistakes.

---

# 📖 A Common Beginner Question

After learning both functions, many beginners ask:

> Which one is better?

At first, this seems like a reasonable question.

However, it is actually the wrong question.

Neither function is universally better.

Each was designed to solve a different type of problem.

The real question is:

> **What problem am I trying to solve?**

Once you answer that,

the correct function often becomes obvious.

---

# 🧠 Mental Model

Imagine you own two tools.

A hammer.

And a screwdriver.

Would you ask:

> Which tool is better?

Of course not.

The answer depends entirely on the task.

If you're driving a nail,

choose the hammer.

If you're tightening a screw,

choose the screwdriver.

The same principle applies to NumPy.

`np.arange()` and `np.linspace()` are different tools for different jobs.

---

# 📖 Thinking Before Coding

Many beginners immediately think about syntax.

For example:

```python
np.arange(...)

np.linspace(...)
```

Experienced programmers think differently.

Before touching the keyboard, they ask:

> What information do I already know?

This single question often determines which function should be used.

---

# 🧩 Scenario 1 — You Know the Step Size

Suppose you're creating timestamps every:

```text
15 minutes
```

What information do you already know?

You know the spacing.

You want every value to be exactly:

```text
15 minutes apart.
```

The number of timestamps is not your primary concern.

In this situation,

the natural choice is:

```python
np.arange()
```

Because the step size is already known.

---

# 🧩 Scenario 2 — You Know the Number of Samples

Now imagine you're performing a scientific experiment.

You need:

```text
1000 measurements
```

between two temperatures.

Do you care about the exact spacing?

Usually not.

Your experiment requires:

```text
Exactly 1000 samples.
```

The spacing should simply be uniform.

This is the perfect job for:

```python
np.linspace()
```

---

# 🌍 Real-World Example — Plotting a Graph

Suppose you want to plot:

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

Would you calculate a step manually?

Probably not.

Instead,

you simply decide:

> I want a smooth graph.

A common solution is:

```python
np.linspace(0, 2 * np.pi, 1000)
```

The graph becomes smooth because you requested many evenly spaced samples.

---

# 🌍 Another Example — Counting

Suppose you're assigning seat numbers.

```text
1

2

3

4

5
```

Each seat number increases by:

```text
1
```

You know the increment.

You don't begin by asking:

> How many seat numbers will exist?

Instead,

you generate them one step at a time.

This naturally leads to:

```python
np.arange()
```

---

# 💡 Did You Notice?

The decision has nothing to do with NumPy itself.

It depends on the information you already have.

Ask yourself:

> Do I know the spacing?

or

> Do I know the number of samples?

That answer determines the function.

---

# ⚠️ Common Misconception

Some beginners try to solve every sequence generation problem with a single function.

For example,

they always use:

```python
np.arange()
```

or always use:

```python
np.linspace()
```

Both approaches work sometimes.

Neither works well all the time.

Good programmers choose the right tool for the problem.

---

# 🧠 Brain Builder

Imagine you are designing a GPS navigation system.

Which question sounds more natural?

> Generate positions every 5 meters.

or

> Generate exactly 500 positions along this road.

Would both produce the same result?

Would one description be easier to work with?

Think about how the available information changes the solution.

---

# 📌 Key Takeaways (So Far)

You now know that:

- Neither function is "better."
- Each function solves a different problem.
- The correct choice depends on the information available.
- Think about the problem before thinking about the syntax.
- Choosing the right tool is an essential programming skill.

---

# 📖 One Problem, Two Solutions

Now that we understand the philosophy behind both functions,

let's solve the **same problem** twice.

Our goal is not to decide which solution is better.

Our goal is to understand **why each solution was designed differently.**

---

# 🎯 The Problem

Suppose we want to generate values between:

```text
0
```

and

```text
10
```

There are at least two possible approaches.

Let's explore both.

---

# 🔬 Solution A — Thinking in Steps

📂 **Example:** `examples/chapter_06/32_compare_arange.py`

```python
import numpy as np

values = np.arange(0, 10, 2)

print(values)
```

Output:

```text
[0 2 4 6 8]
```

Let's examine what happened.

We explicitly told NumPy:

- Start at `0`
- Move by `2`
- Stop before `10`

NumPy simply followed those instructions.

---

# 🧠 How `arange()` Thinks

Internally, the process looks like this.

```text
Current value = 0

↓

Add 2

↓

2

↓

Add 2

↓

4

↓

Add 2

↓

6

↓

Add 2

↓

8

↓

Next value would be 10

↓

Stop
```

Notice something important.

The programmer decided:

```text
Step = 2
```

The total number of values was simply a consequence of that decision.

---

# 🔬 Solution B — Thinking in Samples

Now let's solve the same task differently.

📂 **Example:** `examples/chapter_06/33_compare_linspace.py`

```python
import numpy as np

values = np.linspace(0, 10, 6)

print(values)
```

Output:

```text
[ 0.  2.  4.  6.  8. 10.]
```

This time,

we never mentioned the spacing.

Instead,

we asked for:

```text
Exactly six samples.
```

NumPy calculated everything else.

---

# 🧠 How `linspace()` Thinks

Its reasoning is completely different.

```text
Start = 0

↓

Stop = 10

↓

Need 6 samples

↓

5 equal intervals

↓

Interval size = 2

↓

Generate the samples
```

Notice the difference.

The spacing was **calculated**, not specified.

---

# 📊 Side-by-Side Comparison

| Question | `np.arange()` | `np.linspace()` |
|-----------|---------------|-----------------|
| What do you provide? | Step size | Number of samples |
| What does NumPy calculate? | Number of values | Step size |
| Is the endpoint included? | No | Yes (default) |
| Best for | Counting | Sampling |

Although both examples produced similar sequences,

they answered different questions.

---

# 🌍 Real-World Scenario — Elevator Floors

Imagine programming an elevator.

It stops at every floor.

```text
Ground

↓

1

↓

2

↓

3

↓

4
```

The distance between floors is fixed.

You naturally think in **steps**.

This is a perfect match for:

```python
np.arange()
```

---

# 🌍 Real-World Scenario — Measuring a River

Now imagine measuring the depth of a river.

You want:

```text
100 equally spaced measurements
```

from one bank to the other.

You don't care whether the spacing is:

```text
0.73 meters
```

or

```text
0.728 meters.
```

You simply need exactly:

```text
100 samples.
```

This is the natural domain of:

```python
np.linspace()
```

---

# 💡 Did You Notice?

Both functions create sequences.

But they begin with different assumptions.

`np.arange()` assumes:

> "The spacing is important."

`np.linspace()` assumes:

> "The number of samples is important."

Neither assumption is universally better.

The correct choice depends entirely on the problem.

---

# ⚠️ Common Misconception

A common beginner habit is to convert one solution into the other.

For example,

using:

```python
np.linspace()
```

even when the step size is already known,

or forcing:

```python
np.arange()
```

to produce an exact number of samples.

While this is sometimes possible,

it usually makes the code harder to understand.

Write code that reflects your intent.

Future readers—including your future self—will thank you.

---

# 💻 Mini Challenge

For each situation,

choose the most appropriate function.

Do **not** write code yet.

Simply explain your choice.

---

Generate page numbers.

---

Generate exactly 500 x-values for plotting.

---

Generate timestamps every hour.

---

Generate 200 evenly distributed simulation points.

---

Generate array indices.

---

Generate every fifth element of a sequence.

---

# 🧠 Design Thinking

Before writing any sequence generation code,

ask yourself these questions.

1. What information do I already know?

---

2. Is the spacing fixed?

---

3. Is the number of samples fixed?

---

4. Which choice makes the code easier to understand?

Experienced programmers often spend more time answering these questions than writing the actual code.

---

# 📌 Key Takeaways (So Far)

You now know that:

- The same problem can often be solved in different ways.
- `np.arange()` expresses movement through fixed steps.
- `np.linspace()` expresses distribution through fixed samples.
- Good code communicates intent.
- Choosing the right function improves readability as well as correctness.

---

> **Continue with Part 3**, where we'll examine common beginner mistakes and learn how to recognize them before they become bugs.