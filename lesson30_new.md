# Lesson 30 — Global and Local Variables

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 29 - Variable scope.

**Current Lesson:** Deep dive into **global vs local** variables.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Global variables
- Shadowing
- Best practices

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Global vs local
x = 10  # global

def func():
    x = 5  # local - different from global
    print(f"Inside: {x}")  # 5

func()
print(f"Outside: {x}")  # 10

# Example 2: Modifying global
y = 10

def modify():
    global y
    y = 20

modify()
print(y)  # 20

# Example 3: Shadowing trap
name = "Global"

def greet():
    print(f"Hello, {name}")  # Uses global!

greet()

# Example 4: Avoid globals - pass as parameter
def greet_custom(name):
    print(f"Hello, {name}")

greet_custom("Minh")
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** What prints?
```python
x = 1
def f():
    x = 2
f()
print(x)
```
> **Answer:** 1 (local doesn't affect global)

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Config pattern.

```python
_config = {"debug": True}

def get_config(key):
    return _config.get(key, False)

def set_config(key, value):
    _config[key] = value

set_config("debug", False)
print(get_config("debug"))  # False
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 30 / 2000 |
| **XP** | 300 |

Type **31** to continue