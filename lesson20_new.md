# Lesson 20 — Slicing Deep Dive

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 7 - Basic list indexing.

**Current Lesson:** Deep dive into **slicing** - powerful way to extract portions of sequences.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Start, stop, step
- Negative indexing in slices
- Modify with slice assignment

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Basic
print(numbers[2:5])    # [2,3,4] (index 2 to 4)
print(numbers[:3])     # [0,1,2] (start to 2)
print(numbers[5:])     # [5,6,7,8,9] (5 to end)

# Negative
print(numbers[-3:])    # [7,8,9] (last 3)
print(numbers[:-3])    # [0,1,2,3,4,5,6] (everything except last 3)

# Step
print(numbers[::2])    # [0,2,4,6,8] (every other)
print(numbers[1::2])   # [1,3,5,7,9] (odd indices)
print(numbers[::-1])   # [9,8,7,6,5,4,3,2,1,0] (reversed!)

# Slice assignment
numbers[2:5] = [20, 30]
print(numbers)  # [0,1,20,30,5,6,7,8,9]
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** numbers[::-2] = ?
> **Answer:** [9, 7, 5, 3, 1] (reverse, every other)

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Reverse string using slice.

```python
s = "Python"
print(s[::-1])  # "nohtyP"
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 20 / 2000 |
| **XP** | 200 |

Type **21** to continue