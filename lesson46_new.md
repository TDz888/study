# Lesson 46 — Math Problems in Python

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 45 - Matrix.

**Current Lesson:** Learning **Math Problems** — fundamental mathematical operations in Python.

**Why This Matters:**
- Math operations are fundamental to programming
- Many algorithm problems have mathematical foundations
- Python has excellent built-in math support

**Connection:**
```
Variables → Arithmetic → Advanced Math
   ↓           ↓             ↓
  Store     Calculate     Prime/GCD
  values    operations    Factorial
```

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll master today:**
- Prime number checking (efficient method)
- GCD (Greatest Common Divisor)
- LCM (Least Common Multiple)
- Exponents and logarithms
- Factorials and combinations

**Real-world analogy:**
- **Prime:** A number that can't be evenly divided except by 1 and itself
- **GCD:** The largest "shared divisor" between two numbers
- **LCM:** The first "shared multiple" between two numbers

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is a Prime Number?

A prime number is divisible only by 1 and itself:
```
Prime numbers: 2, 3, 5, 7, 11, 13, 17, 19, 23, 29...
Not prime: 4 (divisible by 2), 6 (divisible by 2,3), 9 (divisible by 3)
```

**Why 1 is not prime:** 1 has only one divisor (itself), not two distinct divisors.

### Efficient Prime Checking

Instead of checking all numbers up to n:
```python
# ❌ SLOW: Check all numbers from 2 to n
for i in range(2, n):
    if n % i == 0:
        return False

# ✅ FAST: Only check up to √n
# If n = a × b, then one of a or b must be ≤ √n
for i in range(2, int(n**0.5) + 1):
```

### GCD vs LCM

```
GCD (Greatest Common Divisor):
  - Find the largest number that divides both
  - GCD(12, 18) = 6 (12: 1,2,3,4,6,12 and 18: 1,2,3,6,9,18 → max common = 6)

LCM (Least Common Multiple):
  - Find the smallest number that both divide into
  - LCM(12, 18) = 36 (12: 12,24,36 and 18: 18,36 → min common = 36)
```

**Key relationship:** `a × b = GCD(a,b) × LCM(a,b)`

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Meaning |
|------|----------------|
| **Prime** | Number divisible only by 1 and itself |
| **Composite** | Number with more than two divisors |
| **GCD** | Greatest Common Divisor — largest shared factor |
| **LCM** | Least Common Multiple — smallest shared multiple |
| **Factorial** | Product of all numbers from 1 to n (n!) |
| **Permutation** | Arrangements of n items taken r at a time |
| **Combination** | Ways to choose r items from n (order doesn't matter) |
| **Exponent** | Power: a raised to b (a^b) |
| **Logarithm** | Inverse of exponent: log base b of x |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

### 1. Prime Number Check

```python
def is_prime(n):
    """
    Check if n is a prime number.
    
    Time: O(√n)
    """
    # Handle edge cases
    if n < 2:
        return False
    if n == 2:
        return True
    if n % 2 == 0:  # Even numbers > 2 are not prime
        return False
    
    # Only check odd divisors up to √n
    for i in range(3, int(n**0.5) + 1, 2):
        if n % i == 0:
            return False
    
    return True


# Test
print(is_prime(7))   # True
print(is_prime(10))  # False
print(is_prime(2))   # True
print(is_prime(1))   # False
```

### 2. GCD (Greatest Common Divisor)

```python
import math

# Method 1: Using built-in
print(math.gcd(12, 18))  # 6

# Method 2: Manual Euclidean algorithm
def gcd(a, b):
    """
    Find GCD using Euclidean algorithm.
    Based on: GCD(a, b) = GCD(b, a % b)
    
    Time: O(log(min(a,b)))
    """
    while b:
        a, b = b, a % b
    return a

print(gcd(12, 18))  # 6


# Trace of gcd(12, 18):
# Step 1: a=12, b=18 → a=18, b=12 (swap because b > a? No wait...)

# Actually:
# Step 1: a=12, b=18 → 18 % 12 = 6 → a=18, b=6
# Step 2: a=18, b=6 → 18 % 6 = 0 → a=6, b=0
# Result: a=6 ✓
```

### 3. LCM (Least Common Multiple)

```python
import math

# Method 1: Using built-in (Python 3.9+)
print(math.lcm(12, 18))  # 36

# Method 2: Using GCD formula
def lcm(a, b):
    """
    Find LCM using formula: LCM(a,b) = a × b / GCD(a,b)
    """
    return abs(a * b) // math.gcd(a, b)

print(lcm(12, 18))  # 36


# Trace:
# GCD(12, 18) = 6
# LCM = |12 × 18| / 6 = 216 / 6 = 36 ✓
```

### 4. Powers and Logarithms

```python
import math

# Powers
print(2 ** 10)                    # 1024
print(pow(2, 10))                 # 1024 (same as **)
print(pow(2, 10, 1000))           # 24 (2^10 mod 1000)

# Logarithms
print(math.log(100, 10))          # 2.0 (log base 10 of 100)
print(math.log10(100))            # 2.0 (base 10 log)
print(math.log2(8))               # 3.0 (base 2 log)
print(math.sqrt(16))              # 4.0

# Natural log (base e)
print(math.log(100))              # ~4.605 (base e)
print(math.log(100, math.e))     # same as above
```

### 5. Factorial and Combinations

```python
import math

# Factorial: n! = 1 × 2 × 3 × ... × n
print(math.factorial(5))   # 120 (1×2×3×4×5)
print(math.factorial(0))   # 1 (by definition)

# Combinations: nCr = n! / (r! × (n-r)!)
# How many ways to choose r items from n?
def combinations(n, r):
    return math.factorial(n) // (math.factorial(r) * math.factorial(n - r))

print(combinations(5, 2))  # 10
# How many ways to choose 2 from 5: C(5,2) = 10

# Permutations: nPr = n! / (n-r)!
# How many ways to arrange r items from n?
def permutations(n, r):
    return math.factorial(n) // math.factorial(n - r)

print(permutations(5, 2))  # 20
# How many ways to arrange 2 from 5: P(5,2) = 20
```

### 6. Random Numbers

```python
import random

# Random integer in range [a, b]
print(random.randint(1, 10))   # Random number 1-10

# Random float in range [0, 1)
print(random.random())         # Random number 0-0.999...

# Random choice from list
print(random.choice([1, 2, 3]))  # Random element

# Shuffle list
nums = [1, 2, 3, 4, 5]
random.shuffle(nums)
print(nums)  # Randomly shuffled
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

### Trace: is_prime(17)

```
Input: n = 17

Step 1: n < 2? → No
Step 2: n == 2? → No
Step 3: n % 2 == 0? → 17 % 2 = 1 ≠ 0 → No

Step 4: Loop from 3 to √17 (4.12) → check 3
        17 % 3 = 2 ≠ 0 → continue

Step 5: i = 5? No, 5 > 4.12 → stop

Result: return True (17 is prime) ✓
```

### Trace: is_prime(15)

```
Input: n = 15

Step 1: n < 2? → No
Step 2: n == 2? → No
Step 3: n % 2 == 0? → 15 % 2 = 1 ≠ 0 → No

Step 4: Loop from 3 to √15 (3.87) → check 3
        15 % 3 = 0 → return False (15 is divisible by 3)

Result: return False (15 is not prime) ✓
```

### Trace: gcd(48, 18)

```
Euclidean algorithm:

Step 1: a=48, b=18
        48 % 18 = 12 → a=18, b=12

Step 2: a=18, b=12
        18 % 12 = 6 → a=12, b=6

Step 3: a=12, b=6
        12 % 6 = 0 → a=6, b=0

Result: a=6 ✓ (GCD is 6)

Verification: 48 ÷ 6 = 8, 18 ÷ 6 = 3
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

### Prime Number Visualization

```
Numbers 1-20 and their divisibility:

1 → only 1 (NOT prime)
2 → 1, 2 (PRIME)
3 → 1, 3 (PRIME)
4 → 1, 2, 4 (composite)
5 → 1, 5 (PRIME)
6 → 1, 2, 3, 6 (composite)
7 → 1, 7 (PRIME)
8 → 1, 2, 4, 8 (composite)
9 → 1, 3, 9 (composite)
10 → 1, 2, 5, 10 (composite)

Primes: 2, 3, 5, 7, 11, 13, 17, 19
```

### GCD Visualization

```
Find GCD(24, 36):

Factors of 24: 1, 2, 3, 4, 6, 8, 12, 24
Factors of 36: 1, 2, 3, 4, 6, 9, 12, 18, 36

Common factors: 1, 2, 3, 4, 6, 12
Largest: 12 → GCD = 12 ✓
```

### LCM Visualization

```
Find LCM(4, 6):

Multiples of 4:  4, 8, 12, 16, 20, 24...
Multiples of 6:  6, 12, 18, 24...

First common: 12 → LCM = 12 ✓

Check: 12 ÷ 4 = 3 ✓, 12 ÷ 6 = 2 ✓
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake 1: Not Checking sqrt

```python
# ❌ WRONG - O(n) algorithm
def is_prime_slow(n):
    for i in range(2, n):
        if n % i == 0:
            return False
    return True

# ✅ CORRECT - O(√n) algorithm
def is_prime(n):
    if n < 2: return False
    if n == 2: return True
    if n % 2 == 0: return False
    for i in range(3, int(n**0.5) + 1, 2):
        if n % i == 0:
            return False
    return True
```

**Why it matters:** For n = 10^12, naive approach checks 10^12 numbers vs ~10^6.

**Prevention:** Remember: if n = a × b, then one factor ≤ √n.

---

### Common Mistake 2: Confusing / and //

```python
# ❌ WRONG - Float division
result = 5 / 2  # 2.5 (not integer!)

# ✅ CORRECT - Integer division
result = 5 // 2  # 2

# Example: LCM calculation
# LCM = (a × b) // GCD
# Must use // to get integer result
```

**Why it happens:** Python's `/` always returns float.

**Prevention:** Use `//` for integer operations, `/` for actual division.

---

### Common Mistake 3: Forgetting Edge Cases

```python
# ❌ WRONG - Doesn't handle all cases
def is_prime(n):
    for i in range(2, n):
        if n % i == 0:
            return False
    return True

# is_prime(0) → True (wrong!)
# is_prime(1) → True (wrong!)
# is_prime(2) → works

# ✅ CORRECT - Handle edge cases
def is_prime(n):
    if n < 2:
        return False
    if n == 2:
        return True
    if n % 2 == 0:
        return False
    for i in range(3, int(n**0.5) + 1, 2):
        if n % i == 0:
            return False
    return True
```

**Why it happens:** Forgetting that 0 and 1 are not prime.

**Prevention:** Always check edge cases: n < 2, n == 2.

---

### Common Mistake 4: Integer Overflow in Factorial

```python
# ❌ WRONG - Will overflow for large n
result = 1
for i in range(1, n+1):
    result *= i

# ✅ CORRECT - Use math.factorial
import math
result = math.factorial(n)  # Handles large numbers

# Or use decimal for very large results
from math import factorial
```

**Why it happens:** Manual multiplication can overflow.

**Prevention:** Use Python's `math.factorial()` which handles arbitrarily large integers.

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Quick Reference

| Operation | Code |
|-----------|------|
| Prime check | `is_prime(n)` |
| GCD | `math.gcd(a, b)` |
| LCM | `math.lcm(a, b)` (Python 3.9+) |
| LCM formula | `abs(a*b) // gcd(a,b)` |
| Square root | `int(n**0.5)` |
| Factorial | `math.factorial(n)` |
| Combinations | `math.comb(n, r)` |
| Power | `a ** b` or `pow(a, b)` |

### Key Formulas

| Formula | Expression |
|---------|------------|
| GCD Euclid | `gcd(a,b) = gcd(b, a % b)` |
| LCM via GCD | `lcm(a,b) = |a×b| / gcd(a,b)` |
| Factorial | `n! = 1×2×3×...×n` |
| Combinations | `C(n,r) = n! / (r!(n-r)!)` |
| Permutations | `P(n,r) = n! / (n-r)!` |

### Decision Tree

```
Math problem?
│
├─ Prime check? → Check up to √n, skip evens
├─ GCD? → math.gcd() or Euclidean algorithm
├─ LCM? → a*b // gcd(a,b)
├─ Factorial? → math.factorial()
├─ Combinations? → math.comb()
└─ Power? → a ** b
```

### Mnemonic

**"Prime Check: 2, then odds up to sqrt"**
1. Handle 0, 1, 2
2. Skip even numbers
3. Check odd divisors up to √n

**"GCD: Keep dividing, remainder becomes divisor"**
- While b ≠ 0: a, b = b, a % b
- When b = 0, a is GCD

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

### Question 1: Concept Check

**Is 17 a prime number? How would you check?**

> **Answer:** Yes, 17 is prime.
>
> Check: 17 is not divisible by any number from 2 to √17 (≈4).
> Not divisible by 2, 3, or 4.
> Therefore, 17 is prime.

---

### Question 2: Prediction

**What is the output of this code?**
```python
import math
print(math.gcd(24, 36))
```

> **Answer:** 12
>
> GCD(24, 36) = 12 (largest number dividing both 24 and 36)

---

### Question 3: Problem Solving

**Calculate LCM(8, 12) without using math.lcm()**

> **Answer:** 24
>
> Method 1: Formula
> - GCD(8, 12) = 4
> - LCM = 8 × 12 / 4 = 96 / 4 = 24
>
> Method 2: List multiples
> - Multiples of 8: 8, 16, 24, 32...
> - Multiples of 12: 12, 24, 36...
> - First common: 24

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

### Problem: Count Primes

**Problem Statement:**
Given an integer n, return the number of prime numbers less than n.

**Example:**
```
Input: n = 10
Output: 4
Explanation: Primes less than 10 are [2, 3, 5, 7] → count = 4
```

**Sieve of Eratosthenes Solution:**
```python
def count_primes(n):
    """
    Count primes less than n using Sieve of Eratosthenes.
    
    Time: O(n log log n)
    Space: O(n)
    """
    if n <= 2:
        return 0
    
    # Assume all numbers are prime initially
    is_prime = [True] * n
    is_prime[0] = is_prime[1] = False
    
    # Sieve: mark multiples of each prime as not prime
    for i in range(2, int(n**0.5) + 1):
        if is_prime[i]:
            # Mark all multiples of i starting from i*i
            for j in range(i * i, n, i):
                is_prime[j] = False
    
    return sum(is_prime)


# Alternative: Simple approach
def count_primes_simple(n):
    """Simple but less efficient."""
    def is_prime(num):
        if num < 2:
            return False
        if num == 2:
            return True
        if num % 2 == 0:
            return False
        for i in range(3, int(num**0.5) + 1, 2):
            if num % i == 0:
                return False
        return True
    
    return sum(1 for i in range(n) if is_prime(i))


# Read input
n = int(input())
print(count_primes(n))
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

### Challenge: Armstrong Number

**Problem:**
An Armstrong number (also called narcissistic number) is a number that equals the sum of its digits each raised to the power of the number of digits.

**Example:**
```
153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = 153 ✓

1634 = 1⁴ + 6⁴ + 3⁴ + 4⁴ = 1 + 1296 + 81 + 256 = 1634 ✓
```

**Solution:**
```python
def is_armstrong(n):
    """
    Check if n is an Armstrong number.
    
    153: 1^3 + 5^3 + 3^3 = 153 → Armstrong
    123: 1^3 + 2^3 + 3^3 = 36 → Not Armstrong
    """
    digits = [int(d) for d in str(n)]
    k = len(digits)  # Number of digits
    
    total = sum(d ** k for d in digits)
    return total == n


# Find all Armstrong numbers in a range
def find_armstrong(start, end):
    results = []
    for n in range(start, end + 1):
        if is_armstrong(n):
            results.append(n)
    return results


# Test
print(is_armstrong(153))    # True
print(is_armstrong(123))    # False
print(is_armstrong(1634))   # True

# Find all 3-digit Armstrong numbers
print(find_armstrong(100, 999))
# Output: [153, 370, 371, 407]
```

**Trace for 153:**
```
n = 153
digits = [1, 5, 3]
k = 3

Sum = 1³ + 5³ + 3³
    = 1 + 125 + 27
    = 153

153 == 153 → True ✓
```

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

### What You Learned Today

1. **Prime Check:** O(√n) algorithm
2. **GCD:** Euclidean algorithm
3. **LCM:** Using GCD formula
4. **Math Functions:** factorial, log, power
5. **Combinations/Permutations:** Using factorial

### Key Takeaways

- Prime check: only need to test up to √n
- GCD/LCM: `gcd(a,b) × lcm(a,b) = |a×b|`
- Use `//` for integer division, not `/`
- Python handles big integers natively

### Common Patterns

| Problem | Solution |
|---------|----------|
| Is prime? | Check divisors up to √n |
| GCD | `math.gcd()` |
| LCM | `a*b // gcd(a,b)` |
| Count primes | Sieve of Eratosthenes |
| Armstrong | Sum of digit^k == n |

### Weak Points to Watch

- Not checking sqrt for prime
- Using `/` instead of `//` for integers
- Forgetting edge cases (0, 1, 2)

### Next Lesson Preview

**Lesson 47:** Recursion — Functions that call themselves

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 46 / 2000 |
| **Chapter** | 5 (Algorithm Patterns) |
| **XP** | 460 |
| **Rank** | Builder |
| **Mastery** | Math Operations |
| **Weaknesses** | Remembering sqrt optimization |
| **Recommended Focus** | Practice GCD/LCM problems |
| **Suggested Review** | Lesson 45 (Matrix - uses math operations) |
| **Next Lesson Readiness** | ✓ Ready for Recursion |

---

**Type 47 to continue**