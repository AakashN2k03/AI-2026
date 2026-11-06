
# Python Strings and String Methods

## 1. What Is a String?

A string is a sequence of characters enclosed in single, double, or triple quotes.

```python
name = "Python"
message = 'Hello World'
description = """Python is easy to learn."""
```

### Types of String Quotes

```python
a = 'Hello'
b = "Hello"
c = """Hello
World"""

print(a)  # Hello
print(b)  # Hello
print(c)
# Hello
# World
```

---

## 2. Characteristics of Strings

- **Ordered:** Characters maintain their order.
- **Indexed:** Indexing starts at `0`.
- **Immutable:** Individual characters cannot be modified in place.
- **Iterable:** We can loop through each character.
- **Duplicates allowed:** Characters can repeat.

### Example

```python
text = "Python"

print(text[0])   # P
print(text[-1])  # n
```

---

## 3. String Immutability

Strings are immutable, meaning their characters cannot be changed in place.

```python
text = "hello"

text[0] = "H"  # TypeError
```

Instead, create a new string and assign it to the variable.

```python
text = "hello"
text = "H" + text[1:]

print(text)  # Hello
```

### Why Doesn't upper() Change the Original String?

```python
text = "hello"

text.upper()
print(text)  # hello
```

`upper()` returns a new string. Since we didn't store its result, `text` remains `"hello"`.

Correct approach:

```python
text = "hello"

text = text.upper()
print(text)  # HELLO
```

We can also print the result directly:

```python
text = "hello"
print(text.upper())  # HELLO
```

**Remember:** `text.upper()` doesn't modify the original string. `text = text.upper()` assigns the new string to `text`.

This behavior also applies to `lower()`, `replace()`, `strip()`, and `title()`.

---

## 4. String Indexing

Indexing accesses individual characters.

```python
language = "Python"

print(language[0])   # P
print(language[1])   # y
print(language[2])   # t
print(language[-1])  # n
print(language[-2])  # o
```
---

## 5. String Slicing

Syntax:

```python
string[start:stop:step]
```

- `start`: Starting index, included.
- `stop`: Ending index, excluded.
- `step`: Number of positions to move each time.

```python
word = "PythonProgramming"

print(word[0:6])   # Python
print(word[:6])    # Python
print(word[6:])    # Programming
print(word[::2])   # PtoPormig
print(word[::-1])  # gnimmargorPnohtyP
```
---

## 6. Changing Letter Case

### upper()

Converts all letters to uppercase.

```python
text = "hello python"
print(text.upper())

# HELLO PYTHON
```

### lower()

Converts all letters to lowercase.

```python
text = "HELLO PYTHON"
print(text.lower())

# hello python
```

### capitalize()

Capitalizes the first character and lowercases the remaining characters.

```python
text = "hELLO PYTHON"
print(text.capitalize())

# Hello python
```

### title()

Capitalizes the beginning of each word.

```python
text = "hello python world"
print(text.title())

# Hello Python World
```

---

## 7. Removing Whitespace

### strip()

Removes whitespace from both ends.

```python
text = "   Hello   "
print(text.strip())

# Hello
```

### lstrip()

Removes whitespace from the left side.

```python
text = "   Hello   "
print(text.lstrip())

# "Hello   "
```

### rstrip()

Removes whitespace from the right side.

```python
text = "   Hello   "
print(text.rstrip())

# "   Hello"
```

These methods are useful when cleaning input from users, files, and APIs.

---

## 8. Replacing Text

The `replace()` method replaces occurrences of a substring.

```python
text = "I like Java"
result = text.replace("Java", "Python")

print(result)
# I like Python

print(text)
# I like Java
```

The original string remains unchanged.

You can limit the number of replacements:

```python
text = "apple apple apple"

print(text.replace("apple", "orange", 2))
# orange orange apple
```

---

## 9. split() Method

The `split()` method separates a string into a list.

```python
text = "Python is easy"

result = text.split()

print(result)
# ['Python', 'is', 'easy']
```

Split using a comma:

```python
text = "apple,banana,orange"

print(text.split(","))
# ['apple', 'banana', 'orange']
```

The default separator is whitespace.

---

## 10. join() Method

The `join()` method combines strings from an iterable into a single string.

```python
words = ["Python", "is", "easy"]

print(" ".join(words))
# Python is easy

print("-".join(words))
# Python-is-easy

print(",".join(words))
# Python,is,easy
```

The string before `.join()` specifies the separator.

### split() vs join()

| Method | Purpose | Result type |
|---|---|---|
| `split()` | Splits a string | List |
| `join()` | Combines strings | String |

---

## 11. Searching and Counting

### find()

Returns the index of the first occurrence of a substring, or `-1` if not found.

```python
text = "banana"

print(text.find("n"))  # 2
print(text.find("a"))  # 1 
print(text.find("z"))  # -1
```

### count()

Counts non-overlapping occurrences of a substring.

```python
text = "banana"

print(text.count("a"))  # 3
print(text.count("n"))  # 2
```

### in Operator

Checks whether a substring exists.

```python
text = "Python programming"

print("Python" in text)  # True
print("Java" in text)    # False
```

---

## 12. Checking String Content

| Method | Purpose | Example | Output |
|---|---|---|---|
| `startswith()` | Checks the beginning | `"Python".startswith("Py")` | `True` |
| `endswith()` | Checks the ending | `"file.pdf".endswith(".pdf")` | `True` |
| `isalpha()` | Checks whether all characters are letters | `"Hello".isalpha()` | `True` |
| `isdigit()` | Checks whether all characters are digits | `"123".isdigit()` | `True` |
| `isalnum()` | Checks whether all characters are letters or digits | `"Python123".isalnum()` | `True` |
| `isspace()` | Checks whether all characters are whitespace | `"   ".isspace()` | `True` |

These `is...()` methods return `False` for an empty string.

Note: `isdigit()` accepts some Unicode digit characters, not just ASCII `0`–`9`.

---

## 13. String Concatenation

Concatenation means combining strings using `+`.

```python
first = "Hello"
second = "Python"

print(first + " " + second)

# Hello Python
```

### Combining Strings and Numbers

This causes a `TypeError`:

```python
age = 23
print("Age: " + age)
```

Convert the number to a string:

```python
age = 23
print("Age: " + str(age))

# Age: 23
```

---

## 14. F-Strings

F-strings provide a convenient way to insert variables and expressions into strings.

```python
name = "Aakash The King"
age = 23

print(f"My name is {name} and I am {age} years old.")

# My name is Aakash The King and I am 23 years old.
```

You can also include expressions:

```python
a = 10
b = 20

print(f"Total: {a + b}")

# Total: 30
```

F-strings are commonly used for readable output, logging, and formatting messages.

---

## 15. Looping Through a String

Strings are iterable, so we can access each character using a loop.

```python
text = "Python"

for char in text:
    print(char)
```

Output:

```text
P
y
t
h
o
n
```

### Count Characters

```python
text = "Python"

print(len(text))  # 6
```

`len()` returns the number of characters in a string.

---

## 16. Important String Methods Summary

| Method | Purpose |
|---|---|
| `upper()` | Convert to uppercase |
| `lower()` | Convert to lowercase |
| `capitalize()` | Capitalize first character |
| `title()` | Capitalize the beginning of each word |
| `strip()` | Remove whitespace from both ends |
| `lstrip()` | Remove whitespace from the left |
| `rstrip()` | Remove whitespace from the right |
| `replace()` | Replace a substring |
| `split()` | Split into a list |
| `join()` | Combine strings |
| `find()` | Find a substring index |
| `count()` | Count occurrences |
| `startswith()` | Check the beginning |
| `endswith()` | Check the ending |
| `isalpha()` | Check for letters |
| `isdigit()` | Check for digits |
| `isalnum()` | Check for letters or digits |
| `isspace()` | Check for whitespace |

---

## 17. Interview Questions

### Q1. What is a string?

A string is an immutable sequence of characters.

### Q2. What does immutable mean?

The string's contents cannot be changed in place. String methods return new strings when they transform text.

### Q3. Why doesn't `text.upper()` update the original string?

Because `upper()` returns a new string and does not modify the original string.

### Q4. What is the difference between `find()` and `index()`?

Both find a substring's position. `find()` returns `-1` when it isn't found, while `index()` raises `ValueError`.

### Q5. What is the difference between `split()` and `join()`?

`split()` converts a string into a list of substrings. `join()` combines strings into one string.

### Q6. What is the difference between `strip()` and `replace()`?

`strip()` removes whitespace or specified characters from the ends. `replace()` replaces matching substrings throughout the string.

### Q7. What does `[::-1]` do?

It creates a reversed copy of the string.

### Q8. What is an f-string?

An f-string allows variables and expressions to be embedded inside a string using `{}`.

---

## 18. Practice Exercises

Try these without checking the solutions.

1. Convert `"hello python"` to uppercase.
2. Convert `"PYTHON"` to lowercase.
3. Reverse `"Programming"` using slicing.
4. Remove extra whitespace from `"   Hello World   "`.
5. Replace `"Java"` with `"Python"` in `"I like Java"`.
6. Split `"red,green,blue"` into a list.
7. Join `["AI", "Engineer"]` using a space.
8. Count how many times `"a"` appears in `"banana"`.
9. Check whether `"report.pdf"` ends with `".pdf"`.
10. Write an f-string that prints a person's name and age.
11. Explain why `text.upper()` doesn't modify the original string.
12. Find the index of `"o"` in `"Python"` using `find()`.

---


