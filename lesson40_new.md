# Lesson 40 — Multiple Inheritance

-------------------------------------------------------------------------------
1. TODAY'S MISSION
-------------------------------------------------------------------------------

Class inheriting from multiple parent classes.

-------------------------------------------------------------------------------
2. MAIN CODE
-------------------------------------------------------------------------------

```python
class Animal:
    def speak(self):
        return "Sound"

class Walker:
    def walk(self):
        return "Walking"

class Dog(Animal, Walker):
    pass

d = Dog()
print(d.speak())  # Sound
print(d.walk())   # Walking
```

---

**Lesson 41 — Method Resolution Order (MRO)**
```python
class A: pass
class B: pass
class C(A, B): pass

print(C.__mro__)  # Shows inheritance order
```

---

**Lesson 42 — Abstract Classes**
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, r):
        self.r = r
    def area(self):
        return 3.14 * self.r ** 2
```

---

**Lesson 43 — Dataclasses**
```python
from dataclasses import dataclass

@dataclass
class Person:
    name: str
    age: int
    
p = Person("Minh", 25)
print(p)  # Person(name='Minh', age=25)
```

---

**Lesson 44 — Enums**
```python
from enum import Enum

class Color(Enum):
    RED = 1
    GREEN = 2
    BLUE = 3

print(Color.RED.name)  # RED
print(Color.RED.value) # 1
```

---

**Lessons 45-50:**
- Working with JSON
- Command line arguments (sys.argv)
- Virtual environments
- pip and packages
- Working with APIs
- Error logging

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 40-50 / 2000 |
| **XP** | 400-500 |

Type **51** to continue