# Bài 42 — String Algorithms

---

## 1. Ôn tập
Bài 41 đã học Sliding Window. Giờ học các **thuật toán xử lý string**.

---

## 2. Mục tiêu bài học
- Reverse string
- Anagram
- Palindrome
- Substring

---

## 3. Reverse String

```python
# Đảo ngược string
s = "hello"

# Cách 1: slicing
print(s[::-1])  # olleh

# Cách 2: reversed
print("".join(reversed(s)))  # olleh

# Cách 3: for loop
def reverse_str(s):
    result = ""
    for c in s:
        result = c + result
    return result
print(reverse_str(s))  # olleh
```

---

## 4. Anagram

```python
# Kiểm tra anagram (cùng chữ cái, khác thứ tự)
def is_anagram(s1, s2):
    return sorted(s1) == sorted(s2)

print(is_anagram("listen", "silent"))  # True
print(is_anagram("hello", "world"))    # False
```

**O(n log n)** - dùng sort

**O(n)** - dùng counter:
```python
from collections import Counter

def is_anagram(s1, s2):
    return Counter(s1) == Counter(s2)
```

---

## 5. Palindrome

```python
# Kiểm tra palindrome
def is_palindrome(s):
    return s == s[::-1]

print(is_palindrome("radar"))   # True
print(is_palindrome("hello"))   # False
```

**Loại bỏ khoảng trắng:**
```python
def is_palindrome(s):
    s = s.lower().replace(" ", "")
    return s == s[::-1]

print(is_palindrome("A man a plan a canal Panama"))  # True
```

---

## 6. Substring

```python
# Kiểm tra substring
s = "hello world"
print("world" in s)     # True
print("python" in s)   # False

# Tìm tất cả vị trí
def find_all(s, sub):
    positions = []
    start = 0
    while True:
        pos = s.find(sub, start)
        if pos == -1:
            break
        positions.append(pos)
        start = pos + 1
    return positions

print(find_all("hello hello hello", "hello"))  # [0, 6, 12]
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Quên case sensitive
```python
# "Listen" và "silent" → False!
# → Dùng .lower()
```

---

### ❌ SAI THỨ 2 — Palindrome với ký tự đặc biệt
```python
# "A man, a plan, a canal: Panama"
# → Cần loại bỏ khoảng trắng và ký tự đặc biệt
s = ''.join(c.lower() for c in s if c.isalnum())
```

---

### ❌ SAI THỨ 3 — find() trả -1 khi không có
```python
if s.find("abc") > -1:  # thay vì != -1
    print("Co")
# Hoặc
if "abc" in s:
    print("Co")
```

---

## 8. Ghi nhớ nhanh

| Bài toán | Cách giải |
|----------|-----------|
| Reverse | s[::-1] |
| Anagram | Counter hoặc sorted |
| Palindrome | s == s[::-1] |
| Substring | `in` hoặc find() |

**MẸO NHỚ:** Anagram = cùng chữ cái, Palindrome = đọc ngược giống.

---

## 9. Mini Test (3 câu)

**Câu 1:** "listen" có anagram với "silent"?
> Đáp án: True

**Câu 2:** "racecar" là palindrome?
> Đáp án: True

**Câu 3:** Đảo ngược "Python":
> Đáp án: "nohtyP"

---

## 10. LeetCode Practice

### Bài tập: Đếm ký tự duy nhất trong string
**Yêu cầu:** Đếm số ký tự duy nhất trong string

**Input:** `leetcode`

**Output:** `4` (l, e, t, c, o, d - các ký tự riêng biệt là l, e, t, c, o, d = 6? Đợi xem)

**Output thực:** `5` (l,e,t,c,o,d → 6 nhưng có lặp e, nên 6-1=5)

**✅ Đáp án:**
```python
from collections import Counter

def count_unique(s):
    freq = Counter(s)
    count = 0
    for v in freq.values():
        if v == 1:
            count += 1
    return count

s = input()
print(count_unique(s))
```

---

## 11. Bonus Challenge

Tìm longest palindrome substring

**Input:** `babad`

**Output:** `bab` hoặc `aba`

**✅ Đáp án:**
```python
def longest_palindrome(s):
    if not s:
        return ""
    
    start, end = 0, 0
    
    for i in range(len(s)):
        len1 = expand(s, i, i)
        len2 = expand(s, i, i+1)
        max_len = max(len1, len2)
        
        if max_len > end - start + 1:
            start = i - (max_len - 1) // 2
            end = i + max_len // 2
    
    return s[start:end+1]

def expand(s, left, right):
    while left >= 0 and right < len(s) and s[left] == s[right]:
        left -= 1
        right += 1
    return right - left - 1

s = input()
print(longest_palindrome(s))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 42 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 420 |
| **Mức độ** | Medium |