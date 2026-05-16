# Lesson 8 — Dictionaries (Từ điển)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 7 - Learned lists to store multiple items in order. Accessed by index (0, 1, 2...).

**Current Lesson:** Learning **dictionaries** - key-value pairs. Instead of indexing by number, you index by meaningful keys.

**Future Usefulness:** Dictionaries are used for fast lookups - user databases, configurations, caches, any data that needs to be accessed by name.

**Connection:** Lists: ordered by position → Dictionaries: ordered by key. Both store multiple items, just different access methods.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Creating dictionaries with key-value pairs
- Accessing values by key
- Adding/modifying/deleting entries
- Iterating over dictionaries
- Common use cases

**Why it matters:** When you need to look up data by name, not by position. "Find user with username 'alice'" - much faster with dict.

**Real programmers use it:** User profiles, API responses, config files, databases - all use key-value structures.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is a Dictionary?

A dictionary stores **key-value pairs**:
- **Key**: The label (like a word in a real dictionary)
- **Value**: The data associated with that key

```python
# Student profile as dictionary
student = {
    "name": "Minh",
    "age": 25,
    "city": "Hanoi"
}
```

```
┌─────────────────────────────────────────┐
│           student dictionary           │
├─────────────────────────────────────────┤
│                                         │
│   "name"   →  "Minh"                   │
│   "age"    →  25                        │
│   "city"   →  "Hanoi"                  │
│                                         │
└─────────────────────────────────────────┘
```

### Accessing Values

```python
student = {"name": "Minh", "age": 25}

print(student["name"])  # Minh (get by key)
print(student["age"])   # 25
```

**Note:** Keys must be unique! Values can be anything.

### When to Use List vs Dictionary

| List | Dictionary |
|------|------------|
| Ordered sequence | Key-value pairs |
| Access by position | Access by key |
| ["apple", "banana"] | {"fruit": "apple"} |
| When order matters | When looking up by name |

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **dictionary** | Collection of key-value pairs |
| **key** | The label used to access a value |
| **value** | The data stored at a key |
| **key-value pair** | A key and its associated value |
| **lookup** | Finding a value by its key |
| **item** | A single key-value pair |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Creating dictionaries
student = {
    "name": "Minh",
    "age": 25,
    "city": "Hanoi"
}

# Accessing values
print("Name:", student["name"])   # Minh
print("Age:", student["age"])     # 25

# Using get() method (safer - doesn't crash if key missing)
print("Country:", student.get("country", "Unknown"))  # Unknown
print("Name:", student.get("name"))  # Minh

# Adding new key-value pairs
student["email"] = "minh@email.com"
print("After add:", student)

# Modifying values
student["age"] = 26
print("After modify:", student)

# Removing entries
removed = student.pop("city")
print("Removed:", removed)  # Hanoi
print("After pop:", student)

del student["email"]  # Another way to delete
print("After del:", student)

# Iterating over dictionary
print("\nAll keys and values:")
for key, value in student.items():
    print(f"{key}: {value}")

# Only keys or only values
print("\nKeys:", student.keys())
print("Values:", student.values())

# Check if key exists
if "name" in student:
    print("\nName exists!")
```

**Output:**
```
Name: Minh
Age: 25
Country: Unknown
Name: Minh
After add: {'name': 'Minh', 'age': 25, 'city': 'Hanoi', 'email': 'minh@email.com'}
After modify: {'name': 'Minh', 'age': 26, 'city': 'Hanoi', 'email': 'minh@email.com'}
Removed: Hanoi
After pop: {'name': 'Minh', 'age': 26, 'email': 'minh@email.com'}
After del: {'name': 'Minh', 'age': 26}

All keys and values:
name: Minh
age: 26

Keys: dict_keys(['name', 'age'])
Values: dict_values(['Minh', 26])

Name exists!
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: student = {"name": "Minh", "age": 25}

Accessing student["name"]:
Step 1: Python sees student["name"]
Step 2: Finds dictionary in memory
Step 3: Looks for key "name"
Step 4: Found! Returns "Minh"
Step 5: print() displays "Minh"


Accessing student["country"] (doesn't exist):
Step 1: Python sees student["country"]
Step 2: Looks for key "country"
Step 3: NOT FOUND - KeyError!
Step 4: CRASHES!

But with get():
Step 1: student.get("country", "Unknown")
Step 2: Looks for "country"
Step 3: Not found - returns default "Unknown"
Step 4: print() displays "Unknown"
```


```
Adding student["email"] = "minh@email.com":
Step 1: Python sees assignment to new key
Step 2: Creates new key "email"
Step 3: Stores value "minh@email.com"
Step 4: Dictionary now has 3 entries
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
DICTIONARY STRUCTURE:

┌─────────────────────────────────────────────────────┐
│              student dictionary                    │
├─────────────────────────────────────────────────────┤
│                                                     │
│   ┌──────────┬─────────────────┐                   │
│   │   KEY    │      VALUE      │                   │
│   ├──────────┼─────────────────┤                   │
│   │  "name"  │     "Minh"      │                   │
│   ├──────────┼─────────────────┤                   │
│   │  "age"   │       25        │                   │
│   ├──────────┼─────────────────┤                   │
│   │  "city"  │    "Hanoi"      │                   │
│   └──────────┴─────────────────┘                   │
│                                                     │
└─────────────────────────────────────────────────────┘

ACCESSING:

student["name"]
        │
        ▼
┌─────────────┐
│  Find key   │──→ "Minh"
│   "name"    │
└─────────────┘

ITERATING:

for key, value in dict.items():
    │
    ├─ key = "name", value = "Minh"
    ├─ key = "age", value = 25
    └─ key = "city", value = "Hanoi"
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — KeyError
```python
student = {"name": "Minh"}
print(student["age"])  # ERROR! Key doesn't exist!
```

**Why it fails:** Key "age" doesn't exist in dictionary.

**✅ Fix - Option 1:** Check first
```python
if "age" in student:
    print(student["age"])
```

**✅ Fix - Option 2:** Use get()
```python
print(student.get("age", 0))  # Returns 0 if not found
```

---

### Common Mistake #2 — Confusing List and Dict Access
```python
fruits = ["apple", "banana"]
student = {"name": "Minh"}

print(fruits[0])      # apple (index)
print(student["name"])  # Minh (key)
```

**Key difference:** Lists use index (number), dicts use key (string/any type).

---

### Common Mistake #3 — Duplicate Keys
```python
d = {"a": 1, "a": 2, "a": 3}
print(d)  # {'a': 3} - only keeps last value!
```

**Why it fails:** Keys must be unique. Duplicate keys overwrite previous values.

---

### Common Mistake #4 — Forgetting Curly Braces
```python
# This is a list, not a dict!
data = ("name", "Minh")  # tuple
data = ["name", "Minh"]  # list

# This is a dict!
data = {"name": "Minh"}  # dict with key-value
```

---

### Prevention Strategy

- Use .get() instead of [] to avoid crashes
- Remember dict uses {}, not []
- Keys must be unique - duplicates overwrite

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- Dictionaries store key-value pairs
- Access values using keys, not indices
- Use .get() to avoid KeyError
- Add/modify/delete with simple operations

### Key Syntax
```python
# Create
dict = {"key1": value1, "key2": value2}

# Access
dict["key"]          # crashes if missing
dict.get("key")      # returns None if missing
dict.get("key", default)  # default if missing

# Add/Modify
dict["new_key"] = value

# Remove
dict.pop("key")
del dict["key"]

# Iterate
for key, value in dict.items():
    print(key, value)
```

### Patterns to Remember
```
{}           → empty dict
{"a": 1}     → dict with one pair
dict["key"]  → access by key
key in dict  → check if key exists
```

### Mistakes to Avoid
- ✗ KeyError when key doesn't exist
- ✗ Using [] instead of {} for dict
- ✗ Duplicate keys (they overwrite!)

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What's the output?
```python
d = {"a": 1, "b": 2}
print(d["b"])
```
> **Answer:** `2`

---

**Question 2:** How do you safely get value for key "age" with default 0?
```python
d = {"name": "Minh"}
```
> **Answer:** `d.get("age", 0)`

---

**Question 3:** What's wrong?
```python
d = {"name": "Minh", "name": "Lan"}
print(d["name"])
```
> **Answer:** Only keeps last value "Lan" - duplicates overwrite!

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Create a dictionary of fruit prices and look up the price of "apple".

**Input:**
- banana: 2
- apple: 5
- orange: 3

**Output:**
```
5
```

**Starter Code:**
```python
fruits = {
    # add your fruit prices
}

# print apple price
```

**Hints:**
- Create dict with fruit names as keys, prices as values
- Use dict["apple"] or dict.get("apple")

**✅ Solution:**
```python
fruits = {
    "banana": 2,
    "apple": 5,
    "orange": 3
}

print(fruits["apple"])  # 5
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Challenge:** Count word frequency in a sentence.

**Input:** "hello world hello python world"

**Output:**
```
{'hello': 2, 'world': 2, 'python': 1}
```

**✅ Solution:**
```python
sentence = "hello world hello python world"
words = sentence.split()

counts = {}
for word in words:
    if word in counts:
        counts[word] = counts[word] + 1
    else:
        counts[word] = 1

print(counts)
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Merge two dictionaries.

**Input:**
- dict1 = {"a": 1, "b": 2}
- dict2 = {"b": 3, "c": 4}

**Output:**
```
{'a': 1, 'b': 3, 'c': 4}
```

**Note:** dict2 overwrites dict1 for key "b"

**✅ Solution:**
```python
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}

merged = dict1.copy()
merged.update(dict2)

print(merged)  # {'a': 1, 'b': 3, 'c': 4}
```

**Key insight:** update() overwrites existing keys!

**Extra Challenge:** Add a function to merge without overwriting duplicates!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- Dictionaries store key-value pairs
- Access by key, not index
- Use .get() to avoid crashes
- Common operations: add, modify, delete, iterate

**Weak points to watch:**
- KeyError when key missing
- Confusing list/dict syntax
- Duplicate keys overwrite

**Next growth target:**
- Move to Lesson 9: Functions - reusable code blocks

**Confidence Check:** Can you create and access a dictionary? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 8 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 80 (+10 for completing) |
| **Rank** | Beginner |
| **Mastery** | 45% |
| **Weaknesses** | KeyError handling |
| **Recommended Focus** | Practice dictionary operations |
| **Suggested Review** | Review get() vs [] access |
| **Next Lesson Readiness** | Ready for Lesson 9 (Functions) |

---

**🎉 You completed Lesson 8!**

Type **9** to continue → Lesson 9 (Functions)