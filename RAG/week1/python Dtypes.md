
# Python Built-in Data Types — Interview Notes

## 1. What are data types in Python?

Data types define the kind of value a variable holds, such as a number, text, or collection of values.

Python is **dynamically typed**, so you do not need to explicitly declare a variable's type. Python determines it at runtime.

```python
x = 10
print(type(x))  # <class 'int'>

x = "Hello"
print(type(x))  # <class 'str'>
```

The same variable can refer to values of different types at different times.

---

## 2. Main Built-in Data Types

| Category | Data Types | Example |
|---|---|---|
| Numeric | `int`, `float`, `complex` | `10`, `10.5`, `2+3j` |
| Text | `str` | `"Python"` |
| Sequence | `list`, `tuple`, `range` | `[1, 2]`, `(1, 2)`, `range(5)` |
| Mapping | `dict` | `{"name": "Aakash"}` |
| Set | `set`, `frozenset` | `{1, 2, 3}` |
| Boolean | `bool` | `True`, `False` |
| None | `NoneType` | `None` |
| Binary | `bytes`, `bytearray`, `memoryview` | `b"Hello"` |

---

## 3. Numeric Types

### int — Integer

Stores whole numbers without decimal points.

```python
age = 23
salary = 50000

print(type(age))  # <class 'int'>
```

### float — Floating-point number

Stores numbers with decimal points.

```python
price = 99.50
percentage = 12.5

print(type(price))  # <class 'float'>
```

### complex — Complex number

Stores a real and an imaginary component.

```python
x = 2 + 3j

print(x)       # (2+3j)
print(x.real)  # 2.0
print(x.imag)  # 3.0
```

---

## 4. String (`str`)

A string stores text. Strings are immutable, meaning their characters cannot be changed in place.

```python
name = "Python"

print(name[0])  # P
print(name[1])  # y
print(name.upper())  # PYTHON
print(name.lower())  # python
```

Strings support indexing and slicing.

```python
text = "Python"

print(text[0:3])  # Pyt
print(text[-1])   # n
```

Strings are immutable:

```python
text = "Python"
# text[0] = "J"  # TypeError
```

---

## 5. List (`list`)

A list stores multiple values in an ordered, mutable collection. Duplicates are allowed.

```python
numbers = [10, 20, 30, 20]

numbers.append(40)
numbers.remove(20)

print(numbers)  # [10, 30, 20, 40]
```

Important operations:

```python
numbers = [10, 20, 30]

numbers.append(40)
numbers.insert(0, 5)
numbers.pop()

print(numbers)  # [5, 10, 20, 30]
```

Use a list when you need to add, remove, or update elements.

---

## 6. Tuple (`tuple`)

A tuple stores multiple values in an ordered, immutable collection. Duplicates are allowed.

```python
coordinates = (10, 20, 30)

print(coordinates[0])  # 10
print(type(coordinates))  # <class 'tuple'>
```

This is not allowed:

```python
# coordinates[0] = 100  # TypeError
```

Use a tuple when the collection should remain unchanged.

A single-element tuple needs a comma:

```python
a = (10,)
print(type(a))  # <class 'tuple'>
```

Without the comma, `(10)` is just an integer.

---

## 7. Range (`range`)

`range` represents a sequence of integers, commonly used in loops.

```python
for i in range(5):
    print(i)
```

Output:

```text
0
1
2
3
4
```

You can specify a start, stop, and step:

```python
print(list(range(2, 11, 2)))
# [2, 4, 6, 8, 10]
```

The stop value is excluded.

---

## 8. Dictionary (`dict`)

A dictionary stores key-value pairs. Keys must be unique and hashable. Dictionaries are mutable.

```python
employee = {
    "name": "Aakash",
    "salary": 50000,
    "age": 23
}

print(employee["name"])  # Aakash

employee["salary"] = 60000
employee["department"] = "IT"

print(employee)
```

Useful methods:

```python
print(employee.keys())
print(employee.values())
print(employee.items())
```

Use a dictionary when you want to look up values using keys.

---

## 9. Set (`set`)

A set stores unique elements. It is mutable and does not guarantee a particular iteration order.

```python
numbers = {10, 20, 20, 30}

print(numbers)  # {10, 20, 30} (order may vary)

numbers.add(40)
numbers.discard(10)

print(numbers)
```

Sets do not support indexing:

```python
# print(numbers[0])  # TypeError
```

Useful for removing duplicates and performing set operations.

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)  # Union: {1, 2, 3, 4, 5}
print(a & b)  # Intersection: {3}
print(a - b)  # Difference: {1, 2}
```

---

## 10. Frozenset (`frozenset`)

A frozenset is an immutable set. You cannot add or remove elements after creating it.

```python
numbers = frozenset({10, 20, 30})

print(numbers)

# numbers.add(40)  # AttributeError
```

### Set vs Frozenset

| Feature | `set` | `frozenset` |
|---|---|---|
| Mutable | Yes | No |
| Add/remove elements | Yes | No |
| Unique elements | Yes | Yes |
| Can be a dictionary key | No | Yes, if its elements are hashable |

---

## 11. Boolean (`bool`)

Boolean values represent truth: `True` or `False`.

```python
is_active = True
is_admin = False

print(type(is_active))  # <class 'bool'>
print(10 > 5)           # True
print(10 == 5)          # False
```

Common falsy values include:

- `False`
- `None`
- `0`
- `0.0`
- `""`
- `[]`
- `{}`
- `set()`

An empty tuple `()` is also falsy.

Other ordinary non-empty values are generally truthy.

---

## 12. None (`NoneType`)

`None` represents the absence of a value.

```python
result = None

print(result)       # None
print(type(result)) # <class 'NoneType'>
print(result is None)  # True
```

### `is None` vs `== None`

- `is None` checks whether the object is the actual `None` object.
- `== None` checks equality, which a custom class can redefine.

#### Note
- is checks whether two references point to the same object.
- == checks whether two objects are equal in value, according to their equality behavior.

---

## 13. Binary Types

These are useful when working with binary data, files, and network operations.

### bytes

An immutable sequence of bytes.

```python
data = b"Hello"

print(data)       # b'Hello'
print(data[0])    # 72 (ASCII value of H)
```

### bytearray

A mutable sequence of bytes.

```python
data = bytearray(b"Hello")
data[0] = 74

print(data)  # bytearray(b'Jello')
```

### memoryview

Provides a view of binary data without copying the underlying data just to create the view.

```python
data = bytearray(b"Hello")
view = memoryview(data)

print(view[0])  # 72
```

---

## 14. Mutable vs Immutable

### Mutable types

Their contents can be changed after creation.

- `list`
- `dict`
- `set`
- `bytearray`

```python
numbers = [1, 2, 3]
numbers[0] = 100

print(numbers)  # [100, 2, 3]
```

### Immutable types

Their contents cannot be changed in place.

- `int`
- `float`
- `bool`
- `str`
- `tuple`
- `frozenset`
- `bytes`
- `range`
- `complex`

```python
name = "Python"
name = name + " Programming"

print(name)  # Python Programming
```

This creates a new string value and reassigns `name`; it does not modify the original string in place.

**Interview tip:** A tuple is immutable, but it can contain a mutable object such as a list. The list inside it can still be modified.

---

## 15. Check Data Types

Use `type()` to inspect an object's type.

```python
x = 100
print(type(x))  # <class 'int'>
```

Use `isinstance()` to check whether an object belongs to a type.

```python
x = 100

print(isinstance(x, int))  # True
print(isinstance(x, str))  # False
```

`isinstance()` also recognizes inheritance and certain type relationships.

---

## 16. Common Interview Questions

### Q1. What are Python's built-in data types?

Common types include `int`, `float`, `complex`, `str`, `list`, `tuple`, `range`, `dict`, `set`, `frozenset`, `bool`, `bytes`, `bytearray`, `memoryview`, and `NoneType`.

### Q2. What is the difference between a list and a tuple?

A list is mutable; a tuple is immutable. Both are ordered and allow duplicates.

### Q3. What is the difference between a set and a list?

A list preserves order and allows duplicates. A set stores unique elements and does not support indexing.

### Q4. What is dynamic typing?

Python determines the type of a value at runtime. A variable can refer to values of different types at different times.

### Q5. What is the difference between `is` and `==`?

`is` checks identity. `==` checks equality.

### Q6. What is the difference between `is None` and `== None`?

Use `is None` to check whether a variable refers to the actual `None` object. Equality can be customized by a class.

### Q7. Can a dictionary have duplicate keys?

No. Assigning a value to an existing key updates the value associated with that key.

```python
data = {"a": 1, "a": 2}
print(data)  # {'a': 2}
```

### Q8. Can a list contain different data types?

Yes.

```python
data = [10, "Python", 3.5, True, None]
```

### Q9. Why can a frozenset be a dictionary key?

A frozenset is immutable and hashable when its elements are hashable, so it can be used as a dictionary key.

---

