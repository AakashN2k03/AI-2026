# Python OOP: Inheritance, Types of Inheritance, and MRO

## 1. What Is Inheritance?

**Inheritance** is an Object-Oriented Programming (OOP) feature that
allows one class to reuse the attributes and methods of another class.

-   **Parent class / Base class:** The class whose features are
    inherited.
-   **Child class / Derived class:** The class that inherits those
    features.

### Basic example

``` python
class Animal:
    def eat(self):
        print("Animal is eating")


class Dog(Animal):
    def bark(self):
        print("Dog is barking")


dog = Dog()
dog.eat()   # Inherited from Animal
dog.bark()  # Defined in Dog
```

Output:

``` text
Animal is eating
Dog is barking
```

`Dog` can use `eat()` because it inherits from `Animal`.

## 2. Types of Inheritance in Python

The five commonly taught types are:

1.  Single inheritance
2.  Multiple inheritance
3.  Multilevel inheritance
4.  Hierarchical inheritance
5.  Hybrid inheritance

### 2.1 Single Inheritance

One child class inherits from one parent class.

``` python
class Parent:
    def show_parent(self):
        print("Parent class")


class Child(Parent):
    def show_child(self):
        print("Child class")


obj = Child()
obj.show_parent()
obj.show_child()
```

Output:

``` text
Parent class
Child class
```

Structure:

``` text
Parent
   |
 Child
```

### 2.2 Multiple Inheritance

One child class inherits from more than one parent class.

``` python
class Father:
    def skills_from_father(self):
        print("Gardening")


class Mother:
    def skills_from_mother(self):
        print("Cooking")


class Child(Father, Mother):
    pass


obj = Child()
obj.skills_from_father()
obj.skills_from_mother()
```

Output:

``` text
Gardening
Cooking
```

Structure:

``` text
Father     Mother
    \       /
      Child
```

Python uses the order of parent classes in the class definition when
calculating the Method Resolution Order (MRO).

### 2.3 Multilevel Inheritance

A class inherits from a child class, forming an inheritance chain.

``` python
class Grandparent:
    def house(self):
        print("Grandparent's house")


class Parent(Grandparent):
    def car(self):
        print("Parent's car")


class Child(Parent):
    def bike(self):
        print("Child's bike")


obj = Child()
obj.house()
obj.car()
obj.bike()
```

Output:

``` text
Grandparent's house
Parent's car
Child's bike
```

Structure:

``` text
Grandparent
     |
   Parent
     |
   Child
```

### 2.4 Hierarchical Inheritance

Multiple child classes inherit from the same parent class.

``` python
class Animal:
    def eat(self):
        print("Eating")


class Dog(Animal):
    def bark(self):
        print("Barking")


class Cat(Animal):
    def meow(self):
        print("Meowing")


dog = Dog()
dog.eat()
dog.bark()

cat = Cat()
cat.eat()
cat.meow()
```

Output:

``` text
Eating
Barking
Eating
Meowing
```

Structure:

``` text
       Animal
       /    \
     Dog    Cat
```

### 2.5 Hybrid Inheritance

Hybrid inheritance is a combination of two or more inheritance types.

For example, the following combines hierarchical and multiple
inheritance:

``` python
class A:
    def show_a(self):
        print("A")


class B(A):
    def show_b(self):
        print("B")


class C(A):
    def show_c(self):
        print("C")


class D(B, C):
    def show_d(self):
        print("D")


obj = D()
obj.show_a()
obj.show_b()
obj.show_c()
obj.show_d()
```

Output:

``` text
A
B
C
D
```

Structure:

``` text
       A
      / \
     B   C
      \ /
       D
```

Python calculates an MRO for this inheritance structure to determine the
order in which methods are searched.

------------------------------------------------------------------------

## 3. Method Resolution Order (MRO)

**MRO (Method Resolution Order)** is the order Python follows to search
for a method or attribute when it is accessed through an object.

MRO is especially important in multiple and hybrid inheritance, where a
class may inherit from multiple parent classes.

### 3.1 Simple MRO example

``` python
class A:
    def show(self):
        print("A")


class B:
    def show(self):
        print("B")


class C(A, B):
    pass


obj = C()
obj.show()
```

Output:

``` text
A
```

Check the MRO:

``` python
print(C.mro())
```

Output:

``` text
[<class '__main__.C'>,
 <class '__main__.A'>,
 <class '__main__.B'>,
 <class 'object'>]
```

The MRO is:

``` text
C -> A -> B -> object
```

**Why does only A execute?**

Python searches for `show()` in this order:

1.  `C` --- no `show()` method.
2.  `A` --- `show()` is found.
3.  Python executes `A.show()` and stops searching for this call.

It does not execute `B.show()` automatically.

Important distinction:

  Concept                         Result
  ------------------------------- --------------------------
  Complete MRO                    C -\> A -\> B -\> object
  Classes searched for `show()`   C -\> A
  Method executed                 `A.show()`
  Output                          `A`

MRO is the complete search order. It does not mean that every class's
method will execute.

### 3.2 How to inspect MRO

You can inspect MRO in two common ways:

``` python
print(MyClass.mro())
print(MyClass.__mro__)
```

Both show the method resolution order. `mro()` returns a list, while
`__mro__` is a tuple.
