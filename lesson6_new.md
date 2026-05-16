# Lesson 6 — While Loops (Vòng lặp While)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 5 - Learned for loops to repeat code a specific number of times using range().

**Current Lesson:** Learning **while loops** - loops that continue as long as a condition is True (not knowing in advance how many iterations).

**Future Usefulness:** While loops are used when you don't know exact count - like waiting for user input, game loops, reading until end of file.

**Connection:** For loops: know how many times → While loops: keep going until condition changes.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- The while loop syntax
- How while differs from for
- Infinite loop dangers
- Using while for input validation
- Break and continue in while

**Why it matters:** Sometimes you don't know when to stop - keep asking until user enters valid input, keep playing until game ends.

**Real programmers use it:** Game loops, input validation, waiting for responses, processing unknown-length data.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### While Loop Syntax

```python
while condition:
    # code that repeats
```

The loop continues WHILE the condition is True.

### How It Works

```python
i = 1
while i <= 5:
    print(i)
    i = i + 1
```

```
Check: i=1, 1 <= 5? YES → print 1, i becomes 2
Check: i=2, 2 <= 5? YES → print 2, i becomes 3
Check: i=3, 3 <= 5? YES → print 3, i becomes 4
Check: i=4, 4 <= 5? YES → print 4, i becomes 5
Check: i=5, 5 <= 5? YES → print 5, i becomes 6
Check: i=6, 6 <= 5? NO → Exit!
```

### For vs While

| For Loop | While Loop |
|----------|------------|
| Know exact iterations | Unknown iterations |
| for i in range(5) | while i < 5 |
| Automatic counter | Manual counter |
| Safe by design | Can be infinite |

### When to Use Each

- **For:** When you know how many times (iterate through list, count to 10)
- **While:** When you don't know (keep asking until valid, game loop)

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **while loop** | Repeats as long as condition is True |
| **condition** | Boolean expression that controls the loop |
| **infinite loop** | A loop that never ends (dangerous!) |
| **counter** | A variable that tracks iterations |
| **increment** | Increasing the counter (i = i + 1) |
| **decrement** | Decreasing the counter (i = i - 1) |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Basic while loop
print("Example 1: Count 1 to 5")
i = 1
while i <= 5:
    print(i)
    i = i + 1

# Example 2: While with input simulation
print("\nExample 2: Keep going until 0")
attempts = 3
while attempts > 0:
    print(f"Attempts left: {attempts}")
    attempts = attempts - 1
print("Out of attempts!")

# Example 3: While with break
print("\nExample 3: Stop at 3")
i = 1
while True:
    if i == 4:
        break
    print(i)
    i = i + 1

# Example 4: While with continue
print("\nExample 4: Skip 3")
i = 0
while i < 5:
    i = i + 1
    if i == 3:
        continue  # Skip when i is 3
    print(i)

# Example 5: Input validation simulation
print("\nExample 5: Keep running until condition")
number = 1
while number != 0:
    print(f"Current number: {number}")
    number = number - 1
print("Number reached 0, loop ends!")
```

**Output:**
```
Example 1: Count 1 to 5
1
2
3
4
5

Example 2: Keep going until 0
Attempts left: 3
Attempts left: 2
Attempts left: 1
Out of attempts!

Example 3: Stop at 3
1
2
3

Example 4: Skip 3
1
2
4
5

Example 5: Keep running until condition
Current number: 1
Number reached 0, loop ends!
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: i = 1, while i <= 5

Iteration 1:
- Check: i = 1, is 1 <= 5? YES → True
- Execute: print(1) → prints 1
- Update: i = 1 + 1 → i = 2

Iteration 2:
- Check: i = 2, is 2 <= 5? YES → True
- Execute: print(2) → prints 2
- Update: i = 2 + 1 → i = 3

Iteration 3:
- Check: i = 3, is 3 <= 5? YES → True
- Execute: print(3) → prints 3
- Update: i = 3 + 1 → i = 4

Iteration 4:
- Check: i = 4, is 4 <= 5? YES → True
- Execute: print(4) → prints 4
- Update: i = 4 + 1 → i = 5

Iteration 5:
- Check: i = 5, is 5 <= 5? YES → True
- Execute: print(5) → prints 5
- Update: i = 5 + 1 → i = 6

Iteration 6:
- Check: i = 6, is 6 <= 5? NO → False
- Exit loop!

FINAL OUTPUT: 1, 2, 3, 4, 5
```

```
Example: Continue - Skip when i == 3

i = 0, while i < 5

i=1: print 1
i=2: print 2  
i=3: i becomes 3, if i == 3? YES → continue (skip print)
i=4: print 4
i=5: i becomes 5, is 5 < 5? NO → exit

OUTPUT: 1, 2, 4, 5 (3 is skipped!)
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
WHILE LOOP FLOW:

┌─────────────────────────────────────────┐
│         i = 1                           │
│         while i <= 5:                   │
│             print(i)                    │
│             i = i + 1                   │
└─────────────────────────────────────────┘
              │
              ▼
         ┌────┴────┐
         │         │
      YES          NO
         │         │
         ▼         ▼
    ┌─────────┐  ┌─────────┐
    │ Execute │  │  EXIT   │
    │  body   │  │  LOOP   │
    └────┬────┘  └─────────┘
         │
         ▼
    ┌─────────┐
    │ Update  │
    │counter  │
    └────┬────┘
         │
         └──────┐
                │
                ▼
         (check again)
```

```
INFINITE LOOP DANGER:

┌─────────────────────────────────────────┐
│         while True:                     │
│             print("Help!")              │
└─────────────────────────────────────────┘
                │
                ▼
         ┌────┴────┐
         │         │
       (always    (never!)
        True)     
         │
         ▼
    ┌─────────┐
    │ FOREVER!│
    │ (crash) │
    └─────────┘

ALWAYS add a way to exit!
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Forgetting to Update Counter
```python
i = 1
while i <= 5:
    print(i)
    # FORGOT: i = i + 1
    # INFINITE LOOP!
```

**Why it fails:** If you don't change i, the condition never becomes False.

**✅ Fix:** Always update the counter!
```python
i = 1
while i <= 5:
    print(i)
    i = i + 1  # Don't forget!
```

---

### Common Mistake #2 — Off-by-One with Condition
```python
# Want 1 to 5, but get 1 to 4
i = 1
while i < 5:  # Should be <= not <
    print(i)
    i = i + 1
```

**Fix:** Use `<=` for inclusive end

---

### Common Mistake #3 — Infinite while True
```python
while True:
    print("Running")  # Never stops!
```

**When OK:** Only with break statement inside
```python
while True:
    x = input()
    if x == "quit":
        break  # This exits!
    print(x)
```

---

### Common Mistake #4 — While for known iterations
```python
# Don't use while when for is better
i = 0
while i < 5:  # This is what for is for!
    print(i)
    i = i + 1

# Better:
for i in range(5):
    print(i)
```

**Key insight:** For loops are cleaner for known iterations.

---

### Prevention Strategy

- Always update counter in while loops
- Use for when you know the count
- Use while only when condition is dynamic
- Test the loop to ensure it eventually ends

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- While loops repeat while condition is True
- Counter must be updated manually
- Can become infinite if not careful
- break exits, continue skips

### Key Syntax
```python
while condition:
    # code
    # update counter

while True:  # needs break inside!
    # code
    if exit_condition:
        break
```

### Patterns to Remember
```
while i < n:    # runs n times (0 to n-1)
while i <= n:   # runs n+1 times (0 to n)
while i > 0:    # countdown
while True:    # infinite until break
```

### Mistakes to Avoid
- ✗ Forgetting to update counter
- ✗ Infinite loops
- ✗ Using while when for is better

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** How many times does this run?
```python
i = 3
while i > 0:
    print(i)
    i = i - 1
```
> **Answer:** 3 times (prints 3, 2, 1)

---

**Question 2:** What's wrong?
```python
while True:
    print("Running")
```
> **Answer:** Infinite loop - needs break inside to exit!

---

**Question 3:** What's the output?
```python
i = 0
while i < 3:
    i = i + 1
    if i == 2:
        continue
    print(i)
```
> **Answer:** 1, 3 (skips 2 because of continue)

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Countdown from 5 to 1.

**Input:** (none)

**Output:**
```
5
4
3
2
1
Liftoff!
```

**Starter Code:**
```python
# Write your while loop here
```

**Hints:**
- Start at 5, while i >= 1, decrement each time

**✅ Solution:**
```python
i = 5
while i >= 1:
    print(i)
    i = i - 1
print("Liftoff!")
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Challenge:** Keep multiplying until product exceeds 100
- Start with number = 2
- Multiply by 2 each iteration
- Stop when product > 100

**Output:**
```
2
4
8
16
32
64
128
```

**✅ Solution:**
```python
product = 2
while product <= 100:
    print(product)
    product = product * 2
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Simulate a simple guessing game

**Secret number: 7**
**Keep guessing until correct**

**Sample Output:**
```
Guess: 5
Too low!
Guess: 10
Too high!
Guess: 7
Correct!
```

**✅ Solution:**
```python
secret = 7
guess = 0

while guess != secret:
    guess = int(input("Guess: "))
    if guess < secret:
        print("Too low!")
    elif guess > secret:
        print("Too high!")
    else:
        print("Correct!")
```

**Extra Challenge:** Add a maximum attempts limit!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- While loops repeat while condition is True
- Need to manually update counter
- Difference between for and while
- break and continue work in while too

**Weak points to watch:**
- Forgetting to update counter (infinite loop)
- Off-by-one with condition
- Using while when for is better

**Next growth target:**
- Move to Lesson 7: Lists - storing multiple values

**Confidence Check:** Can you write a while loop that counts down? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 6 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 60 (+10 for completing) |
| **Rank** | Beginner |
| **Mastery** | 35% |
| **Weaknesses** | Infinite loop prevention |
| **Recommended Focus** | Practice while loops with different conditions |
| **Suggested Review** | Review for vs while differences |
| **Next Lesson Readiness** | Ready for Lesson 7 (Lists) |

---

**🎉 You completed Lesson 6!**

Type **7** to continue → Lesson 7 (Lists)