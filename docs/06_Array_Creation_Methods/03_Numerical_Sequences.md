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

> **Continue with Part 2**, where we'll generate our first numerical sequences using `np.arange()`.