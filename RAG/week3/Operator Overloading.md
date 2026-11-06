
# Operator Overloading in Python

## 1. What is Operator Overloading?

Operator overloading is a concept in polymorphism that allows us to define how operators behave when they are used with objects of our own classes.

In simple words, we can customize the behaviour of operators such as `+`, `-`, `*`, `==`, and `>` for our custom objects.

### Example

Python already knows how to use operators with built-in data types.

```python
a = 10
b = 20

print(a + b)  # 30
```

But what happens when we use `+` with two objects?

```python
class Book:
    def __init__(self, pages):
        self.pages = pages

book1 = Book(100)
book2 = Book(200)

print(book1 + book2)
```

**Output:**
```text
TypeError: unsupported operand type(s) for +: 'Book' and 'Book'
```

Python doesn't automatically know what adding two Book objects means.

We need to define that behaviour ourselves.

---

## 2. How to Achieve Operator Overloading?

Python provides special methods called **Magic Methods (Dunder Methods)**.

These methods allow us to customize the behaviour of operators.

| Operator | Magic Method | Purpose |
|---|---|---|
| `+` | `__add__()` | Addition |
| `-` | `__sub__()` | Subtraction |
| `*` | `__mul__()` | Multiplication |
| `/` | `__truediv__()` | Division |
| `==` | `__eq__()` | Equality comparison |
| `>` | `__gt__()` | Greater than |
| `<` | `__lt__()` | Less than |
| `>=` | `__ge__()` | Greater than or equal |
| `<=` | `__le__()` | Less than or equal |

---

## 3. Example: Overloading the + Operator

We can overload the `+` operator using the `__add__()` method.

```python
class Book:
    def __init__(self, pages):
        self.pages = pages

    def __add__(self, other):
        return self.pages + other.pages


book1 = Book(100)
book2 = Book(200)

print(book1 + book2)
```

**Output:**
```text
300
```

### How does it work?

When Python sees:

```python
book1 + book2
```

It internally calls:

```python
book1.__add__(book2)
```

The arguments are assigned as follows:

| Parameter | Receives | Pages |
|---|---|---|
| `self` | `book1` | 100 |
| `other` | `book2` | 200 |

Therefore:

```python
self.pages + other.pages
```

Becomes:

```python
100 + 200
```

Result: `300`

**Important:** `self` and `other` hold references to the objects, not directly to the page values.

- `self` refers to the left-hand object.
- `other` refers to the right-hand object.

---

## 4. Example: Overloading Multiple Operators

We can overload multiple operators in the same class.

```python
class Calculator:
    def __init__(self, value):
        self.value = value

    def __add__(self, other):
        return self.value + other.value

    def __sub__(self, other):
        return self.value - other.value

    def __mul__(self, other):
        return self.value * other.value


a = Calculator(20)
b = Calculator(10)

print(a + b)
print(a - b)
print(a * b)
```

**Output:**
```text
30
10
200
```

Each operator invokes its corresponding magic method.

---

## 5. Example: Overloading the == Operator

We can also customize comparison operators.

```python
class Student:
    def __init__(self, marks):
        self.marks = marks

    def __eq__(self, other):
        return self.marks == other.marks


s1 = Student(90)
s2 = Student(90)
s3 = Student(80)

print(s1 == s2)
print(s1 == s3)
```

**Output:**
```text
True
False
```

Here, `==` compares the marks instead of comparing whether the two variables refer to the same object.

---

## 6. Real-World Example: Wallet

Imagine an application that handles money.

We have two wallet objects, and we want to calculate their combined balance using the `+` operator.

```python
class Wallet:
    def __init__(self, balance):
        self.balance = balance

    def __add__(self, other):
        return self.balance + other.balance


wallet1 = Wallet(500)
wallet2 = Wallet(1000)

total = wallet1 + wallet2

print("Total Balance:", total)
```

**Output:**
```text
Total Balance: 1500
```

---

## 7. Important Points to Remember

1. Operator overloading is a form of polymorphism.
2. Python implements operator overloading using special methods (magic/dunder methods).
3. `+` calls `__add__()`.
4. `-` calls `__sub__()`.
5. `*` calls `__mul__()`.
6. `==` calls `__eq__()`.
7. We decide what an operator should do for our custom objects.
8. Python also uses operator overloading internally for built-in data types.

### Key Takeaway

Operator overloading allows the same operator to perform different operations depending on the data types or objects involved.

For example:
- `10 + 20` performs numerical addition.
- `"Hello " + "Python"` concatenates strings.
- `book1 + book2` can add the page counts if we implement `__add__()`.

---
