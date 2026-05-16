# Lesson 19 — List Comprehension (Danh sách ngắn gọn)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 18 - Nested loops.

**Current Lesson:** Learning **list comprehension** - compact way to create lists.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Basic list comprehension
- With condition (if)
- Nested comprehension

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Basic - create list from loop
squares = [x**2 for x in range(1, 6)]
print(squares)  # [1, 4, 9, 16, 25]

# With condition - filter
evens = [x for x in range(10) if x % 2 == 0]
print(evens)  # [0, 2, 4, 6, 8]

# Transform
upper = [s.upper() for s in ["apple", "banana"]]
print(upper)  # ['APPLE', 'BANANA']

# Nested comprehension
pairs = [(x, y) for x in [1,2] for y in [3,4]]
print(pairs)  # [(1,3),(1,4),(2,3),(2,4)]

# Dictionary comprehension
squares_dict = {x: x**2 for x in range(5)}
print(squares_dict)  # {0:0, 1:1, 2:4, 3:9, 4:16}
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** [x*2 for x in [1,2,3]] = ?
> **Answer:** [2, 4, 6]

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Filter even numbers and square them.

```python
nums = [1, 2, 3, 4, 5, 6]
result = [x**2 for x in nums if x % 2 == 0]
print(result)  # [4, 16, 36]
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 19 / 2000 |
| **XP** | 190 |

Type **20** to continue