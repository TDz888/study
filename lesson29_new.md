# Lesson 29 — Scope (Phạm vi)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 28 - Recursion.

**Current Lesson:** Understanding **variable scope** - where variables can be accessed.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Local, global, nonlocal
- global keyword
- Closure basics

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Local scope
def func():
    local_var = "I'm local"
    print(local_var)

# Global scope
global_var = "I'm global"

def func2():
    global global_var
    global_var = "Modified!"
    print(global_var)

print(global_var)  # I'm global
func2()            # Modified!
print(global_var)  # Modified! (changed)

# Nonlocal (in nested function)
def outer():
    x = "outer"
    def inner():
        nonlocal x
        x = "modified"
        print(x)
    inner()
    print(x)

outer()

# Closure example
def make_adder(n):
    def adder(x):
        return x + n
    return adder

add5 = make_adder(5)
print(add5(10))  # 15
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** How to modify global variable inside function?
> **Answer:** Use "global" keyword

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Create counter function using closure.

```python
def make_counter():
    count = 0
    def counter():
        nonlocal count
        count += 1
        return count
    return counter

c = make_counter()
print(c(), c(), c())  # 1 2 3
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 29 / 2000 |
| **XP** | 290 |

Type **30** to continue