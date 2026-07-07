# Python OOP vs Java OOP

*A Detailed Lecture for Java Learners Transitioning to Python*

---

# Table of Contents

1. Introduction to OOP
2. Classes and Objects
3. Constructors
4. `self` vs `this`
5. Instance Variables (Attributes)
6. Methods
7. Creating Objects
8. Accessing Attributes
9. Inheritance
10. Encapsulation
11. Static Methods
12. Special Methods (`__str__`, `__repr__`)
13. Complete Example
14. Syntax Comparison Table
15. Mental Model
16. Common Beginner Mistakes
17. Key Takeaways

---

# 1. Introduction to OOP

Object-Oriented Programming (OOP) is a programming paradigm that organizes code around **objects** rather than functions.

An object consists of:

* **Attributes (Data)** → Properties of the object
* **Methods (Behavior)** → Actions the object can perform

### Real-world Example

Imagine a car.

**Attributes**

* Brand
* Color
* Speed

**Methods**

* Start
* Stop
* Accelerate

Programming languages represent this using **classes**.

---

# 2. Classes and Objects

A **class** is a blueprint.

An **object** is an actual instance created from that blueprint.

---

## Python

```python
class Car:
    pass

car1 = Car()
car2 = Car()
```

---

## Java

```java
class Car {

}

Car car1 = new Car();
Car car2 = new Car();
```

---

### Visualization

```
             Car Class
                 │
      ┌──────────┴──────────┐
      │                     │
    car1                  car2
```

The class defines the structure.

Objects hold the actual data.

---

# 3. Constructors

A constructor initializes an object when it is created.

---

## Python

Constructors are always named `__init__`.

```python
class Student:

    def __init__(self, name):
        self.name = name
```

Creating an object:

```python
student = Student("Ali")
```

Python automatically calls:

```python
student.__init__("Ali")
```

(Conceptually.)

---

## Java

The constructor has the same name as the class.

```java
class Student {

    String name;

    Student(String name){
        this.name = name;
    }
}
```

Creating the object:

```java
Student student = new Student("Ali");
```

---

## Comparison

| Python               | Java                          |
| -------------------- | ----------------------------- |
| `__init__()`         | Constructor named after class |
| Called automatically | Called automatically          |
| Uses `self`          | Uses `this`                   |

---

# 4. Understanding `self` vs `this`

This is the most important concept.

---

## Python

```python
class Student:

    def __init__(self, name):
        self.name = name
```

---

## Java

```java
class Student {

    String name;

    Student(String name){
        this.name = name;
    }

}
```

---

### What does `self` mean?

`self` refers to **the current object**.

Suppose:

```python
s1 = Student("Ali")
s2 = Student("Ahmed")
```

Conceptually:

```
s1
-------
name = Ali

s2
-------
name = Ahmed
```

When Python executes:

```python
self.name = name
```

For `s1`:

```
Ali is stored inside s1
```

For `s2`:

```
Ahmed is stored inside s2
```

---

### Java Equivalent

```java
this.name = name;
```

Think of:

```
Python     Java
----------------------
self   ==  this
```

---

# 5. Instance Variables (Attributes)

Attributes store data belonging to an object.

---

## Python

```python
class Student:

    def __init__(self, name, age):
        self.name = name
        self.age = age
```

Usage:

```python
student = Student("Ali", 20)

print(student.name)
print(student.age)
```

---

## Java

```java
class Student{

    String name;
    int age;

    Student(String name, int age){

        this.name = name;
        this.age = age;
    }
}
```

Usage:

```java
Student student = new Student("Ali",20);

System.out.println(student.name);
```

---

# 6. Methods

Methods are functions inside a class.

---

## Python

```python
class Student:

    def __init__(self,name):
        self.name = name

    def introduce(self):
        print("Hello")
```

Call:

```python
student.introduce()
```

---

## Java

```java
class Student{

    void introduce(){

        System.out.println("Hello");
    }

}
```

Call:

```java
student.introduce();
```

---

### Behind the Scenes

Python

```python
student.introduce()
```

is conceptually equivalent to

```python
Student.introduce(student)
```

Python automatically passes the object as the first argument (`self`).

Java hides this completely.

---

# 7. Creating Objects

---

## Python

```python
car = Car("Toyota")
```

---

## Java

```java
Car car = new Car("Toyota");
```

Notice:

Python **does not use** the `new` keyword.

---

# 8. Accessing Attributes

---

## Python

```python
print(car.brand)
```

---

## Java

```java
System.out.println(car.brand);
```

Both use the dot operator (`.`).

---

# 9. Inheritance

Inheritance allows one class to reuse another.

---

## Python

```python
class Animal:

    def speak(self):
        print("Some sound")


class Dog(Animal):

    def speak(self):
        print("Bark")


dog = Dog()

dog.speak()
```

Output

```
Bark
```

---

## Java

```java
class Animal{

    void speak(){

        System.out.println("Some sound");

    }

}

class Dog extends Animal{

    @Override
    void speak(){

        System.out.println("Bark");

    }

}
```

---

Comparison

| Python     | Java             |
| ---------- | ---------------- |
| `(Parent)` | `extends Parent` |

---

# 10. Encapsulation

Encapsulation means keeping data and methods together while controlling access.

---

## Java

```java
class Student{

    private String name;

}
```

The variable is truly private.

---

## Python

Convention:

```python
class Student:

    def __init__(self):
        self._name = "Ali"
```

Name mangling:

```python
class Student:

    def __init__(self):
        self.__name = "Ali"
```

Python does **not** enforce true privacy like Java.

---

# 11. Static Methods

Static methods belong to the class instead of individual objects.

---

## Python

```python
class Math:

    @staticmethod
    def square(x):
        return x * x


print(Math.square(5))
```

---

## Java

```java
class Math{

    static int square(int x){

        return x*x;

    }

}
```

---

# 12. Special Methods

Python has many built-in "magic methods."

One common example is `__str__`.

---

Without `__str__`

```python
class Student:

    def __init__(self,name):
        self.name = name

student = Student("Ali")

print(student)
```

Output:

```
<__main__.Student object at 0x...>
```

---

With `__str__`

```python
class Student:

    def __init__(self,name):
        self.name = name

    def __str__(self):
        return self.name


student = Student("Ali")

print(student)
```

Output

```
Ali
```

---

Java equivalent:

```java
@Override
public String toString(){

    return name;

}
```

Comparison:

| Python      | Java         |
| ----------- | ------------ |
| `__str__()` | `toString()` |

---

# 13. Complete Example

## Python

```python
class BankAccount:

    def __init__(self, owner, balance):
        self.owner = owner
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount

    def withdraw(self, amount):
        self.balance -= amount

    def display(self):
        print(f"Owner: {self.owner}")
        print(f"Balance: {self.balance}")


account = BankAccount("Ali", 1000)

account.deposit(500)
account.withdraw(300)

account.display()
```

Output

```
Owner: Ali
Balance: 1200
```

---

## Java

```java
class BankAccount{

    String owner;
    double balance;

    BankAccount(String owner,double balance){

        this.owner = owner;
        this.balance = balance;

    }

    void deposit(double amount){

        balance += amount;

    }

    void withdraw(double amount){

        balance -= amount;

    }

    void display(){

        System.out.println(owner);
        System.out.println(balance);

    }

    public static void main(String[] args){

        BankAccount account =
                new BankAccount("Ali",1000);

        account.deposit(500);
        account.withdraw(300);

        account.display();

    }

}
```

---

# 14. Syntax Comparison Table

| Concept        | Python                                     | Java                       |
| -------------- | ------------------------------------------ | -------------------------- |
| Class          | `class Car:`                               | `class Car {}`             |
| Constructor    | `__init__()`                               | `Car()`                    |
| Current object | `self`                                     | `this`                     |
| Create object  | `Car()`                                    | `new Car()`                |
| Inheritance    | `class Dog(Animal)`                        | `class Dog extends Animal` |
| Method         | `def method()`                             | `returnType method()`      |
| Static method  | `@staticmethod`                            | `static`                   |
| Print          | `print()`                                  | `System.out.println()`     |
| Private        | `_var`, `__var` (convention/name mangling) | `private`                  |
| Braces         | No                                         | Yes                        |
| Semicolons     | No                                         | Yes                        |
| Typing         | Dynamic                                    | Static                     |

---

# 15. Mental Model

Whenever you write:

```python
student = Student("Ali")
```

Think of it as:

1. Create an empty object.
2. Call `__init__()`.
3. Store values inside the object.
4. Return the object.
5. Assign it to `student`.

When you call:

```python
student.introduce()
```

Python internally treats it like:

```python
Student.introduce(student)
```

This is why every instance method receives `self`.

---

# 16. Common Beginner Mistakes

## ❌ Forgetting `self`

Wrong

```python
class Student:

    def greet():
        print("Hello")
```

Correct

```python
class Student:

    def greet(self):
        print("Hello")
```

---

## ❌ Forgetting `self.` for attributes

Wrong

```python
class Student:

    def __init__(self,name):
        name = name
```

This creates only a local variable.

Correct

```python
class Student:

    def __init__(self,name):
        self.name = name
```

Now the value belongs to the object.

---

## ❌ Trying to use `new`

Wrong

```python
student = new Student("Ali")
```

Correct

```python
student = Student("Ali")
```

---

## ❌ Comparing `self` to a keyword

Many beginners think `self` is a keyword.

It is **not**.

You could technically write:

```python
class Student:

    def __init__(me,name):
        me.name = name
```

This works, but **never do it**.

The Python convention is always to use `self`.

---

# 17. Key Takeaways

* A **class** is a blueprint.
* An **object** is an instance of that blueprint.
* `__init__()` is Python's constructor.
* `self` is equivalent to Java's `this`.
* Instance variables are stored using `self.variable`.
* Methods always receive `self` as their first parameter.
* Python creates objects without the `new` keyword.
* Python uses indentation instead of braces `{}`.
* Java requires explicit data types; Python usually does not.
* The OOP concepts are nearly identical in both languages—the biggest difference is Python's cleaner and more concise syntax.

---

# Final Comparison

| Java                          | Python                      |
| ----------------------------- | --------------------------- |
| `this`                        | `self`                      |
| `new Student()`               | `Student()`                 |
| Constructor name = class name | `__init__()`                |
| `extends`                     | `(Parent)`                  |
| `private`                     | `_variable` or `__variable` |
| `{}`                          | Indentation                 |
| Semicolons                    | None                        |
| Static typing                 | Dynamic typing              |
| `toString()`                  | `__str__()`                 |

---

> **One-sentence summary:**
> If you know Java OOP, learning Python OOP is mostly about learning **Python's simpler syntax**, not new object-oriented concepts.
