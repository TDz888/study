# Lesson 27 — More on Functions

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 26 - Map, Filter, Reduce.

**Current Lesson:** Advanced **function concepts** - args, kwargs, decorators.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- *args and **kwargs
- Function annotations
- Higher-order functions

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# *args - variable arguments
def sum_all(*args):
    return sum(args)

print(sum_all(1, 2, 3))  # 6
print(sum_all(1, 2, 3, 4, 5))  # 15

# **kwargs - keyword arguments
def print_info(**kwargs):
    for k, v in kwargs.items():
        print(f"{k}: {v}")

print_info(name="Minh", age=25)

# Combined
def func(*args, **kwargs):
    print("Args:", args)
    print("Kwargs:", kwargs)

func(1, 2, name="Test")

# Default arguments
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

print(greet("Minh"))        # Hello, Minh!
print(greet("Lan", "Hi"))   # Hi, Lan!
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** What does *args do?
> **Answer:** Accepts variable number of positional arguments

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Create function that accepts any number of lists and concatenates.

```python
def concat_all(*lists):
    result = []
    for lst in lists:
        result.extend(lst)
    return result

print(concat_all([1,2], [3,4], [5]))  # [1,2,3,4,5]
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 27 / 2000 |
| **XP** | 270 |

Type **28** to continue