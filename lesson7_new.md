# Lesson 7 — Lists (Danh sách)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 6 - Learned while loops for repeating code with unknown iterations. Learned to track and update counters.

**Current Lesson:** Learning **lists** - storing multiple values in a single variable. The most common data structure in Python.

**Future Usefulness:** Lists are everywhere - managing tasks, storing scores, holding user data, processing files. Essential for any real program.

**Connection:** Variables store ONE value → Lists store MULTIPLE values. Loops iterate through lists to process each item.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Creating lists
- Accessing list elements (indexing)
- Modifying lists (add, remove, change)
- List slicing
- Common list operations

**Why it matters:** One variable can hold many items. "List of students," "list of prices," "list of actions."

**Real programmers use it:** Every program processes collections of data - all stored in lists or similar structures.

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is a List?

A list is an **ordered collection** of items:
- Ordered: Items have a specific sequence
- Collection: Can hold multiple items
- Any type: Strings, numbers, even other lists!

```python
# List of numbers
numbers = [1, 2, 3, 4, 5]

# List of strings
fruits = ["apple", "banana", "orange"]

# Mixed types
mixed = ["text", 123, 3.14, True]
```

### Indexing (Accessing Items)

Items are numbered starting from **0**:

```
fruits = ["apple", "banana", "orange"]
            [0]        [1]       [2]
```

```python
fruits = ["apple", "banana", "orange"]

print(fruits[0])  # apple (first item)
print(fruits[1])  # banana (second)
print(fruits[2])  # orange (third)
```

### Negative Indexing

```python
fruits = ["apple", "banana", "orange"]

print(fruits[-1])  # orange (last item)
print(fruits[-2])  # banana (second to last)
print(fruits[-3])  # apple (third to last)
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Explanation |
|------|-------------------|
| **list** | An ordered collection of items |
| **element** | A single item in a list |
| **index** | The position number of an element (starts at 0) |
| **indexing** | Accessing element by its position |
| **slicing** | Getting a portion of the list |
| **append** | Add item to the end |
| **insert** | Add item at specific position |
| **remove** | Remove item from list |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

```python
# Creating lists
numbers = [1, 2, 3, 4, 5]
fruits = ["apple", "banana", "orange"]
mixed = ["text", 100, 3.14, True]

# Accessing elements
print("First fruit:", fruits[0])    # apple
print("Last fruit:", fruits[-1])    # orange

# Modifying lists
fruits[0] = "mango"                 # Change first item
print("After change:", fruits)     # ['mango', 'banana', 'orange']

# Adding items
fruits.append("grape")              # Add to end
print("After append:", fruits)     # ['mango', 'banana', 'orange', 'grape']

fruits.insert(1, "cherry")          # Insert at index 1
print("After insert:", fruits)     # ['mango', 'cherry', 'banana', 'orange', 'grape']

# Removing items
fruits.remove("banana")             # Remove by value
print("After remove:", fruits)      # ['mango', 'cherry', 'orange', 'grape']

removed = fruits.pop()              # Remove last item
print("Popped:", removed)           # grape
print("After pop:", fruits)         # ['mango', 'cherry', 'orange']

# List slicing
numbers = [0, 1, 2, 3, 4, 5]
print(numbers[1:4])                 # [1, 2, 3] (index 1 to 3)
print(numbers[:3])                  # [0, 1, 2] (start to 2)
print(numbers[3:])                  # [3, 4, 5] (3 to end)
print(numbers[::2])                 # [0, 2, 4] (every other)

# List length
print("Length:", len(fruits))       # 3
```

**Output:**
```
First fruit: apple
Last fruit: orange
After change: ['mango', 'banana', 'orange']
After append: ['mango', 'banana', 'orange', 'grape']
After insert: ['mango', 'cherry', 'banana', 'orange', 'grape']
After remove: ['mango', 'cherry', 'orange', 'grape']
Popped: grape
After pop: ['mango', 'cherry', 'orange']
[1, 2, 3]
[0, 1, 2]
[3, 4, 5]
[0, 2, 4]
Length: 3
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

```
Example: fruits = ["apple", "banana", "orange"]

Accessing fruits[1]:
Step 1: Python sees fruits[1]
Step 2: Finds list "fruits" in memory
Step 3: Goes to position/index 1
Step 4: Retrieves element at index 1
Step 5: Returns "banana"
Result: print shows "banana"


Example: fruits.append("grape")

Step 1: Python sees .append()
Step 2: Finds the list in memory
Step 3: Goes to the END of the list
Step 4: Adds "grape" there
Step 5: List is now: ["apple", "banana", "orange", "grape"]


Example: fruits[0] = "mango"

Step 1: Python sees assignment to fruits[0]
Step 2: Goes to index 0 in the list
Step 3: Replaces "apple" with "mango"
Step 4: List is now: ["mango", "banana", "orange"]
```

**Index Mapping:**
```
fruits = ["mango", "cherry", "orange", "grape"]
          [0]       [1]      [2]       [3]
          [-4]      [-3]     [-2]      [-1]
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

```
LIST STRUCTURE:

┌─────────────────────────────────────────────────────┐
│                  fruits list                        │
├─────────────────────────────────────────────────────┤
│                                                     │
│   Index:    0        1        2        3           │
│             ▼        ▼        ▼        ▼           │
│          ┌────┬────┬────┬────┐                     │
│          │ 🍎 │ 🍌 │ 🍊 │ 🍇 │                     │
│          │    │    │    │    │                     │
│          │mango│cherry│orange│grape│              │
│          └────┴────┴────┴────┘                     │
│                                                     │
│   Length: 4                                         │
│                                                     │
└─────────────────────────────────────────────────────┘

OPERATIONS:

┌────────────────────────────────────────┐
│  APPEND - add to end                   │
│  ┌────┐                                │
│  │new │ → [🍎][🍌][🍊][🍇][🍒]         │
│  └────┘                                │
└────────────────────────────────────────┘

┌────────────────────────────────────────┐
│  INSERT - add at position              │
│        [🍒] → [🍎][🍒][🍌][🍊][🍇]     │
│         ↑                              │
│         position 1                     │
└────────────────────────────────────────┘

┌────────────────────────────────────────┐
│  REMOVE - remove by value              │
│  [🍎][🍌][🍊][🍇] → [🍎][🍊][🍇]       │
│        (banana removed)                │
└────────────────────────────────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake #1 — Index Out of Range
```python
fruits = ["apple", "banana", "orange"]
print(fruits[3])  # ERROR! Only indices 0, 1, 2 exist!
```

**Why it fails:** Index starts at 0, so length 3 means indices 0-2.

**✅ Fix:** Use valid index
```python
print(fruits[2])  # orange (last valid index)
```

---

### Common Mistake #2 — Forgetting Zero-Based Indexing
```python
numbers = [10, 20, 30]
# Want 20 (second item)
print(numbers[2])  # ERROR! This gives 30!
print(numbers[1])  # Correct! Second item is index 1
```

**Key insight:** First item = index 0, second = index 1, etc.

---

### Common Mistake #3 — Confusing Index and Value in Loop
```python
fruits = ["apple", "banana"]
for f in fruits:
    print(f)  # prints apple, banana (the VALUES)

for i in range(len(fruits)):
    print(i, fruits[i])  # prints 0 apple, 1 banana (index & value)
```

**Remember:** `for f in list` gives values, `for i in range(len())` gives indices

---

### Common Mistake #4 — Modifying While Iterating
```python
numbers = [1, 2, 3, 4, 5]
for n in numbers:
    if n % 2 == 0:
        numbers.remove(n)  # DANGER! Modifies while iterating

# Better approach - use a copy or iterate backwards
for n in numbers[:]:  # iterate over copy
    if n % 2 == 0:
        numbers.remove(n)
```

---

### Prevention Strategy

- Remember: indices start at 0, not 1
- Check: len(list) - 1 is the last valid index
- Never modify a list while iterating over it
- Use `in` to check if value exists before accessing

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Concepts
- Lists store multiple items in order
- Access by index (0-based)
- Append adds to end, insert adds at position
- Remove by value, pop by index
- Slicing gets portions: list[start:end]

### Key Syntax
```python
# Create
list = [item1, item2, item3]

# Access
list[index]
list[-1]  # last item

# Modify
list[index] = new_value
list.append(item)
list.insert(pos, item)
list.remove(item)
list.pop(index)

# Slice
list[start:end]  # portion
```

### Patterns to Remember
```
[0]       → first item
[-1]      → last item
[1:4]     → items at index 1, 2, 3
[:3]      → first 3 items
[::2]     → every other item
```

### Mistakes to Avoid
- ✗ Index out of range (use 0 to len-1)
- ✗ Confusing index 1 with first item
- ✗ Modifying while iterating

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

**Question 1:** What's at fruits[2]?
```python
fruits = ["apple", "banana", "orange", "grape"]
```
> **Answer:** `orange` (index 2 is third item)

---

**Question 2:** What's the output?
```python
numbers = [1, 2, 3, 4, 5]
print(numbers[1:4])
```
> **Answer:** `[2, 3, 4]` (items at index 1, 2, 3)

---

**Question 3:** How do you add "cherry" to the end of fruits?
```python
fruits = ["apple", "banana"]
```
> **Answer:** `fruits.append("cherry")`

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

**Problem:** Create a list of numbers 1-5 and print each number.

**Input:** (none - create list)

**Output:**
```
1
2
3
4
5
```

**Starter Code:**
```python
numbers =  # create your list

# print each number
```

**Hints:**
- Create list: [1, 2, 3, 4, 5]
- Use for loop to iterate

**✅ Solution:**
```python
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    print(num)
```

---

**Difficulty:** ★☆☆☆☆ (Very Easy)

**Challenge:** Find the sum of all numbers in a list.

**Input:** [10, 20, 30, 40, 50]

**Output:**
```
150
```

**✅ Solution:**
```python
numbers = [10, 20, 30, 40, 50]
total = 0
for num in numbers:
    total = total + num
print(total)  # 150
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

**Challenge:** Find the maximum number in a list without using max().

**Input:** [45, 12, 67, 3, 89, 23]

**Output:**
```
89
```

**✅ Solution:**
```python
numbers = [45, 12, 67, 3, 89, 23]
max_num = numbers[0]  # assume first is max

for num in numbers:
    if num > max_num:
        max_num = num

print(max_num)  # 89
```

**Key insight:** Start with first item, compare each subsequent item!

**Extra Challenge:** Find the minimum as well!

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

**What you learned today:**
- Lists store multiple items in order
- Indexing starts at 0
- Add/remove/modify operations
- Slicing for portions

**Weak points to watch:**
- Off-by-one in indexing
- Modifying while iterating
- Confusing value vs index

**Next growth target:**
- Move to Lesson 8: Dictionaries - key-value pairs

**Confidence Check:** Can you access any element in a list? ✓

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 7 / 2000 |
| **Chapter** | 1 - Python Absolute Basics |
| **XP** | 70 (+10 for completing) |
| **Rank** | Beginner |
| **Mastery** | 40% |
| **Weaknesses** | Index confusion |
| **Recommended Focus** | Practice list operations |
| **Suggested Review** | Review indexing and slicing |
| **Next Lesson Readiness** | Ready for Lesson 8 (Dictionaries) |

---

**🎉 You completed Lesson 7!**

Type **8** to continue → Lesson 8 (Dictionaries)