# Lesson 21 — Tuples (Bộ)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 20 - Slicing deep dive.

**Current Lesson:** Learning **tuples** - immutable (unchangeable) sequences.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Creating tuples
- Accessing elements
- Tuple vs list
- Unpacking

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Create
point = (3, 4)
coords = (1, 2, 3)
single = (5,)  # comma needed for single element
empty = ()

# Access - same as list
print(point[0])   # 3
print(point[-1])  # 4

# Cannot modify!
# point[0] = 5  # ERROR!

# Tuple methods
print(coords.count(1))  # 1 (how many 1s)
print(coords.index(2))  # 1 (position of 2)

# Unpacking
x, y = point
print(f"x={x}, y={y}")  # x=3, y=4

# Multiple return from function
def get_stats():
    return 100, 200

a, b = get_stats()
print(a, b)  # 100 200
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** What makes tuple different from list?
> **Answer:** Tuple is immutable (cannot be changed)

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Swap two variables using tuple.

```python
a, b = 1, 2
a, b = b, a
print(a, b)  # 2 1
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 21 / 2000 |
| **XP** | 210 |

Type **22** to continue