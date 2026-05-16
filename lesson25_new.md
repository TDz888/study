# Lesson 25 — Lambda Functions (Hàm Lambda)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 9 - Regular functions.

**Current Lesson:** Learning **lambda** - anonymous inline functions.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Lambda syntax
- Using with map(), filter(), sorted()
- Lambda vs def

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Lambda - anonymous function
square = lambda x: x ** 2
print(square(5))  # 25

# Multiple parameters
add = lambda a, b: a + b
print(add(3, 4))  # 7

# With map
nums = [1, 2, 3, 4]
squared = list(map(lambda x: x**2, nums))
print(squared)  # [1, 4, 9, 16]

# With filter
evens = list(filter(lambda x: x % 2 == 0, nums))
print(evens)  # [2, 4]

# With sorted
pairs = [(1, "one"), (3, "three"), (2, "two")]
sorted_pairs = sorted(pairs, key=lambda x: x[0])
print(sorted_pairs)  # [(1,'one'),(2,'two'),(3,'three')]
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** lambda x: x + 1 with input 5 returns?
> **Answer:** 6

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Sort list by string length.

```python
words = ["apple", "hi", "banana"]
sorted_words = sorted(words, key=lambda w: len(w))
print(sorted_words)  # ['hi','apple','banana']
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 25 / 2000 |
| **XP** | 250 |

Type **26** to continue