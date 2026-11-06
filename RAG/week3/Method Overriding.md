
# Python Method Overriding

## 1. What is Method Overriding?

Method overriding happens when a **parent class and child class have a method with the same name**, and the child class provides its own implementation.

In simple words:

The child class changes the behavior of an inherited method.

## 2. Simple Example

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

### Explanation

1. Child inherits from Parent.
2. Both classes have a method named `show()`.
3. Child provides its own implementation of `show()`.
4. When we call `obj.show()`, the Child method executes instead of the Parent method.

This is called **Method Overriding**.

---

## 3. What Happens If We Don't Override?

```python
class Parent:
    def show(self):
        print("This is Parent class")


class Child(Parent):
    pass


obj = Child()
obj.show()
```

### Output

```text
This is Parent class
```

Here, Child does not have its own `show()` method.

Therefore, Python uses the inherited method from Parent.

---

## 4. When Do We Use Method Overriding?

We use method overriding when a child class needs different behavior from the parent class.

### Example: Payment Application

```python
class Payment:
    def pay(self):
        print("Processing payment")


class UPI(Payment):
    def pay(self):
        print("Processing UPI payment")


class Card(Payment):
    def pay(self):
        print("Processing Card payment")


upi = UPI()
card = Card()

upi.pay()
card.pay()
```

### Output

```text
Processing UPI payment
Processing Card payment
```

Here:
- Parent provides a general `pay()` method.
- UPI overrides it with UPI payment behavior.
- Card overrides it with Card payment behavior.

---

## 5. Conditions for Method Overriding

1. Inheritance must exist between the parent and child classes.
2. Both classes must have a method with the same name.
3. The child class provides its own implementation.
4. The child method should generally maintain a compatible set of parameters with the parent method.

---

### One-Line Definition

**Method overriding is an OOP concept where a child class provides its own implementation of a method already defined in its parent class.**
