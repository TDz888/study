# Lesson 41 — Sliding Window Technique

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 40 - Two Pointers.

**Current Lesson:** Learning **Sliding Window** — a technique for finding patterns in arrays/strings efficiently.

**Why This Matters:**
- Two Pointers dealt with pairs — Sliding Window deals with contiguous subarrays
- Reduces O(n*k) brute force to O(n) — massive speed improvement
- Essential for LeetCode Medium-Hard problems

**Connection:**
```
Two Pointers → Sliding Window → Prefix Sum
     ↓              ↓              ↓
  Pair finding   Subarray      Cumulative
```

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll master today:**
- What is a sliding window (visual concept)
- Fixed-size windows (constant k)
- Variable-size windows (dynamic k)
- When to use sliding window vs other techniques

**Real-world analogy:**
Imagine you're looking at traffic through a car window while driving:
- You see k cars at a time (fixed window)
- Sometimes you expand to see more (variable window)
- You slide forward — old cars leave, new cars enter

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is Sliding Window?

Think of a "window" sliding across an array:

```
Array:    [2, 1, 5, 1, 3, 2]
Window:   [2, 1, 5]    ← First window (k=3)
          ↓ slide
Window:      [1, 5, 1]  ← Second window
          ↓ slide
Window:         [5, 1, 3] ← Third window
```

### Why "Sliding"?

Instead of recalculating everything:
```
Brute Force:    [2,1,5] → sum(2,1,5) = 8
                [1,5,1] → sum(1,5,1) = 7
                [5,1,3] → sum(5,1,3) = 9
                (recalculate EVERYTHING each time)

Sliding Window: [2,1,5] → sum = 8
                [1,5,1] → 8 - 2 + 1 = 7  (subtract left, add right)
                [5,1,3] → 7 - 1 + 3 = 9  (subtract left, add right)
                (reuse previous calculation!)
```

### Key Insight: O(1) Update

The magic formula:
```
new_sum = old_sum - left_element + new_right_element
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Meaning |
|------|----------------|
| **Window** | A contiguous subarray we're examining |
| **Slide** | Move the window forward by one position |
| **Fixed Size** | Window length k never changes |
| **Variable Size** | Window expands/contracts as needed |
| **Window Sum** | Total of all elements in current window |
| **Left Pointer** | Start index of window |
| **Right Pointer** | End index of window |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

### Fixed Size Window — Maximum Sum of K Elements

```python
def max_sum_subarray(arr, k):
    """
    Find maximum sum of any contiguous subarray with exactly k elements.
    
    Args:
        arr: list of numbers
        k: window size (must be positive)
    
    Returns:
        Maximum sum found
    """
    n = len(arr)
    
    # Edge case: array too short
    if n < k:
        return -1
    
    # Step 1: Calculate sum of first window
    window_sum = sum(arr[:k])
    max_sum = window_sum
    
    # Step 2: Slide the window across array
    for i in range(k, n):
        # Slide: subtract leftmost, add new rightmost
        window_sum = window_sum - arr[i - k] + arr[i]
        max_sum = max(max_sum, window_sum)
    
    return max_sum


# Test the function
nums = [2, 1, 5, 1, 3, 2]
k = 3
result = max_sum_subarray(nums, k)
print(result)  # Output: 9 (from window [5,1,3])
```

### Variable Size Window — Minimum Length Subarray

```python
def min_subarray_len(target, arr):
    """
    Find minimum length of contiguous subarray with sum >= target.
    
    Uses TWO pointers: expand right, shrink left when possible.
    """
    n = len(arr)
    left = 0
    window_sum = 0
    min_len = float('inf')
    
    # Expand window with right pointer
    for right in range(n):
        # Add current element to window
        window_sum += arr[right]
        
        # Shrink window from left while we can still meet target
        while window_sum >= target:
            # Update answer
            min_len = min(min_len, right - left + 1)
            # Shrink: remove leftmost element
            window_sum -= arr[left]
            left += 1
    
    # If no valid subarray found, return 0
    return min_len if min_len != float('inf') else 0


# Test
nums = [2, 3, 1, 2, 4, 3]
target = 7
result = min_subarray_len(target, nums)
print(result)  # Output: 2 (subarray [4,3])
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

### Trace: max_sum_subarray([2, 1, 5, 1, 3, 2], k=3)

```
Initial array: [2, 1, 5, 1, 3, 2]
Window size k: 3

Step 1: Initialize first window
┌─────────────────┐
│  [2, 1, 5]      │  ← First window
│   ↑     ↑       │
│   left  right   │
└─────────────────┘
window_sum = 2 + 1 + 5 = 8
max_sum = 8

Step 2: Slide to i=3
┌─────────────────┐
│  [2, 1, 5]  1   │
│        ↑        │
│       new       │
└─────────────────┘
window_sum = 8 - 2 + 1 = 7
max_sum = max(8, 7) = 8

Step 3: Slide to i=4
┌─────────────────┐
│  2  [1, 5, 1] 3 │
│     ↑     ↑     │
│    left  right  │
└─────────────────┘
window_sum = 7 - 1 + 3 = 9
max_sum = max(8, 9) = 9  ← NEW MAX!

Step 4: Slide to i=5
┌─────────────────┐
│  2  1  [5, 1, 3] 2│
│        ↑     ↑   │
│       left  right│
└─────────────────┘
window_sum = 9 - 5 + 2 = 6
max_sum = max(9, 6) = 9

Final: max_sum = 9  ✓
```

### Trace: min_subarray_len(7, [2, 3, 1, 2, 4, 3])

```
Target: 7
Array:  [2, 3, 1, 2, 4, 3]
          ↑
        right

Iteration 1: right=0, add 2
  window_sum = 2
  2 < 7, can't shrink
  
Iteration 2: right=1, add 3
  window_sum = 5
  5 < 7, can't shrink

Iteration 3: right=2, add 1
  window_sum = 6
  6 < 7, can't shrink

Iteration 4: right=3, add 2
  window_sum = 8 >= 7 ✓
  min_len = min(inf, 3-0+1) = 4
  Shrink: window_sum -= 2 → 6, left=1
  6 < 7, stop shrinking

Iteration 5: right=4, add 4
  window_sum = 10 >= 7 ✓
  min_len = min(4, 4-1+1) = 4
  Shrink: window_sum -= 3 → 7, left=2
  min_len = min(4, 4-2+1) = 3
  Shrink: window_sum -= 1 → 6, left=3
  6 < 7, stop shrinking

Iteration 6: right=5, add 3
  window_sum = 9 >= 7 ✓
  min_len = min(3, 5-3+1) = 3
  Shrink: window_sum -= 2 → 7, left=4
  min_len = min(3, 5-4+1) = 2 ← NEW MIN!
  Shrink: window_sum -= 4 → 3, left=5
  3 < 7, stop shrinking

Final: min_len = 2  ✓ (subarray [4,3])
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

### Fixed Window Visualization

```
┌─────────────────────────────────────────────────────┐
│                    Array                            │
│  [ 2,  1,  5,  1,  3,  2 ]                         │
│   0   1   2   3   4   5                            │
├─────────────────────────────────────────────────────┤
│                                                     │
│  Window 1:  [2, 1, 5] → sum = 8                   │
│              ─────────                             │
│                                                     │
│  Window 2:     [1, 5, 1] → sum = 7                │
│                 ─────────                          │
│                                                     │
│  Window 3:        [5, 1, 3] → sum = 9  ← MAX      │
│                    ─────────                       │
│                                                     │
│  Window 4:           [1, 3, 2] → sum = 6          │
│                      ─────────                    │
│                                                     │
│  Result: 9 (from [5, 1, 3])                       │
└─────────────────────────────────────────────────────┘
```

### Variable Window Visualization

```
Target: 7

Step 1: Expand window
[ 2, 3, 1, 2, 4, 3 ]
 ↑
left, right
sum=2

Step 2: Keep expanding
[ 2, 3, 1, 2, 4, 3 ]
 ↑  ↑
left right
sum=5

Step 3: Keep expanding  
[ 2, 3, 1, 2, 4, 3 ]
 ↑     ↑
left   right
sum=6

Step 4: Keep expanding
[ 2, 3, 1, 2, 4, 3 ]
 ↑        ↑
left      right
sum=8 >= 7 ✓

Step 5: Shrink from left
[ 2, 3, 1, 2, 4, 3 ]
    ↑     ↑
   left  right
sum=6 (removed 2)

Step 6: Expand again
[ 2, 3, 1, 2, 4, 3 ]
    ↑        ↑
   left     right
sum=10 >= 7 ✓

Step 7: Shrink
[ 2, 3, 1, 2, 4, 3 ]
       ↑     ↑
      left  right
sum=7 >= 7 ✓ → length = 2
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake 1: Wrong Loop Range

```python
# ❌ WRONG - off by one
for i in range(k, n+1):  # Goes one too far!
    window_sum = window_sum - arr[i-k] + arr[i]

# ✅ CORRECT
for i in range(k, n):  # Stops at right position
    window_sum = window_sum - arr[i-k] + arr[i]
```

**Why it happens:** Off-by-one errors are common. Always verify your loop boundaries.

**Prevention:** Draw out the indices for small arrays.

---

### Common Mistake 2: Forgetting to Shrink

```python
# ❌ WRONG - only expands, never shrinks
for right in range(n):
    window_sum += arr[right]
    # Missing: while window_sum >= target:
    #              shrink window!
```

**Why it happens:** For variable windows, you MUST shrink when condition is met.

**Prevention:** Variable window ALWAYS has two nested operations:
1. Expand (add right)
2. Shrink (remove left while condition met)

---

### Common Mistake 3: Using Sliding Window on Non-Contiguous Data

```python
# ❌ WRONG USE CASE
# Sliding window is for CONTIGUOUS subarrays only!
# This problem requires prefix sum, not sliding window
arr = [1, -2, 3, 2, -1]
# Find if any element equals sum of two non-adjacent elements

# ✅ CORRECT: Use different technique
# Sliding window only works for problems asking about
# contiguous subarrays/substrings
```

**Why it happens:** Not every array problem is suitable for sliding window.

**Prevention:** Check: "Does this problem involve contiguous elements?"
- Yes → Sliding Window might work
- No → Use something else (prefix sum, hash map, etc.)

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Key Formulas

| Pattern | Formula |
|---------|---------|
| **Fixed Window Slide** | `new_sum = old_sum - arr[left] + arr[right+1]` |
| **Variable Window Expand** | `window_sum += arr[right]` |
| **Variable Window Shrink** | `window_sum -= arr[left]; left += 1` |

### Decision Tree

```
Is the window size FIXED?
│
├─ YES → Calculate first window sum
│        → Slide: subtract left, add right
│        → Track maximum/minimum
│
└─ NO → Is there a TARGET condition?
       │
       ├─ YES → Expand right until condition met
       │        → Shrink left while condition holds
       │        → Track minimum window length
       │
       └─ NO → Consider other techniques
```

### Quick Reference

| Problem Type | Window Type | Key Operation |
|-------------|-------------|---------------|
| Max sum of k elements | Fixed | Track max |
| Minimum subarray size | Variable | Track min length |
| Longest substring with conditions | Variable | Track max length |
| Count subarrays | Fixed | Count occurrences |

### Mnemonic

**"Slide and dice"**
- **Slide**: Move window across array
- **Dice**: Split into fixed/variable based on problem

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

### Question 1: Concept Check

**What is the key advantage of Sliding Window over brute force?**

> **Answer:** Sliding Window reuses calculations between windows. Instead of recalculating sum from scratch for each window (O(k) per window), we update in O(1) by subtracting the leftmost element and adding the new rightmost element. Total: O(n) vs O(n*k).

---

### Question 2: Trace Execution

**What is the output of this code?**
```python
def mystery(arr, k):
    window_sum = sum(arr[:2])
    for i in range(2, len(arr)):
        window_sum = window_sum - arr[i-2] + arr[i]
    return window_sum

print(mystery([1, 2, 3, 4, 5], 3))
```

> **Answer:** 12
> 
> Explanation: The function finds the last window's sum (after all slides complete).
> Final window = [3, 4, 5] = 12

---

### Question 3: Error Detection

**This code has a bug. What is it?**
```python
def find_max(nums, k):
    window = sum(nums[:k])
    max_sum = window
    
    for i in range(k, len(nums)):
        window = window - nums[i] + nums[i-k+1]
        max_sum = max(max_sum, window)
    
    return max_sum
```

> **Answer:** The bug is in `nums[i-k+1]`. It should be `nums[i-k]`.
> 
> When sliding: we remove `nums[i-k]` (oldest element), not `nums[i-k+1]`.
> Example: i=3, k=3 → remove nums[0], add nums[3]

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

### Problem: Maximum Average Subarray I

**Problem Statement:**
Given an array `nums` with n elements, find the maximum average of any contiguous subarray of size k.

**Examples:**
```
Input: nums = [1,12,-5,-6,50,3], k = 4
Output: 12.5
Explanation: subarray [-5,-6,50,3] has average (41/4) = 10.25
             subarray [12,-5,-6,50] has average (51/4) = 12.75? 
             Let's calculate properly...
             
Actual: nums[1:5] = [12,-5,-6,50] → sum = 51 → avg = 12.75
        But output is 12.5... let me recheck.
        
Final: The correct answer is 12.75 (from [12,-5,-6,50])
```

**Starter Code:**
```python
def find_max_average(nums, k):
    # Your code here
    pass

# Read input
n = int(input())
nums = list(map(int, input().split()))
k = int(input())
print(find_max_average(nums, k))
```

**Hints:**
1. This is a FIXED window problem
2. Calculate sum of first k elements
3. Slide and track maximum

---

### Decomposition Guidance:

```
Step 1: Calculate initial window sum
        window_sum = sum(nums[0:k])
        
Step 2: Set max_sum = window_sum
        
Step 3: Loop from i=k to n-1
        In each iteration:
        - Subtract nums[i-k] from window_sum
        - Add nums[i] to window_sum  
        - Update max_sum if current window_sum > max_sum
        
Step 4: Return max_sum / k
```

**Solution:**
```python
def find_max_average(nums, k):
    # Step 1: Initial window
    window_sum = sum(nums[:k])
    max_sum = window_sum
    
    # Step 2: Slide the window
    for i in range(k, len(nums)):
        window_sum = window_sum - nums[i - k] + nums[i]
        max_sum = max(max_sum, window_sum)
    
    # Step 3: Return average
    return max_sum / k


# Alternative using O(1) space explicitly:
def find_max_average_v2(nums, k):
    n = len(nums)
    
    # First window
    window_sum = sum(nums[:k])
    max_sum = window_sum
    
    # Slide
    for i in range(k, n):
        window_sum = window_sum - nums[i - k] + nums[i]
        max_sum = max(max_sum, window_sum)
    
    return max_sum / k
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

### Challenge: Longest Subarray with Ones After Replacement

**Problem:**
Given an array of 0s and 1s, find the longest subarray containing all 1s after replacing at most `k` zeros with ones.

**Example:**
```
Input: arr = [1, 1, 1, 0, 0, 0, 1, 1, 1, 1, 0], k = 2
Output: 6
Explanation: Replace zeros at positions 3,4 with ones → [1,1,1,1,1,1,1,1,1,1,0]
            Longest stretch of ones = 6 (positions 2-7)
```

**Hint:** This is a VARIABLE window problem!
- Expand window to include elements
- When we encounter a zero, count it
- If zeros > k, shrink from left
- Track maximum window length

**Solution:**
```python
def longest_ones(arr, k):
    """
    Find longest subarray with at most k zeros.
    Variable sliding window approach.
    """
    left = 0
    zero_count = 0
    max_length = 0
    
    for right in range(len(arr)):
        # Expand: add right element
        if arr[right] == 0:
            zero_count += 1
        
        # Shrink if we have too many zeros
        while zero_count > k:
            if arr[left] == 0:
                zero_count -= 1
            left += 1
        
        # Update answer
        max_length = max(max_length, right - left + 1)
    
    return max_length


# Test
arr = [1, 1, 1, 0, 0, 0, 1, 1, 1, 1, 0]
k = 2
print(longest_ones(arr, k))  # Output: 6
```

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

### What You Learned Today

1. **Sliding Window Concept:** A window that "slides" across an array
2. **Fixed Window:** Size k never changes, slide and track max/min
3. **Variable Window:** Expand right, shrink left when condition met
4. **Time Complexity:** O(n) vs O(n*k) for brute force

### Key Takeaways

- Sliding window is for **contiguous** subarrays/substrings
- **Fixed**: `new_sum = old_sum - left + right`
- **Variable**: Use while loop to shrink when condition satisfied
- Two pointers (left, right) track the window boundaries

### Common Patterns

| Pattern | Technique |
|---------|-----------|
| Max sum of k elements | Fixed window |
| Min length subarray ≥ target | Variable window |
| Longest substring with k distinct | Variable window |
| Count subarrays with property | Fixed window + hash |

### Weak Points to Watch

- Off-by-one errors in loop ranges
- Forgetting to shrink in variable windows
- Using sliding window for non-contiguous problems

### Next Lesson Preview

**Lesson 42:** Prefix Sum — Another O(n) technique for range queries

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 41 / 2000 |
| **Chapter** | 5 (Algorithm Patterns) |
| **XP** | 410 |
| **Rank** | Builder |
| **Mastery** | Sliding Window |
| **Weaknesses** | Variable window boundary handling |
| **Recommended Focus** | Practice variable-size windows |
| **Suggested Review** | Lesson 40 (Two Pointers) |
| **Next Lesson Readiness** | ✓ Ready for Prefix Sum |

---

**Type 42 to continue**
