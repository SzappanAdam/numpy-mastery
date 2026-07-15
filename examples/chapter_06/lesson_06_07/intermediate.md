# 📘 Chapter 06 — Chapter Exercises

## Part 2 — Intermediate Exercises

> [!NOTE]
> **Difficulty:** 🟡 Intermediate
>
> **Estimated Time:** 45–60 minutes
>
> In this section, you'll combine multiple concepts from Chapter 06.
> The focus is no longer on remembering function syntax, but on selecting the most appropriate tool for each task.

---

# 🎯 Objectives

By the end of this exercise set, you should be able to:

- Combine different array creation functions.
- Choose the correct function based on the problem.
- Create multidimensional arrays.
- Build arrays that could realistically appear in scientific or data analysis workflows.
- Explain your design decisions.

---

# 📋 Exercise 1 — Classroom Grades

A teacher wants to prepare a grade sheet for 30 students.

### Requirements

- Create an array containing 30 placeholder grades.
- Every grade should initially be `0`.
- Print the resulting array.

### Reflection

Why is `np.zeros()` a better choice than `np.empty()`?

---

# 📋 Exercise 2 — Chessboard Coordinates

Create two arrays:

- Row indices from `0` to `7`
- Column indices from `0` to `7`

### Requirements

- Use the most appropriate NumPy function.
- Print both arrays.

### Reflection

Why would `np.linspace()` not be the best choice here?

---

# 📋 Exercise 3 — Temperature Sensor

A sensor records one measurement every 10 minutes.

Measurements are taken for 24 hours.

### Tasks

- Generate every measurement time.
- Determine how many measurements are produced.

### Reflection

Which information was known first?

- Step size?
- Number of samples?

---

# 📋 Exercise 4 — Scientific Experiment

A laboratory experiment requires exactly:

- 250 samples
- Between 5 and 15 seconds

### Requirements

- Generate the sampling points.
- Include both endpoints.

### Reflection

Why is `np.linspace()` the natural choice?

---

# 📋 Exercise 5 — Identity Preparation

Create the following arrays:

- A vector of ten zeros.
- A vector of ten ones.
- A vector of ten fives.

Print all three arrays.

---

# 📋 Exercise 6 — Preparing Image Data

A grayscale image has:

- 480 rows
- 640 columns

Create an array that represents an empty black image.

### Questions

- Which function should you use?
- Why?

---

# 📋 Exercise 7 — Simulation Initialization

You are writing a simulation.

The array will immediately be overwritten with calculated values.

### Task

Create an appropriate array with:

- 1000 elements

### Reflection

Which function provides the best performance?

Why should it be used carefully?

---

# 📋 Exercise 8 — Building a Timeline

Generate timestamps from:

- 08:00
- to 18:00

every:

- 30 minutes

Represent the values as minutes after midnight.

---

# 📋 Exercise 9 — Comparing Two Approaches

Generate numbers from:

```text
0
```

to

```text
100
```

using:

### Method A

`np.arange()`

### Method B

`np.linspace()`

Compare the results.

Answer:

- Are they identical?
- Which is easier to understand?
- Which better communicates the programmer's intent?

---

# 📋 Exercise 10 — Matrix Initialization

Create the following matrices:

- 6×6 zeros
- 6×6 ones
- 6×6 filled with `-1`

Print each matrix.

---

# 📋 Exercise 11 — Circular Motion

A robot rotates through one complete revolution.

Generate exactly:

- 360 equally spaced angles.

The first and last angle should **not** represent the same direction.

### Reflection

Which parameter is especially important here?

---

# 📋 Exercise 12 — Engineering Measurements

An engineer records measurements every:

- 0.25 seconds

for:

- 10 seconds

Generate all timestamps.

### Reflection

Would `np.linspace()` also work?

Why is one solution preferable?

---

# 📋 Exercise 13 — Data Conversion

Given the following nested list:

```python
data = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]
```

### Tasks

- Convert it into a NumPy array.
- Print the resulting array.
- Print its type.

---

# 📋 Exercise 14 — Array Factory

Create a small program that generates:

- A vector of zeros.
- A vector of ones.
- A vector filled with a user-defined constant.
- A sequence using `np.arange()`.
- A sequence using `np.linspace()`.

The goal is not interaction, but practicing the use of different array creation functions in a single script.

---

# 📋 Exercise 15 — Function Selection

For each problem below, choose the most appropriate function.

No code is required.

Only explain your reasoning.

| Scenario | Function | Why? |
|----------|----------|------|
| Convert existing Python data | | |
| Create an array of zeros | | |
| Create a constant-valued matrix | | |
| Allocate memory for later use | | |
| Generate indices | | |
| Generate plotting samples | | |
| Generate hourly timestamps | | |
| Generate exactly 100 observations | | |

---

# 🧠 Reflection

These exercises introduced a new challenge:

Many problems could be solved in more than one way.

However, professional programmers aim for the solution that is:

- Correct
- Readable
- Efficient
- Easy to understand

Choosing the right function is part of writing high-quality code.

---

# ✅ Intermediate Milestone

If you completed these exercises successfully, you should now feel comfortable with every array creation function introduced in Chapter 06.

The next section raises the difficulty once again.

Instead of straightforward exercises, you'll solve larger, real-world inspired challenges that combine multiple concepts.

---

> **Next:** Part 3 — Advanced Challenges