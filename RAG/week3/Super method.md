
# Python `super()` Function

## 1. What is `super()`?

`super()` is used in a child class to access and reuse methods from its parent class.

It helps us avoid writing the same code again.

## 2. Simple Example

```python
class Parent:
    def show(self):
        print("This is Parent class")


class Child(Parent):
    def show(self):
        super().show()
        print("This is Child class")


obj = Child()
obj.show()
```

### Output

```text
This is Parent class
This is Child class
```

### How does it work?

1. `obj.show()` calls the Child class method.
2. `super().show()` calls the Parent class method.
3. After that, the remaining Child class code executes.

## 3. Without `super()`

```python
class Parent:
    def show(self):
        print("This is Parent class")


class Child(Parent):
    def show(self):
        print("This is Child class")


obj = Child()
obj.show()
```

### Output

```text
This is Child class
```

The Parent method does not execute because the Child method overrides it and doesn't call `super()`.

## 4. Using `super()` with `__init__()`

We can also use `super()` to call the parent class constructor.

```python
class Parent:
    def __init__(self):
        print("Parent constructor")


class Child(Parent):
    def __init__(self):
        super().__init__()
        print("Child constructor")


obj = Child()
```

### Output

```text
Parent constructor
Child constructor
```

## 5. Key Points

- `super()` helps a child class reuse parent class methods.
- It avoids code duplication.
- It can be used with normal methods and `__init__()`.
- The parent method executes only when we explicitly call it using `super()`.

### Remember

**`super()` = Reuse functionality from the parent class.**
