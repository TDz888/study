# Lesson 45 — Matrix (2D Arrays)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 44 - Stack and Queue.

**Current Lesson:** Learning **Matrix** — a 2D data structure in Python.

**Why This Matters:**
- Matrices are fundamental in many areas (mathematics, image processing, games)
- Understanding 2D arrays opens doors to grid-based problems
- Many LeetCode problems involve matrix traversal

**Connection:**
```
Variables → Arrays → 2D Arrays (Matrix)
   ↓          ↓          ↓
  Single    Linear     Grid
```

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll master today:**
- Creating matrices in Python
- Accessing elements by row and column
- Traversing matrices (row-wise, column-wise)
- Common matrix operations (diagonal, rotation)
- Common pitfalls and how to avoid them

**Real-world analogy:**
- Spreadsheet: rows and columns of data
- Image: grid of pixels
- Game board: 2D grid of cells

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is a Matrix?

A matrix is a 2D array — a collection of elements organized in rows and columns:

```
Matrix (3x3):

    col0  col1  col2
    ───── ───── ─────
row0   1     2     3
row1   4     5     6
row2   7     8     9

Access: matrix[row][col]
matrix[0][0] = 1
matrix[1][2] = 6
```

### Key Terminology

- **m x n matrix:** m rows, n columns
- **Element:** Individual value in the matrix
- **Row:** Horizontal line of elements
- **Column:** Vertical line of elements
- **Diagonal:** Elements where row index = column index

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Meaning |
|------|----------------|
| **Matrix** | A 2D array (list of lists) |
| **Row** | Horizontal array of elements |
| **Column** | Vertical array of elements |
| **Element** | Single value in matrix |
| **Index** | Position (row, col) |
| **Shape** | Dimensions (rows × cols) |
| **Diagonal** | Elements at positions (i,i) |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

### 1. Creating a Matrix

```python
# Method 1: Direct declaration
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Access elements
print(matrix[0][0])  # 1 (row 0, col 0)
print(matrix[1][2])  # 6 (row 1, col 2)
print(matrix[2][1])  # 8 (row 2, col 1)
```

### 2. Dynamic Matrix Creation

```python
# Create m×n matrix with default value
def create_matrix(rows, cols, default=0):
    """
    Create a matrix with given dimensions.
    
    Important: Must use list comprehension, not multiplication!
    """
    return [[default for _ in range(cols)] for _ in range(rows)]


# Create 3×4 matrix of zeros
mat = create_matrix(3, 4)
print(len(mat))      # 3 (number of rows)
print(len(mat[0]))   # 4 (number of columns)

# Create matrix with computed values
mat2 = [[i * j for j in range(3)] for i in range(3)]
# Row 0: [0, 0, 0]
# Row 1: [0, 1, 2]
# Row 2: [0, 2, 4]

# Create identity matrix
def identity_matrix(n):
    return [[1 if i == j else 0 for j in range(n)] for i in range(n)]

identity = identity_matrix(3)
# [[1, 0, 0],
#  [0, 1, 0],
#  [0, 0, 1]]
```

### 3. Matrix Traversal

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

# Row-wise traversal
print("Row-wise:")
for row in matrix:
    for val in row:
        print(val, end=" ")
    print()

# Column-wise traversal
print("\nColumn-wise:")
cols = len(matrix[0])
for col in range(cols):
    for row in range(len(matrix)):
        print(matrix[row][col], end=" ")
    print()

# Using enumerate
print("\nWith indices:")
for i, row in enumerate(matrix):
    for j, val in enumerate(row):
        print(f"({i},{j})={val}", end=" ")
    print()
```

### 4. Diagonal Sum

```python
def diagonal_sum(matrix):
    """
    Calculate sum of main diagonal (row == col).
    """
    total = 0
    n = len(matrix)
    for i in range(n):
        total += matrix[i][i]
    return total


# Test
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
print(diagonal_sum(matrix))  # 1+5+9 = 15


def anti_diagonal_sum(matrix):
    """
    Calculate sum of anti-diagonal (row + col == n-1).
    """
    total = 0
    n = len(matrix)
    for i in range(n):
        total += matrix[i][n - 1 - i]
    return total

print(anti_diagonal_sum(matrix))  # 3+5+7 = 15
```

### 5. Rotate Matrix 90 Degrees

```python
def rotate_90_clockwise(matrix):
    """
    Rotate matrix 90 degrees clockwise.
    
    Original:      Rotated:
    1 2 3           7 4 1
    4 5 6    →     8 5 2
    7 8 9           9 6 3
    
    Formula: rotated[i][j] = original[n-1-j][i]
    """
    n = len(matrix)
    return [[matrix[n - 1 - j][i] for j in range(n)] for i in range(n)]


def rotate_90_counterclockwise(matrix):
    """
    Rotate matrix 90 degrees counter-clockwise.
    
    Formula: rotated[i][j] = original[j][n-1-i]
    """
    n = len(matrix)
    return [[matrix[j][n - 1 - i] for j in range(n)] for i in range(n)]


# Test
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
rotated = rotate_90_clockwise(matrix)
for row in rotated:
    print(row)
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

### Trace: Diagonal Sum

```
matrix = [[1,2,3],
          [4,5,6],
          [7,8,9]]

Loop:
i=0: matrix[0][0] = 1 → total = 1
i=1: matrix[1][1] = 5 → total = 6
i=2: matrix[2][2] = 9 → total = 15

Result: 15 ✓
```

### Trace: Matrix Rotation

```
Original:
[1, 2, 3]
[4, 5, 6]
[7, 8, 9]

i=0 (new row 0):
  j=0: matrix[2][0] = 7
  j=1: matrix[1][0] = 4
  j=2: matrix[0][0] = 1
  → [7, 4, 1]

i=1 (new row 1):
  j=0: matrix[2][1] = 8
  j=1: matrix[1][1] = 5
  j=2: matrix[0][1] = 2
  → [8, 5, 2]

i=2 (new row 2):
  j=0: matrix[2][2] = 9
  j=1: matrix[1][2] = 6
  j=2: matrix[0][2] = 3
  → [9, 6, 3]

Result: [[7,4,1],[8,5,2],[9,6,3]] ✓
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

### Matrix Indexing

```
matrix[row][col]

    col0   col1   col2
        ┌───┬───┬───┐
row0    │ 0 │ 1 │ 2 │
        ├───┼───┼───┤
row1    │ 3 │ 4 │ 5 │
        ├───┼───┼───┤
row2    │ 6 │ 7 │ 8 │
        └───┴───┴───┘

matrix[0][1] = 1
matrix[2][2] = 8
```

### Common Mistake: List Multiplication

```
❌ WRONG:
mat = [[0] * 3] * 3

This creates:
┌───┬───┬───┐
│ 0 │ 0 │ 0 │  ← Same list!
├───┼───┼───┤
│ 0 │ 0 │ 0 │  ← Same list!
├───┼───┼───┤
│ 0 │ 0 │ 0 │  ← Same list!
└───┴───┴───┘

They all point to the SAME list!

Setting mat[0][0] = 1:
┌───┬───┬───┐
│ 1 │ 0 │ 0 │
├───┼───┼───┤
│ 1 │ 0 │ 0 │  ← Changed too!
├───┼───┼───┤
│ 1 │ 0 │ 0 │  ← Changed too!
└───┴───┴───┘

✅ CORRECT:
mat = [[0 for _ in range(3)] for _ in range(3)]

Creates 3 DIFFERENT lists:
┌───┬───┬───┐
│ 0 │ 0 │ 0 │
├───┼───┼───┤
│ 0 │ 0 │ 0 │
├───┼───┼───┤
│ 0 │ 0 │ 0 │
└───┴───┴───┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake 1: Confusing Row and Column

```python
# ❌ WRONG - accessing as matrix[col][row]
matrix = [[1,2,3], [4,5,6]]
print(matrix[1][2])  # Actually row=1, col=2 → 6 (correct by accident)

# ✅ CORRECT - matrix[row][col]
row = 1
col = 2
print(matrix[row][col])  # 6
```

**Why it happens:** Forgetting which index comes first.

**Prevention:** Remember "R for Row comes first" — like the word "arcade" has 'r' (row) before 'c' (column).

---

### Common Mistake 2: Wrong Matrix Shape

```python
# ❌ WRONG - checking wrong dimension
matrix = [[1,2,3], [4,5,6]]
print(len(matrix))      # 2 (number of ROWS)
print(len(matrix[0]))   # 3 (number of COLS)

# If you need number of rows, use len(matrix)
# If you need number of cols, use len(matrix[0])
```

**Why it happens:** Forgetting that len(matrix) gives rows, not columns.

**Prevention:** Use consistent naming and always double-check.

---

### Common Mistake 3: Shared List Reference

```python
# ❌ WRONG - all rows point to same list!
matrix = [[0] * 3] * 3
matrix[0][0] = 1
print(matrix)
# [[1,0,0], [1,0,0], [1,0,0]] ← ALL changed!

# ✅ CORRECT - each row is independent
matrix = [[0 for _ in range(3)] for _ in range(3)]
matrix[0][0] = 1
print(matrix)
# [[1,0,0], [0,0,0], [0,0,0]]
```

**Why it happens:** `*` creates copies of the same reference, not independent copies.

**Prevention:** Always use list comprehension for matrix creation.

---

### Common Mistake 4: Index Out of Bounds

```python
# ❌ WRONG - going past the last element
matrix = [[1,2,3], [4,5,6]]
# Accessing matrix[1][3] would error - col index max is 2

# ✅ CORRECT - stay within bounds
row = 1
col = 2
if row < len(matrix) and col < len(matrix[row]):
    print(matrix[row][col])
```

**Why it happens:** Not tracking indices properly.

**Prevention:** Always validate indices before access.

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Quick Reference

| Operation | Code |
|-----------|------|
| Access element | `matrix[row][col]` |
| Number of rows | `len(matrix)` |
| Number of columns | `len(matrix[0])` |
| Diagonal (i,i) | `matrix[i][i]` |
| Anti-diagonal | `matrix[i][n-1-i]` |

### When to Use Matrix

- Grid-based problems
- Image representation
- Game boards (chess, tic-tac-toe)
- Mathematical calculations

### Decision Tree

```
Need to store 2D data?
│
├─ YES → Use matrix (list of lists)
│        - Remember: row first, col second
│        - Use list comprehension for creation
│
└─ NO → Use 1D array or other structure
```

### Mnemonic

**"R-C" = Row-Column**
- First index = **R**ow
- Second index = **C**olumn

**"Arcade"**
- A = **A**rray
- R = **R**ow first
- C = **C**olumn second

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

### Question 1: Concept Check

**What is matrix[0][1] in the following matrix?**
```
[1, 2, 3]
[4, 5, 6]
```

> **Answer:** 2
> 
> matrix[0][1] means row 0, column 1, which is the value 2.

---

### Question 2: Prediction

**What is the shape of this matrix?**
```
[1, 2]
[3, 4]
[5, 6]
```

> **Answer:** 3 × 2 (3 rows, 2 columns)
> 
> len(matrix) = 3 rows
> len(matrix[0]) = 2 columns

---

### Question 3: Problem Solving

**What is wrong with this code?**
```python
mat = [[0] * 3] * 3
mat[0][0] = 5
print(mat[1][0])  # What gets printed?
```

> **Answer:** It prints 5!
> 
> The problem: All three rows point to the SAME list.
> mat[0][0] = 5 changes ALL three rows.
> Solution: Use `[[0 for _ in range(3)] for _ in range(3)]`

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

### Problem: Set Matrix Zeroes

**Problem Statement:**
Given an m × n matrix, if an element is 0, set its entire row and column to 0.

**Examples:**
```
Input: matrix = [[1,1,1],[1,0,1],[1,1,1]]
Output: [[1,0,1],[0,0,0],[1,0,1]]

Input: matrix = [[0,1,2,0],[3,4,5,2],[1,3,1,5]]
Output: [[0,0,0,0],[0,4,5,0],[0,3,1,0]]
```

**Solution:**
```python
def set_zeroes(matrix):
    """
    Set entire row and column to 0 if element is 0.
    Uses first row and first col to track which should be zero.
    
    Time: O(m*n)
    Space: O(1)
    """
    m = len(matrix)
    n = len(matrix[0])
    
    # Check if first row has zero
    first_row_zero = any(matrix[0][j] == 0 for j in range(n))
    
    # Check if first col has zero
    first_col_zero = any(matrix[i][0] == 0 for i in range(m))
    
    # Use first row and col to mark zeros
    for i in range(1, m):
        for j in range(1, n):
            if matrix[i][j] == 0:
                matrix[i][0] = 0
                matrix[0][j] = 0
    
    # Set zeros based on markers
    for i in range(1, m):
        if matrix[i][0] == 0:
            for j in range(n):
                matrix[i][j] = 0
    
    for j in range(1, n):
        if matrix[0][j] == 0:
            for i in range(m):
                matrix[i][j] = 0
    
    # Handle first row and col
    if first_row_zero:
        for j in range(n):
            matrix[0][j] = 0
    
    if first_col_zero:
        for i in range(m):
            matrix[i][0] = 0
    
    return matrix


# Read input
m = int(input())
matrix = [list(map(int, input().split())) for _ in range(m)]
result = set_zeroes(matrix)
for row in result:
    print(row)
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

### Challenge: Spiral Matrix

**Problem:**
Given an m × n matrix, return all elements in spiral order.

**Example:**
```
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [1,2,3,6,9,8,7,4,5]

Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
```

**Solution:**
```python
def spiral_order(matrix):
    """
    Return elements in spiral order.
    Top row → right col → bottom row → left col → repeat
    """
    if not matrix or not matrix[0]:
        return []
    
    result = []
    m, n = len(matrix), len(matrix[0])
    
    top, bottom = 0, m - 1
    left, right = 0, n - 1
    
    while top <= bottom and left <= right:
        # Top row (left to right)
        for col in range(left, right + 1):
            result.append(matrix[top][col])
        top += 1
        
        # Right column (top to bottom)
        for row in range(top, bottom + 1):
            result.append(matrix[row][right])
        right -= 1
        
        # Bottom row (right to left) if still valid
        if top <= bottom:
            for col in range(right, left - 1, -1):
                result.append(matrix[bottom][col])
            bottom -= 1
        
        # Left column (bottom to top) if still valid
        if left <= right:
            for row in range(bottom, top - 1, -1):
                result.append(matrix[row][left])
            left += 1
    
    return result


# Test
matrix = [[1,2,3],[4,5,6],[7,8,9]]
print(spiral_order(matrix))  # [1,2,3,6,9,8,7,4,5]
```

**Visualization:**
```
[1,2,3]
[4,5,6]
[7,8,9]

Spiral order:
1→2→3 (top row)
  ↓
6→9 (right column, skip visited)
  ↓
8→7 (bottom row, reverse)
  ↓
4 (left column, from bottom up)
  ↓
5 (center)
```

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

### What You Learned Today

1. **Matrix Creation:** Using list comprehension
2. **Element Access:** matrix[row][col]
3. **Diagonal Sum:** matrix[i][i]
4. **Matrix Rotation:** Using list comprehension
5. **Common Pitfall:** Shared list reference

### Key Takeaways

- Matrix = list of lists
- Row index comes first, column second
- Use list comprehension to create independent rows
- Diagonal: indices (i,i), anti-diagonal: (i, n-1-i)

### Common Patterns

| Pattern | Code |
|---------|------|
| Create matrix | `[[default for _ in range(n)] for _ in range(m)]` |
| Diagonal | `matrix[i][i]` |
| Anti-diagonal | `matrix[i][n-1-i]` |
| Rotate | `matrix[n-1-j][i]` |

### Weak Points to Watch

- Confusing row and column indices
- Using `*` instead of list comprehension for matrix creation
- Off-by-one errors in loops

### Next Lesson Preview

**Lesson 46:** Binary Trees — Hierarchical data structures with nodes

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 45 / 2000 |
| **Chapter** | 4 (Data Structures) |
| **XP** | 450 |
| **Rank** | Builder |
| **Mastery** | Matrix Operations |
| **Weaknesses** | Remembering list comprehension for creation |
| **Recommended Focus** | Practice matrix traversal patterns |
| **Suggested Review** | Lesson 44 (Stack/Queue - used in some matrix problems) |
| **Next Lesson Readiness** | ✓ Ready for Trees |

---

**Type 46 to continue**