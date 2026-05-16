# Lesson 3 — Operators (Toán tử)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 2 - Learned variables to store data (string, integer, float). Created variables like `ten = "Minh"` and `tuoi = 25`.

**Current Lesson:** Learning **operators** - symbols that perform operations on data (add, subtract, compare, etc.)

**Future Usefulness:** Operators are essential for any calculation, comparison, or logic in your programs. Every calculator, game, and app uses operators constantly.

**Connection:** Variables store data → Operators manipulate that data. Together they form the foundation of programming logic.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Arithmetic operators (+, -, *, /, //, %, **)
- Comparison operators (==, !=, <, >, <=, >=)
- Assignment operators (+=, -=, etc.)
- Using operators with variables

**Why it matters:** Programs are all about manipulating data. Operators let you calculate, compare, and make decisions.

**Real programmers use it:** Every app, game, and system uses operators for calculations and logic.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### Arithmetic Operators

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `+` | Addition | `5 + 3` | `8` |
| `-` | Subtraction | `5 - 3` | `2` |
| `*` | Multiplication | `5 * 3` | `15` |
| `/` | Division | `15 / 3` | `5.0` |
| `//` | Integer Division | `15 // 4` | `3` |
| `%` | Modulus (remainder) | `15 % 4` | `3` |
| `**` | Exponent (power) | `2 ** 3` | `8` |

### Comparison Operators

These return **True** or **False**:

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `==` | Equal | `5 == 5` | `True` |
| `!=` | Not Equal | `5 != 3` | `True` |
| `>` | Greater Than | `5 > 3` | `True` |
| `<` | Less Than | `5 < 3` | `False` |
| `>=` | Greater or Equal | `5 >= 5` | `True` |
| `<=` | Less or Equal | `5 <= 3` | `False` |

### How It Works

```python
# Math operators
tong = 5 + 3      # tong = 8
hieu = 10 - 4     # hieu = 6
tich = 3 * 4      # tich = 12
thuong = 15 / 3   # thuong = 5.0

# Comparison
print(5 > 3)      # True
print(10 == 10)   # True
print(7 != 7)     # False
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **operator** | A symbol that performs an operation |
| **arithmetic** | Math operations (add, subtract, multiply, divide) |
| **operand** | The value the operator works on |
| **result** | The output of the operation |
| **comparison** | Comparing two values |
| **boolean** | True or False value |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Arithmetic Operators
a = 10
b = 3

print("a + b =", a + b)      # Addition: 13
print("a - b =", a - b)      # Subtraction: 7
print("a * b =", a * b)      # Multiplication: 30
print("a / b =", a / b)      # Division: 3.333...
print("a // b =", a // b)    # Integer division: 3
print("a % b =", a % b)      # Modulus: 1
print("a ** b =", a ** b)    # Exponent: 1000

# Comparison Operators
x = 5
y = 10

print("x == y:", x == y)     # False
print("x != y:", x != y)     # True
print("x > y:", x > y)       # False
print("x < y:", x < y)       # True
print("x >= 5:", x >= 5)     # True
print("y <= 10:", y <= 10)   # True

# Using with variables
so1 = 15
so2 = 7
tong = so1 + so2
print("Tong:", tong)         # Tong: 22
```

**Output:**
```
a + b = 13
a - b = 7
a * b = 30
a / b = 3.3333333333333335
a // b = 3
a % b = 1
a ** b = 1000
x == y: False
x != y: True
x > y: False
x < y: True
x >= 5: True
y <= 10: True
Tong: 22
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example 1: a = 10, b = 3

Operation: a + b
Step 1: Python sees "a + b"
Step 2: Python looks up variable "a" → finds 10
Step 3: Python looks up variable "b" → finds 3
Step 4: Python performs addition: 10 + 3
Step 5: Result is 13
Step 6: print() displays 13

Operation: a // b (integer division)
Step 1: Python calculates 10 / 3 = 3.333...
Step 2: Integer division // drops decimals
Step 3: Result is 3
Step 4: print() displays 3

Operation: a % b (modulus/remainder)
Step 1: 10 divided by 3 = 3 remainder 1
Step 2: Modulus gives the remainder
Step 3: Result is 1
Step 4: print() displays 1
```

```
Example 2: Comparison x = 5, y = 10

Operation: x > y
Step 1: Python sees "x > y"
Step 2: Looks up "x" → 5
Step 3: Looks up "y" → 10
Step 4: Is 5 greater than 10? NO
Step 5: Result is False
Step 6: print() displays False
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
ARITHMETIC OPERATORS:

┌─────────────────────────────────────────┐
│         a = 10, b = 3                   │
├─────────────────────────────────────────┤
│                                         │
│   a + b  →  10 + 3  →  13               │
│   a - b  →  10 - 3  →   7               │
│   a * b  →  10 × 3  →  30               │
│   a / b  →  10 ÷ 3  →  3.33...          │
│   a // b →  10 ÷ 3  →   3 (floor)       │
│   a % b  →  10 ÷ 3  →   1 (remainder)   │
│   a ** b →  10³     → 1000              │
│                                         │
└─────────────────────────────────────────┘

COMPARISON OPERATORS:

┌─────────────────────────────────────────┐
│         x = 5, y = 10                   │
├─────────────────────────────────────────┤
│                                         │
│   x == y  →  5 == 10  →  False         │
│   x != y  →  5 != 10  →  True          │
│   x > y   →  5 > 10    →  False        │
│   x < y   →  5 < 10    →  True         │
│   x >= 5  →  5 >= 5    →  True         │
│   y <= 10 → 10 <= 10   →  True         │
│                                         │
└─────────────────────────────────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Using = instead of ==
```python
if x = 5:  # ERROR! This is assignment, not comparison
```

**Why it fails:** `=` means "assign", `==` means "compare". In if-statements, you need `==`.

**✅ Fix:**
```python
if x == 5:  # Correct - compares x to 5
```

---

### Common Mistake #2 — Confusion between / and //
```python
result = 7 / 2    # result = 3.5 (decimal)
result = 7 // 2   # result = 3 (integer, drops decimal)
```

**Why it matters:** `7/2` gives 3.5 but `7//2` gives 3. Choose based on your needs.

---

### Common Mistake #3 — Modulus confusion
```python
# What does 17 % 5 give?
# 17 ÷ 5 = 3 remainder 2
# So 17 % 5 = 2 (the remainder!)
```

**Key insight:** Modulus always returns the **remainder** after division.

---

### Common Mistake #4 — Integer vs Float confusion
```python
print(10 / 2)    # 5.0 (float!)
print(10 // 2)   # 5 (integer!)
```

**Why it matters:** `/` always returns float, `//` returns integer (when both are integers).

---

### Prevention Strategy

- Remember: `=` is for assignment, `==` is for comparison
- Use `//` when you only want the whole number part
- Use `%` when you want to know what's left over
- Use `/` when you need decimal precision

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- Arithmetic: `+ - * / // % **`
- Comparison returns True/False: `== != > < >= <=`
- `/` gives float, `//` gives integer
- `%` gives remainder after division

### Key Syntax
```python
# Arithmetic
result = a + b
result = a // b  # integer division
result = a % b   # remainder

# Comparison (returns True/False)
is_equal = a == b
is_greater = a > b
```

### Patterns to Remember
```
Math:      a + b, a - b, a * b, a / b, a // b, a % b, a ** b
Compare:   a == b, a != b, a > b, a < b, a >= b, a <= b
```

### Mistakes to Avoid
- ✗ Using `=` instead of `==` in comparisons
- ✗ Confusing `/` with `//`
- ✗ Forgetting modulus returns remainder, not quotient

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What is `17 % 5`?
> **Answer:** `2` (17 ÷ 5 = 3 remainder 2)

---

**Question 2:** What's the difference between `10 / 3` and `10 // 3`?
> **Answer:** `/` gives 3.333... (float), `//` gives 3 (integer)

---

**Question 3:** Fix the error:
```python
if x = 10:
    print("Ten")
```
> **Answer:** Should be `if x == 10:` (double equals for comparison)

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Calculate and print the area of a rectangle with width=5 and height=8.

**Input:** (none - values given)

**Output:**
```
Area = 40
```

**Starter Code:**
```python
width = 5
height = 8

# Calculate area and print
```

**Hints:**
- Area of rectangle = width × height
- Use `*` operator

**✅ Solution:**
```python
width = 5
height = 8
area = width * height
print("Area =", area)  # Output: Area = 40
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Challenge Problem:** Given a=17 and b=5, print:
- Sum (a+b): 22
- Integer division (a//b): 3
- Remainder (a%b): 2

**✅ Solution:**
```python
a = 17
b = 5
print("Sum:", a + b)         # 22
print("Division:", a // b)   # 3
print("Remainder:", a % b)  # 2
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Calculate compound interest
- Principal: 1000
- Rate: 5% per year
- Years: 3

Formula: amount = principal × (1 + rate)^years

**Output:**
```
Amount = 1157.625
```

**✅ Solution:**
```python
principal = 1000
rate = 0.05
years = 3

amount = principal * (1 + rate) ** years
print("Amount =", amount)  # 1157.625
```

**Key Insight:** `**` operator calculates powers for compound interest!

**Extra Challenge:** Try different principal, rate, and years!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- 7 arithmetic operators: +, -, *, /, //, %, **
- 6 comparison operators: ==, !=, >, <, >=, <=
- Difference between / and //
- How modulus (%) works

**Weak points to watch:**
- Confusing `=` with `==`
- Not remembering // drops decimals
- Modulus confusion

**Next growth target:**
- Move to Lesson 4: Conditionals (if/else) - using operators for decisions

**Confidence Check:** Can you calculate `17 % 5` without running code? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 3 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 30 (+10 for completing) |
| **Rank** | Beginner |
| **Mastery** | 20% |
| **Weaknesses** | // vs / confusion |
| **Recommended Focus** | Practice all operators with different values |
| **Suggested Review** | Review operator precedence |
| **Next Lesson Readiness** | Ready for Lesson 4 (Conditionals) |

---

**🎉 You completed Lesson 3!**

Type **4** to continue → Lesson 4 (Conditionals - If/Else)