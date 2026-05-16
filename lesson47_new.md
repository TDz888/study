# Lesson 47 — Bit Manipulation

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 46 - Math Problems.

**Current Lesson:** Learning **Bit Manipulation** — direct operations on binary bits.

**Why This Matters:**
- Bit operations are fundamental to how computers work
- Enables efficient algorithms (O(1) operations)
- Essential for low-level programming and optimization
- Many LeetCode problems use bit manipulation tricks

**Connection:**
```
Math → Binary → Bit Operations
  ↓       ↓           ↓
Numbers  0/1         AND/OR
       representation XOR/NOT
```

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll master today:**
- Binary number system basics
- Bitwise operators: AND, OR, XOR, NOT
- Left and right shift operations
- Common bit manipulation tricks
- Practical applications

**Real-world analogy:**
- Binary is like a light switch board: each switch is either ON (1) or OFF (0)
- Bit operations combine multiple switches at once
- Useful for flags, permissions, encoding

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### Binary Number System

```
Decimal:     0    1    2    3    4    5    6    7    8
Binary:      0    1   10   11  100  101  110  111 1000

Each position represents a power of 2:
  5 in binary = 101
  = 1×2² + 0×2¹ + 1×2⁰
  = 4 + 0 + 1 = 5
```

### Bitwise vs Boolean

```python
# Boolean: treats entire number as True/False
5 and 3    # Returns 3 (last truthy value)
0 and 5    # Returns 0

# Bitwise: operates on each bit individually
5 & 3     # Returns 1 (bit-by-bit AND)
5 | 3     # Returns 7 (bit-by-bit OR)
```

### Why Bit Manipulation?

- **Speed:** O(1) operation (hardware-level)
- **Memory:** Store multiple flags in single integer
- **Tricks:** Many problems have clever bit solutions

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Meaning |
|------|----------------|
| **Bit** | Binary digit (0 or 1) |
| **Byte** | 8 bits |
| **Binary** | Base-2 number system |
| **AND (&)** | Both bits 1 → result 1 |
| **OR (|)** | Either bit 1 → result 1 |
| **XOR (^)** | Bits different → result 1 |
| **NOT (~)** | Flip all bits |
| **Left Shift (<<)** | Multiply by 2^n |
| **Right Shift (>>)** | Divide by 2^n |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

### 1. Basic Bitwise Operators

```python
# AND - Both bits must be 1 to result in 1
print(5 & 3)   # 1
#   5 = 101
#   3 = 011
#   ─────────
#   1 = 001

# OR - Either bit is 1 results in 1
print(5 | 3)   # 7
#   5 = 101
#   3 = 011
#   ─────────
#   7 = 111

# XOR - Bits different results in 1
print(5 ^ 3)   # 6
#   5 = 101
#   3 = 011
#   ─────────
#   6 = 110

# NOT - Flip all bits (returns negative due to 2's complement)
print(~5)      # -6
```

### 2. Shift Operations

```python
# Left Shift - Multiply by 2^n
print(5 << 1)  # 10 (5 × 2 = 10)
print(5 << 2)  # 20 (5 × 4 = 20)
#   5 = 101
#   5 << 1 = 1010 = 10
#   5 << 2 = 10100 = 20

# Right Shift - Divide by 2^n (floor)
print(10 >> 1)  # 5 (10 ÷ 2 = 5)
print(10 >> 2)  # 2 (10 ÷ 4 = 2.5 → 2)
#   10 = 1010
#   10 >> 1 = 0101 = 5
#   10 >> 2 = 0010 = 2
```

### 3. Check Specific Bit

```python
def check_bit(n, i):
    """
    Check if the i-th bit is set (1) in number n.
    i=0 is the rightmost (least significant) bit.
    """
    return (n >> i) & 1


# Test
print(check_bit(5, 0))  # 1 (5 = 101, bit 0 = 1)
print(check_bit(5, 1))  # 0 (5 = 101, bit 1 = 0)
print(check_bit(5, 2))  # 1 (5 = 101, bit 2 = 1)


# Visual:
# n = 5 = 101
#       ↑  ↑  ↑
#       2  1  0  ← bit positions

# check_bit(5, 1):
# 5 >> 1 = 2 (010 in binary)
# 2 & 1 = 0
# Result: 0 (bit is not set)
```

### 4. Set a Bit (Make it 1)

```python
def set_bit(n, i):
    """
    Set the i-th bit to 1 in number n.
    """
    return n | (1 << i)


# Test
print(set_bit(4, 1))  # 6
#   4 = 100
#   1 << 1 = 010
#   100 | 010 = 110 = 6

print(set_bit(0, 3))  # 8
#   0 = 000
#   1 << 3 = 1000
#   000 | 1000 = 1000 = 8
```

### 5. Clear a Bit (Make it 0)

```python
def clear_bit(n, i):
    """
    Clear (set to 0) the i-th bit in number n.
    """
    return n & ~(1 << i)


# Test
print(clear_bit(6, 1))  # 4
#   6 = 110
#   1 << 1 = 010
#   ~010 = ...111101 (inverted)
#   110 & ...111101 = 100 = 4

print(clear_bit(7, 2))  # 3
#   7 = 111
#   clear bit 2 → 011 = 3
```

### 6. Toggle a Bit (Flip)

```python
def toggle_bit(n, i):
    """
    Toggle (flip) the i-th bit in number n.
    """
    return n ^ (1 << i)


# Test
print(toggle_bit(5, 0))  # 4 (5=101 → 100=4)
print(toggle_bit(4, 0))  # 5 (4=100 → 101=5)
```

### 7. Binary Conversions

```python
# Decimal to Binary string
print(bin(5))         # '0b101'
print(bin(255))       # '0b11111111'

# Binary string to Decimal
print(int("101", 2))  # 5

# Format with leading zeros
print(format(5, '08b'))  # '00000101' (8-bit representation)

# Format for different bit widths
print(format(5, '04b'))  # '0101'
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

### Trace: 5 & 3

```
Step 1: Convert to binary
  5 = 101 (3 bits)
  3 = 011 (3 bits)

Step 2: Align and AND each column
    101
  & 011
  ─────
    001

Step 3: Convert result to decimal
  001 = 1

Result: 5 & 3 = 1 ✓
```

### Trace: check_bit(13, 2)

```
Input: n = 13, i = 2

13 in binary: 1101

Step 1: Shift right by i positions
  13 >> 2 = 3
  1101 >> 2 = 11 (in decimal) = 011 (in binary)

Step 2: AND with 1
  011 & 001 = 001 = 1

Result: bit 2 of 13 is 1 ✓

Verification: 13 = 8 + 4 + 1 = 2³ + 2² + 2⁰
              bit 2 (2² position) = 1 ✓
```

### Trace: set_bit(9, 3)

```
Input: n = 9, i = 3

9 in binary: 1001

Step 1: Create mask (1 shifted left by i)
  1 << 3 = 1000

Step 2: OR with n
  1001
| 1000
───────
  1001 → wait, let me redo

  1001
| 1000
───────
  1001? No...

  1001 (9)
| 1000 (8)
───────
  1001 (9)? That's not right either...

Let me think again:
  1 << 3 = 8 = 1000
  9 = 1001
  
  1001
| 1000
───────
  1001? That can't be...

Actually:
  9 = 1001
  8 = 1000
  OR:
    1 0 0 1
  | 1 0 0 0
    ───────
    1 0 0 1 = 9? No, I think I'm confusing myself.

Let's do it properly:
  1001 (9)
| 1000 (8)
───────
  1001 = 9??

Wait, 1001 | 1000:
  bit 0: 1 | 0 = 1
  bit 1: 0 | 0 = 0
  bit 2: 0 | 0 = 0
  bit 3: 1 | 1 = 1
  
  Result: 1001 = 9?

Hmm, let me recalculate. Setting bit 3 of 9:
  9 = 1001 in binary
  Bit 3 is the 4th from right (0-indexed)
  1 << 3 = 1000 in binary = 8
  
  9 | 8 = 1001 | 1000 = 1001? No!

1001 OR 1000:
  Position 3: 1 OR 1 = 1
  Position 2: 0 OR 0 = 0
  Position 1: 0 OR 0 = 0
  Position 0: 1 OR 0 = 1
  Result: 1001 = 9? That's the same?

Oh I see, bit 3 of 9 is already 1! (9 = 8 + 1 = 1000 + 0001)
So setting it doesn't change anything.

Let me do: set_bit(1, 3)
  1 = 0001
  1 << 3 = 1000
  0001 | 1000 = 1001 = 9 ✓

OK, set_bit(4, 1):
  4 = 0100
  1 << 1 = 0010
  0100 | 0010 = 0110 = 6 ✓
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

### AND Operation

```
Bits 1 & 0 = 1
Bits 0 & 1 = 0
Bits 1 & 1 = 1
Bits 0 & 0 = 0

Example: 5 & 3

    5 = 1 0 1
    3 = 0 1 1
    ──────────
    1 = 0 0 1
```

### OR Operation

```
Bits 1 | 0 = 1
Bits 0 | 1 = 1
Bits 1 | 1 = 1
Bits 0 | 0 = 0

Example: 5 | 3

    5 = 1 0 1
    3 = 0 1 1
    ──────────
    7 = 1 1 1
```

### XOR Operation

```
Bits 1 ^ 0 = 1
Bits 0 ^ 1 = 1
Bits 1 ^ 1 = 0
Bits 0 ^ 0 = 0

Example: 5 ^ 3

    5 = 1 0 1
    3 = 0 1 1
    ──────────
    6 = 1 1 0
```

### Shift Operations

```
Left Shift (<< n): Multiply by 2^n

    5 << 1:
    101 → 1010
    5 → 10

    5 << 2:
    101 → 10100
    5 → 20

Right Shift (>> n): Divide by 2^n (floor)

    10 >> 1:
    1010 → 0101
    10 → 5

    10 >> 2:
    1010 → 0010
    10 → 2
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake 1: Confusing & and and

```python
# ❌ WRONG - Boolean, not bitwise
print(5 and 3)   # 3 (returns last truthy value)
print(0 and 5)   # 0 (returns first falsy value)

# ✅ CORRECT - Bitwise AND
print(5 & 3)    # 1 (101 & 011 = 001)
```

**Why it happens:** Python's `and` is boolean, `&` is bitwise.

**Prevention:** Use `&` for bit operations, `and` for boolean logic.

---

### Common Mistake 2: Using | instead of OR in conditions

```python
# ❌ WRONG - This is OR for boolean, not bitwise
if x == 1 | 2:  # Means: if x == (1 | 2) = if x == 3
    ...

# ✅ CORRECT - Use parentheses
if x == 1 or x == 2:
    ...

# Or for bit flags:
if x & (FLAG_A | FLAG_B):
    ...
```

**Why it happens:** `|` has lower precedence than `==`.

**Prevention:** Use `or` for conditions, `|` only for bit operations with clear precedence.

---

### Common Mistake 3: Misunderstanding NOT

```python
# ❌ WRONG - Thinking ~5 = -5
print(~5)   # -6 (not -5)

# Why? Two's complement representation
# ~5 = -6 because -6 + 5 = 0 (in two's complement)
```

**Why it happens:** Negative numbers use two's complement in computers.

**Prevention:** Remember: `~n = -(n+1)`

---

### Common Mistake 4: Shifting too far

```python
# For 32-bit integers, shifting by 32+ can cause issues
# In Python it's fine (arbitrary precision), but be careful
# in other languages!

# ❌ RISKY in some languages
x = 1 << 100  # Fine in Python, but overkill
```

**Why it happens:** Fixed-width integers have limits.

**Prevention:** In Python it's safe, but be careful in C/Java.

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Quick Reference

| Operator | Symbol | Operation | Example |
|----------|--------|-----------|---------|
| AND | `&` | Both 1 → 1 | `5 & 3 = 1` |
| OR | `\|` | Either 1 → 1 | `5 \| 3 = 7` |
| XOR | `^` | Different → 1 | `5 ^ 3 = 6` |
| NOT | `~` | Flip bits | `~5 = -6` |
| Left Shift | `<<` | Multiply by 2^n | `5 << 1 = 10` |
| Right Shift | `>>` | Divide by 2^n | `10 >> 1 = 5` |

### Common Patterns

| Task | Code |
|------|------|
| Check bit | `(n >> i) & 1` |
| Set bit | `n \| (1 << i)` |
| Clear bit | `n & ~(1 << i)` |
| Toggle bit | `n ^ (1 << i)` |
| Check power of 2 | `n & (n-1) == 0` |
| Count bits | `n &= (n-1)` loop |

### Decision Tree

```
Bit operation?
│
├─ Check bit? → (n >> i) & 1
├─ Set bit? → n | (1 << i)
├─ Clear bit? → n & ~(1 << i)
├─ Toggle bit? → n ^ (1 << i)
└─ Count set bits? → n &= (n-1) loop
```

### Mnemonic

**"OR adds, XOR flips"**
- OR: Turn on bits
- XOR: Toggle bits
- AND: Isolate bits (check if set)

**"Right shift = cut off from right"**

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

### Question 1: Concept Check

**What is 5 ^ 5 equal to? Why?**

> **Answer:** 0
>
> XOR of a number with itself = 0
> Because every bit matches (1^1=0, 0^0=0)

---

### Question 2: Prediction

**What does this code output?**
```python
print(8 >> 2)
```

> **Answer:** 2
>
> 8 in binary: 1000
> 8 >> 2 = 0010 = 2
> (Dividing by 2² = 4, 8/4 = 2)

---

### Question 3: Problem Solving

**How would you check if the least significant bit of a number is set?**

> **Answer:** Use `(n & 1)`
>
> ```python
> if n & 1:
>     print("LSB is 1 (odd number)")
> else:
>     print("LSB is 0 (even number)")
> ```
>
> This works because checking bit 0 is just AND with 1.

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

### Problem: Count Number of 1 Bits

**Problem Statement:**
Write a function that takes an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).

**Example:**
```
Input: n = 11 (binary: 1011)
Output: 3

Input: n = 128 (binary: 10000000)
Output: 1
```

**Solution:**
```python
def count_bits(n):
    """
    Count number of 1 bits using Brian Kernighan's algorithm.
    
    Time: O(k) where k is number of set bits
    """
    count = 0
    while n:
        n &= (n - 1)  # Remove lowest set bit
        count += 1
    return count


# Alternative: Built-in
def count_bits_pythonic(n):
    """Using Python's bin() method."""
    return bin(n).count('1')


# Alternative: Manual loop
def count_bits_manual(n):
    """Check each bit."""
    count = 0
    while n:
        count += n & 1
        n >>= 1
    return count


# Test
print(count_bits(11))   # 3 (1011 has 3 ones)
print(count_bits(128)) # 1 (10000000 has 1 one)


# Trace for n = 11 (1011):
# Step 1: n=11 (1011), n-1=10 (1010), n&=10 = 1010 (1010), count=1
# Step 2: n=10 (1010), n-1=9 (1001), n&=9 = 1000 (1000), count=2
# Step 3: n=8 (1000), n-1=7 (0111), n&=7 = 0 (0000), count=3
# Result: 3 ✓
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

### Challenge: Hamming Distance

**Problem:**
The Hamming distance between two integers is the number of positions at which the corresponding bits are different.

**Example:**
```
Input: x = 1, y = 4
Output: 2
Explanation:
  1 = 0b0001
  4 = 0b0100
  Bits differ at positions 2 and 3 → distance = 2
```

**Solution:**
```python
def hamming_distance(x, y):
    """
    Find Hamming distance (positions where bits differ).
    Uses XOR: different bits become 1.
    
    Time: O(k) where k is number of set bits in XOR
    """
    xor = x ^ y
    count = 0
    
    while xor:
        xor &= (xor - 1)  # Remove lowest set bit
        count += 1
    
    return count


# Alternative using built-in
def hamming_distance_pythonic(x, y):
    return bin(x ^ y).count('1')


# Alternative using n & (n-1) trick
def hamming_distance_v2(x, y):
    return bin(x ^ y).count('1')


# Test
print(hamming_distance(1, 4))  # 2
print(hamming_distance(3, 1))  # 1 (11 ^ 01 = 10)


# Trace for x=1, y=4:
# xor = 1 ^ 4 = 5 (0101 in binary)
# 
# Step 1: xor=5 (0101), xor-1=4 (0100), xor&=4=4 (0100), count=1
# Step 2: xor=4 (0100), xor-1=3 (0011), xor&=3=0 (0000), count=2
# Result: 2 ✓
```

**Why XOR works:**
```
x = 1 = 0001
y = 4 = 0100
x ^ y = 0101 (bits that differ become 1)
Count the 1s in 0101 = 2
```

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

### What You Learned Today

1. **Bitwise Operators:** &, |, ^, ~ (bit manipulation)
2. **Shift Operations:** << (multiply), >> (divide)
3. **Common Tricks:** Check, set, clear, toggle bits
4. **Counting Bits:** Brian Kernighan's algorithm
5. **Binary Conversions:** bin(), format()

### Key Takeaways

- Bit operations work on individual bits
- XOR is useful for toggling and finding differences
- `n & (n-1)` removes the lowest set bit
- Shift left = multiply by 2^n, shift right = divide by 2^n

### Common Patterns

| Pattern | Code | Use Case |
|---------|------|----------|
| Check bit i | `(n >> i) & 1` | Is bit set? |
| Set bit i | `n \| (1 << i)` | Turn on |
| Clear bit i | `n & ~(1 << i)` | Turn off |
| Count ones | `while n: n &= n-1` | Popcount |
| XOR swap | `a ^= b; b ^= a; a ^= b` | Swap without temp |

### Weak Points to Watch

- Confusing & with and (boolean)
- Forgetting ~ returns -(n+1)
- Not handling edge cases

### Next Lesson Preview

**Lesson 48:** Graph Algorithms — Traversal and pathfinding

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 47 / 2000 |
| **Chapter** | 5 (Algorithm Patterns) |
| **XP** | 470 |
| **Rank** | Builder |
| **Mastery** | Bit Manipulation |
| **Weaknesses** | Remembering operator behavior |
| **Recommended Focus** | Practice n & (n-1) trick |
| **Suggested Review** | Lesson 46 (Math - binary representation) |
| **Next Lesson Readiness** | ✓ Ready for Graphs |

---

**Type 48 to continue**