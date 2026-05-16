# Lesson 1 — Hello World! (Chào thế giới!)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** (none - this is the first lesson)

**Current Lesson:** Learning `print()` function - the most fundamental Python command

**Future Usefulness:** Every Python program you'll ever write will use `print()` to display output. This is your first step into the world of programming.

**Connection:** Just like saying "Hello" to start a conversation, `print()` is how your program speaks to you.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- What `print()` is and how it works
- How to display text on screen
- What is a string (text data)
- How to run your first Python program

**Why it matters:** Without `print()`, you can't see what your program is doing. It's the window into your code's behavior.

**Real programmers use it:** Every developer uses `print()` constantly - for debugging, logging, and showing results.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is print()?

Think of `print()` like a speaker - it speaks words out loud. But instead of sound, it shows text on your screen.

```
print("Hello")
   ↓
[Your Screen shows: Hello]
```

### What is a String?

A **string** is just text - letters, words, sentences. In Python, text must be wrapped in quotes:

- `"Hello"` = string
- `'Hello'` = also a string
- `123` = NOT a string (that's a number)

### The Anatomy of print()

```
print("Hello World!")
│    │              │
│    │              │
│    └──────────────┘
│         │
│         └text inside─this is the STRING
│
└──THE FUNCTION that outputs to screen
```

### Analogy

`print()` is like a printer:
- You give it paper (text in quotes)
- It prints (displays) onto the screen

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **function** | A reusable block of code that does something specific |
| **print()** | The function that displays text on screen |
| **string** | Text data - characters wrapped in quotes |
| **parameter** | The input value placed inside the parentheses |
| **" "** (quotes) | The markers that tell Python "this is text, not code" |
| **()** (parentheses) | The container for the function's input |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Your first Python program - displays greeting on screen
print("Hello World!")
```

**Output:**
```
Hello World!
```

**Code Breakdown:**
```python
print(        )  # The print function - outputs to screen
   │           │
   │           └── parentheses (function container)
   │
   └────────────"Hello World!"  # The string (text) to display
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

Let's trace exactly what happens when Python runs your code:

```
STEP 1: Python reads the line
        ↓
STEP 2: Python sees "print"
        ↓
STEP 3: Python sees "(" - knows this is a function call
        ↓
STEP 4: Python sees "Hello World!" inside quotes
        ↓
        └─ recognizes this as a STRING (text data)
        ↓
STEP 5: Python executes print() with that string
        ↓
STEP 6: Text appears on your screen
        ↓
RESULT: Hello World!
```

**Line-by-line computer thinking:**
```python
print("Hello World!")
│
│  "I need to call the print function"
│           │
│           "The parameter is 'Hello World!' - that's a string"
│                    │
│                    "I'll display this text on screen"
│
└──> Hello World! (appears on screen)
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
┌─────────────────────────────────────┐
│           YOUR COMPUTER             │
├─────────────────────────────────────┤
│                                     │
│   Code: print("Hello World!")       │
│           │                         │
│           ▼                         │
│   ┌─────────────────────────┐      │
│   │    print() FUNCTION     │      │
│   │  ┌───────────────────┐  │      │
│   │  │ "Hello World!"    │  │      │
│   │  │   (STRING)        │  │      │
│   │  └───────────────────┘  │      │
│   └───────────┬─────────────┘      │
│               ▼                     │
│   ┌─────────────────────────┐      │
│   │      OUTPUT SCREEN       │      │
│   │   Hello World!           │      │
│   └─────────────────────────┘      │
│                                     │
└─────────────────────────────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Beginner Mistake #1 — Missing Quotes
```python
print(Hello World!)  # ERROR!
```

**Why it fails:** Without quotes, Python thinks "Hello" and "World!" are variable names (code), not text.

**Correct thinking:** Text must be wrapped in quotes to tell Python "this is just text, don't try to run it as code."

**✅ Fix:**
```python
print("Hello World!")
```

---

### Common Beginner Mistake #2 — Missing Closing Quote
```python
print("Hello World!)  # ERROR!
```

**Why it fails:** Python sees the opening quote but can't find the closing quote - it keeps waiting.

**✅ Fix:**
```python
print("Hello World!")
```

---

### Common Beginner Mistake #3 — Wrong Quote Style (Smart Quotes)
```python
print(”Hello World!”)  # ERROR! (these are "smart" quotes)
```

**Why it fails:** The curly quotes " " are different from straight quotes " ". Python only accepts straight quotes.

**✅ Fix:**
```python
print("Hello World!")  # Use straight quotes
```

---

### Prevention Strategy

**Always ask yourself:**
- Did I open with " ? ✓
- Did I close with " ? ✓
- Are they straight quotes, not curly? ✓

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- `print()` displays text on screen
- Text (strings) must use quotes: `"text"` or `'text'`
- The parentheses () hold the function's input

### Key Syntax
```python
print("your text here")
```

### Pattern to Remember
```
function_name("what to do it with")
```

### Mistakes to Avoid
- ✗ Missing quotes around text
- ✗ Using smart/curly quotes
- ✗ Forgetting closing quote

**Memory Hook:** Think of quotes as "bookends" for text - they hold the text in place.

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What will `print("Xin chào")` display?
> **Answer:** `Xin chào` (the text inside the quotes)

---

**Question 2:** Why does this code fail?
```python
print(Xin chào)
```
> **Answer:** Missing quotes - Python thinks "Xin" and "chào" are variables (code), not text. Without quotes, Python tries to find variables named Xin and chào.

---

**Question 3:** Fix this error:
```python
print("Hello World!
```
> **Answer:** Missing closing quote. Correct: `print("Hello World!")`

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Write a program that prints: `Chao ban den voi Python`

**Input:** (none required)

**Output:**
```
Chao ban den voi Python
```

**Starter Code:**
```python
# Write your code here
```

**Hints:**
- Use the `print()` function
- Put the text inside quotes
- Don't forget both opening and closing quotes

**✅ Solution:**
```python
print("Chao ban den voi Python")
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Decomposition Guidance:**
1. What function displays text? → `print()`
2. What text needs to be shown? → `"Chao ban den voi Python"`
3. Combine them → `print("Chao ban den voi Python")`

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Print 3 separate lines:
```
Toi la Python
Toi dang hoc print()
Den day di!
```

**Requirements:** Use 3 separate print() statements

**✅ Solution:**
```python
print("Toi la Python")
print("Toi dang hoc print()")
print("Den day di!")
```

**Key Insight:** Each `print()` creates a new line of output.

**Extra Challenge:** Can you print 5 lines? Try it!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- `print()` is the function to display output
- Strings must be wrapped in quotes
- Each print() produces one line of output

**Weak points to watch:**
- Forgetting quotes around text
- Using smart quotes instead of straight quotes

**Next growth target:**
- Move to Lesson 2: Variables - learning how to store data
- Practice: Try printing different messages on your own

**Confidence Check:** Can you write `print("Your name")` without looking? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 1 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 10 |
| **Rank** | Beginner |
| **Mastery** | 10% |
| **Weaknesses** | Quote handling, string concept |
| **Recommended Focus** | Practice print() with different texts |
| **Suggested Review** | Review string vs variable concept |
| **Next Lesson Readiness** | Ready for Lesson 2 (Variables) |

---

**🎉 Congratulations! You completed Lesson 1!**

Type **2** to continue → Lesson 2 (Variables)