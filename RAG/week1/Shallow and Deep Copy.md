# Python Shallow Copy vs Deep Copy

## 1. What Is Copying?

Copying means creating another object with the same data.

Python provides two common ways to copy objects:

- **Shallow copy** — creates a new outer object, but nested objects are shared.
- **Deep copy** — creates a new outer object and recursively copies nested objects.

The `copy` module provides both:

```python
import copy

shallow = copy.copy(original)
deep = copy.deepcopy(original)
```

---

## 2. Understanding the Outer Object and Nested Objects

Consider this nested list:

```python
data = [[10, 20], [30, 40]]
```

It contains three list objects:

- **Outer list:** `[[10, 20], [30, 40]]`
- **Nested list 1:** `[10, 20]`
- **Nested list 2:** `[30, 40]`

Think of the outer list as a box containing two smaller boxes.

### Diagram: One nested list

```text
                  OUTER LIST
          data = [[10, 20], [30, 40]]
                     /       \
                    /         \
                   v           v
             NESTED LIST 1  NESTED LIST 2
               [10, 20]       [30, 40]
```

The outer list contains references to the nested lists.

---

## 3. Shallow Copy

A **shallow copy** creates a new outer object, but its nested objects are still shared with the original.

```python
import copy

original = [[10, 20], [30, 40]]
shallow = copy.copy(original)
```

### Diagram: Shallow copy

```text
  original (outer list)       shallow (outer list)
          |                           |
          |                           |
          +------------+--------------+
                       |
                       v
             SHARED NESTED LISTS
              [10, 20] [30, 40]
```

The outer lists are different objects, but both refer to the same nested lists.

### Example A: Modify the outer list

```python
original = [[10, 20], [30, 40]]
shallow = copy.copy(original)

original.append([50, 60])

print(original)
# [[10, 20], [30, 40], [50, 60]]

print(shallow)
# [[10, 20], [30, 40]]
```

**Why?** The outer lists are separate. Adding an item to `original` does not add it to `shallow`.

### Example B: Modify a nested list

```python
original = [[10, 20], [30, 40]]
shallow = copy.copy(original)

original[0].append(99)

print(original)
# [[10, 20, 99], [30, 40]]

print(shallow)
# [[10, 20, 99], [30, 40]]
```

**Why?** Both lists refer to the same nested list `[10, 20]`, so the nested change is visible through both variables.

---

## 4. Deep Copy

A **deep copy** creates a new outer object and recursively copies its nested objects too.

```python
import copy

original = [[10, 20], [30, 40]]
deep = copy.deepcopy(original)
```

### Diagram: Deep copy

```text
       original (outer list)        deep (outer list)
                |                          |
                v                          v
          [10, 20] [30, 40]          [10, 20] [30, 40]
           original's lists             deep's lists
              SEPARATE                    SEPARATE
```

The nested lists in `original` and `deep` are independent objects.

### Example: Modify a nested list in the original

```python
import copy

original = [[10, 20], [30, 40]]
deep = copy.deepcopy(original)

original[0][0] = 100

print(original)
# [[100, 20], [30, 40]]

print(deep)
# [[10, 20], [30, 40]]
```

**Why?** `deep` has its own nested lists, so changing `original` does not change `deep`.

The reverse is also true:

```python
deep[0][0] = 999

print(original[0][0])
# 100

print(deep[0][0])
# 999
```

Changing `deep` does not change `original`.

---

## 5. Shallow Copy vs Deep Copy

| Feature | Shallow copy | Deep copy |
|---|---|---|
| Outer object | New object | New object |
| Nested mutable objects | Shared | Recursively copied |
| Nested changes visible in both? | Yes, when the shared object is modified | No, for independently copied objects |
| Function | `copy.copy()` | `copy.deepcopy()` |
| Typical performance | Usually faster | Usually slower |
| Useful when | Sharing nested objects is acceptable | Nested data must be independent |

---

## 6. What Happens With a Single-Level List?

For a list containing integers, shallow and deep copies usually behave the same way.

```python
import copy

original = [10, 20, 30]

shallow = copy.copy(original)
deep = copy.deepcopy(original)

original[0] = 100

print(original)
# [100, 20, 30]

print(shallow)
# [10, 20, 30]

print(deep)
# [10, 20, 30]
```

The lists are separate. Integers are immutable, so assigning a new integer to an element in one list does not change the other lists.

**Key point:** A shallow copy is not the same as sharing the entire list. It creates a new outer list; the difference becomes important when nested mutable objects are present.

---

## 7. What About Nested Dictionaries?

The same concept applies to dictionaries.

```python
import copy

original = {
    "name": "Aakash",
    "skills": {"frontend": "React"}
}

shallow = copy.copy(original)
deep = copy.deepcopy(original)

original["skills"]["frontend"] = "Python"

print(shallow["skills"]["frontend"])
# Python

print(deep["skills"]["frontend"])
# React
```

The nested dictionary under `"skills"` is shared by `original` and `shallow`, but independently copied in `deep`.

---

## 8. What If We Use `=` Instead?

Assignment does not create a copy.

```python
original = [[10, 20], [30, 40]]
copied = original

original[0].append(99)

print(copied)
# [[10, 20, 99], [30, 40]]
```

Both variables refer to the **same outer list**.

### Diagram: Assignment

```text
       original
           \
            \
             v
       SAME OUTER LIST
             ^
            /
           /
        copied
```

---


### Full working example

```python
import copy

original = [[10, 20, 30], [100, 200, 300]]

shallow = copy.copy(original)
deep = copy.deepcopy(original)

original[0][0] = 1
shallow[0][0] = 100

print("Original:", original)
print("Shallow:", shallow)
print("Deep:", deep)
```

Output:

```text
Original: [[100, 20, 30], [100, 200, 300]]
Shallow:  [[100, 20, 30], [100, 200, 300]]
Deep:     [[10, 20, 30], [100, 200, 300]]
```

Both `original` and `shallow` show `100` because they share the same nested list. `deep` remains unchanged because its nested lists are separate.

---
