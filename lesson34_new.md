# Lesson 34 — Generators (Bộ tạo)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 33 - Decorators.

**Current Lesson:** Learning **generators** - memory-efficient iterators.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Generator functions with yield
- Generator expressions
- next() and iter()

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Generator function
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

gen = count_up_to(5)
print(next(gen))  # 1
print(next(gen))  # 2
print(list(gen))  # [3, 4, 5]

# Generator expression
squares = (x**2 for x in range(5))
print(list(squares))  # [0, 1, 4, 9, 16]

# Using with for
def fib_gen(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

for num in fib_gen(10):
    print(num, end=" ")
print()

# Memory efficient
def large_range(n):
    for i in range(n):
        yield i

# Doesn't create list in memory!
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** What does yield do?
> **Answer:** Pauses function and returns value, keeps state

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Create infinite number generator.

```python
def natural_numbers():
    n = 1
    while True:
        yield n
        n += 1

gen = natural_numbers()
print(next(gen), next(gen), next(gen))  # 1 2 3
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 34 / 2000 |
| **XP** | 340 |

Type **35** to continue