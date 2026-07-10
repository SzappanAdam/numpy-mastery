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

# 📖 Learning from Mistakes

Making mistakes is a natural part of learning.

In fact,

many programming concepts become truly clear only after seeing what can go wrong.

In this section,

we'll explore some of the most common beginner mistakes when choosing between:

- `np.arange()`
- `np.linspace()`

More importantly,

we'll learn **why** they happen and how to avoid them.

---

# ❌ Mistake 1 — Expecting `np.arange()` to Include the Stop Value

Consider the following code.

```python
import numpy as np

values = np.arange(0, 10, 2)

print(values)
```

Output:

```text
[0 2 4 6 8]
```

Many beginners expect:

```text
[0 2 4 6 8 10]
```

Why doesn't `10` appear?

Because `np.arange()` always treats the stop value as an **exclusive boundary**.

The sequence stops **before** reaching the stop value.

---

## ✅ Correct Mental Model

Think of the stop value as a fence.

```text
0 ---- 2 ---- 4 ---- 6 ---- 8 | 10
                               ↑
                           Boundary
```

The sequence may approach the fence,

but it never crosses or stands on it.

---

# ❌ Mistake 2 — Misunderstanding the Third Argument of `np.linspace()`

Look at this example.

```python
np.linspace(0, 100, 5)
```

Some beginners think:

```text
Step = 5
```

This is incorrect.

The third argument represents:

```text
Number of samples
```

The correct output is:

```text
[  0.  25.  50.  75. 100.]
```

NumPy calculated the spacing automatically.

---

## ✅ Correct Mental Model

Remember:

```text
arange()

↓

step
```

```text
linspace()

↓

samples
```

If you remember only this distinction,

you'll avoid one of the most common beginner mistakes.

---

# ❌ Mistake 3 — Using `np.arange()` for Exact Floating-Point Sampling

Suppose you write:

```python
np.arange(0, 1, 0.1)
```

At first glance,

this seems perfectly reasonable.

However,

floating-point numbers cannot always be represented exactly in binary.

As a result,

small rounding errors may accumulate.

Although the output often looks correct,

the underlying values may not be mathematically exact.

---

## ✅ Better Choice

If your goal is:

> Generate an exact number of evenly spaced samples across an interval.

Prefer:

```python
np.linspace(0, 1, 11)
```

This communicates your intention more clearly

and usually produces more predictable results for numerical work.

---

# ❌ Mistake 4 — Choosing the Wrong Tool

Imagine you need exactly:

```text
500 samples
```

between two values.

Some beginners still try to use:

```python
np.arange()
```

Then they spend time adjusting the step size,

checking the output,

and repeating the process.

The code becomes more complicated than necessary.

Instead,

simply write:

```python
np.linspace(start, stop, 500)
```

The code immediately expresses your intent.

---

# ❌ Mistake 5 — Choosing a Function Based on Habit

After learning a new function,

it's tempting to use it everywhere.

For example,

some programmers always write:

```python
np.linspace(...)
```

even when they simply need:

```text
0

1

2

3

4
```

Others always use:

```python
np.arange(...)
```

even for scientific sampling.

Neither habit is ideal.

Choose the function that best matches the problem.

---

# 🌍 Real-World Analogy

Imagine you're packing for a trip.

You own:

- hiking boots,
- running shoes,
- formal shoes.

Would you always wear the same pair,

regardless of where you're going?

Of course not.

Each shoe has a purpose.

Programming tools work the same way.

---

# 💡 Did You Notice?

None of these mistakes involve complicated mathematics.

They all come from misunderstanding the purpose of each function.

Learning the philosophy behind the tools is just as important as learning their syntax.

---

# 💻 Mini Challenge

For each statement,

decide whether it is **True** or **False**.

---

`np.arange()` includes the stop value.

---

The third argument of `np.linspace()` is the step size.

---

`np.linspace()` is usually a better choice when the number of samples is known.

---

`np.arange()` is well suited for generating integer indices.

---

Using the same function for every sequence generation task is good programming practice.

---

# 🧠 Design Thinking

Whenever you're unsure which function to use,

pause for a moment and ask:

> What information is fixed?

If the spacing is fixed,

choose:

```python
np.arange()
```

If the number of samples is fixed,

choose:

```python
np.linspace()
```

This simple habit prevents many common mistakes.

---

# 📌 Key Takeaways (So Far)

You now know that:

- `np.arange()` excludes the stop value.
- The third argument of `np.linspace()` is the number of samples.
- Floating-point sampling often favors `np.linspace()`.
- The best function depends on the problem, not personal preference.
- Understanding intent helps prevent programming mistakes.

---

# 📖 From Knowledge to Decision Making

By now, you understand what both functions do.

You also know their strengths and limitations.

The next step is learning how to make the right decision quickly.

Experienced programmers rarely memorize rules.

Instead, they develop simple decision frameworks.

These frameworks reduce uncertainty and make code more consistent.

---

# 🧠 The Four Questions

Whenever you need to generate a numerical sequence, ask yourself these four questions.

---

## Question 1

> **Do I know the distance between consecutive values?**

For example:

- Every 5 minutes
- Every 10 centimeters
- Every 2 pixels
- Every integer

If your answer is **yes**, you're already thinking in terms of a **step size**.

That strongly suggests using:

```python
np.arange()
```

---

## Question 2

> **Do I know exactly how many values I need?**

Examples:

- 100 measurements
- 500 simulation points
- 1000 x-values for plotting
- 365 daily observations

If the number of values is fixed,

you're thinking in terms of **samples**.

This naturally suggests:

```python
np.linspace()
```

---

## Question 3

> **Does the final value matter?**

Sometimes the endpoint is important.

Examples include:

- Measuring from 0°C to exactly 100°C
- Plotting a graph over a closed interval
- Sampling the complete duration of an experiment

In these situations,

including the endpoint is often desirable.

`np.linspace()` does this by default.

---

Sometimes the endpoint should **not** be included.

Examples:

- Looping animations
- Circular angles
- Repeating patterns
- Periodic signals

Here,

excluding the endpoint avoids duplicate values.

```python
np.linspace(..., endpoint=False)
```

---

## Question 4

> **Am I working with integers or continuous values?**

Integer-based tasks often involve:

- indices,
- counters,
- identifiers,
- positions in arrays.

These are natural applications for:

```python
np.arange()
```

Continuous quantities often involve:

- time,
- distance,
- temperature,
- probability,
- mathematical functions.

These frequently benefit from:

```python
np.linspace()
```

---

# 📊 The Decision Flow

```
Start

↓

Do you know the step size?

│

├── Yes
│
│     ↓
│
│  Use np.arange()

│

└── No

      ↓

Do you know the number of samples?

│

├── Yes
│
│     ↓
│
│  Use np.linspace()

│

└── No

      ↓

Reconsider the problem.

You may not yet have enough information.
```

This simple framework solves the majority of sequence generation tasks.

---

# 🌍 Scenario 1 — Image Processing

You are processing pixels.

Every fifth pixel should be selected.

Known information:

- Fixed spacing.

Recommended function:

```python
np.arange()
```

---

# 🌍 Scenario 2 — Scientific Experiment

You must record exactly:

```text
250 observations
```

between two temperatures.

Known information:

- Number of samples.

Recommended function:

```python
np.linspace()
```

---

# 🌍 Scenario 3 — Creating Tick Marks on a Plot

You want exactly:

```text
11 tick marks
```

between:

```text
0
```

and

```text
100
```

Known information:

- Number of ticks.

Recommended function:

```python
np.linspace()
```

---

# 🌍 Scenario 4 — Iterating Through Rows

You want every row index.

Known information:

- Integer increments.

Recommended function:

```python
np.arange()
```

---

# 💡 Why This Framework Works

Notice that none of the questions ask:

> Which function do I remember?

Instead,

they ask:

> What information do I already have?

This is a subtle but important shift in thinking.

You're no longer choosing a function.

You're describing the problem.

The function follows naturally.

---

# ⚠️ Why Not...?

Suppose you need exactly:

```text
1000 samples
```

Could you use:

```python
np.arange()
```

Yes.

But first you would have to calculate the correct step size.

That adds unnecessary complexity.

Now consider the opposite.

Suppose you need values every:

```text
5 seconds.
```

Could you use:

```python
np.linspace()
```

Yes.

But now you would first need to calculate how many samples are required.

Again,

you're solving an extra problem before solving the real one.

The best code avoids unnecessary calculations.

---

# 💻 Mini Challenge

For each situation,

choose the most appropriate function and explain **why**.

---

Generate every tenth page number.

---

Generate exactly 1000 x-values for a graph.

---

Generate timestamps every hour for one week.

---

Generate 50 evenly distributed probability values.

---

Generate array indices from 0 to 99.

---

Generate 360 evenly spaced angles around a circle, excluding the duplicate endpoint.

---

# 🧠 Design Thinking

Professional programmers often follow this sequence:

1. Understand the problem.
2. Identify the known information.
3. Choose the most appropriate abstraction.
4. Write the code.

Notice that writing code is the **last** step, not the first.

---

# 📌 Key Takeaways (So Far)

You now know that:

- Good decisions begin with understanding the problem.
- Step size naturally leads to `np.arange()`.
- Number of samples naturally leads to `np.linspace()`.
- The endpoint may or may not be part of the solution.
- Simple decision frameworks reduce programming mistakes.

---

# 📖 Applying What You've Learned

Understanding a concept is one thing.

Applying it to real-world situations is another.

In this lesson,

you'll analyze practical scenarios and decide which function best fits each problem.

The goal is not simply to choose the correct function.

The goal is to explain **why** your choice makes sense.

---

# 🧩 Case Study 1 — Plotting a Mathematical Function

You are writing a program that plots:

```text
y = x²
```

for values between:

```text
-10
```

and

```text
10
```

You want the graph to look smooth.

### Available Information

- Start value: known
- Stop value: known
- Desired number of points: 1000

---

## Analysis

The exact spacing is not important.

What matters is generating enough points to produce a smooth curve.

---

## Recommended Solution

```python
import numpy as np

x = np.linspace(-10, 10, 1000)
```

### Why?

Because the problem is defined by the **number of samples**, not the spacing.

---

# 🧩 Case Study 2 — Processing Log Files

Suppose a server records data every:

```text
5 minutes
```

You need to generate timestamps.

### Available Information

- Step size is fixed.
- Number of timestamps is unknown.

---

## Recommended Solution

```python
import numpy as np

minutes = np.arange(0, 60, 5)
```

### Why?

The interval between measurements is fixed.

This naturally suggests `np.arange()`.

---

# 🧩 Case Study 3 — Creating Image Coordinates

Imagine generating pixel positions.

Every coordinate should increase by:

```text
1 pixel
```

### Available Information

- Integer increments.
- Fixed spacing.

---

## Recommended Solution

```python
x = np.arange(0, 1920)
```

### Why?

Pixel positions are discrete integer values.

The spacing is known in advance.

---

# 🧩 Case Study 4 — Scientific Simulation

You are simulating an experiment.

The simulation requires exactly:

```text
5000 samples
```

between:

```text
0
```

and

```text
1
```

---

## Recommended Solution

```python
samples = np.linspace(0, 1, 5000)
```

### Why?

The number of samples is fixed.

The spacing should be computed automatically.

---

# 🧩 Case Study 5 — Circular Motion

You are generating angles around a full circle.

The first angle is:

```text
0°
```

The last angle would normally be:

```text
360°
```

However,

those two angles represent the same direction.

---

## Recommended Solution

```python
angles = np.linspace(
    0,
    360,
    360,
    endpoint=False
)
```

### Why?

Including both `0°` and `360°` would duplicate the starting position.

Using `endpoint=False` avoids this problem.

---

# 🧩 Case Study 6 — Array Indexing

Suppose an array contains:

```text
250 elements
```

You need to generate every valid index.

---

## Recommended Solution

```python
indices = np.arange(250)
```

### Why?

Array indices increase by one.

The spacing is fixed.

---

# 📊 Summary Table

| Scenario | Recommended Function | Primary Reason |
|----------|----------------------|----------------|
| Plotting graphs | `np.linspace()` | Fixed number of samples |
| Scientific simulations | `np.linspace()` | Fixed number of samples |
| Temperature measurements | `np.linspace()` | Even sampling |
| Time intervals | `np.arange()` | Fixed step size |
| Array indices | `np.arange()` | Integer increments |
| Pixel coordinates | `np.arange()` | Known spacing |
| Circular sampling | `np.linspace(endpoint=False)` | Avoid duplicate endpoint |

---

# ⚠️ Why Not...?

Let's revisit one example.

Suppose you need:

```text
1000 plotting points.
```

Could you use:

```python
np.arange()
```

Yes.

But first,

you would need to calculate the exact spacing.

That introduces unnecessary work.

Now consider timestamps every:

```text
30 seconds.
```

Could you use:

```python
np.linspace()
```

Again,

yes.

But first,

you must determine how many timestamps will exist.

The code becomes less direct.

Choose the function that matches the information you already know.

---

# 💻 Practice Challenge

For each situation,

answer the following questions.

1. Which function would you choose?
2. Why?
3. Which information is fixed?
4. Would the endpoint matter?

---

Generate every:

```text
2 centimeters
```

along a ruler.

---

Generate exactly:

```text
365 daily observations.
```

---

Generate:

```text
1000 x-values
```

for plotting.

---

Generate integer IDs from:

```text
1000
```

to

```text
1999.
```

---

Generate:

```text
720 angles
```

for a rotating animation.

---

# 🧠 Design Thinking

Professional developers don't memorize examples.

They recognize patterns.

When you encounter a new problem,

ask yourself:

- Have I seen a similar situation before?
- Is this fundamentally a spacing problem?
- Or is it fundamentally a sampling problem?

Pattern recognition is one of the most valuable programming skills you can develop.

---

# 📌 Key Takeaways (So Far)

You now know that:

- Real-world problems naturally suggest one function over the other.
- The correct choice depends on the available information.
- Similar-looking sequences may be generated for completely different reasons.
- Good programmers explain **why** they selected a solution.
- Recognizing patterns is more valuable than memorizing code.

---

> **Continue with Part 6**, where you'll complete this lesson with a comprehensive summary, mastery checklist, and practical exercises to reinforce everything you've learned.