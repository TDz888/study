# Lesson 9 — Functions (Hàm)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 8 - Learned dictionaries (key-value pairs) for structured data storage.

**Current Lesson:** Learning **functions** - reusable blocks of code that perform a specific task. One of the most important concepts in programming.

**Future Usefulness:** Functions are everywhere - organized code, avoid repetition, build libraries, create reusable components. Every large program is built from functions.

**Connection:** Variables store data → Functions store code. Both can be reused throughout your program.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Defining functions
- Function parameters and arguments
- Return values
- Calling functions
- Function best practices

**Why it matters:** Write once, use many times. "Calculate area" function can be called 100 times with different sizes.

**Real programmers use it:** Every program uses functions - from simple scripts to complex systems. It's how code is organized and reused.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is a Function?

A function is a **reusable block of code**:
- Has a name
- Can accept input (parameters)
- Can return output (return value)
- Can be called multiple times

```python
# Define a function
def greet():
    print("Hello!")

# Call the function
greet()  # prints "Hello!"
```

### Function with Parameters

```python
def greet_person(name):
    print(f"Hello, {name}!")

greet_person("Minh")  # Hello, Minh!
greet_person("Lan")   # Hello, Lan!
```

### Function with Return Value

```python
def add_numbers(a, b):
    result = a + b
    return result

sum = add_numbers(5, 3)  # sum = 8
print(add_numbers(10, 20))  # prints 30
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **function** | A reusable block of code |
| **define** | Create a function |
| **call** | Use/execute a function |
| **parameter** | Input variable in function definition |
| **argument** | Actual value passed when calling |
| **return** | Send a value back from function |
| **def** | Keyword to define a function |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Simple function
def say_hello():
    print("Hello, World!")

say_hello()

# Example 2: Function with parameter
def greet(name):
    print(f"Hello, {name}!")

greet("Minh")
greet("Lan")

# Example 3: Function with multiple parameters
def introduce(name, age):
    print(f"I am {name}, {age} years old")

introduce("Minh", 25)
introduce("Lan", 30)

# Example 4: Function with return value
def add(a, b):
    return a + b

result = add(5, 3)
print("Sum:", result)  # 8

# Example 5: Function with default parameter
def greet_with_default(name="Friend"):
    print(f"Hello, {name}!")

greet_with_default("Minh")  # Hello, Minh!
greet_with_default()        # Hello, Friend!

# Example 6: Multiple return values
def get_stats(numbers):
    total = sum(numbers)
    average = total / len(numbers)
    return total, average

total, average = get_stats([10, 20, 30])
print(f"Total: {total}, Average: {average}")
```

**Output:**
```
Hello, World!
Hello, Minh!
Hello, Lan!
I am Minh, 25 years old
I am Lan, 30 years old
Sum: 8
Hello, Minh!
Hello, Friend!
Total: 60, Average: 20.0
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: greet("Minh")

Step 1: Python sees greet("Minh")
Step 2: Finds function "greet" definition
Step 3: Passes argument "Minh" to parameter "name"
Step 4: Executes function body: print(f"Hello, {name}!")
Step 5: name = "Minh" → prints "Hello, Minh!"
Step 6: Function ends, returns to caller
```


```
Example: add(5, 3)

Step 1: Python sees add(5, 3)
Step 2: Finds function "add" definition
Step 3: Passes 5 → parameter a, 3 → parameter b
Step 4: Executes: result = a + b → result = 8
Step 5: Returns 8 to caller
Step 6: result = 8
```

**Function Call Flow:**
```
┌─────────────┐
│  Call      │
│ add(5, 3)  │
└──────┬──────┘
       │
       ▼
┌─────────────────┐
│  Function      │
│  Definition    │
├─────────────────┤
│ def add(a, b): │
│     return a+b │
└──────┬─────────┘
       │
       ▼
┌─────────────┐
│  Execute   │
│ a=5, b=3   │
│ return 8   │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│   Return   │
│   value 8  │
└─────────────┘
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
FUNCTION STRUCTURE:

┌─────────────────────────────────────────────────┐
│           def function_name(parameters):        │
│                    │                            │
│            function name                         │
│            │                                    │
│            ▼                                    │
│         parameters (inputs)                      │
│                    │                            │
│                    ▼                            │
│           ┌─────────────────┐                   │
│           │  function body   │                   │
│           │   (code block)  │                   │
│           └────────┬────────┘                   │
│                    │                            │
│                    ▼                            │
│               return value                      │
│               (output)                          │
└─────────────────────────────────────────────────┘

CALLING A FUNCTION:

┌───────────────────────────────────────────────┐
│                                               │
│   add(5, 3)          →   def add(a, b):      │
│   arguments              parameters          │
│   (5, 3)                 (a, b)              │
│                                               │
│           ┌───────────────┐                   │
│           │   Execute    │                    │
│           │   a + b = 8   │                    │
│           └───────┬───────┘                   │
│                   │                            │
│                   ▼                            │
│           ┌───────────────┐                   │
│           │   Return 8    │                   │
│           └───────────────┘                   │
│                                               │
└───────────────────────────────────────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Forgetting to Call Function
```python
def say_hello():
    print("Hello!")

say_hello  # OOPS! Forgot ()
```

**Why it fails:** Without (), it's just referencing the function, not calling it.

**✅ Fix:**
```python
say_hello()  # Call with parentheses
```

---

### Common Mistake #2 — Wrong Number of Arguments
```python
def add(a, b):
    return a + b

result = add(5)  # ERROR! Only one argument, needs two
```

**Why it fails:** Function expects 2 parameters, only 1 given.

**✅ Fix:**
```python
result = add(5, 3)  # Two arguments
```

---

### Common Mistake #3 — Forgetting Return
```python
def add(a, b):
    c = a + b
    # FORGOT: return c

result = add(5, 3)
print(result)  # None! (function returns nothing)
```

**Why it fails:** Without return, function returns None.

**✅ Fix:**
```python
def add(a, b):
    return a + b  # Return the result
```

---

### Common Mistake #4 — Variable Scope
```python
def modify():
    x = 10  # local variable

x = 5
modify()
print(x)  # Still 5! Not 10!
```

**Why it fails:** Function's x is local, doesn't affect outside x.

**Key insight:** Variables inside function are local - don't affect outside.

---

### Prevention Strategy

- Always call with parentheses: function_name()
- Match arguments to parameters
- Use return to send back values
- Understand local vs global scope

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- Functions are reusable code blocks
- Parameters receive input, return sends output
- Define with def, call with ()

### Key Syntax
```python
# Define
def function_name(param1, param2):
    # code
    return value

# Call
function_name(arg1, arg2)

# With default
def function(param=value):
    # code
```

### Patterns to Remember
```
def name():           # no params
def name(x):         # one param  
def name(x, y):      # multiple params
def name(x=1):       # default param
return value         # return something
```

### Mistakes to Avoid
- ✗ Forgetting () when calling
- ✗ Wrong number of arguments
- ✗ Forgetting return (gets None)
- ✗ Thinking local changes affect outside

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What's the output?
```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Minh"))
```
> **Answer:** `Hello, Minh!`

---

**Question 2:** What happens?
```python
def add(a, b):
    c = a + b

print(add(5, 3))
```
> **Answer:** `None` (forgot to return!)

---

**Question 3:** Fix to make it work:
```python
def double(x):
    return x * 2

result = double  # What's missing?
```
> **Answer:** Should be `result = double(5)` - need () and argument

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Write a function that returns the square of a number.

**Input:** 5

**Output:**
```
25
```

**Starter Code:**
```python
def square(n):
    # write your code

print(square(5))
```

**Hints:**
- Multiply n by itself or use n ** 2

**✅ Solution:**
```python
def square(n):
    return n * n

print(square(5))  # 25
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Challenge:** Write a function to check if a number is even.

**Input:** 7

**Output:**
```
False
```

**✅ Solution:**
```python
def is_even(n):
    return n % 2 == 0

print(is_even(7))  # False
print(is_even(8))  # True
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Write a function that finds the maximum of three numbers.

**Input:** 5, 8, 3

**Output:**
```
8
```

**✅ Solution:**
```python
def find_max(a, b, c):
    if a >= b and a >= c:
        return a
    elif b >= a and b >= c:
        return b
    else:
        return c

print(find_max(5, 8, 3))  # 8
```

**Key insight:** Compare each number to find the largest!

**Extra Challenge:** Do it with only 2 comparisons using nested conditionals!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- Functions are reusable code blocks
- Parameters receive input, return sends output
- Define with def, call with ()
- Default parameters and multiple return values

**Weak points to watch:**
- Forgetting () when calling
- Wrong argument count
- Forgetting return (gets None)

**Next growth target:**
- Move to Lesson 10: Modules - using code from other files

**Confidence Check:** Can you write a function that takes input and returns output? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 9 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 90 (+10 for completing) |
| **Rank** | Beginner |
| **Mastery** | 50% |
| **Weaknesses** | Return statement |
| **Recommended Focus** | Practice function definitions |
| **Suggested Review** | Review parameter vs argument |
| **Next Lesson Readiness** | Ready for Lesson 10 (Modules) |

---

**🎉 You completed Lesson 9!**

Type **10** to continue → Lesson 10 (Modules)