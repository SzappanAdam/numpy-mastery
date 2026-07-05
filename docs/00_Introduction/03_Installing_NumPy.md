# 📘 Lesson 03 — Installing NumPy

> [!NOTE]
> **Difficulty:** 🟢 Beginner  
> **Reading Time:** ~20 minutes  
> **Practice Time:** ~15 minutes  
> **Prerequisites:** Lesson 02 — Why NumPy?

---

> *"The best tool in the world is useless if you don't know how to prepare it."*

---

# 🎯 Learning Objectives

By the end of this lesson, you will be able to:

- Understand what Python packages are.
- Explain the purpose of `pip`.
- Install NumPy correctly.
- Verify that NumPy is installed and working.
- Understand why virtual environments are recommended.
- Prepare your computer for the rest of this course.

---

# 🧠 Mental Model

Imagine you've just bought a brand-new smartphone.

When you turn it on for the first time, it already knows how to make calls, send messages, and perform a few basic tasks.

But what if you want to edit photos?

Or navigate with GPS?

Or play games?

The phone doesn't magically know how to do everything.

Instead, you install **apps**.

Python works in a very similar way.

When you install Python, it comes with a powerful standard library that provides many useful tools.

However, the Python community has created thousands of additional libraries that extend Python's capabilities.

NumPy is one of those libraries.

Just as installing a photo editing app gives your phone new abilities, installing NumPy gives Python powerful numerical computing capabilities.

Keep this mental model in mind:

> Python is the operating system.

> NumPy is one of the professional tools you install to extend it.

---

# 📖 What Is a Python Package?

Before installing NumPy, it's important to understand **what we're actually installing**.

A **package** is a collection of Python code that has been organized to solve a particular problem.

Different packages specialize in different tasks.

For example:

| Package | Purpose |
|----------|---------|
| NumPy | Numerical computing |
| Pandas | Data analysis |
| Matplotlib | Data visualization |
| SciPy | Scientific computing |
| Requests | HTTP communication |
| Flask | Web applications |

Instead of writing every tool yourself, you can install packages created and maintained by experienced developers around the world.

This is one of Python's greatest strengths.

---

# 🌍 The Python Ecosystem

One of the reasons Python has become so popular is its enormous ecosystem.

Millions of developers contribute libraries that solve real-world problems.

Rather than reinventing the wheel, Python encourages developers to reuse reliable, well-tested solutions.

A simplified view of the ecosystem looks like this:

```text
                 Python
                    │
     ┌──────────────┼──────────────┐
     │              │              │
   NumPy         Requests       Flask
     │
     ├──────── Pandas
     │
     ├──────── SciPy
     │
     ├──────── scikit-learn
     │
     └──────── Many more...
```

Notice something interesting.

Many scientific libraries are built **on top of NumPy**.

This is why learning NumPy first is such an important investment.

Once you understand NumPy, many other libraries become much easier to learn.

---

# 📦 What Is pip?

If packages are like apps on your phone, then you need a way to install them.

This is where **pip** comes in.

`pip` is Python's package manager.

Its job is to:

- download packages,
- install them,
- update them,
- remove them,
- manage their dependencies.

You can think of `pip` as an app store—but for Python libraries.

Instead of downloading files manually from websites, you simply ask `pip` to install a package.

For example:

```bash
pip install numpy
```

With a single command, `pip` will download NumPy, install it, and make it available to your Python programs.

Simple for the user.

Quite sophisticated behind the scenes.

---

# 🧰 Toolbox

> [!TIP]
> **Command**
>
> ```bash
> pip --version
> ```
>
> This command displays the installed version of `pip` and confirms that it is available on your system.

Example output:

```text
pip 25.1 from .../site-packages/pip (python 3.12)
```

If you see something similar, you're ready to continue.

---

# 📥 Installing NumPy

Installing NumPy usually requires only a single command.

Open your terminal (or command prompt) and run:

```bash
pip install numpy
```

After pressing **Enter**, `pip` will begin downloading NumPy and any required dependencies.

Depending on your internet connection, this usually takes only a few seconds.

During the installation, you'll see messages describing each step.

Don't worry if you don't understand every line yet.

The important thing is that the installation finishes successfully without any error messages.

---

# 💡 Platform Notes

> [!NOTE]
> The commands shown throughout this course work on **Windows**, **macOS**, and **Linux**.
>
> On some systems, especially Linux and macOS, you may need to use:
>
> ```bash
> python3 -m pip install numpy
> ```
>
> instead of:
>
> ```bash
> pip install numpy
> ```
>
> Both commands perform the same task. The difference depends on how Python is installed and configured on your computer.

---

# 🚀 Best Practice

> [!IMPORTANT]
> Instead of relying on the standalone `pip` command, many experienced Python developers prefer:
>
> ```bash
> python -m pip install numpy
> ```
>
> Why?
>
> Because this guarantees that the package is installed into the same Python interpreter that is executing your programs.
>
> As you begin working with multiple Python versions or virtual environments, this habit can prevent many confusing installation problems.

---

# ⚠️ Common Mistakes

One of the most common beginner mistakes is confusing Python with `pip`.

For example:

```bash
python numpy
```

This command does **not** install NumPy.

Likewise,

```bash
import numpy
```

typed directly into the operating system terminal will not work either.

Remember:

- The **terminal** runs system commands.
- **Python** runs Python code.

Knowing which environment you're currently using is an important skill that will save you many hours of debugging.

---

# 📌 Key Takeaways (So Far)

At this point, you should understand that:

- NumPy is distributed as a Python package.
- Packages extend Python with new functionality.
- `pip` is the standard package manager for Python.
- Installing NumPy usually requires only a single command.
- Using `python -m pip` is considered a best practice.

---

# ✅ Verifying the Installation

Installing NumPy is only the first step.

Before we continue, we should verify that the installation completed successfully.

Fortunately, this is very easy.

Open your terminal and start Python.

Depending on your operating system, one of these commands will usually work:

```bash
python
```

or

```bash
python3
```

If Python starts successfully, you'll see something similar to this:

```text
Python 3.12.3 (main, ...)
>>>
```

The `>>>` symbol is called the **Python prompt**.

It indicates that Python is waiting for you to enter code.

Now type:

```python
import numpy as np
```

If nothing happens...

Congratulations!

That is exactly what we want.

A successful `import` produces no output.

Python has simply loaded the NumPy library into memory and is now ready to use it.

---

# 🔍 Checking the Installed Version

Let's verify which version of NumPy is installed.

Type:

```python
import numpy as np

print(np.__version__)
```

Example output:

```text
2.3.1
```

Your version number may be different, and that's perfectly normal.

NumPy is actively developed, so newer versions are released regularly.

Throughout this course we focus on concepts that remain stable across versions, so minor version differences should not affect your learning.

---

# 🧰 Toolbox

> [!TIP]
> **Useful Commands**
>
> ```bash
> pip show numpy
> ```
>
> Displays detailed information about the installed package.

Example output:

```text
Name: numpy
Version: 2.x.x
Location: ...
Requires:
```

This command is particularly useful when you're unsure:

- whether NumPy is installed,
- which version is installed,
- where it was installed.

---

# 🔄 Upgrading NumPy

Software evolves over time.

Bugs are fixed.

Performance improves.

New features are added.

To upgrade NumPy to the latest available version, run:

```bash
python -m pip install --upgrade numpy
```

If you're already using the latest version, `pip` will simply tell you that nothing needs to be updated.

Upgrading is generally safe, but in professional projects developers often pin a specific version to ensure consistent behavior.

We'll briefly discuss version pinning later in this lesson.

---

# 🗑️ Uninstalling NumPy

Occasionally, you may want to remove NumPy.

For example:

- to reinstall it,
- to free space,
- to troubleshoot an installation problem.

The command is straightforward:

```bash
python -m pip uninstall numpy
```

`pip` will ask for confirmation before removing the package.

---

# 🌱 Why Virtual Environments Matter

Imagine you're working on two different Python projects.

Project A requires:

```
NumPy 2.2
```

Project B requires:

```
NumPy 2.3
```

If both projects use the same global Python installation, one project may stop working when the other upgrades NumPy.

This is called a **dependency conflict**.

A dependency is simply another piece of software that your project depends on.

Virtual environments solve this problem.

Each project gets its own isolated Python environment with its own installed packages.

Think of it as giving every project its own toolbox.

Nothing gets mixed together.

---

# 🧠 Mental Model

Imagine two professional chefs sharing a single kitchen.

Chef A needs one recipe.

Chef B needs another.

If they constantly rearrange each other's ingredients, confusion is inevitable.

Now imagine each chef has their own kitchen.

Everything is organized.

Nothing interferes.

Virtual environments work in exactly this way.

Each project has its own isolated workspace.

---

# 📦 Creating a Virtual Environment

Creating a virtual environment is surprisingly simple.

From your project folder, run:

```bash
python -m venv .venv
```

This creates a new directory named `.venv`.

Inside it, Python stores a completely isolated environment for this project.

---

# ▶️ Activating the Environment

Before installing packages into the virtual environment, it must be activated.

### Windows

```bash
.venv\Scripts\activate
```

### macOS / Linux

```bash
source .venv/bin/activate
```

After activation, your terminal prompt often changes to something like:

```text
(.venv)
```

This is a helpful reminder that you're currently working inside the virtual environment.

From this point onward, any packages you install belong only to this project.

---

# 📌 Best Practice

> [!IMPORTANT]
> For almost every real-world Python project, create a virtual environment **before** installing any third-party packages.
>
> It keeps projects isolated, reproducible, and much easier to maintain.

---

# ⚠️ Common Mistakes

### Installing into the wrong Python interpreter

Many beginners accidentally install NumPy into one Python installation while running a different one.

Symptoms include:

- `ModuleNotFoundError`
- NumPy appears installed but cannot be imported.

Using:

```bash
python -m pip install numpy
```

instead of simply:

```bash
pip install numpy
```

helps avoid many of these issues.

---

# 📌 Key Takeaways (So Far)

You should now know how to:

- verify a NumPy installation,
- check the installed version,
- upgrade NumPy,
- uninstall NumPy,
- create a virtual environment,
- activate it,
- understand why virtual environments are recommended.

---

# 📄 Reproducible Projects with `requirements.txt`

Imagine that you've spent weeks building a Python project.

Everything works perfectly on your computer.

Now you send the project to a friend.

They run your code...

...and immediately receive an error.

Why?

Because your friend doesn't have the same packages installed.

Professional Python projects solve this problem using a file called:

```text
requirements.txt
```

This file lists the packages (and often their versions) required by the project.

A simple example might look like this:

```text
numpy==2.3.1
```

If your project depends on additional libraries, they would simply appear on separate lines:

```text
numpy==2.3.1
pandas==2.3.0
matplotlib==3.10.0
```

Anyone can then recreate the same environment using:

```bash
python -m pip install -r requirements.txt
```

The `-r` flag tells `pip` to read the package list from the file.

---

# 🧰 Toolbox

> [!TIP]
> **Creating a requirements file**
>
> You can save every package installed in your current environment by running:
>
> ```bash
> python -m pip freeze > requirements.txt
> ```
>
> This command is especially useful when sharing projects or deploying applications.

---

# 🧠 Behind the Scenes

Running:

```bash
python -m pip install numpy
```

looks deceptively simple.

Behind the scenes, however, several things happen.

A simplified overview looks like this:

```text
You run the command
        │
        ▼
Python starts pip
        │
        ▼
pip connects to the Python Package Index (PyPI)
        │
        ▼
pip finds the correct NumPy package
        │
        ▼
The package is downloaded
        │
        ▼
Dependencies are checked
        │
        ▼
Files are installed into your Python environment
        │
        ▼
NumPy becomes available for import
```

Although all of this usually takes only a few seconds, many individual steps are happening in the background.

One of the reasons Python feels so user-friendly is that tools like `pip` hide much of this complexity.

---

# 🔬 Deep Dive (Optional)

You may have noticed that installing NumPy is much faster than compiling a large software project from source.

Why?

In most cases, `pip` downloads a **precompiled wheel**.

A **wheel** is a package format that already contains compiled binaries for your operating system and Python version.

This means your computer usually does **not** need to compile NumPy from its C source code.

Instead, it simply downloads the appropriate prebuilt files and installs them.

If a compatible wheel is unavailable, `pip` may attempt to build the package from source—but for NumPy on modern systems, this is relatively uncommon.

This is one of the reasons installation is usually so quick.

---

# 🤔 Think Before You Continue

Imagine you have three different Python projects:

- A machine learning project
- A web application
- A scientific simulation

Should they all share the same global Python installation?

Think about:

- Different package versions
- Different dependencies
- Future maintenance

We'll revisit this question later when working on larger projects.

---

# 💻 Mini Challenge

Try completing the following tasks on your own.

1. Check your installed Python version.
2. Check your installed `pip` version.
3. Verify your NumPy version.
4. Create a virtual environment named `.venv`.
5. Activate it.
6. Install NumPy inside the virtual environment.
7. Confirm that `import numpy as np` works correctly.

Don't worry if you need to refer back to the lesson.

The goal is understanding—not memorization.

---

# ⚠️ Common Mistakes

Here are a few issues beginners frequently encounter.

### Forgetting to activate the virtual environment

Packages may end up being installed globally instead of inside the project.

---

### Installing with the wrong Python interpreter

Always prefer:

```bash
python -m pip install ...
```

instead of relying on whichever `pip` happens to be first in your system's PATH.

---

### Ignoring error messages

If an installation fails, don't panic.

Read the first error carefully.

Many installation problems are caused by simple issues such as:

- typing mistakes,
- internet connection problems,
- permission issues,
- using the wrong Python interpreter.

Learning to read error messages is one of the most valuable programming skills you can develop.

---

# 📌 Key Takeaways

At this point, you should understand that:

- NumPy is distributed as a Python package.
- `pip` is responsible for installing and managing packages.
- `python -m pip` is considered a reliable installation method.
- Virtual environments isolate project dependencies.
- `requirements.txt` makes projects reproducible.
- `pip` usually installs precompiled wheels instead of compiling packages from source.

---

# ✅ Knowledge Check

Without looking back, answer these questions.

1. What is the purpose of `pip`?
2. Why is `python -m pip` often preferred?
3. What problem do virtual environments solve?
4. What is the purpose of `requirements.txt`?
5. What is a wheel?
6. Why doesn't NumPy usually need to be compiled manually?
7. What command displays the installed NumPy version?

If you can answer these confidently, you're ready for the next lesson.

---

# 🚀 Looking Ahead

Congratulations!

Your development environment is now ready.

This may not seem like the most exciting part of learning NumPy, but it is one of the most important.

A properly configured environment saves countless hours of frustration later.

In the next lesson, everything changes.

We'll write our first NumPy program.

You'll create your first `ndarray`, inspect it, and begin exploring the data structure that forms the foundation of the entire NumPy ecosystem.

The journey into numerical computing truly begins there.

---

# 📚 Further Reading

- NumPy User Guide
- Python Packaging User Guide
- PEP 405 – Virtual Environments
- PEP 427 – The Wheel Binary Package Format