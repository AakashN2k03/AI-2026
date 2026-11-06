# Python OOP – Abstraction

## 1. What is Abstraction?

Abstraction means **hiding internal implementation details and showing only the essential functionality to the user.**

### Real-world example: ATM

When we withdraw money from an ATM:
- Insert card.
- Enter PIN.
- Enter amount.
- Receive cash.

We don't need to know how the ATM communicates with the bank server or verifies our PIN internally.

This is Abstraction.

## 2. Abstraction in Python

Python provides the `abc` module to implement abstraction.

Two important concepts:

- **Abstract Class:** A blueprint that defines the common structure for child classes.
- **Abstract Method:** A method declared in an abstract class that concrete child classes must implement.

## 3. Abstract Class

An abstract class is a class that cannot be instantiated directly when it contains unimplemented abstract methods.

We create abstract classes using `ABC`.

```python
from abc import ABC, abstractmethod

class Payment(ABC):
    pass
```

Here:
- `ABC` means Abstract Base Class.
- `Payment` inherits from `ABC`.
- Therefore, it is an abstract base class.

**Note:** A class inheriting from `ABC` without abstract methods can still be instantiated.

## 4. Abstract Method

An abstract method is a method that requires concrete child classes to provide their own implementation.

We use the `@abstractmethod` decorator.

```python
from abc import ABC, abstractmethod

class Payment(ABC):

    @abstractmethod
    def pay(self, amount):
        pass
```

Here:
- `@abstractmethod` marks `pay()` as abstract.
- `pass` means there is no implementation in this example.
- The concrete child class must implement `pay()`.

**Important:** Even if an abstract method contains actual code, it remains abstract as long as it has the `@abstractmethod` decorator.

## 5. Implementing an Abstract Class

Example: Different payment methods.

```python
from abc import ABC, abstractmethod

class Payment(ABC):

    @abstractmethod
    def pay(self, amount):
        pass


class UPI(Payment):

    def pay(self, amount):
        print(f"Paid ₹{amount} using UPI")


class CreditCard(Payment):

    def pay(self, amount):
        print(f"Paid ₹{amount} using Credit Card")


upi = UPI()
card = CreditCard()

upi.pay(500)
card.pay(1000)
```

Output:

```text
Paid ₹500 using UPI
Paid ₹1000 using Credit Card
```

### Explanation

1. `Payment` defines a common structure.
2. It declares `pay()` as an abstract method.
3. `UPI` inherits from `Payment` and implements `pay()`.
4. `CreditCard` also implements `pay()`.
5. Both child classes can now be instantiated.

## 6. What if a Child Class Doesn't Implement the Abstract Method?

```python
class Cash(Payment):
    pass

cash = Cash()
```

Output:

```text
TypeError: Can't instantiate abstract class Cash
with abstract method pay
```

Reason: `Cash` has not implemented the inherited abstract method.

## 7. Can an Abstract Method Have an Implementation?

Yes!

```python
from abc import ABC, abstractmethod

class Payment(ABC):

    @abstractmethod
    def pay(self):
        print("Testing from parent")


class UPI(Payment):

    def pay(self):
        super().pay()
        print("Payment through UPI")


upi = UPI()
upi.pay()
```

Output:

```text
Testing from parent
Payment through UPI
```

Important points:
- An abstract method can contain actual code.
- It is still abstract because of `@abstractmethod`.
- The child must override it before instantiation.
- `super()` can call the parent's implementation.

## 8. Can an Abstract Class Have Multiple Abstract Methods?

Yes!

```python
from abc import ABC, abstractmethod

class Payment(ABC):

    @abstractmethod
    def pay(self, amount):
        pass

    @abstractmethod
    def refund(self, amount):
        pass


class UPI(Payment):

    def pay(self, amount):
        print(f"Paid ₹{amount} using UPI")

    def refund(self, amount):
        print(f"Refunded ₹{amount} using UPI")
```

The child class must implement **all inherited abstract methods** before it can be instantiated.

## 9. Real-World Applications

### Example 1: Payment Gateway

Abstract class: `PaymentGateway`

Abstract method: `pay()`

Child classes:
- Razorpay
- Stripe
- PayPal

Each payment provider implements its own payment logic.

### Example 2: Database Connections

Abstract class: `Database`

Abstract methods:
- `connect()`
- `execute_query()`
- `disconnect()`

Child classes:
- MySQL
- PostgreSQL
- MongoDB

Each database implements its own connection and query logic.

### Example 3: AI / LLM Integration

Abstract class: `LLMProvider`

Abstract method: `generate_response()`

Child classes:
- OpenAI
- Gemini
- Claude

Each provider implements its own response-generation logic.

## 10. Abstract Class vs Abstract Method

| Abstract Class | Abstract Method |
|---|---|
| Blueprint for child classes | Defines required method behaviour |
| Created using `ABC` | Created using `@abstractmethod` |
| Can contain normal and abstract methods | Can contain an implementation or just `pass` |
| Cannot be instantiated while abstract methods remain unimplemented | Must be implemented by concrete child classes |

## 11. Abstraction vs Encapsulation

| Encapsulation | Abstraction |
|---|---|
| Protects and controls access to data | Hides implementation complexity |
| Focuses on data and access | Focuses on essential functionality |
| Uses private attributes, properties and methods | Uses abstract classes and methods |
| Example: Private bank balance | Example: Common payment interface |

## 12. Why Do We Need Abstraction?

Suppose an application supports multiple payment methods.

Without abstraction, we might have to manage many payment-specific conditions in different places.

With abstraction:
- Define a common structure.
- Make every child class implement required methods.
- Add new implementations without changing the common interface.
- Make applications easier to extend and maintain.

**Important:** Abstraction does not automatically improve execution speed. Its main benefit is better software design and maintainability.

## 13. Important Rules to Remember

1. Import `ABC` and `abstractmethod` from the `abc` module.
2. Inherit from `ABC` to create an abstract base class.
3. Use `@abstractmethod` to declare abstract methods.
4. An abstract class with unimplemented abstract methods cannot be instantiated.
5. A child class must implement all inherited abstract methods to become instantiable.
6. An abstract method can contain actual code.
7. An abstract class can contain normal methods too.
8. An abstract class can contain multiple abstract methods.
9. Inheriting from `ABC` alone does not prevent instantiation.

## 14. Interview Questions

1. What is abstraction in Python?
2. What is an abstract class?
3. What is an abstract method?
4. Why do we use the `abc` module?
5. Can we instantiate an abstract class?
6. Can an abstract method contain actual code?
7. Can an abstract class have normal methods?
8. What happens if a child class doesn't implement an abstract method?
9. Can an abstract class contain multiple abstract methods?
10. What is the difference between abstraction and encapsulation?
---