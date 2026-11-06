# Python Lambda Functions — Notes & Interview Reference

## 1. What is a lambda function?

A **lambda function** is a small anonymous function created using the `lambda` keyword. It can accept multiple parameters, but its body must be a **single expression**.

### Syntax

```python
lambda parameters: expression
```

Example:

```python
add = lambda a, b: a + b
print(add(3, 7))
```

Output:

```text
10
```

The expression's result is returned automatically, so a lambda does not need an explicit `return` statement.

---


## 2. Example 2: `filter()` with lambda

```python
data = [10, 20, 30]

output = list(filter(lambda x: x > 20, data))
print(output)
```

Output:

```text
[30]
```

### How it works

1. `filter()` checks each item in `data`.
2. `lambda x: x > 20` returns `True` when the item is greater than `20`.
3. `filter()` keeps only items for which the condition is `True`.
4. `list()` converts the filter result into a list.

| Item (`x`) | Condition (`x > 20`) | Kept? |
|---:|---|---|
| 10 | `False` | No |
| 20 | `False` | No |
| 30 | `True` | Yes |

**Remember:** `filter()` selects items based on a condition; it does not transform them into new values.

---

## 3. Example 3: `map()` with lambda

```python
data = [10, 20, 30]

output = list(map(lambda x: x + x, data))
print(output)
```

Output:

```text
[20, 40, 60]
```

### How it works

1. `map()` applies the lambda function to every item.
2. `lambda x: x + x` doubles each item.
3. `list()` converts the map result into a list.

| Input | Operation | Output |
|---:|---|---:|
| 10 | `10 + 10` | 20 |
| 20 | `20 + 20` | 40 |
| 30 | `30 + 30` | 60 |

**Remember:** `map()` transforms every item; `filter()` selects matching items.

---

## 4. Example 4: `sorted()` with lambda

```python
data = [
    {"name": "Aakash", "salary": 100000},
    {"name": "Harini", "salary": 10000000},
]

result = sorted(
    data,
    key=lambda x: x["salary"],
    reverse=True
)

print(result)
```

Output:

```python
[
    {"name": "Harini", "salary": 10000000},
    {"name": "Aakash", "salary": 100000}
]
```

### How it works

- `sorted(data, ...)` returns a new sorted list.
- `key=lambda x: x["salary"]` tells Python to sort each dictionary by its `salary` value.
- `reverse=True` sorts in descending order (highest to lowest).
- `x` represents one dictionary at a time.

To sort from lowest to highest, remove `reverse=True` or set `reverse=False`.

**Practical use:** Sorting employees by salary, products by price, or RAG search results by relevance score.

---

## 5. `map()` vs. `filter()` vs. `sorted()`

| Function | Purpose | Example | Result |
|---|---|---|---|
| `map()` | Transforms every item | `map(lambda x: x * 2, [1, 2, 3])` | `[2, 4, 6]` |
| `filter()` | Keeps matching items | `filter(lambda x: x > 1, [1, 2, 3])` | `[2, 3]` |
| `sorted()` | Sorts items | `sorted([3, 1, 2])` | `[1, 2, 3]` |

In Python 3, `map()` and `filter()` return iterators, so `list(...)` is often used when you want to see or store all the results as a list.

---

## 6. Common interview questions

### Q1. What is a lambda function?

A lambda function is a small anonymous function created with `lambda`. It can have multiple parameters, but its body is a single expression whose value is returned automatically.

### Q2. What is the difference between `lambda` and `def`?

- `lambda` is suited to short, simple expressions.
- `def` supports multiple statements, docstrings, and more complex logic.
- Prefer `def` for larger or reusable functions.

### Q3. Does a lambda function support multiple parameters?

Yes.

```python
multiply = lambda a, b: a * b
print(multiply(4, 5))
```

Output: `20`

### Q4. What is the difference between `map()` and `filter()`?

- `map()` applies a function to every item and produces transformed results.
- `filter()` keeps items for which the condition is truthy.

### Q5. Why use `key` in `sorted()`?

The `key` argument tells Python which value to use when comparing items for sorting.

```python
names = ["Harini", "Aakash", "Ravi"]
print(sorted(names, key=lambda name: len(name)))
```

Output:

```text
['Ravi', 'Aakash', 'Harini']
```

This sorts strings by their length.

### Q6. Does lambda need `return`?

No. The expression's value is returned automatically.

```python
square = lambda x: x * x
```

### Q7. Can a lambda contain multiple statements?

No. A lambda body must be a single expression. Use `def` when you need multiple statements or more complex logic.

---
