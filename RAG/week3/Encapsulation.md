# Encapsulation in Python

## 1. What is Encapsulation?

Encapsulation is one of the four major pillars of Object-Oriented Programming (OOP).

**Definition:** Encapsulation is the process of combining data (variables) and methods (functions) into a single unit (class), while controlling how that data can be accessed or modified.

In simple words:

- Keep data and the methods that operate on it together.
- Control how external code accesses or modifies that data.
- Prevent accidental or invalid modifications.

### Real-world example: Bank Account

Imagine you have ₹10,000 in your bank account.

You cannot directly modify your bank's internal balance. Instead, you interact with the bank through controlled operations:

- Deposit money.
- Withdraw money.
- Check your balance.

The bank controls how your balance gets modified.

This is the basic idea behind Encapsulation.

---

## 2. Access Modifiers in Python

Python uses naming conventions to indicate different levels of access.

There are three commonly discussed access levels:

| Access level | Syntax | Meaning |
|---|---|---|
| Public | `name` | Accessible from anywhere |
| Protected | `_name` | Intended for internal use and subclasses |
| Private | `__name` | Name-mangled to discourage direct access |

### A. Public Attributes

Public attributes can be accessed and modified from outside the class.

```python
class Student:
    def __init__(self, name):
        self.name = name


student = Student("Aakash")

print(student.name)

student.name = "Rahul"

print(student.name)
```

**Output:**
```text
Aakash
Rahul
```

Here, `name` is public.

### B. Protected Attributes (`_`)

A single underscore indicates that an attribute is intended for internal use or use by subclasses.

```python
class Student:
    def __init__(self, name):
        self._name = name


student = Student("Aakash")

print(student._name)
```

**Output:**
```text
Aakash
```

Important: Python still allows direct access to `_name`.

A single underscore is a naming convention, not strict access protection.

### C. Private Attributes (`__`)

A double leading underscore triggers a Python mechanism called Name Mangling.

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance


account = BankAccount(10000)

print(account.__balance)
```

**Output:**
```text
AttributeError
```

Python internally transforms:

```python
self.__balance
```

Into:

```python
self._BankAccount__balance
```

This makes accidental direct access harder.

---

## 3. What is Name Mangling?

Name Mangling is a mechanism in Python that changes the name of an attribute or method starting with two leading underscores (`__`) inside a class.

Its main purpose is to avoid accidental access and naming conflicts, especially when inheritance is involved.

### Example

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance


account = BankAccount(10000)

print(account._BankAccount__balance)
```

**Output:**
```text
10000
```

Notice that we accessed the private attribute using its mangled name.

### Name Mangling with Inheritance

Imagine both parent and child classes have an attribute with the same name.

```python
class Parent:
    def __init__(self):
        self.__value = 100


class Child(Parent):
    def __init__(self):
        super().__init__()
        self.__value = 200


obj = Child()

print(obj._Parent__value)
print(obj._Child__value)
```

**Output:**
```text
100
200
```

Why?

Python transforms the attributes differently:

- Parent's `__value` becomes `_Parent__value`.
- Child's `__value` becomes `_Child__value`.

So they don't accidentally overwrite each other.

**Important:** Name Mangling is not security. It doesn't make an attribute completely inaccessible. It mainly prevents accidental access and naming conflicts.

---

## 4. What are Getters and Setters?

When an attribute is private, we generally don't want external code to modify it directly.

But we still need ways to:

- Read the value.
- Update the value.
- Validate the new value before updating it.

That's where Getters and Setters come in.

| Method | Purpose |
|---|---|
| Getter | Retrieves the value of an attribute |
| Setter | Updates the value of an attribute, usually with validation |

### Example without Getters and Setters

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance


account = BankAccount(10000)

print(account._BankAccount__balance)
```

We can access the value using Name Mangling, but this bypasses the intended interface.

We should provide proper methods instead.

### Example using Getter and Setter

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance

    # Getter
    def get_balance(self):
        return self.__balance

    # Setter
    def set_balance(self, amount):
        if amount >= 0:
            self.__balance = amount
        else:
            print("Invalid balance")


account = BankAccount(10000)

# Getting the balance
print(account.get_balance())

# Updating the balance
account.set_balance(15000)

print(account.get_balance())

# Trying to set a negative balance
account.set_balance(-500)

print(account.get_balance())
```

**Output:**
```text
10000
15000
Invalid balance
15000
```

### How does it work?

**Getter:**

```python
def get_balance(self):
    return self.__balance
```

It retrieves the private balance.

**Setter:**

```python
def set_balance(self, amount):
    if amount >= 0:
        self.__balance = amount
    else:
        print("Invalid balance")
```

It validates the incoming amount before updating the balance.

---

## 5. What is a Decorator?

A decorator is a Python feature that allows us to modify or extend the behaviour of a function or method without changing its original code directly.

In simple words, a decorator wraps additional functionality around an existing function.

Python uses the `@` symbol to apply decorators.

Example:

```python
@property
def balance(self):
    return self.__balance
```

Here, `@property` changes how the method is accessed.

Instead of calling:

```python
account.balance()
```

We can call:

```python
account.balance
```

`@property` is a built-in Python decorator.

---

## 6. What is the `@property` Decorator?

Python provides a convenient way to implement Getters and Setters using the `@property` decorator.

Instead of calling:

```python
account.get_balance()
account.set_balance(15000)
```

We can access and update the value like a normal attribute:

```python
account.balance
account.balance = 15000
```

But internally, Python calls the getter and setter methods.

### Example using `@property`

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance

    # Getter
    @property
    def balance(self):
        return self.__balance

    # Setter
    @balance.setter
    def balance(self, amount):
        if amount >= 0:
            self.__balance = amount
        else:
            print("Invalid balance")


account = BankAccount(10000)

# Getter
print(account.balance)

# Setter
account.balance = 15000

print(account.balance)

# Invalid update
account.balance = -500

print(account.balance)
```

**Output:**
```text
10000
15000
Invalid balance
15000
```

### How does `@property` work?

#### A. `@property` – Getter

```python
@property
def balance(self):
    return self.__balance
```

When you execute:

```python
print(account.balance)
```

Python automatically calls the getter method.

#### B. `@balance.setter` – Setter

```python
@balance.setter
def balance(self, amount):
    if amount >= 0:
        self.__balance = amount
```

When you execute:

```python
account.balance = 15000
```

Python automatically calls the setter method and passes `15000` as `amount`.

**Important syntax rules:**

- `@property` defines the getter.
- `@attribute_name.setter` defines the setter.
- The setter decorator must use the same name as the property.
- The getter and setter methods use the same method name.

---

## 7. Difference Between Normal Getters/Setters and `@property`

| Normal Getter/Setter | `@property` |
|---|---|
| `get_balance()` | `balance` |
| `set_balance(15000)` | `balance = 15000` |
| Explicit method calls | Attribute-like syntax |
| Traditional approach | Pythonic approach |

Both approaches achieve the same purpose. `@property` provides cleaner attribute-like access.

---

## 8. Real-World Example: LLM Configuration

Imagine developing a RAG application where you need to manage the maximum number of tokens.

```python
class LLMConfig:
    def __init__(self, max_tokens):
        self.__max_tokens = max_tokens

    @property
    def max_tokens(self):
        return self.__max_tokens

    @max_tokens.setter
    def max_tokens(self, value):
        if value > 0:
            self.__max_tokens = value
        else:
            print("Token limit must be positive")


config = LLMConfig(1000)

print(config.max_tokens)

config.max_tokens = 2000

print(config.max_tokens)
```

**Output:**
```text
1000
2000
```

Here, we prevent an invalid token limit from being assigned.

---
## 9. Interview Questions

1. What is Encapsulation in Python?
2. What are the four pillars of OOP?
3. What is the difference between public, protected and private attributes?
4. Does Python support strict private variables?
5. What is Name Mangling?
6. Why does Python use Name Mangling?
7. Is Name Mangling a security mechanism?
8. What are Getters and Setters?
9. What is the difference between a Getter and a Setter?
10. What is the `@property` decorator?
11. What is the purpose of `@attribute.setter`?
12. What is the difference between normal Getters/Setters and `@property`?
13. What is a decorator in Python?
14. How does Encapsulation help with data validation?

--- 
### Key Takeaway

Encapsulation is not just about hiding variables. It is about controlling how an object's internal data is accessed and modified.

---

