# Lesson 28 — Recursion (Đệ quy)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 27 - Advanced function concepts.

**Current Lesson:** Learning **recursion** - function calling itself.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Base case and recursive case
- Stack overflow prevention
- Classic recursion examples

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Factorial with recursion
def factorial(n):
    if n <= 1:
        return 1
    return n * factorial(n-1)

print(factorial(5))  # 120

# Fibonacci
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)

print(fib(6))  # 8

# Count down
def countdown(n):
    if n <= 0:
        print("Done!")
        return
    print(n)
    countdown(n-1)

countdown(3)

# Sum of list
def sum_list(lst):
    if not lst:
        return 0
    return lst[0] + sum_list(lst[1:])

print(sum_list([1, 2, 3, 4, 5]))  # 15
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** factorial(3) = ?
> **Answer:** 6 (3*2*1)

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Reverse string recursively.

```python
def reverse_str(s):
    if len(s) <= 1:
        return s
    return s[-1] + reverse_str(s[:-1])

print(reverse_str("Python"))  # nohtyP
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 28 / 2000 |
| **XP** | 280 |

Type **29** to continue