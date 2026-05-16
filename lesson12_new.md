# Lesson 12 — Exception Handling (Xử lý ngoại lệ)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 11 - Learned File I/O to read/write files. Learned about FileNotFoundError.

**Current Lesson:** Learning **Exception Handling** - handling errors gracefully instead of crashing. Essential for robust programs.

**Future Usefulness:** Every real program encounters errors - bad user input, network issues, file problems. Handle them, don't crash!

**Connection:** File I/O can cause errors (FileNotFoundError) → Exception handling catches and handles those errors.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- What are exceptions
- Try-except blocks
- Multiple exception types
- Finally block
- Raising exceptions

**Why it matters:** When error occurs, program shouldn't crash - it should handle the error gracefully and continue.

**Real programmers use it:** Every robust program uses try-except to handle potential errors.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is an Exception?

An exception is an **error that disrupts normal program flow**:
- Division by zero
- File not found
- Invalid input
- Type errors

### The Try-Except Structure

```python
try:
    # Code that might cause error
except ExceptionType:
    # What to do if error occurs
```

### Common Exception Types

| Exception | When it occurs |
|-----------|----------------|
| ZeroDivisionError | Dividing by zero |
| FileNotFoundError | File doesn't exist |
| ValueError | Wrong value type |
| TypeError | Wrong data type |
| IndexError | Index out of range |
| KeyError | Key not in dictionary |

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **exception** | An error that interrupts program |
| **raise** | Create an exception intentionally |
| **try** | Block where errors might occur |
| **except** | Block that catches and handles errors |
| **finally** | Block that always executes |
| **traceback** | The error message showing where problem occurred |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Basic try-except
print("=== Basic try-except ===")
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Example 2: Multiple except
print("\n=== Multiple except ===")
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ValueError:
    print("Invalid input - not a number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Example 3: Catch all exceptions
print("\n=== Catch all ===")
try:
    x = int("abc")
except Exception as e:
    print(f"Error: {e}")

# Example 4: Try-except-else-finally
print("\n=== Finally block ===")
try:
    f = open("test.txt", "r")
    content = f.read()
except FileNotFoundError:
    print("File not found!")
finally:
    print("This always runs - cleanup here!")
    # if 'f' exists, close it

# Example 5: Raising exceptions
print("\n=== Raising exceptions ===")
def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero!")
    return a / b

try:
    result = divide(10, 0)
except ValueError as e:
    print(f"Caught: {e}")

# Example 6: Practical example
print("\n=== Practical handling ===")
def safe_divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return "Error: Division by zero"

print(safe_divide(10, 2))  # 5.0
print(safe_divide(10, 0))  # Error message
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: try: 10/0 except ZeroDivisionError: print("Error")

Step 1: Python enters try block
Step 2: Executes: 10 / 0
Step 3: Division by zero! → ZeroDivisionError raised
Step 4: Python jumps to except ZeroDivisionError block
Step 5: Executes: print("Cannot divide by zero!")
Step 6: Continues after except block

If no error:
Step 1: Try block executes fully
Step 2: Skip except block
Step 3: Continue after except
```

```
Example: try-except-else-finally

try:
    code
except:
    error handling
else:
    runs if NO error (new in Python 3)
finally:
    ALWAYS runs
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
EXCEPTION FLOW:

┌─────────────────────────┐
│      try block          │
│   (code that might       │
│    cause error)          │
└────────┬────────────────┘
         │
    ┌────┴────┐
    │         │
  Error    No Error
    │         │
    ▼         ▼
┌────────┐ ┌──────────┐
│ except │ │   else   │
│ block  │ │ (optional│
└────┬───┘ └────┬─────┘
     │          │
     └────┬─────┘
          │
          ▼
     ┌──────────┐
     │ finally  │
     │ (always) │
     └──────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Bare Except
```python
try:
    x = int(input())
except:  # BAD! Catches EVERYTHING
    print("Error")
```

**Why it fails:** Catches even keyboard interrupts, hides real errors.

**✅ Fix:** Catch specific exception
```python
except ValueError:
    print("Invalid input")
```

---

### Common Mistake #2 — Wrong Order of Except
```python
try:
    x = int(input())
except Exception:  # Too broad!
    print("Error")
except ValueError:  # NEVER REACHED!
    print("Invalid number")
```

**Why it fails:** First matching except catches everything.

**✅ Fix:** Put specific exceptions first
```python
except ValueError:
    print("Invalid")
except Exception:
    print("Other error")
```

---

### Common Mistake #3 — Swallowing the Error
```python
try:
    dangerous()
except:
    pass  # Silently ignores error!
```

**Why it fails:** No feedback, no logging, impossible to debug.

**✅ Fix:** At least log the error
```python
except Exception as e:
    print(f"Error occurred: {e}")
```

---

### Prevention Strategy

- Catch specific exceptions, not all
- Put more specific exceptions first
- Always log or handle the error somehow
- Use finally for cleanup

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- Try-except catches errors instead of crashing
- Can have multiple except blocks
- Finally always runs - for cleanup
- Raise creates custom exceptions

### Key Syntax
```python
try:
    # risky code
except ExceptionType:
    # handle
except Exception as e:
    # catch all as variable
finally:
    # cleanup
```

### Patterns
```
try-except           → basic handling
try-except-else      → runs if no error
try-except-finally  → always runs
raise ValueError    → create error
```

### Mistakes to Avoid
- ✗ Bare except (catches everything)
- ✗ Wrong order (specific after general)
- ✗ Silencing errors (pass)

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What prints?
```python
try:
    print(5 / 0)
except ZeroDivisionError:
    print("Error")
```
> **Answer:** "Error" (caught ZeroDivisionError)

---

**Question 2:** Fix to catch both errors:
```python
try:
    x = int("abc")
except:
    # catch both ValueError and generic
```
> **Answer:** Use `except Exception as e:` to catch all, or separate except blocks

---

**Question 3:** What always runs regardless of error?
> **Answer:** finally block

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Write a safe function to convert string to integer.

**Input:** "42" → 42
**Input:** "abc" → "Invalid"

**✅ Solution:**
```python
def safe_convert(s):
    try:
        return int(s)
    except ValueError:
        return "Invalid"

print(safe_convert("42"))  # 42
print(safe_convert("abc")) # Invalid
```

---

**Difficulty:** ★☆☆☆☆

**Challenge:** Create a safe file reader that returns "File not found" if error.

**✅ Solution:**
```python
def read_file(filename):
    try:
        with open(filename, "r") as f:
            return f.read()
    except FileNotFoundError:
        return "File not found"

print(read_file("test.txt"))
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Create a calculator with exception handling.

**Features:** +, -, *, / with error handling for invalid input

**✅ Solution:**
```python
def calculator():
    try:
        a = float(input("First number: "))
        op = input("Operator (+,-,*,/): ")
        b = float(input("Second number: "))
        
        if op == "+":
            print(a + b)
        elif op == "-":
            print(a - b)
        elif op == "*":
            print(a * b)
        elif op == "/":
            if b == 0:
                print("Cannot divide by zero!")
            else:
                print(a / b)
        else:
            print("Invalid operator")
    except ValueError:
        print("Invalid number input")

calculator()
```

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- Try-except blocks for error handling
- Multiple exception types
- Finally for cleanup
- Raising exceptions

**Weak points to watch:**
- Bare except catches too much
- Wrong order of except blocks

**Next growth target:**
- Lesson 13: Classes and Objects

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 12 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 120 |
| **Rank** | Apprentice |
| **Mastery** | 65% |

---

Type **13** to continue → Lesson 13 (Classes and Objects)