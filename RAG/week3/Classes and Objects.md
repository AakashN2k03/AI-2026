# Python OOP: Class, Object, `self`, and `__init__()`

## 1. What is OOP?

**Object-Oriented Programming (OOP)** is a way to organize code using objects that contain data and behavior.

For example, a student has:
- **Data (attributes):** name, age
- **Behavior (methods):** study, introduce

## 2. Class

A **class** is a blueprint used to create objects.

```python
class Student:
    pass
```

- `class` defines a class.
- `Student` is the class name.
- `pass` means the class body is empty for now.

## 3. Object

An **object** is an instance of a class.

```python
class Student:
    pass

s1 = Student()
s2 = Student()

print(type(s1))
```

Example output:

```text
<class '__main__.Student'>
```

`s1` and `s2` are two separate objects created from the `Student` class.

## 4. What is `__init__()`?

`__init__()` is an initializer method that Python calls when an object is created. It is commonly used to initialize the object's attributes.

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

s1 = Student("Aakash The King", 22)
s2 = Student("Priya", 23)

print(s1.name, s1.age)
print(s2.name, s2.age)
```

Output:

```text
Aakash The King 22
Priya 23
```

When `Student("Aakash The King", 22)` runs:
- `name` receives `"Aakash The King"`.
- `age` receives `22`.
- `self.name = name` stores the name on the current object.
- `self.age = age` stores the age on the current object.

**Technical note:** `__new__()` creates the instance; `__init__()` initializes it.

## 5. What is `self`?

`self` refers to the **current instance**.

```python
class Student:
    def __init__(self, name):
        self.name = name

s1 = Student("Aakash The King")
s2 = Student("Priya")

print(s1.name)
print(s2.name)
```

Output:

```text
Aakash The King
Priya
```

When `s1` is initialized, `self` refers to `s1`. When `s2` is initialized, `self` refers to `s2`.

### Understand `self.name = name`

- `self.name` is an attribute stored on the current object.
- `name` is the parameter containing the value passed in.

The name `self` is not a reserved keyword, but it is the standard Python convention.

## 6. Can we create objects without `__init__()`?

**Yes.** Defining your own `__init__()` is optional.

```python
class Student:
    def study(self):
        print("Student is studying")

s1 = Student()
s1.study()
```

Output:

```text
Student is studying
```

You can also assign attributes after creating an object:

```python
class Student:
    pass

s1 = Student()
s1.name = "Aakash The King"
s1.age = 22

print(s1.name, s1.age)
```

Output:

```text
Aakash The King 22
```

If an attribute was never assigned, accessing it raises an `AttributeError`:

```python
s2 = Student()
print(s2.name)  # AttributeError
```

## 7. Why use `__init__()`?

Without an initializer, you may have to assign each object's attributes separately:

```python
class Student:
    pass

s1 = Student()
s1.name = "Aakash The King"
s1.age = 22

s2 = Student()
s2.name = "Priya"
s2.age = 23
```

With `__init__()`, initialization is more concise and consistent:

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

s1 = Student("Aakash The King", 22)
s2 = Student("Priya", 23)
```

For many objects, use a loop:

```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

students_data = [
    ("Aakash The King", 22),
    ("Priya", 23),
    ("Kumar", 21),
]

students = []

for name, age in students_data:
    students.append(Student(name, age))

for student in students:
    print(student.name, student.age)
```

Output:

```text
Aakash The King 22
Priya 23
Kumar 21
```

| Without your own `__init__()` | With `__init__()` |
|---|---|
| Objects can still be created. | Objects can be created with initial data. |
| Attributes can be assigned afterward. | Attributes are initialized during creation. |
| It is easy to forget an attribute. | Required arguments can be enforced by the method signature. |
| Suitable when no custom initialization is needed. | Useful when each object needs initial data or setup. |

## 8. Can we omit `self`?

For a normal instance method, Python automatically passes the current instance as the first argument.

This code fails:

```python
class Student:
    def __init__(name):
        print(name)

s1 = Student("Aakash The King")
```

It raises a `TypeError` because Python passes the instance and `"Aakash The King"`, but the method accepts only one argument.

You can technically use another parameter name:

```python
class Student:
    def __init__(this, name):
        this.name = name

s1 = Student("Aakash The King")
print(s1.name)
```

Output:

```text
Aakash The King
```

However, always prefer `self` because it is the standard Python convention.

## 9. Attributes vs. methods

| Term | Meaning | Example |
|---|---|---|
| Class | Blueprint for instances | `Student` |
| Object / instance | A specific instance | `s1` |
| Attribute | Data associated with an object | `self.name` |
| Method | Function defined inside a class | `study()` |
| `self` | Reference to the current instance | `self.name` |
| `__init__()` | Initializer called during object creation | `def __init__(self, name)` |

