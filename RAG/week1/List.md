
# Python Lists — Complete Notes

## 1. What Is a List?

A list is an ordered, mutable collection that allows duplicate values and different data types.

```python
numbers = [10, 20, 30, 20]
data = [10, "Hello", 3.14, True]
```

### Key Characteristics
- **Ordered:** Maintains element order.
- **Mutable:** Elements can be added, removed, or modified.
- **Duplicates allowed:** The same value can appear multiple times.
- **Heterogeneous:** Can contain different data types.
- **Indexed:** Indexing starts from `0`.

---

## 2. Accessing List Elements

```python
fruits = ["apple", "banana", "orange"]

print(fruits[0])   # apple
print(fruits[1])   # banana
print(fruits[-1])  # orange
```

### Negative Indexing

| Index | Element |
|---|---|
| `-1` | Last element |
| `-2` | Second-last element |
| `-3` | Third-last element |

---

## 3. List Slicing

Syntax:

```python
list[start:stop:step]
```

The `stop` index is excluded.

```python
numbers = [10, 20, 30, 40, 50]

print(numbers[1:4])  # [20, 30, 40]
print(numbers[:3])   # [10, 20, 30]
print(numbers[2:])   # [30, 40, 50]
print(numbers[::2])  # [10, 30, 50]
print(numbers[::-1]) # [50, 40, 30, 20, 10]
```

---

## 4. Adding Elements

### append()

Adds one item to the end of a list.

```python
numbers = [1, 2, 3]
numbers.append(4)

print(numbers)
# [1, 2, 3, 4]
```

Appending a list adds it as a single nested element:

```python
numbers = [1, 2]
numbers.append([3, 4])

print(numbers)
# [1, 2, [3, 4]]
```

### extend()

Adds each item from an iterable to the list.

```python
numbers = [1, 2]
numbers.extend([3, 4])

print(numbers)
# [1, 2, 3, 4]
```

### insert()

Inserts an item at a specified index.

```python
numbers = [10, 30]
numbers.insert(1, 20)

print(numbers)
# [10, 20, 30]
```

### append() vs extend()

| Method | Behavior |
|---|---|
| `append([3, 4])` | Adds the entire list as one item |
| `extend([3, 4])` | Adds `3` and `4` individually |

---

## 5. Removing Elements

### remove()

Removes the first occurrence of a specified value.

```python
numbers = [10, 20, 30, 20]
numbers.remove(20)

print(numbers)
# [10, 30, 20]
```

If the value doesn't exist, `remove()` raises `ValueError`.

### pop()

Removes and returns an item by index. If no index is supplied, it removes the last item.

```python
numbers = [10, 20, 30]

result = numbers.pop()

print(result)   # 30
print(numbers)  # [10, 20]
```

```python
numbers = [10, 20, 30]
result = numbers.pop(0)

print(result)   # 10
print(numbers)  # [20, 30]
```

### clear()

Removes all items from the list.

```python
numbers = [1, 2, 3]
numbers.clear()

print(numbers)
# []
```

---

## 6. Searching and Counting

### index()

Returns the index of the first occurrence of a value.

```python
fruits = ["apple", "banana", "orange"]

print(fruits.index("banana"))
# 1
```

Raises `ValueError` if the value is not found.

### count()

Counts how many times a value occurs.

```python
numbers = [1, 2, 2, 3, 2]

print(numbers.count(2))
# 3
```

### in operator

Checks whether an item exists in a list.

```python
fruits = ["apple", "banana"]

print("apple" in fruits)  # True
print("orange" in fruits) # False
```

---

## 7. Sorting Lists

### sort()

Sorts the original list in place and returns `None`.

```python
numbers = [3, 1, 2]

result = numbers.sort()

print(numbers)  # [1, 2, 3]
print(result)   # None
```

**Why does `sort()` return `None`?**

`sort()` modifies the existing list instead of creating and returning a new sorted list. Its return value is `None` by design.

Correct usage:

```python
numbers = [3, 1, 2]
numbers.sort()

print(numbers)
# [1, 2, 3]
```

Descending order:

```python
numbers = [3, 1, 2]
numbers.sort(reverse=True)

print(numbers)
# [3, 2, 1]
```

### sorted()

Returns a new sorted list and leaves the original list unchanged.

```python
numbers = [3, 1, 2]

result = sorted(numbers)

print(result)   # [1, 2, 3]
print(numbers)  # [3, 1, 2]
```

Descending order:

```python
print(sorted(numbers, reverse=True))
# [3, 2, 1]
```

### sort() vs sorted()

| Feature | `sort()` | `sorted()` |
|---|---|---|
| Modifies original list | Yes | No |
| Returns sorted list | No, returns `None` | Yes |
| Works with other iterables | No, list method | Yes, for iterables |
| Descending order | `reverse=True` | `reverse=True` |

---

## 8. Reversing a List

`reverse()` reverses the existing order. It does not sort the elements.

```python
numbers = [3, 1, 2]
numbers.reverse()

print(numbers)
# [2, 1, 3]
```

Remember:

- `sort()` sorts values.
- `reverse()` reverses the current order.
- `sorted()` creates a new sorted list.

---

## 9. Copying a List

### copy()

Creates a shallow copy of a list.

```python
original = [10, 20, 30]
copied = original.copy()

copied.append(40)

print(original)  # [10, 20, 30]
print(copied)    # [10, 20, 30, 40]
```

### Assignment vs Copy

```python
a = [1, 2, 3]
b = a

b.append(4)

print(a)  # [1, 2, 3, 4]
print(b)  # [1, 2, 3, 4]
```

Here, `a` and `b` refer to the same list.

Using `copy()`:

```python
a = [1, 2, 3]
b = a.copy()

b.append(4)

print(a)  # [1, 2, 3]
print(b)  # [1, 2, 3, 4]
```

**Note:** `copy()` is shallow. Nested mutable objects are still shared between the original and copied lists.

---

## 10. Other Useful List Operations

```python
numbers = [10, 20, 30]

print(len(numbers))  # 3
print(min(numbers))  # 10
print(max(numbers))  # 30
print(sum(numbers))  # 60
```

Modify an element:

```python
numbers = [10, 20, 30]
numbers[1] = 99

print(numbers)
# [10, 99, 30]
```

Combine lists:

```python
a = [1, 2]
b = [3, 4]

print(a + b)
# [1, 2, 3, 4]
```

Repeat a list:

```python
print([1, 2] * 3)
# [1, 2, 1, 2, 1, 2]
```

---

## 11. Important Concept: Methods That Return None

Some list methods modify the list in place and return `None`.

```python
numbers = [3, 1, 2]

result = numbers.sort()
print(result)  # None
```

Other examples:

```python
numbers = [1, 2]
print(numbers.append(3))  # None

numbers.reverse()
# Returns None

numbers.clear()
# Returns None
```

The operation still works. `None` simply means the method does not return a useful result value.

---


# 12. Python List Comprehension

## 1. What is List Comprehension?

List comprehension is a short way to create a new list from an iterable using a single line of code.

## 2. Syntax

```python
[expression for item in iterable]
```

- `expression`: Value to add to the new list.
- `item`: Variable representing each element.
- `iterable`: List or other iterable to loop through.

## 3. Basic Example

### Normal For Loop

```python
numbers = [1, 2, 3, 4, 5]
squares = []

for num in numbers:
    squares.append(num ** 2)

print(squares)
```

### List Comprehension

```python
numbers = [1, 2, 3, 4, 5]
squares = [num ** 2 for num in numbers]

print(squares)
```

Output:

```text
[1, 4, 9, 16, 25]
```

## 4. List Comprehension with `if`

Filter even numbers:

```python
numbers = [1, 2, 3, 4, 5, 6]
result = [num for num in numbers if num % 2 == 0]

print(result)
```

Output: `[2, 4, 6]`

Syntax:

```python
[expression for item in iterable if condition]
```

## 5. List Comprehension with `if-else`

```python
numbers = [1, 2, 3, 4, 5]
result = ["Even" if n % 2 == 0 else "Odd" for n in numbers]

print(result)
```

Output:

```text
['Odd', 'Even', 'Odd', 'Even', 'Odd']
```



## 13. Interview Questions

### Q1. What is the difference between a list and a tuple?

A list is mutable; a tuple is immutable. Both are ordered and allow duplicates.

### Q2. What is the difference between append() and extend()?

`append()` adds one item. `extend()` adds items from an iterable individually.

### Q3. What is the difference between remove() and pop()?

`remove()` deletes by value. `pop()` deletes by index and returns the removed item.

### Q4. Why does sort() return None?

Because it sorts the original list in place rather than returning a new list.

### Q5. What is the difference between sort() and sorted()?

`sort()` modifies the original list. `sorted()` returns a new sorted list.

### Q6. What happens when you assign one list to another variable?

Both variables refer to the same list unless you create a separate copy.

### Q7. What is slicing?

Slicing extracts part of a sequence using `list[start:stop:step]`.

---

## 13. Practice Exercises

Try solving these without looking at the answers.

1. Create a list of five numbers and print the first and last elements.
2. Add `60` to the end of `[10, 20, 30, 40, 50]`.
3. Use `extend()` to combine `[1, 2]` and `[3, 4]`.
4. Remove the value `20` from `[10, 20, 30]`.
5. Find how many times `5` appears in `[5, 1, 5, 2, 5]`.
6. Sort `[40, 10, 30, 20]` in descending order.
7. Reverse `[1, 2, 3, 4]` without sorting it.
8. Explain why `result = numbers.sort()` assigns `None` to `result`.
9. Explain the difference between `b = a` and `b = a.copy()`.
10. Use slicing to get every second element from `[10, 20, 30, 40, 50, 60]`.

---

## 14. Quick Revision

- Lists are ordered and mutable.
- Indexing starts at `0`.
- Negative indexing starts at `-1` for the last element.
- `append()` adds one item.
- `extend()` adds multiple items from an iterable.
- `insert()` adds an item at a specified index.
- `remove()` removes by value.
- `pop()` removes and returns an item.
- `count()` counts occurrences.
- `index()` finds the first matching index.
- `sort()` modifies the original list and returns `None`.
- `sorted()` returns a new sorted list.
- `reverse()` reverses the current order.
- `copy()` creates a shallow copy.
- `clear()` empties the list.

