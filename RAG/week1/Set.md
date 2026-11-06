
# Python Sets and Frozensets

## 1. What is a Set?

A set is a collection of unique elements in Python.

### Key Properties
- Stores only unique elements (duplicates are removed).
- Unordered — no guaranteed element order.
- Mutable — elements can be added or removed.
- Does not support indexing or slicing.
- Can contain different data types, provided every element is hashable.

### Example

```python
numbers = {10, 20, 30, 20, 10}

print(numbers)
# Output: {10, 20, 30}
```

Duplicates are automatically removed.

---

## 2. Creating Sets

```python
# Using curly braces
fruits = {"apple", "banana", "orange"}

# Using set()
numbers = set([10, 20, 30, 20])

print(fruits)
print(numbers)
```

### Creating an Empty Set

```python
a = {}
b = set()

print(type(a))  # <class 'dict'>
print(type(b))  # <class 'set'>
```

**Remember:** `{}` creates an empty dictionary, not a set. Use `set()`.

---

## 3. Sets with Different Data Types

A set can contain multiple data types, provided each element is hashable.

```python
data = {10, "Python", 3.14, True, (1, 2)}

print(data)
```

Possible elements:
- `int` → `10`
- `str` → `"Python"`
- `float` → `3.14`
- `bool` → `True`
- `tuple` → `(1, 2)`

### Important: True and 1

In Python, `True == 1` and both have the same hash.

```python
data = {True, 1, 2}

print(len(data))
# Output: 2
```

Only one of `True` and `1` is retained as a distinct set element.

### What Cannot Be Stored in a Set?

Lists and dictionaries cannot be elements because they are unhashable.

```python
# TypeError
# data = {10, "Python", [1, 2]}

# TypeError
# data = {10, {"name": "Alex"}}
```

A tuple can be an element if all its contents are hashable.

```python
data = {(1, 2), (3, 4)}
print(data)
```

---

## 4. Adding and Removing Elements

```python
fruits = {"apple", "banana"}

# Add one element
fruits.add("mango")

# Add multiple elements
fruits.update(["orange", "grapes"])

# Remove an existing element
fruits.remove("apple")

# Remove an element if present, without raising KeyError
fruits.discard("pineapple")

print(fruits)
```

### Common Set Methods

| Method | Description |
|---|---|
| `add(x)` | Adds one element |
| `update(iterable)` | Adds multiple elements |
| `remove(x)` | Removes an element; raises KeyError if absent |
| `discard(x)` | Removes an element if present |
| `pop()` | Removes and returns an arbitrary element |
| `clear()` | Removes all elements |
| `copy()` | Returns a shallow copy |

Note: `pop()` does not guarantee which element will be removed.

---

## 5. Checking Elements

Use `in` and `not in` to check membership.

```python
skills = {"Python", "React", "SQL"}

print("Python" in skills)       # True
print("Java" in skills)         # False
print("Java" not in skills)     # True
```

---

## 6. Set Operations

Consider two developers with different skills.

```python
developer1 = {"Python", "React", "SQL"}
developer2 = {"Python", "Java", "SQL"}
```

### A. Union (`|`)

Combines all unique elements from both sets.

```python
print(developer1 | developer2)
# {'Python', 'React', 'SQL', 'Java'}
```

Method equivalent:

```python
developer1.union(developer2)
```

### B. Intersection (`&`)

Returns elements common to both sets.

```python
print(developer1 & developer2)
# {'Python', 'SQL'}
```

Method equivalent:

```python
developer1.intersection(developer2)
```

### C. Difference (`-`)

Returns elements in the first set but not in the second.

```python
print(developer1 - developer2)
# {'React'}
```

Method equivalent:

```python
developer1.difference(developer2)
```

Note: Difference is directional.

```python
print(developer2 - developer1)
# {'Java'}
```

### D. Symmetric Difference (`^`)

Returns elements present in either set, but not in both.

```python
print(developer1 ^ developer2)
# {'React', 'Java'}
```

Method equivalent:

```python
developer1.symmetric_difference(developer2)
```

---

## 7. Subset, Superset and Disjoint

```python
a = {1, 2, 3}
b = {1, 2}
c = {4, 5}

print(b.issubset(a))       # True
print(a.issuperset(b))     # True
print(a.isdisjoint(c))     # True
```

| Method | Meaning |
|---|---|
| `issubset()` | Every element in this set exists in the other set |
| `issuperset()` | This set contains every element in the other set |
| `isdisjoint()` | The sets have no common elements |

Operators are also available:

```python
print(b <= a)  # True: subset
print(a >= b)  # True: superset
```

---

## 8. Useful Built-in Functions

```python
numbers = {10, 20, 30}

print(len(numbers))  # 3
print(min(numbers))  # 10
print(max(numbers))  # 30
print(sum(numbers))  # 60
```

You can iterate over a set:

```python
for number in numbers:
    print(number)
```

The iteration order is not guaranteed.

---

## 9. Removing Duplicates from a List

One common use of sets is removing duplicates from a list.

```python
numbers = [10, 20, 10, 30, 20]

unique_numbers = set(numbers)

print(unique_numbers)
# {10, 20, 30}
```

If you need a list afterward:

```python
unique_list = list(set(numbers))
print(unique_list)
```

**Important:** This method does not preserve the original list order. To remove duplicates while preserving order, use:

```python
unique_list = list(dict.fromkeys(numbers))

print(unique_list)
# [10, 20, 30]
```

---

## 10. What Is a Frozenset?

A frozenset is an immutable version of a set.

After creating it, you cannot add or remove elements.

```python
numbers = frozenset([10, 20, 30, 20])

print(numbers)
# frozenset({10, 20, 30})

# numbers.add(40)  # AttributeError
```

### Frozenset Operations

Operations such as union, intersection and difference still work.

```python
a = frozenset({1, 2, 3})
b = frozenset({2, 3, 4})

print(a | b)  # Union
print(a & b)  # Intersection
print(a - b)  # Difference
```

These operations return new sets or frozensets; they do not modify the original frozensets.

---

## 11. Set vs Frozenset

| Feature | Set | Frozenset |
|---|---|---|
| Mutable | Yes | No |
| Add elements | Yes | No |
| Remove elements | Yes | No |
| Duplicates | Removed | Removed |
| Set operations | Supported | Supported |
| Can be a dictionary key | No | Yes, if its elements are hashable |
| Can be an element of another set | No | Yes |

### Frozenset as a Dictionary Key

```python
permissions = frozenset({"read", "write"})

data = {
    permissions: "Editor"
}

print(data[permissions])
# Editor
```

A frozenset is hashable when its elements are hashable, allowing it to be used as a dictionary key or a set element.

---

## 12. Common Mistakes

### Mistake 1: Creating an empty set

```python
a = {}
print(type(a))  # dict
```

Correct:

```python
a = set()
print(type(a))  # set
```

### Mistake 2: Accessing by index

```python
numbers = {10, 20, 30}

# numbers[0]  # TypeError
```

Sets do not support indexing.

### Mistake 3: Adding a list to a set

```python
# data = {[1, 2], [3, 4]}  # TypeError
```

Use tuples instead if the elements inside them are hashable:

```python
data = {(1, 2), (3, 4)}
```

### Mistake 4: Expecting a fixed order

```python
numbers = {30, 10, 20}
print(numbers)
```

Do not rely on the displayed order. Use `sorted()` when you need ordered output:

```python
print(sorted(numbers))
# [10, 20, 30]
```

---

## 13. Interview Questions

### Q1. What is a set in Python?

A set is a mutable, unordered collection of unique, hashable elements.

### Q2. Can a set contain duplicate elements?

No. Duplicate elements are automatically removed.

### Q3. Can a set contain different data types?

Yes, if all elements are hashable.

```python
data = {10, "Hello", 3.14, (1, 2)}
```

### Q4. What is the difference between `remove()` and `discard()`?

- `remove()` raises `KeyError` if the element does not exist.
- `discard()` does not raise an error if the element does not exist.

### Q5. What is the difference between a set and a frozenset?

A set is mutable, whereas a frozenset is immutable.

### Q6. What is the difference between union and intersection?

- Union combines all unique elements.
- Intersection returns only common elements.

### Q7. Can a set contain a tuple?

Yes, if every element inside the tuple is hashable.

### Q8. Can a set contain a list?

No. Lists are unhashable.

### Q9. How do you remove duplicates from a list?

```python
numbers = [1, 2, 2, 3, 3]
print(set(numbers))
```

### Q10. Why can a frozenset be used as a dictionary key?

Because a frozenset is immutable and hashable when all its elements are hashable.

---

## 14. Practice Exercises

Try solving these without looking at the answers first.

### Exercise 1: Remove Duplicates

```python
numbers = [1, 2, 2, 3, 4, 4, 5]

# Convert this list into a set.
```

Expected elements: `{1, 2, 3, 4, 5}`

### Exercise 2: Find Common Elements

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

# Find elements present in both sets.
```

Expected result: `{3, 4}`

### Exercise 3: Find Unique Skills

```python
frontend = {"HTML", "CSS", "JavaScript"}
backend = {"Python", "SQL", "JavaScript"}

# Find all skills without duplicates.
```

Expected elements: `{"HTML", "CSS", "JavaScript", "Python", "SQL"}`

### Exercise 4: Difference

```python
a = {10, 20, 30, 40}
b = {30, 40, 50}

# Find elements present in a but not in b.
```

Expected result: `{10, 20}`

### Exercise 5: Frozenset

Create a frozenset containing `10, 20, 30`. Then try adding `40` and observe what happens.

---

## 15. Quick Revision

- `set()` → creates an empty set.
- `add()` → adds one element.
- `update()` → adds multiple elements.
- `remove()` → removes an element or raises an error.
- `discard()` → removes an element without raising an error if missing.
- `|` → union.
- `&` → intersection.
- `-` → difference.
- `^` → symmetric difference.
- `issubset()` → checks subset.
- `issuperset()` → checks superset.
- `isdisjoint()` → checks whether two sets have no common elements.
- `frozenset()` → creates an immutable set.

