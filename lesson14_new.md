# Lesson 14 — Inheritance (Kế thừa)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 13 - Learned classes and objects. Grouping data and methods together.

**Current Lesson:** Learning **Inheritance** - classes can inherit from other classes. Reuse and extend code.

**Future Usefulness:** OOP relies heavily on inheritance. Building class hierarchies for real-world modeling.

**Connection:** Classes group code → Inheritance lets classes share code. Child class gets parent's attributes/methods.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Parent and child classes
- Using super()
- Method overriding
- Multiple inheritance
- isinstance()

**Why it matters:** Don't repeat code! Dog class can inherit from Animal class, adding only what's unique to dogs.

**Real programmers use it:** Framework classes inherit from base classes. Django, Flask all use inheritance.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is Inheritance?

A child class inherits attributes and methods from a parent class:
```
Animal (parent)
  ↓ inherits
Dog (child) - gets all Animal attributes + its own
```

### Syntax

```python
class Parent:
    # attributes and methods

class Child(Parent):
    # inherits everything from Parent
    # plus its own additions
```

-------------------------------------------------------------------------------
4. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Basic inheritance
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        return "Some sound"

class Dog(Animal):  # Dog inherits from Animal
    def speak(self):
        return "Woof!"

dog = Dog("Max")
print(dog.name)      # Max (inherited)
print(dog.speak())  # Woof! (overridden)

# Example 2: Using super()
class Cat(Animal):
    def __init__(self, name, color):
        super().__init__(name)  # call parent's __init__
        self.color = color      # add new attribute
    
    def speak(self):
        return "Meow!"

cat = Cat("Whiskers", "orange")
print(cat.name)   # Whiskers (from parent)
print(cat.color)  # orange (new)

# Example 3: Multiple inheritance
class Animal:
    def __init__(self, name):
        self.name = name

class Swimmer:
    def swim(self):
        return "Swimming..."

class Duck(Animal, Swimmer):  # inherits from both
    def speak(self):
        return "Quack!"

duck = Duck("Donald")
print(duck.name)   # Donald (from Animal)
print(duck.swim()) # Swimming... (from Swimmer)
print(duck.speak()) # Quack!

# Example 4: isinstance
print(isinstance(dog, Dog))    # True
print(isinstance(dog, Animal)) # True (Dog is subclass of Animal)
print(isinstance(dog, str))    # False
```

-------------------------------------------------------------------------------
5. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Forgetting to call super()
```python
class Dog(Animal):
    def __init__(self, name, breed):
        self.name = name      # Missing super().__init__(name)!
        self.breed = breed
```

**Fix:** Always call super().__init__() in child __init__

---

### Common Mistake #2 — Method Override
```python
class Parent:
    def greet(self):
        return "Hello"

class Child(Parent):
    def greet(self):  # Overrides parent's greet
        return "Hi there!"
```

This is correct - child can override parent methods.

-------------------------------------------------------------------------------
6. MINI TEST
-------------------------------------------------------------------------------

**Question:** What prints?
```python
class A:
    def test(self):
        return "A"

class B(A):
    pass

b = B()
print(b.test())
```
> **Answer:** "A" (inherits from A)

-------------------------------------------------------------------------------
7. BONUS CHALLENGE
-------------------------------------------------------------------------------

Create a Vehicle base class with Car and Motorcycle subclasses.

**✅ Solution:**
```python
class Vehicle:
    def __init__(self, brand):
        self.brand = brand

class Car(Vehicle):
    def __init__(self, brand, doors):
        super().__init__(brand)
        self.doors = doors

class Motorcycle(Vehicle):
    def __init__(self, brand, engine):
        super().__init__(brand)
        self.engine = engine

car = Car("Toyota", 4)
print(car.brand, car.doors)  # Toyota 4
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 14 / 2000 |
| **XP** | 140 |
| **Rank** | Apprentice |

---

Type **15** to continue → Lesson 15