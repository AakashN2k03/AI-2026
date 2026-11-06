
# Python Method Overloading

## 1. What is Method Overloading?

Method overloading means defining multiple methods with the **same name but different parameters**.

For example:

- `add(10, 20)` → Adds two numbers.
- `add(10, 20, 30)` → Adds three numbers.

The method name is the same, but the number of arguments is different.

Method Overloading comes under **Polymorphism** in OOP.

---

## 2. Method Overloading in C++

C++ supports traditional method overloading.

We can define multiple methods with the same name but different parameters.

### Example

```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    void add(int a, int b) {
        cout << a + b << endl;
    }

    void add(int a, int b, int c) {
        cout << a + b + c << endl;
    }
};

int main() {
    Calculator obj;

    obj.add(10, 20);
    obj.add(10, 20, 30);

    return 0;
}
```

### Output

```text
30
60
```

### Explanation

- Both methods have the same name: `add()`.
- The first method accepts two arguments.
- The second method accepts three arguments.
- C++ automatically selects the appropriate method based on the arguments.

---

## 3. Method Overloading in Python

Python does not support traditional method overloading directly.

If we define multiple methods with the same name in a class, the latest definition replaces the previous one.

### Example

```python
class Calculator:

    def add(self, a, b):
        print(a + b)

    def add(self, a, b, c):
        print(a + b + c)


obj = Calculator()

obj.add(10, 20)
```

### Output

```text
TypeError: Calculator.add() missing 1 required positional argument: 'c'
```

### Why does this happen?

Python keeps only the latest `add()` definition.

The earlier `add()` method is replaced.

---

## 4. How to Achieve Similar Behavior in Python?

We can use default arguments or `*args`.

### Method 1: Using Default Arguments

```python
class Calculator:
    def add(self, a, b, c=0):
        print(a + b + c)


obj = Calculator()

obj.add(10, 20)
obj.add(10, 20, 30)
```

### Output

```text
30
60
```

**Explanation:**

- If we pass two arguments, `c` takes the default value `0`.
- If we pass three arguments, all three values are added.

### Method 2: Using `*args`

```python
class Calculator:
    def add(self, *args):
        print(sum(args))


obj = Calculator()

obj.add(10, 20)
obj.add(10, 20, 30)
obj.add(10, 20, 30, 40)
```

### Output

```text
30
60
100
```

**Explanation:**

- `*args` accepts any number of positional arguments.
- `sum(args)` adds all the received values.

---

## 5. Difference Between C++ and Python

| Feature | C++ | Python |
|---|---|---|
| Traditional method overloading | Supported | Not directly supported |
| Multiple methods with same name | Yes | Latest definition replaces earlier one |
| Selects method based on arguments | Yes | No traditional overload resolution |
| Alternative approach | Method overloading | Default arguments, `*args` |

---

## 6. Key Points to Remember

- Method overloading comes under Polymorphism.
- It means using the same method name with different parameters.
- C++ supports traditional method overloading.
- Python does not support traditional method overloading directly.
- Python can achieve similar behavior using default arguments and `*args`.

### One-Line Definition

**Method Overloading means using the same method name with different parameter lists to perform different operations.**
