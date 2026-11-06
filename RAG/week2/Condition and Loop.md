
# Python Conditions and Loops

## 1. Conditions in Python

Conditions help Python make decisions based on whether an expression is `True` or `False`.

### if, elif, and else

```python
age = 20

if age >= 18:
    print("Eligible to vote")
elif age == 17:
    print("Almost eligible")
else:
    print("Not eligible")
```

Output:
```text
Eligible to vote
```

- `if`: Executes code when the condition is true.
- `elif`: Checks another condition if the previous condition is false.
- `else`: Executes when all previous conditions are false.

**Important:** Python uses indentation (spaces) to define code blocks.

---

## 2. Comparison Operators

Comparison operators compare two values and return `True` or `False`.

| Operator | Meaning | Example | Result |
|---|---|---|---|
| `==` | Equal to | `5 == 5` | `True` |
| `!=` | Not equal to | `5 != 3` | `True` |
| `>` | Greater than | `10 > 5` | `True` |
| `<` | Less than | `3 < 5` | `True` |
| `>=` | Greater than or equal to | `5 >= 5` | `True` |
| `<=` | Less than or equal to | `4 <= 5` | `True` |

**Remember:**
- `=` assigns a value.
- `==` compares two values.

```python
x = 10

print(x == 10)  # True
print(x != 5)   # True
```

---

## 3. Logical Operators

Logical operators combine or reverse conditions.

### and

Both conditions must be true.

```python
age = 25
has_id = True

if age >= 18 and has_id:
    print("Entry allowed")
```

Output:
```text
Entry allowed
```

### or

At least one condition must be true.

```python
age = 17

if age >= 18 or age == 17:
    print("Condition satisfied")
```

Output:
```text
Condition satisfied
```

### not

Reverses a Boolean value.

```python
is_raining = False

if not is_raining:
    print("You can go outside")
```

Output:
```text
You can go outside
```

---

## 4. for Loop

A `for` loop iterates over items in a sequence, such as a list, string, or range.

```python
names = ["Arun", "Priya", "Kumar"]

for name in names:
    print(name)
```

Output:
```text
Arun
Priya
Kumar
```

Python assigns each list item to `name` during each iteration.

### Using range()

`range()` generates a sequence of numbers.

```python
for i in range(1, 6):
    print(i)
```

Output:
```text
1
2
3
4
5
```

**Important:** The ending value is excluded.


The general syntax is:

```python
range(start, stop, step)
```

- `start`: Starting number (default is `0`).
- `stop`: Ending boundary, which is excluded.
- `step`: Difference between numbers (default is `1`).

---

## 5. while Loop

A `while` loop repeats a block of code as long as its condition is true.

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

Output:
```text
1
2
3
4
5
```

**Warning:** If a `while` loop condition never becomes false, it can create an infinite loop.

---

## 6. break Statement

`break` immediately terminates the loop.

```python
for i in range(1, 6):
    if i == 3:
        break
    print(i)
```

Output:
```text
1
2
```

When `i` becomes `3`, the loop stops completely.

---

## 7. continue Statement

`continue` skips the current iteration and moves to the next one.

```python
for i in range(1, 6):
    if i == 3:
        continue
    print(i)
```

Output:
```text
1
2
4
5
```

When `i` is `3`, Python skips `print(i)` for that iteration.

### Difference between break and continue

| Statement | What it does |
|---|---|
| `break` | Stops the entire loop |
| `continue` | Skips only the current iteration |

---

## 8. Combining Conditions and Loops

Conditions and loops are often used together to process data.

### Example: Filter invoice amounts

```python
invoices = [2000, 7500, 4000, 12000, 500]

for amount in invoices:
    if amount > 5000:
        print(amount)
```

Output:
```text
7500
12000
```

**Explanation:**
- The `for` loop checks each invoice amount.
- The `if` condition checks whether the amount is greater than `5000`.
- Only matching amounts are printed.


```python
prices = [100, 200, 300]
total = 0

for price in prices:
    total += price

print(total)
```

Output:
```text
600
```

---

## 9. Nested Conditions

A nested condition is a condition inside another condition.

```python
age = 25
has_id = True

if age >= 18:
    if has_id:
        print("Entry allowed")
    else:
        print("ID required")
else:
    print("Underage")
```

Output:
```text
Entry allowed
```

Nested conditions are useful when a decision depends on multiple levels of checks.

---

## 10. Nested Loops

A nested loop is a loop inside another loop.

```python
for i in range(1, 4):
    for j in range(1, 3):
        print(i, j)
```

Output:
```text
1 1
1 2
2 1
2 2
3 1
3 2
```

For every iteration of the outer loop, the inner loop completes all its iterations.

---
