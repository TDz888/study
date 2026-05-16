# Lesson 2 — Variables (Biến)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 1 - Learned `print()` to display text on screen. Text must be wrapped in quotes: `"Hello"`.

**Current Lesson:** Learning **variables** - how to store and use data in your programs.

**Future Usefulness:** Variables are the foundation of every program. You'll use them constantly for storing user input, calculations, game scores, and more.

**Connection:** If `print()` is the mouth (output), variables are the memory (storage). Programs need to remember things, just like you need a notepad.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- What is a variable (a container for storing data)
- How to create and use variables
- Basic data types: string, integer, float
- Using variables with print()

**Why it matters:** Without variables, programs can't remember anything. Every piece of data your program works with is stored in a variable.

**Real programmers use it:** Every program uses variables - from simple scripts to complex AI systems.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is a Variable?

A **variable** is like a labeled box:
- The **label** (variable name) identifies the box
- The **content** (value) is what you store inside

```
┌─────────────────────┐
│      ten            │  ← Variable name (label)
│  ┌───────────────┐  │
│  │    "Minh"     │  │  ← Value (content)
│  └───────────────┘  │
└─────────────────────┘
```

### Creating Variables

```python
ten = "Minh"     # Create variable named 'ten' with value "Minh"
```

The `=` sign means "assign" - put the right side into the left side.

### Basic Data Types

| Type | Description | Example |
|------|-------------|---------|
| **string** | Text (wrapped in quotes) | `"Minh"`, `"Hello"` |
| **integer** | Whole numbers | `25`, `100`, `-5` |
| **float** | Decimal numbers | `1.75`, `3.14`, `-0.5` |

### Using Variables

```python
# Create variables
ten = "Minh"
tuoi = 25

# Use them in print
print(ten)           # Prints: Minh
print("Toi ten la", ten)  # Prints: Toi ten la Minh
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **variable** | A container (box) that stores data |
| **assign** | The `=` operator - puts a value into a variable |
| **string** | Text data - characters inside quotes |
| **integer** | Whole number (no decimal) |
| **float** | Decimal number (has decimal point) |
| **value** | The actual data stored in a variable |
| **naming** | Giving a variable its unique identifier |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Creating variables of different types
ten = "Minh"           # string - text data
tuoi = 25              # integer - whole number
chieu_cao = 1.75       # float - decimal number

# Printing variables
print(ten)
print(tuoi)
print(chieu_cao)

# Combining text and variables
print("Toi ten la", ten)
print("Toi", tuoi, "tuoi")
```

**Output:**
```
Minh
25
1.75
Toi ten la Minh
Toi 25 tuoi
```

**Code Breakdown:**
```python
ten = "Minh"     # name = value  → creates box named 'ten' with "Minh"
     │    │
     │    └── the value (text string)
     │
     └── the variable name (label)

print(ten)       # looks up box named 'ten' → gets "Minh" → prints it
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

Let's trace the computer's thinking:

```
STEP 1: ten = "Minh"
        │
        ├─ Creates a memory box labeled "ten"
        ├─ Puts "Minh" inside that box
        └─ Box now contains: "Minh"

STEP 2: tuoi = 25
        │
        ├─ Creates memory box labeled "tuoi"  
        ├─ Puts 25 inside (as integer)
        └─ Box now contains: 25

STEP 3: print(ten)
        │
        ├─ Python sees print() function
        ├─ Python sees 'ten' inside parentheses
        ├─ Python looks up box labeled "ten"
        ├─ Python finds "Minh" inside
        └─ Prints: Minh

STEP 4: print("Toi ten la", ten)
        │
        ├─ Sees "Toi ten la" → that's a string → print it
        ├─ Sees comma → adds a space
        ├─ Sees 'ten' → looks up box → finds "Minh"
        └─ Prints: Toi ten la Minh
```

**Variable Changes Over Time:**
```
ten:        (empty) → "Minh"
tuoi:       (empty) → 25
chieu_cao:  (empty) → 1.75
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
┌─────────────────────────────────────────────────────────────┐
│                    COMPUTER MEMORY                          │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐  │
│   │   VARIABLE   │    │   VARIABLE   │    │   VARIABLE   │  │
│   │              │    │              │    │              │  │
│   │      ten     │    │     tuoi     │    │  chieu_cao   │  │
│   │  ┌────────┐  │    │  ┌────────┐  │    │  ┌────────┐  │  │
│   │  │ "Minh" │  │    │  │   25   │  │    │  │  1.75  │  │  │
│   │  │ (str)  │  │    │  │  (int) │  │    │  │ (float)│  │  │
│   │  └────────┘  │    │  └────────┘  │    │  └────────┘  │  │
│   └──────────────┘    └──────────────┘    └──────────────┘  │
│        │                   │                   │            │
│        └───────────────────┼───────────────────┘            │
│                            ▼                                 │
│              ┌─────────────────────────┐                     │
│              │    print(ten)           │                    │
│              │    → looks up "ten"     │                    │
│              │    → finds "Minh"       │                    │
│              │    → displays: Minh    │                    │
│              └─────────────────────────┘                    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Missing Quotes for Strings
```python
ten = Minh  # ERROR!
```

**Why it fails:** Without quotes, Python thinks "Minh" is a variable name (code), not text.

**Root cause:** Forgetting that text (strings) must always be wrapped in quotes.

**✅ Fix:**
```python
ten = "Minh"  # Correct - text needs quotes
```

---

### Common Mistake #2 — Variable Name with Spaces
```python
ten cua toi = "Minh"  # ERROR!
```

**Why it fails:** Python can't understand spaces in variable names - it thinks each word is a separate item.

**Root cause:** Variable names cannot contain spaces.

**✅ Fix (two options):**
```python
ten_cua_toi = "Minh"  # Use underscore
# OR
tenCuaToi = "Minh"    # Use camelCase
```

---

### Common Mistake #3 — Confusing String "25" with Integer 25
```python
tuoi_string = "25"   # This is TEXT (string)
tuoi_int = 25        # This is NUMBER (integer)
```

**Why it matters:** You can't do math with strings!
```python
print("25" + "25")  # Results in: "2525" (text concatenation)
print(25 + 25)      # Results in: 50 (math addition)
```

**Root cause:** Not understanding that `"25"` and `25` are different data types.

---

### Prevention Strategy

**Always check:**
- ✓ Text values have quotes: `"text"`
- ✓ Variable names use underscores or camelCase: `my_var` or `myVar`
- ✓ Know your data type: string vs number affects what operations work

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- Variables store data for later use
- `=` assigns a value to a variable
- Three main types: string (text), integer (whole numbers), float (decimals)

### Key Syntax
```python
variable_name = value
```

### Pattern
```python
# Create variable
name = "value"

# Use variable
print(name)
```

### Mistakes to Avoid
- ✗ `name = value` (forgetting quotes for text)
- ✗ `my name = "Minh"` (spaces in variable name)
- ✗ `num = "5"` then expecting math to work

**Memory Hook:** Variable = "box with a label" - label outside, value inside.

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What is the output?
```python
x = 5
y = 10
print(x + y)
```
> **Answer:** `15` (adds the numbers mathematically)

---

**Question 2:** Fix this error:
```python
ho_ten = Nam
```
> **Answer:** Missing quotes - should be: `ho_ten = "Nam"`

---

**Question 3:** How many data types in this code?
```python
a = 3
b = 3.5
c = "3"
```
> **Answer:** 3 types - `a` is integer, `b` is float, `c` is string

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Create three variables and print them:
- `ho` = "Nguyen"
- `ten` = "An"
- `tuoi` = 20

**Input:** (none required)

**Output:**
```
Nguyen
An
20
Nguyen An, 20 tuoi
```

**Starter Code:**
```python
ho = "Nguyen"
ten = "An"
tuoi = 20

# Write your print statements below
```

**Hints:**
1. Use print() to display each variable
2. Use commas in print() to combine text and variables
3. Print all three together at the end

**✅ Solution:**
```python
ho = "Nguyen"
ten = "An"
tuoi = 20

print(ho)
print(ten)
print(tuoi)
print(ho, ten, tuoi, "tuoi")
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Decomposition:**
1. Create 3 variables with given values
2. Print each variable on separate lines
3. Print all combined with extra text

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Calculate and print the sum of two numbers
- First number: 15
- Second number: 27

**Output:**
```
Tong = 42
```

**✅ Solution:**
```python
so1 = 15
so2 = 27
tong = so1 + so2
print("Tong =", tong)
```

**Key Insight:** You can do math with variables that contain numbers!

**Extra Challenge:** Try subtracting, multiplying, and dividing!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- Variables are containers for storing data
- Three main types: string, integer, float
- Using variables in print() with text
- Basic math operations with number variables

**Weak points to watch:**
- Forgetting quotes around string values
- Confusing string "25" with integer 25
- Using spaces in variable names

**Next growth target:**
- Move to Lesson 3: Operators - learning how to manipulate data
- Practice: Create variables for your favorite things

**Confidence Check:** Can you create a variable and print it? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 2 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 20 (+10 for completing) |
| **Rank** | Beginner |
| **Mastery** | 15% |
| **Weaknesses** | String vs number confusion |
| **Recommended Focus** | Practice creating different variable types |
| **Suggested Review** | Review string vs integer difference |
| **Next Lesson Readiness** | Ready for Lesson 3 (Operators) |

---

**🎉 You completed Lesson 2!**

Type **3** to continue → Lesson 3 (Operators)