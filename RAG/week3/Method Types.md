# Python Method Types in OOP

Python has three main types of methods inside a class:

1. Instance Method
2. Class Method
3. Static Method

## 1. Instance Method

An instance method works with an individual object.

- It uses `self` as its first parameter.
- `self` refers to the current object.
- It can access and modify instance variables.

### Example

```python
class Employee:

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def display(self):
        print(self.name, self.age)


e1 = Employee("Aakash", 23)
e2 = Employee("Rahul", 25)

e1.display()
e2.display()
```

**Output:**

```text
Aakash 23
Rahul 25
```

Here:
- When `e1.display()` is called, `self` refers to `e1`.
- When `e2.display()` is called, `self` refers to `e2`.

### When to use?

Use instance methods when you need to work with an individual object's data.

Examples:
- Display employee details.
- Deposit money into a particular bank account.
- Generate a response using a particular LLM model.

---

## 2. Class Method

A class method works with the class itself rather than an individual object.

- It uses `cls` as its first parameter.
- `cls` refers to the current class.
- It can access and modify class variables.
- It is defined using the `@classmethod` decorator.

### Example

```python
class Employee:

    company = "Fusion Practice"

    @classmethod
    def change_company(cls, new_company):
        cls.company = new_company


Employee.change_company("OpenAI")

print(Employee.company)
```

**Output:**

```text
OpenAI
```

Here:
- `cls` refers to the Employee class.
- `cls.company` accesses the class variable.
- We can call the method directly using the class name.
- We don't need to create an object.


### When to use?

Use class methods when:
- You need to access or modify class variables.
- You want to perform an operation related to the class itself.

---

## 3. Static Method

A static method is a method inside a class that doesn't automatically receive `self` or `cls`.

- It doesn't depend on individual object data.
- It doesn't require class data.
- It is defined using the `@staticmethod` decorator.
- Object creation is not mandatory.

### Example

```python
class Calculator:

    @staticmethod
    def add(a, b):
        return a + b


print(Calculator.add(10, 20))
```

**Output:**

```text
30
```

Notice that we called the method directly using the class name.

We can also call it using an object:

```python
calc = Calculator()

print(calc.add(10, 20))
```

### Real-world Example

```python
class BankAccount:

    def __init__(self, balance):
        self.balance = balance

    @staticmethod
    def is_valid_amount(amount):
        return amount > 0

    def deposit(self, amount):
        if BankAccount.is_valid_amount(amount):
            self.balance += amount
            print("Deposit successful")
        else:
            print("Invalid amount")


account = BankAccount(1000)

account.deposit(500)
account.deposit(-200)

print(account.balance)
```

**Output:**

```text
Deposit successful
Invalid amount
1500
```

Here:
- `deposit()` is an instance method because it modifies an individual account's balance.
- `is_valid_amount()` is a static method because it only validates the given amount.

### When to use?

Use static methods for:
- Input validation.
- Mathematical calculations.
- Formatting and conversion.
- Utility functions related to a class.

---

## 4. Difference Between All Three Methods

| Feature | Instance Method | Class Method | Static Method |
|---|---|---|---|
| Decorator | Not required | `@classmethod` | `@staticmethod` |
| First parameter | `self` | `cls` | None automatically |
| Works with | Individual object | Class | Independent logic |
| Access instance variables | Yes | No automatic access | No automatic access |
| Access class variables | Yes | Yes | No automatic access |
| Object required to call? | Normally yes | No | No |

**Important:** A static method can still access class variables by explicitly referring to the class name. It just doesn't receive `cls` automatically.

---


## 5. Quick Revision

Remember these three points:

- **Instance Method:** Works with an individual object using `self`.
- **Class Method:** Works with the class using `cls`.
- **Static Method:** Performs related operations without automatically receiving `self` or `cls`.

