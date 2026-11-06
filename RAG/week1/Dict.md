
# Python Dictionaries (`dict`) and Dictionary Methods

## 1. What Is a Dictionary?

A dictionary is a built-in Python data structure that stores data as **key-value pairs**.

```python
person = {
    "name": "Aakash The King",
    "age": 23,
    "city": "Chennai"
}

print(person)
print(person["name"])
```

Output:

```text
{'name': 'Aakash The King', 'age': 23, 'city': 'Chennai'}
Aakash The King
```

Here:
- `"name"` is a key.
- `"Aakash The King"` is its value.
- `"age"` is a key.
- `23` is its value.

### Important Properties

- Stores data as key-value pairs.
- Mutable: entries can be added, updated, or removed.
- Keys must be unique.
- Keys must be hashable.
- Values can be any data type.
- Preserves insertion order in modern Python.
- Supports nested dictionaries.

---

## 2. Creating Dictionaries

### Method 1: Using Curly Braces

```python
person = {
    "name": "Aakash The King",
    "age": 25
}
```

### Method 2: Using `dict()`

```python
person = dict(name="Aakash The King", age=25)

print(person)
# {'name': 'Aakash The King', 'age': 25}
```

### Method 3: Creating an Empty Dictionary

```python
person = {}
# Or
person = dict()
```

### Method 4: Using Key-Value Pairs

```python
person = dict([
    ("name", "Aakash The King"),
    ("age", 25)
])

print(person)
# {'name': 'Aakash The King', 'age': 25}
```

---

## 3. Dictionary Keys and Values

Keys must be unique and hashable.

```python
data = {
    "name": "Aakash The King",
    101: "Employee ID",
    (1, 2): "Coordinates"
}

print(data)
```

Strings, integers, and tuples containing only hashable elements can be dictionary keys.

Lists, dictionaries, and sets cannot be dictionary keys because they are unhashable.

### Duplicate Keys

```python
data = {
    "name": "Aakash The King",
    "age": 25,
    "name": "Aakash The King"
}

print(data)
# {'name': 'Aakash The King', 'age': 25}
```

The later value replaces the earlier value for the same key.

### Values Can Be Any Data Type

```python
employee = {
    "name": "Aakash The King",
    "age": 23,
    "skills": ["Python", "React"],
    "active": True,
    "address": {
        "city": "Chennai",
        "country": "India"
    }
}
```

---

## 4. Accessing Dictionary Values

### Using Square Brackets `[]`

```python
person = {
    "name": "Aakash The King",
    "age": 25
}

print(person["name"])
# Aakash The King

# print(person["salary"])
# KeyError because the key doesn't exist
```

### Using `get()`

```python
person = {
    "name": "Aakash The King",
    "age": 25
}

print(person.get("name"))
# Aakash The King

print(person.get("salary"))
# None

print(person.get("salary", 30000))
# 30000
```

### Difference Between `[]` and `get()`

| Method | Missing key |
|---|---|
| `d["key"]` | Raises `KeyError` |
| `d.get("key")` | Returns `None` |
| `d.get("key", default)` | Returns the specified default |

---

## 5. Adding and Updating Entries

### Adding a New Entry

```python
person = {"name": "Aakash The King"}

person["age"] = 25

print(person)
# {'name': 'Aakash The King', 'age': 25}
```

### Updating an Existing Entry

```python
person = {"name": "Aakash The King", "age": 25}

person["age"] = 26

print(person)
# {'name': 'Aakash The King', 'age': 26}
```

### Using `update()`

Adds new entries and updates existing ones.

```python
person = {
    "name": "Aakash The King",
    "age": 25
}

person.update({
    "age": 26,
    "city": "Chennai"
})

print(person)
# {'name': 'Aakash The King', 'age': 26, 'city': 'Chennai'}
```

---

## 6. Important Dictionary Methods

| Method | Purpose |
|---|---|
| `get()` | Retrieves a value safely |
| `keys()` | Returns a view of all keys |
| `values()` | Returns a view of all values |
| `items()` | Returns a view of key-value pairs |
| `update()` | Adds or updates entries |
| `pop(key)` | Removes a specified key and returns its value |
| `popitem()` | Removes and returns the last inserted pair |
| `setdefault()` | Returns a value, adding the key if missing |
| `copy()` | Creates a shallow copy |
| `clear()` | Removes all entries |
| `dict.fromkeys()` | Creates a dictionary from given keys |

---

## 7. `keys()`, `values()`, and `items()`

```python
person = {
    "name": "Aakash The King",
    "age": 25,
    "city": "Chennai"
}

print(person.keys())
print(person.values())
print(person.items())
```

Output:

```text
dict_keys(['name', 'age', 'city'])
dict_values(['Aakash The King', 25, 'Chennai'])
dict_items([('name', 'Aakash The King'), ('age', 25), ('city', 'Chennai')])
```

### `keys()`

Returns a dynamic view of the dictionary's keys.

```python
print(list(person.keys()))
# ['name', 'age', 'city']
```

### `values()`

Returns a dynamic view of the dictionary's values.

```python
print(list(person.values()))
# ['Aakash The King', 25, 'Chennai']
```

### `items()`

Returns a dynamic view of key-value pairs.

```python
print(list(person.items()))
# [('name', 'Aakash The King'), ('age', 25), ('city', 'Chennai')]
```

These views reflect changes to the dictionary.

---

## 8. `pop()` vs `popitem()`

### `pop(key)`

Removes the specified key and returns its value.

```python
d = {
    "name": "Aakash The King",
    "age": 25,
    "city": "Chennai"
}

result = d.pop("age")

print(result)
# 25

print(d)
# {'name': 'Aakash The King', 'city': 'Chennai'}
```

If the key doesn't exist, `pop()` raises `KeyError` unless you provide a default.

```python
print(d.pop("salary", 0))
# 0
```

### `popitem()`

Removes and returns the last inserted key-value pair.

```python
d = {
    "name": "Aakash The King",
    "age": 25,
    "city": "Chennai"
}

result = d.popitem()

print(result)
# ('city', 'Chennai')

print(d)
# {'name': 'Aakash The King', 'age': 25}
```

### Important Difference

| Method | Behavior |
|---|---|
| `pop("age")` | Removes the specified key |
| `popitem()` | Removes the last inserted pair |
| `pop()` without arguments | Raises `TypeError` |

---

## 9. `setdefault()`

Returns the value of a key. If the key doesn't exist, inserts it with the specified default value.

```python
person = {
    "name": "Aakash The King"
}

person.setdefault("city", "Chennai")
person.setdefault("name", "Kumar")

print(person)
# {'name': 'Aakash The King', 'city': 'Chennai'}
```

Explanation:

- `"city"` didn't exist, so it was added.
- `"name"` already existed, so `"Aakash The King"` remained unchanged.

```python
d = {}

result = d.setdefault("age", 25)

print(result)
# 25

print(d)
# {'age': 25}
```

---

## 10. `fromkeys()`

Creates a dictionary using the given keys and a shared initial value.

```python
keys = ["name", "age", "city"]

person = dict.fromkeys(keys, None)

print(person)
# {'name': None, 'age': None, 'city': None}
```

Another example:

```python
keys = ["a", "b", "c"]

data = dict.fromkeys(keys, 0)

print(data)
# {'a': 0, 'b': 0, 'c': 0}
```

### Important: Shared Mutable Values

Avoid using `fromkeys()` to create independent lists for every key.

```python
d = dict.fromkeys(["a", "b"], [])

d["a"].append(10)

print(d)
# {'a': [10], 'b': [10]}
```

Both keys reference the same list.

Use a dictionary comprehension when you need separate lists:

```python
d = {key: [] for key in ["a", "b"]}

d["a"].append(10)

print(d)
# {'a': [10], 'b': []}
```

---

## 11. Removing Dictionary Entries

### `del`

```python
person = {
    "name": "Aakash The King",
    "age": 25
}

del person["age"]

print(person)
# {'name': 'Aakash The King'}
```

`del` removes the specified entry but doesn't return its value.

### `clear()`

```python
person = {
    "name": "Aakash The King",
    "age": 25
}

person.clear()

print(person)
# {}
```

### Quick Comparison

| Operation | Result |
|---|---|
| `del d["key"]` | Removes a specified entry |
| `d.pop("key")` | Removes an entry and returns its value |
| `d.popitem()` | Removes and returns the last inserted pair |
| `d.clear()` | Removes every entry |

---

## 12. Looping Through Dictionaries

### Loop Through Keys

```python
employee = {
    "name": "Aakash The King",
    "role": "Developer",
    "salary": 50000
}

for key in employee:
    print(key)
```

Output:

```text
name
role
salary
```

This is equivalent to:

```python
for key in employee.keys():
    print(key)
```

### Loop Through Values

```python
for value in employee.values():
    print(value)
```

### Loop Through Keys and Values

```python
for key, value in employee.items():
    print(key, ":", value)
```

Output:

```text
name : Aakash The King
role : Developer
salary : 50000
```

---

## 13. Checking Whether a Key Exists

Use `in` and `not in`.

```python
employee = {
    "name": "Aakash The King",
    "salary": 50000
}

print("name" in employee)
# True

print("age" in employee)
# False

print("age" not in employee)
# True
```

**Important:** `in` checks keys by default, not values.

```python
print("Aakash The King" in employee)
# False

print("Aakash The King" in employee.values())
# True
```

---

## 14. Nested Dictionaries

A dictionary can contain other dictionaries.

```python
employees = {
    "E101": {
        "name": "Aakash The King",
        "salary": 50000
    },
    "E102": {
        "name": "Aakash The King",
        "salary": 60000
    }
}

print(employees["E101"]["name"])
# Aakash The King

print(employees["E102"]["salary"])
# 60000
```

### Updating Nested Values

```python
employees["E101"]["salary"] = 55000

print(employees["E101"]["salary"])
# 55000
```

### Adding a Nested Entry

```python
employees["E101"]["city"] = "Chennai"
```

Nested dictionaries are common in JSON data and API responses.

---

## 15. Dictionary Comprehension

Dictionary comprehension creates a dictionary using a compact expression.

### Example 1: Squares

```python
numbers = [1, 2, 3, 4, 5]

squares = {n: n ** 2 for n in numbers}

print(squares)
# {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

### Example 2: With a Condition

```python
numbers = [1, 2, 3, 4, 5, 6]

even_squares = {
    n: n ** 2
    for n in numbers
    if n % 2 == 0
}

print(even_squares)
# {2: 4, 4: 16, 6: 36}
```

### Example 3: Convert Names to Uppercase

```python
names = ["Aakash The King", "Aakash The King", "alex"]

result = {name: name.upper() for name in names}

print(result)
# {'Aakash The King': 'Aakash The King', 'Aakash The King': 'Aakash The King', 'alex': 'ALEX'}
```

---

## 16. Dictionary Copying

### Assignment Is Not a Copy

```python
original = {"name": "Aakash The King", "age": 25}

copy1 = original

copy1["age"] = 30

print(original)
# {'name': 'Aakash The King', 'age': 30}
```

Both variables refer to the same dictionary.

### Using `copy()`

```python
original = {"name": "Aakash The King", "age": 25}

copy2 = original.copy()

copy2["age"] = 30

print(original)
# {'name': 'Aakash The King', 'age': 25}

print(copy2)
# {'name': 'Aakash The King', 'age': 30}
```

`copy()` creates a shallow copy. Nested mutable objects are still shared.

For a deep copy:

```python
import copy

original = {
    "name": "Aakash The King",
    "skills": ["Python", "SQL"]
}

new_data = copy.deepcopy(original)

new_data["skills"].append("React")

print(original["skills"])
# ['Python', 'SQL']
```

---

## 17. Common Mistakes

### Mistake 1: Accessing a Missing Key

```python
d = {"name": "Aakash The King"}

# print(d["age"])  # KeyError

print(d.get("age"))
# None
```

### Mistake 2: Using a List as a Key

```python
# Invalid: list keys are unhashable
# d = {[1, 2]: "value"}
```

Use a tuple of hashable elements instead:

```python
d = {(1, 2): "value"}
```

### Mistake 3: Expecting `pop()` to Remove the Last Entry

```python
d = {"a": 1, "b": 2, "c": 3}

d.pop("a")   # Removes key "a"
d.popitem()  # Removes last remaining inserted pair, ("c", 3)
```

## 18. Interview Questions

### Q1. What is a dictionary?

A mutable data structure that stores key-value pairs.

### Q2. Can dictionary keys be duplicated?

No. A later assignment to the same key replaces its value.

### Q3. Can dictionary values have duplicate values?

Yes. Values don't need to be unique.

### Q4. What is the difference between `get()` and `[]`?

`get()` returns `None` or a specified default for a missing key; `[]` raises `KeyError`.

### Q5. What is the difference between `pop()` and `popitem()`?

`pop(key)` removes a specified key. `popitem()` removes the last inserted pair.

### Q6. What does `items()` return?

A dynamic view of key-value pairs.

### Q7. What is dictionary comprehension?

A concise way to create a dictionary using an expression and optional conditions.

### Q8. What is the difference between `copy()` and assignment?

Assignment creates another reference to the same dictionary. `copy()` creates a shallow copy.

### Q9. Can a dictionary contain another dictionary?

Yes, as a value. A dictionary cannot be a key because it is unhashable.

### Q10. Are dictionaries ordered?

Yes. Python dictionaries preserve insertion order.

---

## 19. Practice Exercises

Try these exercises before checking the expected output.

### Exercise 1: Access a Value

```python
student = {
    "name": "Aakash The King",
    "age": 22,
    "course": "Python"
}

# Print the student's course.
```

Expected output:

```text
Python
```

### Exercise 2: Add and Update

```python
employee = {
    "name": "Aakash The King",
    "salary": 40000
}

# Update salary to 50000.
# Add a department key with value "IT".
```

Expected dictionary:

```python
{'name': 'Aakash The King', 'salary': 50000, 'department': 'IT'}
```

### Exercise 3: Remove a Key

```python
data = {
    "a": 10,
    "b": 20,
    "c": 30
}

# Remove key "b" using pop().
# Print the removed value and the remaining dictionary.
```

Expected removed value: `20`

### Exercise 4: Loop Through Entries

```python
person = {
    "name": "Aakash The King",
    "age": 25,
    "city": "Chennai"
}

# Print each key and value using items().
```

### Exercise 5: Dictionary Comprehension

Create a dictionary where each number from 1 to 5 is a key and its square is the value.

Expected output:

```python
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

### Exercise 6: Count Occurrences

Given:

```python
fruits = ["apple", "banana", "apple", "orange", "banana", "apple"]
```

Create a dictionary counting how many times each fruit appears.

Expected output:

```python
{'apple': 3, 'banana': 2, 'orange': 1}
```

Hint: Use a loop and update a count for each fruit.

### Exercise 7: Filter a Dictionary

Given:

```python
scores = {
    "Aakash The King": 80,
    "Aakash The King": 95,
    "Alex": 65,
    "Priya": 90
}
```

Create a new dictionary containing only students whose score is at least 80.

Expected output:

```python
{'Aakash The King': 80, 'Aakash The King': 95, 'Priya': 90}
```

---

## 20. Quick Revision

- `d[key]` → access a value.
- `d.get(key)` → safely access a value.
- `d[key] = value` → add or update an entry.
- `d.update(...)` → add or update multiple entries.
- `d.keys()` → get keys.
- `d.values()` → get values.
- `d.items()` → get key-value pairs.
- `d.pop(key)` → remove a specified key and return its value.
- `d.popitem()` → remove and return the last inserted pair.
- `d.setdefault(key, default)` → get or initialize a value.
- `dict.fromkeys(keys, value)` → create a dictionary from keys.
- `d.copy()` → create a shallow copy.
- `d.clear()` → empty the dictionary.
- `{key: value for ...}` → dictionary comprehension.

