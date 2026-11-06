
# Python Modules and Packages

## 1. What is a Module?

A **module** is a Python file (`.py`) that can contain functions, variables, and classes.

### Example

Create a file named `math_utils.py`:

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

pi = 3.14
```

Here, `math_utils.py` is a module containing functions and a variable.

### Importing a Module

Create another file named `main.py`:

```python
import math_utils

print(math_utils.add(10, 5))
print(math_utils.subtract(10, 5))
print(math_utils.pi)
```

Output:

```text
15
5
3.14
```

We can reuse functions and variables from one Python file in another by importing the module.

### Different Ways to Import

**1. Import the entire module**

```python
import math

print(math.sqrt(25))
```

Output: `5.0`

**2. Import a specific function**

```python
from math import sqrt

print(sqrt(25))
```

Output: `5.0`

**3. Import using an alias**

```python
import math as m

print(m.sqrt(36))
```

Output: `6.0`

---

## 2. What is a Package?

A **package** is a directory used to organize related Python modules.

### Example Folder Structure

```text
my_project/
│
├── main.py
│
└── employees/
    ├── __init__.py
    ├── salary.py
    └── attendance.py
```

Here:

- `salary.py` is a module.
- `attendance.py` is a module.
- `employees/` is a package.
- `__init__.py` is commonly used to mark a directory as a regular Python package.

Modern Python also supports namespace packages without an `__init__.py` file.

### Example: salary.py

```python
def calculate_salary(basic, bonus):
    return basic + bonus
```

### Importing from a Package

In `main.py`:

```python
from employees.salary import calculate_salary
from employees.attendance import check_attendance

print(calculate_salary(30000, 5000))
print(check_attendance(24, 30))
```

Output:

```text
35000
80.0
```

The import path follows this structure:

`package_name.module_name.function_name`

---

## 3. Module vs Package

| Feature | Module | Package |
|---|---|---|
| Meaning | A Python file containing code | A directory organizing related modules |
| Example | `salary.py` | `employees/` |
| Contains | Functions, variables, and classes | Modules and potentially subpackages |
| Purpose | Reuse code | Organize code |
| Import example | `import math_utils` | `from employees import salary` |

---

### Easy Way to Remember

**Functions and variables → Module → Package**

A module doesn't need multiple functions. Even a Python file containing only one variable can be a module.

---
