# Lesson 43 — Hashing and Hash Tables

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 42 - String Algorithms.

**Current Lesson:** Learning **Hashing** — a technique for fast data lookup.

**Why This Matters:**
- Hash tables provide O(1) average-case lookup
- Used in countless real-world applications (databases, caches, dictionaries)
- Essential for solving many algorithm problems efficiently

**Connection:**
```
Arrays → Search → Hash Tables
   ↓        ↓        ↓
Sequential  O(n)    O(1)
```

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll master today:**
- What is a hash table and how it works
- Dictionary (dict) in Python — the ultimate hash table
- Set — the unique value collection
- Solving classic problems like Two Sum
- When to use hashing vs other data structures

**Real-world analogy:**
Think of a dictionary book:
- You look up "apple" → instant find by alphabet
- Not flipping through every page (O(n))
- Hash tables work the same way: key → instant location

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is Hashing?

Hashing is a technique that maps data to a fixed-size array index.

```
Data: "apple" → Hash Function → Index: 4
Data: "banana" → Hash Function → Index: 2

O(1) lookup! No need to search.
```

### How Python Dictionaries Work

Python's `dict` is a hash table under the hood:

```python
# Create a dictionary (hash table)
phonebook = {
    "Alice": "555-1234",
    "Bob": "555-5678",
    "Charlie": "555-9999"
}

# O(1) lookup!
print(phonebook["Alice"])  # 555-1234

# O(1) insertion
phonebook["Diana"] = "555-0000"
```

### Why Hash Tables are Fast

| Operation | Array | Hash Table |
|------------|-------|------------|
| Search | O(n) | O(1) average |
| Insert | O(1) | O(1) average |
| Delete | O(n) | O(1) average |

The secret: **direct addressing** via hash function.

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Meaning |
|------|----------------|
| **Hash Function** | Converts a key to an index number |
| **Hash Table** | Data structure that uses hash function for fast lookup |
| **Key** | The identifier used to store/retrieve data |
| **Value** | The data stored at a key |
| **Collision** | When two keys map to the same index (Python handles this) |
| **Load Factor** | How full the hash table is |
| **Set** | Collection of unique values (no duplicates) |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

### 1. Basic Hash Table Operations

```python
# Create a dictionary (hash table)
student = {
    "name": "Alice",
    "age": 20,
    "grade": "A"
}

# Access values (O(1))
print(student["name"])  # Alice

# Add/Update (O(1))
student["score"] = 95
student["age"] = 21

# Delete (O(1))
del student["grade"]

# Check existence (O(1))
if "name" in student:
    print("Name exists")
```

---

### 2. Counting with Dictionary

```python
# Count character frequency in a string
text = "hello world"
freq = {}

for char in text:
    # Get value, default to 0 if not exists
    freq[char] = freq.get(char, 0) + 1

print(freq)
# Output: {'h': 1, 'e': 1, 'l': 3, 'o': 2, ' ': 1, 'w': 1, 'r': 1, 'd': 1}

# Alternative: use Counter (more Pythonic)
from collections import Counter
freq = Counter(text)
print(freq)  # Same result!
```

---

### 3. Set — Unique Values Only

```python
# Create a set (removes duplicates)
numbers = [1, 2, 3, 2, 1, 4, 3, 5]
unique = set(numbers)
print(unique)  # {1, 2, 3, 4, 5}

# O(1) membership check
if 3 in unique:
    print("3 is in the set")

# Add and remove
unique.add(6)      # O(1)
unique.discard(1)  # O(1), no error if not exists
unique.remove(2)   # O(1), raises error if not exists

# Set operations
set1 = {1, 2, 3}
set2 = {2, 3, 4}

print(set1 | set2)  # Union: {1, 2, 3, 4}
print(set1 & set2)  # Intersection: {2, 3}
print(set1 - set2)  # Difference: {1}
```

---

### 4. Classic Two Sum Problem

```python
def two_sum(nums, target):
    """
    Find two numbers that add up to target.
    Returns indices of the two numbers.
    
    Time: O(n)
    Space: O(n)
    """
    seen = {}  # Maps number -> its index
    
    for i, num in enumerate(nums):
        complement = target - num
        
        # Check if complement exists
        if complement in seen:
            return [seen[complement], i]
        
        # Store current number with its index
        seen[num] = i
    
    return []  # No solution found


# Test
nums = [2, 7, 11, 15]
target = 9
print(two_sum(nums, target))  # [0, 1] (2 + 7 = 9)

# Another example
nums = [3, 2, 4]
target = 6
print(two_sum(nums, target))  # [1, 2] (2 + 4 = 6)
```

---

### 5. Finding Missing Number

```python
def find_missing(n, nums):
    """
    Find the missing number in range 1 to n.
    Input: n = 5, nums = [1, 2, 4, 5, 5]
    Output: 3
    """
    # Create expected set
    expected = set(range(1, n + 1))
    
    # Get actual numbers
    actual = set(nums)
    
    # Find difference
    missing = expected - actual
    
    return list(missing)[0] if missing else -1


# Test
n = 5
nums = [1, 2, 4, 5, 5]
print(find_missing(n, nums))  # 3
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

### Trace: Two Sum

```
nums = [2, 7, 11, 15], target = 9

Step 1: i=0, num=2
  complement = 9 - 2 = 7
  Is 7 in seen? → No (seen is empty)
  seen[2] = 0
  seen = {2: 0}

Step 2: i=1, num=7
  complement = 9 - 7 = 2
  Is 2 in seen? → YES! seen[2] = 0
  Return [0, 1] ✓

Result: [0, 1] (nums[0]=2 + nums[1]=7 = 9)
```

### Trace: Character Frequency

```
text = "hello"

Loop:
1. char='h': freq.get('h',0)+1 = 0+1=1 → freq={'h':1}
2. char='e': freq.get('e',0)+1 = 0+1=1 → freq={'h':1,'e':1}
3. char='l': freq.get('l',0)+1 = 0+1=1 → freq={'h':1,'e':1,'l':1}
4. char='l': freq.get('l',0)+1 = 1+1=2 → freq={'h':1,'e':1,'l':2}
5. char='o': freq.get('o',0)+1 = 0+1=1 → freq={'h':1,'e':1,'l':2,'o':1}

Final: {'h':1, 'e':1, 'l':2, 'o':1} ✓
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

### Hash Table Visualization

```
Dictionary: {"name": "Alice", "age": 20}

Memory Layout (conceptual):
┌─────────┬──────────────┬──────────┐
│   Key   │    Hash      │  Value  │
├─────────┼──────────────┼──────────┤
│ "name"  │    1234      │ "Alice" │
│ "age"   │    5678      │    20   │
└─────────┴──────────────┴──────────┘

Access "name": Hash("name") → 1234 → value "Alice"
```

### Two Sum Visualization

```
nums = [2, 7, 11, 15], target = 9

Iteration 1:
┌─────────────────────────┐
│  i=0, num=2             │
│  complement = 7         │
│  seen = {}              │
│  7 not in seen          │
│  seen[2] = 0            │
└─────────────────────────┘
seen = {2: 0}

Iteration 2:
┌─────────────────────────┐
│  i=1, num=7             │
│  complement = 2         │
│  seen = {2:0}           │
│  2 IN seen! ✓           │
│  Return [seen[2], 1]    │
└─────────────────────────┘
       ↓
     [0, 1]
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake 1: Using List for Large Data

```python
# ❌ WRONG - O(n) search!
big_list = [1, 2, 3, ..., 10000]
target = 9999
for x in big_list:  # Loops through 9999 items!
    if x == target:
        print("Found")

# ✅ CORRECT - O(1) lookup
big_set = set(big_list)
if target in big_set:  # Instant!
    print("Found")
```

**Why it happens:** Not realizing list search is slow for large data.

**Prevention:** Always use set/dict for membership checks on large data.

---

### Common Mistake 2: Confusing Keys and Values

```python
# ❌ WRONG - Checking values with 'in'
d = {"a": 1, "b": 2}
if 1 in d:  # Checks keys, not values!
    print("Found")  # Won't print

# ✅ CORRECT - Check values properly
if 1 in d.values():
    print("Found")  # Will print
```

**Why it happens:** `in` operator checks keys by default for dicts.

**Prevention:** Use `.values()` when checking values.

---

### Common Mistake 3: Not Handling Missing Keys

```python
# ❌ WRONG - Would crash if key doesn't exist
d = {}
print(d["missing"])  # KeyError!

# ✅ CORRECT - Use get() with default
d = {}
print(d.get("missing", 0))  # Returns 0, doesn't crash
print(d.get("existing", -1))  # Returns -1 for missing key
```

**Why it happens:** Accessing non-existent keys raises KeyError.

**Prevention:** Always use `.get(key, default)` instead of `d[key]`.

---

### Common Mistake 4: Forgetting to Initialize

```python
# ❌ WRONG - May get UnboundLocalError
seen = {}
for num in [1, 2, 3]:
    if num not in seen:
        seen[num] = 1
    else:
        seen[num] += 1  # Works but verbose

# ✅ CORRECT - Use get()
seen = {}
for num in [1, 2, 3]:
    seen[num] = seen.get(num, 0) + 1
```

**Why it happens:** Manual checking is verbose and error-prone.

**Prevention:** Use `.get(key, default)` for one-liner initialization.

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Quick Reference

| Operation | Time Complexity |
|-----------|-----------------|
| dict[key] | O(1) |
| key in dict | O(1) |
| dict.get(key) | O(1) |
| key in set | O(1) |
| list lookup | O(n) |

### When to Use Hashing

| Problem Type | Solution |
|-------------|----------|
| Find duplicates | Use set |
| Count occurrences | Use dict/Counter |
| Two sum | Use dict to store seen |
| Find missing | Use set difference |
| Fast lookup | Use dict/set |

### Decision Tree

```
Need to store key-value pairs?
│
├─ YES → dict (hash map)
│
└─ NO → Need unique values only?
         ├─ YES → set
         └─ NO → list
```

### Mnemonic

**"D-S-C"**
- **D**ictionary: key → value (O(1))
- **S**et: unique only (O(1) lookup)
- **C**ounter: automatic counting

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

### Question 1: Concept Check

**What is the time complexity of checking if an element exists in a set?**

> **Answer:** O(1) average case.
> 
> Hash tables provide constant-time lookup because the hash function directly computes the index.

---

### Question 2: Prediction

**What is the output of this code?**
```python
d = {"a": 1, "b": 2}
d.get("c", -1)
```

> **Answer:** -1
> 
> `.get("c", -1)` returns the default value -1 because key "c" doesn't exist in the dictionary.

---

### Question 3: Problem Solving

**How would you find all unique elements in a list using hashing?**

> **Answer:** Convert the list to a set.
> 
> ```python
> unique = set(your_list)
> ```
> 
> Sets automatically remove duplicates because they can only contain unique values.

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

### Problem: Majority Element

**Problem Statement:**
Given an array `nums` of size n, return the majority element. The majority element is the element that appears more than ⌊n/2⌋ times.

**Examples:**
```
Input: nums = [3,2,3]
Output: 3

Input: nums = [2,2,1,1,1,2,2]
Output: 2 (appears 4 times > 7/2 = 3)
```

**Approach:** Use Counter

```python
from collections import Counter

def majority_element(nums):
    """
    Find majority element (appears > n/2 times).
    
    Time: O(n)
    Space: O(n)
    """
    freq = Counter(nums)
    threshold = len(nums) // 2
    
    for num, count in freq.items():
        if count > threshold:
            return num
    
    return -1  # Should not happen if majority exists


# Alternative: Boyer-Moore Voting (O(1) space)
def majority_element_v2(nums):
    """
    Boyer-Moore Voting Algorithm.
    
    Time: O(n)
    Space: O(1)
    """
    count = 0
    candidate = None
    
    for num in nums:
        if count == 0:
            candidate = num
        count += (1 if num == candidate else -1)
    
    return candidate


# Read input
nums = list(map(int, input().split()))
print(majority_element(nums))
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

### Challenge: Find the Difference

**Problem:**
You are given two strings s and t where t was formed by shuffling s and adding a new character. Find the index of the new character.

**Example:**
```
Input: s = "abcd", t = "abcde"
Output: "e"

Input: s = "", t = "y"
Output: "y"

Input: s = "a", t = "aa"
Output: "a"
```

**Solution:**
```python
def find_the_difference(s, t):
    """
    Find added character.
    
    Method 1: Using Counter
    """
    from collections import Counter
    
    # Count characters in t
    freq_t = Counter(t)
    
    # Subtract characters in s
    for c in s:
        freq_t[c] -= 1
    
    # Find the character with count > 0
    for char, count in freq_t.items():
        if count > 0:
            return char
    
    return ""


# Alternative: Sum method
def find_the_difference_v2(s, t):
    """
    Sum of char codes.
    """
    return chr(sum(ord(c) for c in t) - sum(ord(c) for c in s))


# Alternative: XOR method
def find_the_difference_v3(s, t):
    """
    XOR all characters - duplicates cancel out!
    """
    result = 0
    for c in s + t:
        result ^= ord(c)
    return chr(result)


# Test
print(find_the_difference("abcd", "abcde"))  # e
print(find_the_difference("", "y"))          # y
print(find_the_difference("a", "aa"))       # a
```

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

### What You Learned Today

1. **Hash Tables:** Fast O(1) lookup data structure
2. **Dictionary:** Key-value storage with O(1) access
3. **Set:** Unique values with O(1) membership check
4. **Two Sum:** Classic problem using hash tables
5. **Counting:** Using Counter for frequency analysis

### Key Takeaways

- Hash tables provide constant-time operations
- Use dict for key-value pairs
- Use set for unique values
- Use Counter for automatic counting

### Common Patterns

| Pattern | Code |
|---------|------|
| Count | `Counter(list)` |
| Unique | `set(list)` |
| Lookup | `if x in dict/set` |
| Default | `dict.get(key, default)` |

### Weak Points to Watch

- Using list instead of set for membership checks
- Confusing keys vs values in dict
- Forgetting `.get()` and using direct access

### Next Lesson Preview

**Lesson 44:** Introduction to Dynamic Programming — Building solutions from subproblems

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 43 / 2000 |
| **Chapter** | 5 (Algorithm Patterns) |
| **XP** | 430 |
| **Rank** | Builder |
| **Mastery** | Hash Tables |
| **Weaknesses** | Remembering when to use dict vs set |
| **Recommended Focus** | Practice more Two Sum variations |
| **Suggested Review** | Lesson 41 (Sliding Window uses hash) |
| **Next Lesson Readiness** | ✓ Ready for Dynamic Programming |

---

**Type 44 to continue**