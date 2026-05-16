# Lesson 10 — Modules (Mô-đun)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 9 - Learned functions to create reusable code blocks within a program.

**Current Lesson:** Learning **modules** - using code from other files/programs. The foundation of Python's extensive library.

**Future Usefulness:** Modules let you use millions of pre-written functions. Don't reinvent the wheel - import and use!

**Connection:** Functions organize code within a file → Modules organize code across files. Both promote reusability.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- What is a module
- Importing modules
- Using module functions
- Common standard modules (math, random, datetime)
- Creating your own modules

**Why it matters:** Python's power is its libraries. Want to do math? Import math. Want random numbers? Import random. Everything is a module!

**Real programmers use it:** Every large Python program imports modules. Built-in, third-party, and custom modules.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is a Module?

A module is a **file containing Python code**:
- Functions
- Variables
- Classes
- Can be imported into other files

### Why Use Modules?

1. **Reuse**: Don't rewrite code someone else already wrote
2. **Organize**: Split code into logical files
3. **Share**: Use code across different programs

### How to Import

```python
import math          # Import entire module
print(math.pi)       # Use: module.function

from math import pi  # Import specific item
print(pi)           # Use directly

import math as m     # Import with alias
print(m.pi)         # Use: m.function
```

### Common Modules

| Module | Purpose | Example |
|--------|---------|---------|
| **math** | Math functions | math.sqrt(16) = 4.0 |
| **random** | Random numbers | random.randint(1, 10) |
| **datetime** | Date/time | datetime.now() |
| **os** | Operating system | os.getcwd() |
| **sys** | System info | sys.version |

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **module** | A Python file with code |
| **import** | Bring in a module to use |
| **library** | Collection of modules |
| **package** | Collection of modules |
| **alias** | Nickname for module |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Import entire module
import math

print("Pi:", math.pi)           # 3.141592653589793
print("Square root of 16:", math.sqrt(16))  # 4.0
print("Floor of 4.7:", math.floor(4.7))    # 4
print("Ceiling of 4.1:", math.ceil(4.1))   # 5
print("Power 2^3:", math.pow(2, 3))        # 8.0

# Example 2: Import specific items
from math import pi, sqrt

print("Pi:", pi)               # 3.141592653589793
print("Square root of 9:", sqrt(9))  # 3.0

# Example 3: Import with alias
import random as r

print("Random number 1-10:", r.randint(1, 10))
print("Random float 0-1:", r.random())
print("Choice from list:", r.choice(["apple", "banana", "orange"]))

# Example 4: Datetime module
import datetime

now = datetime.datetime.now()
print("Current time:", now)
print("Year:", now.year)
print("Month:", now.month)
print("Day:", now.day)

# Example 5: OS module
import os

print("Current directory:", os.getcwd())
print("List directory:", os.listdir("."))

# Example 6: Create and import custom module
# (This would be in a separate file called mymodule.py)
# def greet(name):
#     return f"Hello, {name}!"
#
# To use: from mymodule import greet

print("\n--- Common Module Functions ---")
print("abs(-5):", abs(-5))           # 5
print("max([1,5,3]):", max([1, 5, 3]))  # 5
print("min([1,5,3]):", min([1, 5, 3]))  # 1
print("len('hello'):", len("hello"))    # 5
print("type(5):", type(5))             # <class 'int'>
```

**Output:**
```
Pi: 3.141592653589793
Square root of 16: 4.0
Floor of 4.7: 4
Ceiling of 4.1: 5
Power 2^3: 8.0
Pi: 3.141592653589793
Square root of 9: 3.0
Random number 1-10: (varies)
Random float 0-1: (varies)
Choice from list: (varies)
Current time: 2024-01-15 12:30:45.123456
Year: 2024
Month: 1
Day: 15
Current directory: /path/to/dir
List directory: ['file1.py', 'file2.py']

--- Common Module Functions ---
abs(-5): 5
max([1,5,3]): 5
min([1,5,3]): 1
len('hello'): 5
type(5): <class 'int'>
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: import math, math.sqrt(16)

Step 1: Python sees "import math"
Step 2: Python looks for file "math.py"
Step 3: Found! Loads the module into memory
Step 4: Creates namespace "math" with all its functions

Step 5: Python sees "math.sqrt(16)"
Step 6: Finds "sqrt" inside "math" module
Step 7: Executes sqrt(16) = 4.0
Step 8: Returns 4.0

Result: 4.0
```


```
Example: from math import pi

Step 1: Python sees "from math import pi"
Step 2: Loads math module
Step 3: Takes only "pi" from it
Step 4: Adds pi directly to current namespace

Step 5: print(pi) works directly!
(No need for math.pi)
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
IMPORT PROCESS:

┌─────────────────────────────────────────────────┐
│              Your Python File                   │
├─────────────────────────────────────────────────┤
│                                                 │
│   import math                                   │
│        │                                       │
│        ▼                                       │
│   ┌──────────────────────────────────────┐     │
│   │        Python查找math.py             │     │
│   │        (Search for math.py)          │     │
│   └──────────────────┬───────────────────┘     │
│                      │                          │
│                      ▼                          │
│   ┌──────────────────────────────────────┐     │
│   │   Load math module into memory      │     │
│   │   (Load into current program)       │     │
│   └──────────────────┬───────────────────┘     │
│                      │                          │
│                      ▼                          │
│   ┌──────────────────────────────────────┐     │
│   │   Use: math.sqrt(), math.pi, etc.   │     │
│   └──────────────────────────────────────┘     │
│                                                 │
└─────────────────────────────────────────────────┘

NAMESPACES:

┌─────────────┐    ┌─────────────┐
│ math module │    │  Your code  │
├─────────────┤    ├─────────────┤
│ pi          │    │   pi = 3    │  ← can conflict!
│ sqrt()      │    │   x = 10    │
│ floor()     │    └─────────────┘
│ ceil()      │
│ ...         │
└─────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Module Not Found
```python
import maths  # WRONG! Not "maths", it's "math"
```

**Why it fails:** Module is named "math", not "maths".

**✅ Fix:**
```python
import math  # Correct spelling
```

---

### Common Mistake #2 — Wrong Function Name
```python
import math
print(math.squareroot(16))  # WRONG!
print(math.sqrt(16))       # Correct!
```

**Why it fails:** Function is sqrt, not squareroot.

**✅ Fix:** Check the correct function name in documentation.

---

### Common Mistake #3 — Forgetting Module Name
```python
from math import pi
print(sqrt(16))  # ERROR! sqrt not imported, need math.sqrt
```

**Why it fails:** Only imported pi, not sqrt.

**✅ Fix:**
```python
from math import sqrt, pi
print(sqrt(16))  # Now works!
```

---

### Common Mistake #4 — Conflicting Names
```python
import math
pi = 3  # This shadows the math.pi!

print(math.pi)  # Still works
print(pi)        # 3, not 3.14...
```

**Key insight:** Your variables can conflict with module names.

---

### Prevention Strategy

- Check module name spelling (math not maths)
- Check function names (sqrt not squareroot)
- Import what you need: from module import function
- Be aware of name conflicts

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- Modules are Python files with reusable code
- import brings modules into your program
- Use module.function() to call functions
- Many useful modules: math, random, datetime, os

### Key Syntax
```python
import module
from module import function
from module import function as alias
import module as alias
```

### Common Modules
```
math      → sqrt, pi, floor, ceil, pow
random    → randint, random, choice
datetime  → now, date, time
os        → getcwd, listdir, path
sys       → version, argv, exit
```

### Mistakes to Avoid
- ✗ Wrong module name (math not maths)
- ✗ Wrong function name (sqrt not squareroot)
- ✗ Forgetting to import specific items

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** How do you get square root of 16?
```python
import math
# ?
```
> **Answer:** `math.sqrt(16)` → 4.0

---

**Question 2:** What's the output?
```python
import random
print(random.randint(1, 5))
```
> **Answer:** Random integer between 1 and 5 (varies!)

---

**Question 3:** Fix the error:
```python
import maths
print(maths.sqrt(4))
```
> **Answer:** Should be `import math` (not maths!)

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Use math module to calculate the area of a circle with radius 7.

**Input:** radius = 7

**Output:**
```
153.94
```

**Hint:** Area = π × r² (use math.pi and math.pow)

**Starter Code:**
```python
import math

radius = 7
# calculate area

print(f"Area: {area:.2f}")
```

**✅ Solution:**
```python
import math

radius = 7
area = math.pi * math.pow(radius, 2)
print(f"Area: {area:.2f}")  # 153.94
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Challenge:** Generate a random number between 1 and 100.

**Output:**
```
(random number, e.g., 42)
```

**✅ Solution:**
```python
import random

number = random.randint(1, 100)
print(number)
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Create a simple dice simulator.

**Output (example):**
```
Rolling dice...
You rolled: 5
```

**✅ Solution:**
```python
import random

print("Rolling dice...")
dice = random.randint(1, 6)
print(f"You rolled: {dice}")
```

**Key insight:** Use randint(1, 6) for 6-sided dice!

**Extra Challenge:** Simulate rolling TWO dice and show the total!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- Modules are files with reusable code
- import brings modules into your program
- Common modules: math, random, datetime, os
- Using module functions: module.function()

**Weak points to watch:**
- Wrong module/function names
- Forgetting to import

**Next growth target:**
- Move to Lesson 11: File I/O - reading and writing files

**Confidence Check:** Can you import and use a module? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 10 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 100 (+10 for completing) |
| **Rank** | Beginner → Apprentice |
| **Mastery** | 55% |
| **Weaknesses** | Module naming |
| **Recommended Focus** | Practice using common modules |
| **Suggested Review** | Review math and random modules |
| **Next Lesson Readiness** | Ready for Lesson 11 (File I/O) |

---

**🎉 You completed Lesson 10!**

**🎊 LEVEL UP! Rank: Beginner → Apprentice!**

Type **11** to continue → Lesson 11 (File I/O)