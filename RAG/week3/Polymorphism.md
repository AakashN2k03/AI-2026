
# Python Polymorphism

## 1. What is Polymorphism?

Polymorphism means **one thing can take many forms or behave in different ways**.

In Python, the same method can behave differently depending on which object calls it.

- Poly = Many
- Morph = Forms

## 2. Simple Real-World Example

Consider a payment application:

- UPI → Payment through UPI
- Card → Payment through Card
- Cash → Payment through Cash

All three perform payment, but each works differently.

This is called Polymorphism.

## 3. Python Example

```python
class UPI:
    def pay(self):
        print("Payment through UPI")


class Card:
    def pay(self):
        print("Payment through Card")


class Cash:
    def pay(self):
        print("Payment through Cash")


upi = UPI()
card = Card()
cash = Cash()

upi.pay()
card.pay()
cash.pay()
```

### Output

```text
Payment through UPI
Payment through Card
Payment through Cash
```

### Explanation

1. All three classes have the same method name: `pay()`.
2. Each class has its own implementation of `pay()`.
3. When we call `pay()` using different objects, different outputs are produced.

This is Polymorphism.

## 4. Polymorphism Using a Common Function

We can also use one function to handle different objects.

```python
def make_payment(payment_method):
    payment_method.pay()


make_payment(UPI())
make_payment(Card())
make_payment(Cash())
```

### Output

```text
Payment through UPI
Payment through Card
Payment through Cash
```

### Explanation

- We created only one function: `make_payment()`.
- We passed different objects to that function.
- Python executes the appropriate `pay()` method based on the object.

## 5. Key Points to Remember

- Polymorphism means many forms.
- The same method name can have different behaviors.
- Different objects can respond differently to the same method call.
- It helps us write reusable and flexible code.

### One-Line Definition

**Polymorphism is an OOP concept where the same method or interface can behave differently depending on the object using it.**
