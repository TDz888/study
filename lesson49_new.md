# Lesson 49 — Time and Space Complexity

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 48 - Common Algorithm Patterns.

**Current Lesson:** Learning **Big O Notation** — how to measure algorithm efficiency.

**Why This Matters:**
- Interviewers always ask about complexity
- Helps you choose the best solution
- Enables you to predict performance on large inputs

**Connection:**
```
All Patterns → Complexity Analysis → Optimal Solution
      ↓                 ↓                ↓
  Algorithms        How fast?         Best choice
```

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll master today:**
- Understanding Big O notation
- Time complexity of common operations
- Space complexity analysis
- Comparing algorithms
- Optimization techniques

**Real-world analogy:**
- Big O is like measuring speed in car racing
- O(1) = teleport (instant)
- O(n) = driving (linear time)
- O(n²) = walking through a maze (gets slow fast)

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is Big O?

Big O describes how the runtime grows as input size increases:

```
Input Size (n)
    │
 1M ┤
    │              * O(2^n) - Too slow!
100K│         * O(n²) - Slow for large n
    │     * O(n log n) - Good
 10K│   * O(n) - Linear
    │ * O(log n) - Fast
1000│
    │*
 100│
    └─────────────────────────►
      1   10   100   1000   10000
```

### Common Complexities (from best to worst)

| Big O | Name | Example |
|-------|------|---------|
| O(1) | Constant | Access array by index |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Loop through array |
| O(n log n) | Linearithmic | Efficient sorting |
| O(n²) | Quadratic | Nested loops |
| O(2^n) | Exponential | Fibonacci (naive) |
| O(n!) | Factorial | Permutations |

### Key Insight: Worst Case

When we say "O(n)", we mean worst-case time. We drop:
- Constants (O(2n) = O(n))
- Lower-order terms (O(n² + n) = O(n²))
- Base of logarithm (O(log₂n) = O(log n))

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Meaning |
|------|----------------|
| **Big O** | Notation for measuring algorithm growth rate |
| **Time Complexity** | How long algorithm takes to run |
| **Space Complexity** | How much memory algorithm uses |
| **Constant** | Doesn't change with input size |
| **Linear** | Grows proportionally with input |
| **Quadratic** | Grows with square of input |
| **Worst Case** | Maximum time/space the algorithm needs |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

### 1. O(1) - Constant Time

```python
def get_first_element(arr):
    """
    Access first element - always instant regardless of size.
    Time: O(1), Space: O(1)
    """
    return arr[0]


def get_element_by_index(arr, index):
    """
    Access by index - constant time.
    Time: O(1)
    """
    return arr[index]


def check_empty(arr):
    """
    Check if empty - constant.
    Time: O(1)
    """
    return len(arr) == 0
```

### 2. O(n) - Linear Time

```python
def find_max(arr):
    """
    Find maximum - must check all elements.
    Time: O(n), Space: O(1)
    """
    max_val = arr[0]
    for num in arr:
        if num > max_val:
            max_val = num
    return max_val


def count_occurrences(arr, target):
    """
    Count how many times target appears.
    Time: O(n), Space: O(1)
    """
    count = 0
    for num in arr:
        if num == target:
            count += 1
    return count


def is_unique(arr):
    """
    Check if all elements are unique.
    Time: O(n), Space: O(n) for set
    """
    seen = set()
    for num in arr:
        if num in seen:
            return False
        seen.add(num)
    return True
```

### 3. O(n²) - Quadratic Time

```python
def bubble_sort(arr):
    """
    Bubble sort - nested loops.
    Time: O(n²), Space: O(1)
    """
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr


def find_pairs_with_sum(arr, target):
    """
    Find all pairs that sum to target - nested loops.
    Time: O(n²), Space: O(1)
    """
    result = []
    n = len(arr)
    for i in range(n):
        for j in range(i + 1, n):
            if arr[i] + arr[j] == target:
                result.append([arr[i], arr[j]])
    return result


def is_anagram_brute(s1, s2):
    """
    Check anagram by comparing all pairs.
    Time: O(n²) - but actually O(n log n) if we sort
    """
    # Sort approach is O(n log n)
    return sorted(s1) == sorted(s2)
```

### 4. O(log n) - Logarithmic Time

```python
def binary_search(arr, target):
    """
    Binary search - halves search space each step.
    Time: O(log n), Space: O(1)
    """
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1


def power_of_two(n):
    """
    Check if n is power of 2 using divide by 2.
    Time: O(log n), Space: O(1)
    """
    while n > 1:
        if n % 2 != 0:
            return False
        n = n // 2
    return True


# Trace: binary_search([1,2,3,4,5,6,7,8,9], 5)
# Step 1: left=0, right=8, mid=4, arr[4]=5 → Found! ✓
# Step 2: binary_search([1,2,3,4,5], 1)
#   left=0, right=4, mid=2, arr[2]=3 > 1 → right=1
#   left=0, right=1, mid=0, arr[0]=1 → Found! ✓
```

### 5. O(n log n) - Linearithmic Time

```python
def merge_sort(arr):
    """
    Merge sort - divide array, sort halves, merge.
    Time: O(n log n), Space: O(n)
    """
    if len(arr) <= 1:
        return arr
    
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    
    return merge(left, right)


def merge(left, right):
    """Merge two sorted arrays."""
    result = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    
    result.extend(left[i:])
    result.extend(right[j:])
    return result


def quick_sort(arr):
    """
    Quick sort - partition around pivot.
    Time: O(n log n) average, O(n²) worst, Space: O(log n)
    """
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quick_sort(left) + middle + quick_sort(right)
```

### 6. Space Complexity Examples

```python
# O(1) - Constant space
def sum_array(arr):
    total = 0  # Only one variable
    for num in arr:
        total += num
    return total


# O(n) - Linear space
def create_copy(arr):
    return arr[:]  # Creates new array of same size


# O(n) - Space for hash map
def count_frequencies(arr):
    freq = {}  # Could have up to n entries
    for num in arr:
        freq[num] = freq.get(num, 0) + 1
    return freq


# O(log n) - Recursion stack
def binary_search_recursive(arr, target, left=0, right=None):
    if right is None:
        right = len(arr) - 1
    
    if left > right:
        return -1
    
    mid = (left + right) // 2
    
    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        return binary_search_recursive(arr, target, mid + 1, right)
    else:
        return binary_search_recursive(arr, target, left, mid - 1)
# Space: O(log n) due to recursion depth
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

### Trace: Binary Search Time Complexity

```
n = 16 elements

Step 1: Search 16 → mid = 8
Step 2: Search 8 → mid = 4
Step 3: Search 4 → mid = 2
Step 4: Search 2 → mid = 1
Step 5: Search 1 → found or not found

16 → 8 → 4 → 2 → 1
   2⁴ = 16

log₂(16) = 4 steps ✓
```

### Trace: Bubble Sort Time Complexity

```
n = 5 elements

Outer loop: i = 0,1,2,3,4 (5 iterations)
  Inner loop: j runs n-i-1 times
    i=0: j = 0,1,2,3 (4)
    i=1: j = 0,1,2 (3)
    i=2: j = 0,1 (2)
    i=3: j = 0 (1)
    i=4: j = (0) - no inner loop

Total comparisons: 4 + 3 + 2 + 1 = 10 = n(n-1)/2 = O(n²)
```

### Trace: O(1) vs O(n)

```
arr = [1, 2, 3, 4, 5]

Access arr[0]: O(1) - always 1 operation
Find max: O(n) - check each element once

For n = 10,000:
  arr[0]: 1 operation
  find max: 10,000 operations
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

### Complexity Growth Chart

```
Operations
    │
    │     O(n²)
1000│   ╱
    │  ╱
    │ ╱  O(n log n)
 100│╱────────────────
    │
    │     O(n)
  10│   ╱
    │  ╱ O(log n)
    │ ╱
    │╱────────────── O(1)
    └──────────────────────────────►
    1    10     100    1000
         Input Size (n)
```

### Common Operations Time Complexity

```
┌──────────────────┬─────────────┬─────────────┐
│ Operation        │ Average     │ Worst       │
├──────────────────┼─────────────┼─────────────┤
│ Access by index  │ O(1)        │ O(1)        │
│ Search           │ O(n)        │ O(n)        │
│ Binary search    │ O(log n)    │ O(log n)    │
│ Insert at end    │ O(1)        │ O(n)        │
│ Insert at start  │ O(n)        │ O(n)        │
│ Delete at end    │ O(1)        │ O(1)        │
│ Delete at start  │ O(n)        │ O(n)        │
└──────────────────┴─────────────┴─────────────┘
```

### Sorting Algorithm Comparison

```
┌─────────────────┬─────────────┬─────────────┐
│ Algorithm        │ Time        │ Space       │
├──────────────────┼─────────────┼─────────────┤
│ Bubble Sort      │ O(n²)       │ O(1)        │
│ Selection Sort   │ O(n²)       │ O(1)        │
│ Insertion Sort   │ O(n²)       │ O(1)        │
│ Merge Sort       │ O(n log n)  │ O(n)        │
│ Quick Sort       │ O(n log n)  │ O(log n)    │
│ Timsort (Python) │ O(n log n)  │ O(n)        │
└──────────────────┴─────────────┴─────────────┘
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake 1: Counting Nested Loops

```python
# ❌ WRONG - Thinking O(n²)
for i in range(n):
    process(i)  # This is O(n), not nested!

# ❌ WRONG - Missing that inner loop depends on i
for i in range(n):
    for j in range(i):  # j only goes to i, not n
        ...

# For j range(i): total = 0+1+2+...+(n-1) = n(n-1)/2 = O(n²)

# ✅ CORRECT - Analyze actual iterations
# Nested loops where inner depends on outer:
# Sum of 1 to n = O(n²)
# Sum of 1 to n/2 for each outer = O(n²/2) = O(n²)
```

**Why it happens:** Forgetting that loop range matters.

**Prevention:** Think about total iterations, not just "how many loops".

---

### Common Mistake 2: Dropping Constants

```python
# ❌ WRONG - Thinking O(2n) is different from O(n)
for i in range(n):
    print(i)
for i in range(n):
    print(i)
# This is O(2n) = O(n)

# ❌ WRONG - Thinking O(n + log n) is O(n²)
# O(n + log n) = O(n) because log n is much smaller than n
```

**Why it happens:** Big O drops constants and lower-order terms.

**Prevention:** Remember: O(2n) = O(n), O(n + 1000) = O(n).

---

### Common Mistake 3: Confusing Time and Space

```python
# ❌ WRONG - Thinking space is same as time
def create_matrix(n):
    matrix = [[0 for _ in range(n)] for _ in range(n)]
    # Time: O(n²) - creating n² elements
    # Space: O(n²) - storing n² elements
    return matrix

# ✅ CORRECT - Analyze separately
# Time complexity: O(n²) - nested loops
# Space complexity: O(n²) - n×n matrix stored
```

**Why it happens:** Time and space are different dimensions.

**Prevention:** Always analyze time and space separately.

---

### Common Mistake 4: Not Considering Worst Case

```python
# Binary search worst case: O(log n)
# But best case is O(1) if target is at mid

# Quick sort worst case: O(n²) - already sorted!
# But average case: O(n log n)

# Always consider worst case for Big O
```

**Why it happens:** Forgetting to consider the worst input.

**Prevention:** Always analyze for the worst-case scenario.

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Complexity Ranking

```
Best ◄───────────────────────────────► Worst

O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2^n) < O(n!)
```

### Quick Reference

| Complexity | When 1K Elements | When 10K Elements |
|-----------|-----------------|-------------------|
| O(1) | 1 | 1 |
| O(log n) | ~10 | ~14 |
| O(n) | 1,000 | 10,000 |
| O(n log n) | ~10,000 | ~130,000 |
| O(n²) | 1,000,000 | 100,000,000 |
| O(2^n) | Too slow! | Extremely slow! |

### Common Patterns

| Pattern | Complexity | Example |
|---------|-----------|---------|
| Single loop | O(n) | for i in range(n) |
| Two nested loops | O(n²) | for i in range(n): for j in range(n) |
| Half each step | O(log n) | Binary search |
| Divide by 2 | O(log n) | Power of 2 |
| Creating set/dict | O(n) | set(arr) |
| Sort | O(n log n) | sorted(arr) |

### Decision Tree

```
What type of operation?
│
├─ Access by index? → O(1)
├─ Search unsorted? → O(n)
├─ Search sorted? → O(log n)
├─ Nested loops? → O(n²) or worse
└─ Divide in half? → O(log n)
```

### Mnemonic

**"L-log-N-squared-2-N-factorial"**
- **L**inear: O(n)
- **log**: O(log n)
- **N log N**: O(n log n)
- **S**quared: O(n²)
- **2 to the N**: O(2^n)
- **N factorial**: O(n!)

**"Find the dominant term"**
- Drop constants
- Drop lower-order terms
- Keep highest-growing term

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

### Question 1: Concept Check

**What is the time complexity of this code?**
```python
for i in range(n):
    for j in range(n):
        for k in range(n):
            print(i, j, k)
```

> **Answer:** O(n³)
>
> Three nested loops = n × n × n = n³

---

### Question 2: Prediction

**What is the time complexity?**
```python
while n > 1:
    n = n // 2
```

> **Answer:** O(log n)
>
> Each iteration halves n. How many times until n=1?
> For n=16: 16 → 8 → 4 → 2 → 1 = 4 steps = log₂(16)

---

### Question 3: Problem Solving

**What's the Big O of creating a set from n elements?**

> **Answer:** O(n)
>
> Must process each element once to add to set.
> No matter what the elements are, you touch each one exactly once.

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

### Problem: Analyze Algorithm Complexity

**Task:** Determine the Big O of these functions:

```python
# Function A
def function_a(arr):
    return arr[0]  # ???

# Function B  
def function_b(arr, target):
    for x in arr:
        if x == target:
            return True
    return False

# Function C
def function_c(arr):
    for i in range(len(arr)):
        for j in range(len(arr)):
            if arr[i] == arr[j]:
                return True
    return False
```

**Answers:**
```python
# Function A: O(1) - direct access by index

# Function B: O(n) - in worst case, check all elements

# Function C: O(n²) - nested loops, compare all pairs

# But wait, function C returns early, so let's analyze:
# Best case: O(1) if first pair matches
# Worst case: O(n²) if no matches
# Average: O(n²) - but for analysis, we say worst case
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

### Challenge: Compare Sorting Algorithms

**Task:** Analyze time and space for different sorting approaches

```python
def bubble_sort(arr):
    """Time: O(n²), Space: O(1)"""
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr


def selection_sort(arr):
    """Time: O(n²), Space: O(1)
    Slightly faster than bubble (fewer swaps)
    """
    n = len(arr)
    for i in range(n):
        min_idx = i
        for j in range(i+1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr


def insertion_sort(arr):
    """Time: O(n²), Space: O(1)
    Fast for nearly sorted arrays (best O(n))
    """
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr


def merge_sort(arr):
    """Time: O(n log n), Space: O(n)"""
    if len(arr) <= 1:
        return arr
    
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    
    return merge(left, right)


def quick_sort(arr):
    """Time: O(n log n) avg, O(n²) worst, Space: O(log n)"""
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    mid = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quick_sort(left) + mid + quick_sort(right)
```

### Summary Table

| Algorithm | Best | Average | Worst | Space |
|-----------|------|---------|-------|-------|
| Bubble Sort | O(n) | O(n²) | O(n²) | O(1) |
| Selection Sort | O(n²) | O(n²) | O(n²) | O(1) |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) |
| Python sorted() | O(n log n) | O(n log n) | O(n log n) | O(n) |

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

### What You Learned Today

1. **Time Complexity:** How runtime grows with input size
2. **Space Complexity:** How much memory algorithm uses
3. **Common Complexities:** O(1), O(log n), O(n), O(n²), etc.
4. **Analysis:** How to count operations and determine Big O
5. **Optimization:** When to use which algorithm

### Key Takeaways

- Big O describes growth rate, not exact speed
- Drop constants and lower-order terms
- Always consider worst-case complexity
- O(n log n) is much better than O(n²) for large n

### Common Complexity Summary

| Complexity | Example Situation |
|-----------|-------------------|
| O(1) | Access array element |
| O(log n) | Binary search |
| O(n) | Single loop |
| O(n log n) | Efficient sorting |
| O(n²) | Nested loops |
| O(2^n) | Recursive without memoization |
| O(n!) | Generate all permutations |

### Weak Points to Watch

- Forgetting loop range matters
- Confusing time and space complexity
- Not considering worst case

### Next Lesson Preview

**Lesson 50:** Recursion — Functions that call themselves

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 49 / 2000 |
| **Chapter** | 5 (Algorithm Patterns) |
| **XP** | 490 |
| **Rank** | Builder |
| **Mastery** | Complexity Analysis |
| **Weaknesses** | Counting iterations correctly |
| **Recommended Focus** | Practice analyzing code |
| **Suggested Review** | Lesson 48 (Common Patterns) |
| **Next Lesson Readiness** | ✓ Ready for Recursion |

---

**Type 50 to continue**