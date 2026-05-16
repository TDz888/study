# Bài 46 — Math Problems (Toán học)

---

## 1. Ôn tập
Bài 45 đã học Matrix. Giờ học các **bài toán toán học** trong Python.

---

## 2. Mục tiêu bài học
- Số nguyên tố
- Ước số chung lớn nhất (GCD)
- Bội số chung nhỏ nhất (LCM)
- Số mũ và log

---

## 3. Số nguyên tố

```python
# Kiểm tra số nguyên tố
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

print(is_prime(7))   # True
print(is_prime(10))  # False
```

---

## 4. GCD và LCM

```python
import math

# GCD - Ước số chung lớn nhất
print(math.gcd(12, 18))  # 6

# LCM - Bội số chung nhỏ nhất
def lcm(a, b):
    return abs(a * b) // math.gcd(a, b)

print(lcm(12, 18))  # 36

# Không dùng thư viện
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a
```

---

## 5. Số mũ và Log

```python
import math

# Power
print(2 ** 10)        # 1024
print(pow(2, 10))     # 1024
print(pow(2, 10, 1000))  # 24 (2^10 % 1000)

# Log
print(math.log(100, 10))  # 2.0
print(math.log10(100))   # 2.0
print(math.log2(8))      # 3.0

# Số ngẫu nhiên
import random
print(random.randint(1, 10))   # 1-10
print(random.random())         # 0-1
print(random.choice([1,2,3]))  # Chọn ngẫu nhiên
```

---

## 6. Số nguyên lớn

```python
# Factorial
import math
print(math.factorial(20))  # 2432902008176640000

# Tổ hợp (nCr)
def combinations(n, r):
    return math.factorial(n) // (math.factorial(r) * math.factorial(n-r))

print(combinations(5, 2))  # 10

# Hoán vị (nPr)
def permutations(n, r):
    return math.factorial(n) // math.factorial(n-r)
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Kiểm tra số nguyên tố sai
```python
# Thử tất cả số - O(n)
def is_prime_slow(n):
    for i in range(2, n):
        if n % i == 0:
            return False
    return True

# Đúng - chỉ thử đến sqrt(n) - O(sqrt(n))
def is_prime(n):
    if n < 2: return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True
```

---

### ❌ SAI THỨ 2 — Nhầm / và //
```python
# / cho số thập phân
print(5 / 2)   # 2.5

# // cho số nguyên
print(5 // 2)  # 2
```

---

## 8. Ghi nhớ nhanh

| Hàm | Ý nghĩa |
|-----|---------|
| `math.gcd(a,b)` | Ước chung lớn nhất |
| `math.lcm(a,b)` | Bội chung nhỏ nhất (3.9+) |
| `math.sqrt(n)` | Căn bậc 2 |
| `math.factorial(n)` | Giai thừa |

**MẸO NHỚ:** Prime = "nguyên tố" (chỉ chia hết cho 1 và chính nó).

---

## 9. Mini Test (3 câu)

**Câu 1:** GCD(24, 36)?
> Đáp án: `12`

**Câu 2:** is_prime(1)?
> Đáp án: `False` (1 không phải số nguyên tố)

**Câu 3:** 2^10 = ?
> Đáp án: `1024`

---

## 10. LeetCode Practice

### Bài tập: Tìm số nguyên tố đầu tiên
**Yêu cầu:** Tìm số nguyên tố đầu tiên trong khoảng n đến 2n

**Input:** `10`

**Output:** `11`

**✅ Đáp án:**
```python
def is_prime(n):
    if n < 2: return False
    if n == 2: return True
    if n % 2 == 0: return False
    for i in range(3, int(n**0.5)+1, 2):
        if n % i == 0: return False
    return True

n = int(input())
for num in range(n+1, 2*n+1):
    if is_prime(num):
        print(num)
        break
```

---

## 11. Bonus Challenge

Kiểm tra số Armstrong (số bằng tổng lũy thừa các chữ số)

**Input:** `153`

**Output:** `True` (1³+5³+3³=1+125+27=153)

**✅ Đáp án:**
```python
def is_armstrong(n):
    digits = [int(d) for d in str(n)]
    k = len(digits)
    return sum(d ** k for d in digits) == n

n = int(input())
print(is_armstrong(n))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 46 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 460 |
| **Mức độ** | Easy |