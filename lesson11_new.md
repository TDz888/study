# Lesson 11 — File I/O (Đọc/Ghi File)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 10 - Learned modules to import external code (math, random).

**Current Lesson:** Learning **File I/O** - reading and writing files on your computer. Essential for saving data, loading config, processing logs.

**Future Usefulness:** Every real program saves/loads data. Games save progress, apps store settings, scripts process data files.

**Connection:** Modules give you tools → File I/O lets you persist data. Together they create useful programs.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Opening and closing files
- Reading file contents
- Writing to files
- Working with text and binary files
- Context managers (with statement)

**Why it matters:** Data in variables is lost when program ends. Files let you save data permanently.

**Real programmers use it:** Configuration files, data processing, log files, user data - all use file I/O.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### File Operations

| Mode | Purpose |
|------|---------|
| `'r'` | Read (default) - file must exist |
| `'w'` | Write - creates new or overwrites |
| `'a'` | Append - adds to end of file |
| `'rb'` | Read binary |
| `'wb'` | Write binary |

### Opening a File

```python
file = open("filename.txt", "r")  # Opens for reading
```

### Reading Methods

```python
file.read()        # Read entire file as string
file.readline()    # Read one line
file.readlines()   # Read all lines as list
```

### Writing

```python
file.write("text")     # Write string
file.writelines(list)  # Write multiple lines
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **I/O** | Input/Output - reading/writing data |
| **file handle** | A variable that represents the open file |
| **read** | Get data from file into program |
| **write** | Send data from program to file |
| **append** | Add to the end of existing file |
| **context manager** | The "with" statement that handles cleanup |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Reading entire file
print("=== Reading entire file ===")
with open("sample.txt", "r") as file:
    content = file.read()
    print(content)

# Example 2: Reading line by line
print("\n=== Reading line by line ===")
with open("sample.txt", "r") as file:
    for line in file:
        print(line.strip())

# Example 3: Reading as list of lines
print("\n=== Reading as list ===")
with open("sample.txt", "r") as file:
    lines = file.readlines()
    print(f"Total lines: {len(lines)}")
    for i, line in enumerate(lines):
        print(f"Line {i+1}: {line.strip()}")

# Example 4: Writing to a new file
print("\n=== Writing to file ===")
with open("output.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("This is line 2\n")
    file.write("Line 3\n")

# Example 5: Appending to file
print("\n=== Appending to file ===")
with open("output.txt", "a") as file:
    file.write("Appended line 1\n")
    file.write("Appended line 2\n")

# Example 6: Reading and writing
print("\n=== Copy file content ===")
with open("sample.txt", "r") as source:
    with open("copy.txt", "w") as dest:
        for line in source:
            dest.write(line)
```

**Note:** To run these examples, create "sample.txt" with some text first.

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: with open("file.txt", "r") as f: content = f.read()

Step 1: Python sees open("file.txt", "r")
Step 2: Searches for "file.txt" in current directory
Step 3: Opens the file, creates file handle
Step 4: Assigns handle to variable f
Step 5: Python enters "with" block
Step 6: Executes: content = f.read()
        - Reads entire file content
        - Stores in variable "content"
Step 7: Python exits "with" block
Step 8: File automatically closed!

Key insight: "with" ensures file is closed even if error occurs!
```


```
Example: f.write("Hello")

Step 1: Python sees f.write("Hello")
Step 2: Takes "Hello" string
Step 3: Writes to file at current position
Step 4: File now contains "Hello"
Step 5: File position moves forward
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
FILE READING:

┌─────────────────┐     ┌─────────────────────┐
│   Hard Drive   │     │   Python Program    │
├─────────────────┤     ├─────────────────────┤
│                 │     │                     │
│  sample.txt     │     │  file = open(...)   │
│  ┌───────────┐  │     │         │           │
│  │ Line 1    │───────────►read() │           │
│  │ Line 2    │  │     │         ▼           │
│  │ Line 3    │  │     │   "Line 1\nLine 2..."│
│  └───────────┘  │     │                     │
│                 │     └─────────────────────┘
└─────────────────┘

FILE WRITING:

┌─────────────────────┐     ┌─────────────────┐
│   Python Program    │     │   Hard Drive   │
├─────────────────────┤     ├─────────────────┤
│                     │     │                 │
│ "New content" ──────►write()│  sample.txt   │
│                     │     │  ┌───────────┐  │
│                     │     │  │New content│  │
│                     │     │  └───────────┘  │
│                     │     │                 │
└─────────────────────┘     └─────────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — File Not Found
```python
file = open("missing.txt", "r")  # ERROR!
```

**Why it fails:** File doesn't exist for reading.

**✅ Fix:**
```python
# Option 1: Create the file first
# Option 2: Check if exists first
import os
if os.path.exists("missing.txt"):
    file = open("missing.txt", "r")
```

---

### Common Mistake #2 — Forgetting to Close
```python
file = open("data.txt", "w")
file.write("Hello")
# FORGOT: file.close()
# If program crashes, data might be lost!
```

**✅ Fix:** Use "with" statement!
```python
with open("data.txt", "w") as file:
    file.write("Hello")
# Automatically closed!
```

---

### Common Mistake #3 — Write Mode Overwrites
```python
with open("data.txt", "w") as file:
    file.write("New")  # Previous content GONE!
```

**Why it fails:** 'w' mode deletes existing content.

**✅ Fix:** Use 'a' to append instead of 'w'.

---

### Common Mistake #4 — Reading Without Strip
```python
with open("file.txt", "r") as f:
    for line in f:
        print(line)  # Has extra newline!
```

**Why it fails:** Each line includes '\n' from file.

**✅ Fix:** Use .strip() to remove whitespace
```python
print(line.strip())
```

---

### Prevention Strategy

- Use "with" to ensure files close properly
- Use 'w' carefully - it overwrites existing data
- Use .strip() when reading lines
- Handle FileNotFoundError

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- 'r' = read, 'w' = write (overwrite), 'a' = append
- with statement ensures file closes automatically
- read() for entire file, readlines() for list
- write() takes string, must include '\n' for newlines

### Key Syntax
```python
# Read
with open("file.txt", "r") as f:
    content = f.read()

# Write
with open("file.txt", "w") as f:
    f.write("text\n")

# Append
with open("file.txt", "a") as f:
    f.write("text\n")
```

### Patterns to Remember
```
'r'  → read (file must exist)
'w'  → write (creates/overwrites)
'a'  → append (adds to end)
```

### Mistakes to Avoid
- ✗ FileNotFoundError for 'r'
- ✗ Forgetting to close files
- ✗ 'w' overwrites existing content

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What's the output?
```python
with open("test.txt", "w") as f:
    f.write("Hello")
    f.write("World")
```
> **Answer:** File contains "HelloWorld" (no newline between!)

---

**Question 2:** Which mode to use to add to existing file?
> **Answer:** 'a' (append mode)

---

**Question 3:** Fix:
```python
file = open("data.txt", "r")
# forgot something?
```
> **Answer:** Need `file.close()` or use `with` statement

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Read a file and count the number of lines.

**Input:** File "numbers.txt" with multiple lines

**Output:**
```
Number of lines: 5
```

**Starter Code:**
```python
# Count lines in "numbers.txt"
```

**Hints:**
- Use readlines() and len(), or loop and count

**✅ Solution:**
```python
with open("numbers.txt", "r") as f:
    lines = f.readlines()
    print(f"Number of lines: {len(lines)}")
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Challenge:** Write numbers 1-5 to a file, one per line.

**Output (file content):**
```
1
2
3
4
5
```

**✅ Solution:**
```python
with open("numbers.txt", "w") as f:
    for i in range(1, 6):
        f.write(str(i) + "\n")
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Create a simple note-taking program.

**Features:**
- Add a note
- View all notes
- Notes saved to file

**✅ Solution:**
```python
def add_note():
    note = input("Enter note: ")
    with open("notes.txt", "a") as f:
        f.write(note + "\n")

def view_notes():
    with open("notes.txt", "r") as f:
        print(f.read())

while True:
    print("1. Add note 2. View notes 3. Exit")
    choice = input("Choose: ")
    if choice == "1":
        add_note()
    elif choice == "2":
        view_notes()
    else:
        break
```

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- Opening and closing files
- Reading and writing modes
- Using "with" statement
- Reading line by line vs entire file

**Weak points to watch:**
- FileNotFoundError
- Forgetting to close files
- Write mode overwrites

**Next growth target:**
- Move to Lesson 12: Exception Handling

**Confidence Check:** Can you read and write files? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 11 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 110 (+10 for completing) |
| **Rank** | Apprentice |
| **Mastery** | 60% |
| **Weaknesses** | File modes |
| **Recommended Focus** | Practice file operations |
| **Suggested Review** | Review file modes |
| **Next Lesson Readiness** | Ready for Lesson 12 |

---

**🎉 You completed Lesson 11!**

Type **12** to continue → Lesson 12 (Exception Handling)