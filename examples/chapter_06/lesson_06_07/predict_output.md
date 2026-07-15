# 📘 Chapter 06 — Chapter Exercises

## Part 4 — Predict the Output

> [!NOTE]
> **Difficulty:** 🟡–🔴 Mixed
>
> **Estimated Time:** 30–45 minutes
>
> **Rule:** Do **not** run the code.
> Read it carefully, predict the output, and explain your reasoning before checking your answer.

---

# 🎯 Objectives

These exercises develop an essential programming skill:

**mentally executing code.**

For each exercise:

1. Predict the output.
2. Explain *why* that output is produced.
3. Identify any important NumPy behavior involved.

---

# 📋 Exercise 41

```python
import numpy as np

a = np.array([1, 2, 3])

print(a)
```

### Questions

- What is printed?
- What is the type of `a`?

---

# 📋 Exercise 42

```python
import numpy as np

a = np.zeros(5)

print(a)
```

### Questions

- How many elements are printed?
- What values do they contain?

---

# 📋 Exercise 43

```python
import numpy as np

a = np.ones((2, 3))

print(a)
```

### Questions

- How many rows?
- How many columns?

---

# 📋 Exercise 44

```python
import numpy as np

a = np.full(4, 7)

print(a)
```

What is the output?

---

# 📋 Exercise 45

```python
import numpy as np

a = np.arange(2, 12, 2)

print(a)
```

### Questions

- Is `12` included?
- Why or why not?

---

# 📋 Exercise 46

```python
import numpy as np

a = np.arange(10, 0, -3)

print(a)
```

Predict every value in the array.

---

# 📋 Exercise 47

```python
import numpy as np

a = np.linspace(0, 10, 6)

print(a)
```

### Questions

- How many values are generated?
- Is `10` included?

---

# 📋 Exercise 48

```python
import numpy as np

a = np.linspace(
    0,
    1,
    5,
    endpoint=False
)

print(a)
```

Explain why the final value is **not** equal to `1`.

---

# 📋 Exercise 49

```python
import numpy as np

a = np.arange(5)

print(type(a))
```

What type is printed?

---

# 📋 Exercise 50

```python
import numpy as np

a = np.full((2, 2), -1)

print(a)
```

Sketch the resulting matrix.

---

# 📋 Exercise 51

```python
import numpy as np

a = np.linspace(-1, 1, 5)

print(a)
```

Write every value in order.

---

# 📋 Exercise 52

```python
import numpy as np

a = np.arange(1, 10)

print(len(a))
```

Predict the printed value.

Explain how you determined it.

---

# 📋 Exercise 53

```python
import numpy as np

a = np.zeros((3, 4))

print(a.shape)
```

What tuple is printed?

---

# 📋 Exercise 54

```python
import numpy as np

a = np.ones(1)

print(a)
```

Is the result:

- a scalar?
- a list?
- a NumPy array?

Explain your answer.

---

# 📋 Exercise 55

```python
import numpy as np

a = np.linspace(0, 100, 11)

print(a[5])
```

Predict the printed value.

Explain how you found it.

---

# 🧠 Reflection

Did you notice a pattern?

The more you understand:

- function parameters,
- default behavior,
- and NumPy conventions,

the easier it becomes to predict the output without executing the program.

This ability is one of the hallmarks of experienced developers.

---

# 🏁 Section Complete

If you were able to solve most of these exercises without running the code, you've developed a strong understanding of NumPy array creation.

If not, revisit the relevant lessons and try again.

Reading code is just as important as writing it.

---

> **Next:** Part 5 — Debugging Exercises