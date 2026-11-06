
# Python Exception Handling

## 1. What Is Exception Handling?

Exception handling is a way to handle errors that occur while a Python program is running, allowing the program to respond appropriately.

### Without Exception Handling

```python
a = 10
b = 0

print(a / b)
print("Program completed")
```

Output:
```text
ZeroDivisionError: division by zero
```

The program stops when the exception occurs, so `"Program completed"` is not printed.

### With Exception Handling

```python
try:
    a = 10
    b = 0
    print(a / b)
except ZeroDivisionError:
    print("Cannot divide by zero")

print("Program completed")
```

Output:
```text
Cannot divide by zero
Program completed
```

The exception is handled, allowing the remaining code to execute.

---

## 2. try and except

- `try`: Contains code that might raise an exception.
- `except`: Handles a matching exception if one occurs.

### Syntax

```python
try:
    # Code that might cause an exception
    risky_operation()
except SomeException:
    # Handle the exception
    print("Something went wrong")
```

`risky_operation()` and `SomeException` are placeholders in this example.

---

## 3. Common Python Exceptions

| Exception | Meaning | Example |
|---|---|---|
| `ZeroDivisionError` | Dividing by zero | `10 / 0` |
| `ValueError` | Invalid value for an operation | `int("hello")` |
| `TypeError` | Incompatible data types | `"10" + 5` |
| `IndexError` | List index does not exist | `[10, 20][5]` |
| `KeyError` | Dictionary key does not exist | `{"name": "Arun"}["age"]` |
| `FileNotFoundError` | File does not exist at the specified path | Opening a missing file |

---

## 4. Handling ValueError

Suppose a user enters text instead of a valid integer.

```python
try:
    age = int(input("Enter your age: "))
    print("Your age is", age)
except ValueError:
    print("Please enter a valid number")
```

If the user enters `hello`, the output is:

```text
Please enter a valid number
```

Python raises a `ValueError` because `"hello"` cannot be converted to an integer.

---

## 5. The else Block

The `else` block executes **only when no exception occurs inside the `try` block**.

### Example

```python
try:
    number = int(input("Enter a number: "))
except ValueError:
    print("Invalid input! Please enter a number.")
else:
    print("Conversion successful!")
    print("Your number is:", number)
```

### Case 1: Valid Input

Input:
```text
Enter a number: 25
```

Output:
```text
Conversion successful!
Your number is: 25
```

### Case 2: Invalid Input

Input:
```text
Enter a number: hello
```

Output:
```text
Invalid input! Please enter a number.
```

### How It Works

- `try`: Attempts to convert the input to an integer.
- `except`: Handles the `ValueError` if conversion fails.
- `else`: Runs only if the conversion succeeds.

**Easy way to remember:** `else` means "If the try block succeeds, execute this code."

---

## 6. The finally Block

The `finally` block normally executes whether an exception occurs or not. It is often used for cleanup operations.

```python
try:
    number = int("100")
    print(number)
except ValueError:
    print("Invalid number")
finally:
    print("Execution completed")
```

Output:
```text
100
Execution completed
```

Even if the conversion fails, the `finally` block still runs.

---

## 7. Using try, except, else, and finally Together

```python
try:
    number = int(input("Enter a number: "))
except ValueError:
    print("Invalid input")
else:
    print("Conversion successful:", number)
finally:
    print("Program execution finished")
```

If the user enters `10`, the output is:

```text
Conversion successful: 10
Program execution finished
```

If the user enters `hello`, the output is:

```text
Invalid input
Program execution finished
```

The `else` block runs only when no exception occurs in `try`. The `finally` block runs in either case.

---
