# Lesson 33 — Decorators (Trang trí)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 32 - Type hints.

**Current Lesson:** Learning **decorators** - functions that modify other functions.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Basic decorator syntax
- Using @ decorator
- Decorator with arguments

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Basic decorator
def my_decorator(func):
    def wrapper():
        print("Before")
        func()
        print("After")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()

# Decorator with arguments
def timer(func):
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"Took {time.time() - start:.2f}s")
        return result
    return wrapper

@timer
def slow_function():
    import time
    time.sleep(1)
    return "Done"

print(slow_function())

# Decorator for validation
def validate_positive(func):
    def wrapper(*args, **kwargs):
        for arg in args:
            if isinstance(arg, (int, float)) and arg < 0:
                raise ValueError("Must be positive!")
        return func(*args, **kwargs)
    return wrapper

@validate_positive
def divide(a, b):
    return a / b
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** @decorator above function means?
> **Answer:** Function is passed to decorator and modified

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Create a decorator that logs function calls.

```python
def logger(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        result = func(*args, **kwargs)
        print(f"{func.__name__} returned {result}")
        return result
    return wrapper

@logger
def add(a, b):
    return a + b

add(3, 4)
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 33 / 2000 |
| **XP** | 330 |

Type **34** to continue