# Lesson 5 — For Loops (Vòng lặp For)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 4 - Learned if/elif/else conditionals. Code that runs only when conditions are True.

**Current Lesson:** Learning **loops** - running the same code multiple times without rewriting it.

**Future Usefulness:** Every program needs repetition - processing lists, reading files, game loops, automation. For loops are the most common loop type.

**Connection:** Conditionals decide WHICH code runs → Loops decide HOW MANY TIMES code runs.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- What is a loop and why we need it
- The for loop syntax
- The range() function
- Using loop variables
- Loop control: break and continue

**Why it matters:** Writing "print(i)" 100 times is silly. Loops let you write once, run many times.

**Real programmers use it:** Processing data, automating tasks, games - everything uses loops.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### Why Do We Need Loops?

Without loops:
```python
print(1)
print(2)
print(3)
print(4)
print(5)
# ... imagine doing this 100 times!
```

With loops:
```python
for i in range(1, 6):
    print(i)
# Done! Much cleaner!
```

### For Loop Syntax

```python
for variable in sequence:
    # code that repeats
```

### The range() Function

| Syntax | Result | Example |
|--------|--------|---------|
| `range(n)` | 0 to n-1 | `range(5)` → 0,1,2,3,4 |
| `range(start, end)` | start to end-1 | `range(1,5)` → 1,2,3,4 |
| `range(start, end, step)` | with step | `range(0,10,2)` → 0,2,4,6,8 |

### How It Works

```python
for i in range(1, 4):
    print(i)
```
```
Loop 1: i = 1 → print(1)
Loop 2: i = 2 → print(2)
Loop 3: i = 3 → print(3)
Loop 4: i = 4 → stops (4 >= 4 is False)
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXTERNATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **loop** | Code that repeats multiple times |
| **iteration** | One execution of the loop body |
| **for loop** | A loop that iterates over a sequence |
| **range()** | Generates a sequence of numbers |
| **loop variable** | The variable that changes each iteration |
| **break** | Exit the loop immediately |
| **continue** | Skip to next iteration |
| **indentation** | Defines the loop body |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Basic for loop
print("Example 1: Count 1 to 5")
for i in range(1, 6):
    print(i)

# Example 2: Range without start
print("\nExample 2: 0 to 4")
for i in range(5):
    print(i)

# Example 3: With step
print("\nExample 3: Even numbers 0 to 8")
for i in range(0, 10, 2):
    print(i)

# Example 4: Using loop variable
print("\nExample 4: Multiplication table")
for i in range(1, 6):
    print(f"5 x {i} = {5 * i}")

# Example 5: Looping through string
print("\nExample 5: Letters in 'Hello'")
for letter in "Hello":
    print(letter)

# Example 6: break statement
print("\nExample 6: Stop at 3")
for i in range(1, 10):
    if i == 4:
        break
    print(i)
```

**Output:**
```
Example 1: Count 1 to 5
1
2
3
4
5

Example 2: 0 to 4
0
1
2
3
4

Example 3: Even numbers 0 to 8
0
2
4
6
8

Example 4: Multiplication table
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25

Example 5: Letters in 'Hello'
H
e
l
l
o

Example 6: Stop at 3
1
2
3
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: for i in range(1, 4)

Iteration 1:
- i = 1
- Check: 1 < 4? YES → True
- Execute: print(1) → prints 1

Iteration 2:
- i = 2
- Check: 2 < 4? YES → True  
- Execute: print(2) → prints 2

Iteration 3:
- i = 3
- Check: 3 < 4? YES → True
- Execute: print(3) → prints 3

Iteration 4:
- i = 4
- Check: 4 < 4? NO → False
- Exit loop

FINAL OUTPUT: 1, 2, 3
```

```
Example: break at i == 4

for i in range(1, 10):
    │
    ├─ i=1: print 1
    ├─ i=2: print 2  
    ├─ i=3: print 3
    ├─ i=4: if i == 4? YES → break!
    └─ Exit loop (stops here!)

OUTPUT: 1, 2, 3
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
FOR LOOP EXECUTION FLOW:

┌─────────────────────────────────────────────┐
│         for i in range(1, 4):               │
│             print(i)                        │
└─────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────┐
│         ITERATION 1                         │
│  ┌─────────────────────────────────────┐    │
│  │ i = 1                                │    │
│  │ Is 1 < 4? YES → enter body          │    │
│  │ print(1) → output: 1                 │    │
│  └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────┐
│         ITERATION 2                         │
│  ┌─────────────────────────────────────┐    │
│  │ i = 2                                │    │
│  │ Is 2 < 4? YES → enter body          │    │
│  │ print(2) → output: 2               │    │
│  └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────┐
│         ITERATION 3                         │
│  ┌─────────────────────────────────────┐    │
│  │ i = 3                                │    │
│  │ Is 3 < 4? YES → enter body          │    │
│  │ print(3) → output: 3               │    │
│  └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────┐
│         EXIT LOOP                           │
│  ┌─────────────────────────────────────┐    │
│  │ i = 4                                │    │
│  │ Is 4 < 4? NO → exit                 │    │
│  └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Off-by-One Error
```python
# Want 1 to 5, but get 1 to 4!
for i in range(1, 5):
    print(i)  # 1, 2, 3, 4 (wrong!)

# Fix: range(start, end) gives start to end-1
for i in range(1, 6):  # 1 to 5
    print(i)  # 1, 2, 3, 4, 5 (correct!)
```

**Key insight:** range(1, 6) means 1,2,3,4,5 (stops before 6!)

---

### Common Mistake #2 — Forgetting Indentation
```python
for i in range(5):
print(i)  # ERROR! Not indented - not part of loop!
```

**Why it fails:** Python needs indentation to know which code is inside the loop.

**✅ Fix:**
```python
for i in range(5):
    print(i)  # Indented - inside the loop
```

---

### Common Mistake #3 — Infinite Loop (while) but not in for
```python
# For loops with range() NEVER infinite
# because range() has definite end

# But if using while, be careful:
i = 0
while True:  # DANGER! Infinite loop!
    print(i)
```

**For loops are safe** - they always end because range() is finite.

---

### Common Mistake #4 — Wrong Step Direction
```python
# Trying to count down - but this gives NOTHING!
for i in range(5, 1):  # 5 to end-1 = nothing!
    print(i)  # No output!

# Fix: need negative step
for i in range(5, 0, -1):  # 5, 4, 3, 2, 1
    print(i)  # Works!
```

---

### Prevention Strategy

- Remember: range(1, 6) gives 1,2,3,4,5 (stops before 6)
- Always indent loop body
- Use negative step for countdown: range(5, 0, -1)

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- `for` loops iterate over a sequence
- `range(n)` gives 0 to n-1
- `range(start, end)` gives start to end-1
- `range(start, end, step)` changes increment
- `break` exits loop, `continue` skips iteration

### Key Syntax
```python
for variable in range(start, end):
    # code

for variable in range(end):        # 0 to end-1
for variable in range(start, end): # start to end-1  
for variable in range(start, end, step): # with step
```

### Patterns to Remember
```
range(5)        → 0,1,2,3,4
range(1,6)      → 1,2,3,4,5
range(0,10,2)   → 0,2,4,6,8
range(5,0,-1)   → 5,4,3,2,1
```

### Mistakes to Avoid
- ✗ Off-by-one: range(1,5) gives 1,2,3,4 (not 5!)
- ✗ Forgetting indentation
- ✗ Wrong step sign for countdown

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What does `range(1, 8, 2)` generate?
> **Answer:** 1, 3, 5, 7 (start at 1, stop before 8, step by 2)

---

**Question 2:** How many times does this loop run?
```python
for i in range(3):
    print(i)
```
> **Answer:** 3 times (i = 0, 1, 2)

---

**Question 3:** What's the output?
```python
for i in range(3, 0, -1):
    print(i)
```
> **Answer:** 3, 2, 1 (countdown from 3 to 1)

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Print all numbers from 1 to 10.

**Input:** (none - fixed range)

**Output:**
```
1
2
3
4
5
6
7
8
9
10
```

**Starter Code:**
```python
# Write your for loop here
```

**Hints:**
- Use range(1, 11) to get 1 to 10

**✅ Solution:**
```python
for i in range(1, 11):
    print(i)
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Challenge Problem:** Calculate the sum of numbers 1 to 100.

**Output:**
```
5050
```

**✅ Solution:**
```python
total = 0
for i in range(1, 101):
    total = total + i

print(total)  # 5050
```

**Key insight:** Add up all numbers from 1 to 100.

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Print only even numbers from 1 to 20

**Output:**
```
2
4
6
8
10
12
14
16
18
20
```

**✅ Solution:**
```python
for i in range(2, 21, 2):
    print(i)
```

**Alternative:** Use if statement with modulus
```python
for i in range(1, 21):
    if i % 2 == 0:
        print(i)
```

**Extra Challenge:** Print odd numbers from 1 to 20!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- For loops repeat code a specific number of times
- range() generates number sequences
- Loop variable changes each iteration
- break and continue control flow

**Weak points to watch:**
- Off-by-one errors in range()
- Indentation mistakes
- Wrong step for countdown

**Next growth target:**
- Move to Lesson 6: While Loops - another type of loop

**Confidence Check:** Can you write a for loop to print 1 to 5? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 5 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 50 (+10 for completing) |
| **Rank** | Beginner |
| **Mastery** | 30% |
| **Weaknesses** | Off-by-one in range() |
| **Recommended Focus** | Practice range() with different parameters |
| **Suggested Review** | Review range() behavior |
| **Next Lesson Readiness** | Ready for Lesson 6 (While Loops) |

---

**🎉 You completed Lesson 5!**

Type **6** to continue → Lesson 6 (While Loops)