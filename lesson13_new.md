# Lesson 13 — Classes and Objects (Lớp và Đối tượng)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 12 - Learned exception handling to deal with errors gracefully.

**Current Lesson:** Learning **Classes and Objects** - the foundation of Object-Oriented Programming (OOP). Grouping data and functions together.

**Future Usefulness:** Large programs use OOP - organized, reusable, maintainable code. Django, Flask, all frameworks use classes.

**Connection:** Functions group code → Classes group data AND code together. The next level of organization.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- What is a class
- What is an object
- Creating classes with attributes and methods
- The __init__ method
- Self parameter
- Creating multiple objects

**Why it matters:** OOP is how real software is built. Grouping related data and functions into "objects" that can be reused.

**Real programmers use it:** Every large application uses classes to model real-world concepts.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is a Class?

A class is a **blueprint** for creating objects:
- Defines what data (attributes) an object has
- Defines what actions (methods) an object can do

### What is an Object?

An object is a **specific instance** created from a class:
- Class = blueprint, Object = actual house built from blueprint
- Multiple objects can be created from one class

### Class vs Object

```
Class: Dog (blueprint)
  - attributes: name, breed, age
  - methods: bark(), eat()

Object: My dog "Max" (actual dog)
  - name = "Max"
  - breed = "Poodle"
  - age = 3
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **class** | Blueprint for creating objects |
| **object** | Instance of a class |
| **attribute** | Data/variable in a class |
| **method** | Function in a class |
| **__init__** | Constructor method - runs when object created |
| **self** | Reference to the object itself |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Basic class
print("=== Basic Class ===")
class Dog:
    # Class attribute (shared by all objects)
    species = "Canis familiaris"
    
    # Constructor - runs when object is created
    def __init__(self, name, age):
        # Instance attributes (unique to each object)
        self.name = name
        self.age = age
    
    # Method (function inside class)
    def bark(self):
        return f"{self.name} says Woof!"
    
    def get_info(self):
        return f"{self.name} is {self.age} years old"

# Create objects (instances)
my_dog = Dog("Max", 3)
your_dog = Dog("Buddy", 5)

print(my_dog.name)        # Max
print(your_dog.age)        # 5
print(my_dog.bark())      # Max says Woof!
print(Dog.species)        # Canis familiaris (class attribute)

# Example 2: Class with methods
print("\n=== More Methods ===")
class Calculator:
    def __init__(self):
        self.result = 0
    
    def add(self, x):
        self.result += x
        return self
    
    def subtract(self, x):
        self.result -= x
        return self
    
    def get_result(self):
        return self.result

calc = Calculator()
calc.add(10).add(5).subtract(3)
print(calc.get_result())  # 12

# Example 3: String representation
print("\n=== __str__ method ===")
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def __str__(self):
        return f"Person: {self.name}, Age: {self.age}"

p = Person("Minh", 25)
print(p)  # Uses __str__
```

**Output:**
```
=== Basic Class ===
Max
5
Max says Woof!
Canis familiaris

=== More Methods ===
12

=== __str__ method ===
Person: Minh, Age: 25
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: Dog("Max", 3)

Step 1: Python sees Dog("Max", 3)
Step 2: Creates new empty object
Step 3: Calls __init__(self, "Max", 3)
Step 4: Inside __init__:
        - self.name = "Max"
        - self.age = 3
Step 5: Returns the object
Step 6: Variable my_dog points to that object


Method call: my_dog.bark()

Step 1: Python sees my_dog.bark()
Step 2: Finds the Dog class
Step 3: Calls bark method with self = my_dog
Step 4: Inside bark: return f"{self.name} says Woof!"
Step 5: self.name = "Max"
Step 6: Returns "Max says Woof!"
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
CLASS STRUCTURE:

┌─────────────────────────────────────────────┐
│            class Dog                        │
├─────────────────────────────────────────────┤
│                                             │
│  CLASS ATTRIBUTES:                          │
│    species = "Canis familiaris"             │
│                                             │
│  ─────────────────────────────────────────  │
│                                             │
│  __init__(self, name, age):                 │
│    self.name = name      ← instance attr    │
│    self.age = age        ← instance attr    │
│                                             │
│  ─────────────────────────────────────────  │
│                                             │
│  METHODS:                                   │
│    bark(self):         ← function           │
│    get_info(self):     ← function           │
│                                             │
└─────────────────────────────────────────────┘

OBJECTS:

┌──────────────────┐     ┌──────────────────┐
│   my_dog         │     │   your_dog       │
├──────────────────┤     ├──────────────────┤
│  name: "Max"     │     │  name: "Buddy"   │
│  age: 3          │     │  age: 5          │
│  species: (same) │     │  species: (same) │
└──────────────────┘     └──────────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Forgetting self
```python
class Dog:
    def bark():  # ERROR! Missing self
        print("Woof!")
```

**Why it fails:** Methods need self as first parameter.

**✅ Fix:**
```python
def bark(self):
    print("Woof!")
```

---

### Common Mistake #2 — Forgetting __init__
```python
class Dog:
    name = "Max"  # Class attribute, not instance!
    
dog1 = Dog()
print(dog1.name)  # Max - works but wrong approach
```

**Why it fails:** Without __init__, can't pass different values.

**✅ Fix:**
```python
class Dog:
    def __init__(self, name):
        self.name = name
```

---

### Common Mistake #3 — Confusing class vs instance attributes
```python
class Dog:
    species = "Dog"  # Class - shared!
    
dog1 = Dog()
dog2 = Dog()
dog1.species = "Cat"  # Creates instance attribute only for dog1!
print(dog1.species)  # Cat (instance)
print(dog2.species)  # Dog (class)
```

---

### Prevention Strategy

- Always include self in method definitions
- Use __init__ to set instance attributes
- Understand difference between class and instance attributes

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- Classes are blueprints, objects are instances
- __init__ initializes new objects
- self refers to the current object
- Methods are functions inside classes

### Key Syntax
```python
class ClassName:
    def __init__(self, param1, param2):
        self.attr1 = param1
        self.attr2 = param2
    
    def method(self):
        # code
```

### Patterns
```
class Name:         → define class
def __init__(self): → constructor
self.attribute      → instance attribute
ClassName.attribute → class attribute
```

### Mistakes to Avoid
- ✗ Forgetting self in methods
- ✗ Not using __init__ for custom attributes

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What does __init__ do?
> **Answer:** Constructor - runs when object is created to initialize attributes

---

**Question 2:** What's the output?
```python
class Cat:
    def __init__(self, name):
        self.name = name
    
    def meow(self):
        return f"{self.name} says Meow!"

cat = Cat("Whiskers")
print(cat.meow())
```
> **Answer:** "Whiskers says Meow!"

---

**Question 3:** What's missing?
```python
class Car:
    def drive():
        print("Driving")
```
> **Answer:** Need `self` parameter: `def drive(self):`

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Create a Student class with name and grade attributes.

**✅ Solution:**
```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade
    
    def passed(self):
        return self.grade >= 50

student = Student("Minh", 85)
print(student.name)    # Minh
print(student.passed()) # True
```

---

**Difficulty:** ★☆☆☆☆

**Challenge:** Add a method to calculate average of 3 grades.

**✅ Solution:**
```python
class Student:
    def __init__(self, name, g1, g2, g3):
        self.name = name
        self.g1 = g1
        self.g2 = g2
        self.g3 = g3
    
    def average(self):
        return (self.g1 + self.g2 + self.g3) / 3

s = Student("Lan", 80, 90, 85)
print(s.average())  # 85.0
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Create a BankAccount class.

**Features:**
- deposit(amount)
- withdraw(amount)
- check balance

**✅ Solution:**
```python
class BankAccount:
    def __init__(self, balance=0):
        self.balance = balance
    
    def deposit(self, amount):
        self.balance += amount
        return f"Deposited {amount}, new balance: {self.balance}"
    
    def withdraw(self, amount):
        if amount > self.balance:
            return "Insufficient funds!"
        self.balance -= amount
        return f"Withdrew {amount}, new balance: {self.balance}"
    
    def get_balance(self):
        return self.balance

account = BankAccount(100)
print(account.deposit(50))    # 150
print(account.withdraw(30))   # 120
print(account.get_balance()) # 120
```

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- Classes are blueprints, objects are instances
- __init__ initializes objects
- Methods use self to access object data

**Next growth target:**
- Lesson 14: Inheritance

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 13 / 2000 |
| **Chapter** | 2 - Control Flow & Functions |
| **XP** | 130 |
| **Rank** | Apprentice |

---

Type **14** to continue → Lesson 14 (Inheritance)