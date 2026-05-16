# Lesson 4 — Conditionals (Điều kiện If/Else)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 3 - Learned operators for math (+, -, *, /, //, %, **) and comparison (==, !=, >, <, >=, <=). These return True or False.

**Current Lesson:** Learning **conditionals** - using those True/False values to make decisions in your program.

**Future Usefulness:** Every program makes decisions - login systems, games, apps all use if/else to respond differently based on conditions.

**Connection:** Operators create conditions (True/False) → Conditionals use those to decide what code runs.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- The if statement - running code only when condition is True
- The else statement - running code when condition is False
- The elif statement - multiple conditions
- Comparison operators in real decisions
- Indentation in Python

**Why it matters:** Programs aren't useful without decisions. "If user entered correct password, let them in. Otherwise, show error."

**Real programmers use it:** Every app uses conditionals - from simple checks to complex AI logic.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### The Basic If Statement

```python
if condition:
    # code runs ONLY if condition is True
```

**Key:** The code after `if` MUST be indented (tabbed in).

### If-Else Structure

```python
if condition:
    # runs if True
else:
    # runs if False
```

### If-Elif-Else Structure

```python
if condition1:
    # runs if condition1 is True
elif condition2:
    # runs if condition1 is False but condition2 is True
else:
    # runs if all conditions are False
```

### How It Works

```python
tuoi = 18

if tuoi >= 18:
    print("Ban la nguoi lon")  # This runs!
else:
    print("Ban la tre con")    # This does NOT run
```

```
tuoi = 18

Is 18 >= 18 ? → YES → True
       ↓
Enter the if block
       ↓
Print: "Ban la nguoi lon"
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **conditional** | A statement that checks a condition and acts based on it |
| **if** | "If this is true, do this" |
| **else** | "Otherwise (if false), do this" |
| **elif** | Short for "else if" - checking another condition |
| **condition** | An expression that evaluates to True or False |
| **indentation** | The spaces/tabs at the start of a line |
| **block** | A group of code statements together |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Simple if
diem = 75

if diem >= 50:
    print("Ban do qua mon!")

# Example 2: if-else
diem = 40

if diem >= 50:
    print("Ban do qua mon!")
else:
    print("Ban khong qua mon!")

# Example 3: if-elif-else
diem = 85

if diem >= 90:
    print("Grade: A")
elif diem >= 80:
    print("Grade: B")
elif diem >= 70:
    print("Grade: C")
elif diem >= 60:
    print("Grade: D")
else:
    print("Grade: F")

# Example 4: Multiple conditions
tuoi = 25
has_license = True

if tuoi >= 18 and has_license:
    print("Ban duoc lai xe!")
else:
    print("Ban khong duoc lai xe.")
```

**Output:**
```
Example 1: Ban do qua mon!
Example 2: Ban khong qua mon!
Example 3: Grade: B
Example 4: Ban duoc lai xe!
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: diem = 85 with if-elif-else

Line 1: diem = 85

Line 2: if diem >= 90:
         Check: Is 85 >= 90? NO → False
         Skip this block

Line 3: elif diem >= 80:
         Check: Is 85 >= 80? YES → True
         Enter this block
         Print: "Grade: B"
         Skip remaining elif/else

FINAL OUTPUT: Grade: B
```

```
Example: Multiple conditions with "and"

tuoi = 25, has_license = True

if tuoi >= 18 and has_license:
         │
         ├─ Check tuoi >= 18 → 25 >= 18 → True
         │
         ├─ Check has_license → True
         │
         ├─ True and True → True
         │
         └─ Enter block, print "Ban duoc lai xe!"
```

**Variable Changes:** None - conditionals don't change variables, they just control which code runs.

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
IF-ELSE FLOW CHART:

    ┌──────────────┐
    │  Condition  │
    │   (True?)   │
    └──────┬───────┘
           │
     ┌─────┴─────┐
     │           │
   YES          NO
     │           │
     ▼           ▼
┌─────────┐  ┌─────────┐
│   IF    │  │  ELSE   │
│  block  │  │  block  │
└─────────┘  └─────────┘
     │           │
     └─────┬─────┘
           │
           ▼
     Continue...


IF-ELIF-ELSE FLOW:

    ┌──────────────┐
    │  cond1 True?│
    └──────┬───────┘
           │
     ┌─────┴─────┐
   YES          NO
     │           │
     ▼           ▼
┌─────────┐  ┌──────────────┐
│ block1  │  │ cond2 True?  │
└─────────┘  └──────┬───────┘
     │           │
     │     ┌─────┴─────┐
     │   YES          NO
     │     │           │
     │     ▼           ▼
     │  ┌─────────┐  ┌─────────┐
     │  │ block2  │  │  ELSE   │
     │  └─────────┘  └─────────┘
     │     │           │
     └─────┴───────────┘
           │
           ▼
     Continue...
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Missing Colon
```python
if diem >= 50    # ERROR! Missing colon
    print("Do")
```

**Why it fails:** The colon `:` tells Python "this is the start of a condition block"

**✅ Fix:**
```python
if diem >= 50:   # Correct - has colon
    print("Do")
```

---

### Common Mistake #2 — Wrong Indentation
```python
if diem >= 50:
print("Do")  # ERROR! Not indented
```

**Why it fails:** Python uses indentation to know which code belongs to the if block. No indentation = not part of the block.

**✅ Fix:**
```python
if diem >= 50:
    print("Do")  # Correct - indented
```

---

### Common Mistake #3 — Using = instead of ==
```python
diem = 50
if diem = 50:  # ERROR! Assignment, not comparison
    print("Do")
```

**Why it fails:** `=` assigns, `==` compares.

**✅ Fix:**
```python
if diem == 50:  # Correct - comparison
    print("Do")
```

---

### Common Mistake #4 — Forgetting to Check All Cases
```python
# What if diem is exactly 60?
if diem > 70:
    print("Pass")
elif diem > 60:
    print("Good")
else:
    print("Fail")

# For diem = 60:
# - 60 > 70? No
# - 60 > 60? No (60 is NOT greater than 60)
# - Goes to else → prints "Fail" ← WRONG for 60!
```

**Key insight:** Use `>=` for ranges, not just `>`

---

### Prevention Strategy

- Always add `:` after if/elif/else
- Always indent the block code
- Use `==` for comparison, `=` for assignment
- Test boundary values (exactly at the threshold)

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- `if` checks condition → runs block if True
- `else` runs when if is False
- `elif` checks another condition
- Indentation defines which code is in which block
- Colon `:` marks the start of a condition

### Key Syntax
```python
if condition:
    # code

if condition:
    # code
else:
    # code

if condition1:
    # code
elif condition2:
    # code
else:
    # code
```

### Patterns to Remember
```
if → else
if → elif → else
if → elif → elif → else
```

### Mistakes to Avoid
- ✗ Forgetting colon `:`
- ✗ Not indenting the block
- ✗ Using `=` instead of `==`
- ✗ Wrong comparison operators (use >= not > for ranges)

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What prints?
```python
x = 5
if x > 3:
    print("A")
else:
    print("B")
```
> **Answer:** `A` (5 > 3 is True)

---

**Question 2:** What's wrong?
```python
if x = 10:
    print("Ten")
```
> **Answer:** Should be `==` not `=` (comparison, not assignment)

---

**Question 3:** What prints?
```python
score = 75
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
else:
    print("C")
```
> **Answer:** `C` (75 doesn't meet >= 90 or >= 80)

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Write a program that checks if a number is even or odd.

**Input:** A number (let's say number = 7)

**Output:**
```
Odd
```

**Starter Code:**
```python
number = 7

# Write your if-else here
```

**Hints:**
- Use modulus `%` - even numbers have remainder 0 when divided by 2
- If number % 2 == 0 → even
- Otherwise → odd

**✅ Solution:**
```python
number = 7

if number % 2 == 0:
    print("Even")
else:
    print("Odd")
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Challenge:** Check if a person can vote (age >= 18)

**Input:** age = 17

**Output:**
```
Cannot vote
```

**✅ Solution:**
```python
age = 17

if age >= 18:
    print("Can vote")
else:
    print("Cannot vote")
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Determine the larger of two numbers

**Input:** a = 15, b = 23

**Output:**
```
23 is larger
```

**✅ Solution:**
```python
a = 15
b = 23

if a > b:
    print(a, "is larger")
elif b > a:
    print(b, "is larger")
else:
    print("Both are equal")
```

**Key Insight:** Can also use `max(a, b)` for simpler solution!

**Extra Challenge:** Find the largest of THREE numbers!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- if statement for conditional execution
- else for alternative execution
- elif for multiple conditions
- Indentation and colon syntax
- Using operators in real decisions

**Weak points to watch:**
- Forgetting colon
- Wrong indentation
- Using = instead of ==
- Boundary value errors

**Next growth target:**
- Move to Lesson 5: Loops (For) - repeating code with conditions

**Confidence Check:** Can you write an if-else to check if a number is positive? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 4 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 40 (+10 for completing) |
| **Rank** | Beginner |
| **Mastery** | 25% |
| **Weaknesses** | Indentation errors |
| **Recommended Focus** | Practice if-elif-else with different conditions |
| **Suggested Review** | Review comparison and logical operators |
| **Next Lesson Readiness** | Ready for Lesson 5 (For Loops) |

---

**🎉 You completed Lesson 4!**

Type **5** to continue → Lesson 5 (For Loops)