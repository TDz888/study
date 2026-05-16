# Lesson 18 — Nested Loops (Vòng lặp lồng)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 17 - While loops deep dive.

**Current Lesson:** Learning **nested loops** - loops inside loops. Essential for 2D data, patterns.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Loop inside another loop
- 2D list traversal
- Pattern printing
- Performance considerations

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Multiplication table
print("=== Multiplication Table ===")
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i} x {j} = {i*j}", end="\t")
    print()  # new line after each row

# Example 2: 2D list
print("\n=== 2D List ===")
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
for row in matrix:
    for col in row:
        print(col, end=" ")
    print()

# Example 3: Pattern
print("\n=== Triangle Pattern ===")
for i in range(1, 5):
    print("*" * i)

# Example 4: Sum 2D list
print("\n=== Sum 2D ===")
total = 0
for row in matrix:
    for num in row:
        total += num
print(f"Total: {total}")
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** How many times does inner loop run in for i in range(3): for j in range(2):?
> **Answer:** 6 times (3 x 2)

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Print pyramid pattern.

```python
for i in range(1, 6):
    print(" " * (5-i) + "*" * (2*i-1))
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 18 / 2000 |
| **XP** | 180 |

Type **19** to continue