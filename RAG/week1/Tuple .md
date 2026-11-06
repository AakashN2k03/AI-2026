
# Python Tuples — Complete Notes

## 1. What Is a Tuple?

A tuple is an ordered, immutable collection of elements.

```python
numbers = (10, 20, 30, 40)

print(numbers)
# (10, 20, 30, 40)
```

A tuple can contain different data types.

```python
data = ("Aakash The King", 23, 75000.50, True)

print(data)
# ('Aakash The King', 23, 75000.5, True)
```

### Characteristics of Tuples

- **Ordered:** Elements maintain their order.
- **Immutable:** Elements cannot be replaced, added, or removed directly.
- **Duplicates allowed:** Values can appear multiple times.
- **Indexed:** Indexing starts at `0`.
- **Heterogeneous:** Different data types can be stored together.

---

## 2. Creating Tuples

### Using parentheses

```python
fruits = ("apple", "banana", "orange")
print(type(fruits))
# <class 'tuple'>
```

### Without parentheses

Commas can create a tuple even without parentheses.

```python
numbers = 10, 20, 30

print(numbers)
# (10, 20, 30)

print(type(numbers))
# <class 'tuple'>
```

### Single-element tuple

This is a common interview question.

```python
a = (10)
b = (10,)

print(type(a))
# <class 'int'>

print(type(b))
# <class 'tuple'>
```

**Remember:** The comma makes a single-element tuple.

---

## 3. Accessing Tuple Elements

Tuple indexing works like list indexing.

```python
fruits = ("apple", "banana", "orange")

print(fruits[0])   # apple
print(fruits[1])   # banana
print(fruits[-1])  # orange
print(fruits[-2])  # banana
```

### Indexing Rules

- Positive indexing starts at `0`.
- Negative indexing starts at `-1` for the last element.
- An invalid index raises `IndexError`.

---

## 4. Tuple Slicing

Syntax:

```python
tuple[start:stop:step]
```

The stop index is excluded.

```python
numbers = (10, 20, 30, 40, 50)

print(numbers[1:4])
# (20, 30, 40)

print(numbers[:3])
# (10, 20, 30)

print(numbers[::2])
# (10, 30, 50)

print(numbers[::-1])
# (50, 40, 30, 20, 10)
```

Slicing returns a new tuple.

---

## 5. Tuple Immutability

Tuples cannot be modified in place.

```python
numbers = (10, 20, 30)

numbers[0] = 100
# TypeError: 'tuple' object does not support item assignment
```

Unlike lists, tuples do not support direct item assignment.

### Creating a New Tuple

```python
numbers = (10, 20, 30)

numbers = (100,) + numbers[1:]

print(numbers)
# (100, 20, 30)
```

This creates a new tuple and assigns it to the variable.

---

## 6. Tuple Methods

Tuples have two main methods: `count()` and `index()`.

### count()

Counts how many times a value occurs.

```python
numbers = (10, 20, 10, 30, 10)

print(numbers.count(10))
# 3
```

### index()

Returns the index of the first occurrence of a value.

```python
fruits = ("apple", "banana", "orange", "banana")

print(fruits.index("banana"))
# 1
```

If the value does not exist, `index()` raises `ValueError`.

```python
numbers = (10, 20, 30)

print(numbers.index(50))
# ValueError
```

### Tuple Methods Summary

| Method | Purpose |
|---|---|
| `count(value)` | Counts occurrences |
| `index(value)` | Finds the first matching index |

Tuples do not have `append()`, `remove()`, `sort()`, or `reverse()` methods.

---

## 7. Useful Built-in Functions

Although tuples have only two methods, several built-in functions work with them.

```python
numbers = (10, 20, 30, 40)

print(len(numbers))  # 4
print(min(numbers))  # 10
print(max(numbers))  # 40
print(sum(numbers))  # 100
```

These functions do not modify the tuple.

---

## 8. Tuple Packing and Unpacking

### Packing

Combining multiple values into a tuple.

```python
person = "Harini", 23, "Developer"

print(person)
# ('Harini', 23, 'Developer')
```

### Unpacking

Assigning tuple values to separate variables.

```python
person = ("Harini", 23, "Developer")

name, age, role = person

print(name)  # Harini
print(age)   # 23
print(role)  # Developer
```

The number of variables must match the number of tuple elements unless starred unpacking is used.

### Starred Unpacking

```python
numbers = (10, 20, 30, 40, 50)

first, *middle, last = numbers

print(first)
# 10

print(middle)
# [20, 30, 40]

print(last)
# 50
```

**Note:** The starred variable receives a list.

---

## 9. Tuple vs List

| Feature | List | Tuple |
|---|---|---|
| Syntax | `[1, 2, 3]` | `(1, 2, 3)` |
| Ordered | Yes | Yes |
| Mutable | Yes | No |
| Duplicates allowed | Yes | Yes |
| Indexing | Yes | Yes |
| Slicing | Yes | Yes |
| Methods | Many | `count()`, `index()` |
| Typical use | Data that changes | Fixed collections of values |

### List Example

```python
numbers = [10, 20, 30]

numbers.append(40)
numbers[0] = 100

print(numbers)
# [100, 20, 30, 40]
```

### Tuple Example

```python
numbers = (10, 20, 30)

# numbers.append(40)  # AttributeError
# numbers[0] = 100    # TypeError
```

---

## 10. Can a Tuple Contain a Mutable Object?

Yes! A tuple can contain a list.

```python
data = (10, [20, 30], 40)

data[1].append(50)

print(data)
# (10, [20, 30, 50], 40)
```

Why does this work?

- The tuple's elements cannot be replaced.
- The second element refers to a list.
- The list itself is mutable, so its contents can change.

Tuple immutability does not make nested mutable objects immutable.

---

## 11. Where Are Tuples Used?

### Example 1: Coordinates

```python
location = (13.0827, 80.2707)

latitude, longitude = location

print(latitude)
# 13.0827

print(longitude)
# 80.2707
```

### Example 2: Returning Multiple Values

Python functions can return multiple values, which are packed into a tuple.

```python
def calculate(a, b):
    return a + b, a * b

result = calculate(10, 5)

print(result)
# (15, 50)
```

Unpacking the returned tuple:

```python
total, product = calculate(10, 5)

print(total)    # 15
print(product)  # 50
```

### Example 3: Fixed Configuration Values

```python
screen_size = (1920, 1080)

width, height = screen_size

print(width)   # 1920
print(height)  # 1080
```

---

## 12. Tuple as a Dictionary Key

A tuple can be a dictionary key if all its elements are hashable.

```python
locations = {
    (10, 20): "Point A",
    (30, 40): "Point B"
}

print(locations[(10, 20)])
# Point A
```

A tuple containing a list cannot be used as a dictionary key because lists are unhashable.

```python
# Invalid dictionary key:
# data = {(10, [20, 30]): "Example"}
```

---

## 13. Interview Questions

### Q1. What is a tuple?

A tuple is an ordered, immutable collection of elements.

### Q2. What is the difference between a list and a tuple?

Lists are mutable, while tuples are immutable.

### Q3. How do you create a single-element tuple?

Use a trailing comma: `(10,)`.

### Q4. How many built-in methods do tuples have?

Two main tuple methods: `count()` and `index()`.

### Q5. Can a tuple contain a list?

Yes. The list inside the tuple can be modified, but the tuple's element reference cannot be replaced.

### Q6. Can tuples be dictionary keys?

Yes, if all their elements are hashable.

### Q7. What is tuple unpacking?

Assigning tuple elements to separate variables.

### Q8. What does `[::-1]` do?

Returns a reversed tuple.

### Q9. What is tuple packing?

Combining multiple values into a tuple.

### Q10. Are tuples always more memory-efficient than lists?

Tuples are often smaller than lists for comparable contents, but exact memory usage depends on the objects and Python implementation.

---

## 14. Practice Exercises

Try solving these without checking the answers.

1. Create a tuple containing five numbers.
2. Print the first and last elements.
3. Print every second element using slicing.
4. Reverse a tuple using slicing.
5. Count the number of occurrences of `20` in `(10, 20, 20, 30, 20)`.
6. Find the index of `"Python"` in `("Java", "Python", "C++")`.
7. Create a single-element tuple containing `100`.
8. Unpack `("Harini", 23, "Developer")` into three variables.
9. Explain why `(10)` is not a tuple.
10. Modify a list stored inside a tuple.
11. Return the sum and product of two numbers from a function.
12. Use a tuple as a dictionary key.

---
