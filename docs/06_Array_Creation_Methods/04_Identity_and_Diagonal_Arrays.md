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

> **Continue with Part 2**, where we'll generate our first sequence using `np.linspace()` and compare it directly with `np.arange()`.