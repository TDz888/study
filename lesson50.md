# Bài 50 — Practice Complete

---

## 1. Ôn tập
Bài 49 đã học Complexity. Đây là bài tổng hợp cuối cùng của chương!

---

## 2. Mục tiêu bài học
- Tổng kết kiến thức
- Ôn tất cả topics
- Chuẩn bị cho advanced

---

## 3. Tổng kết Topics đã học

| Chương | Topics |
|--------|--------|
| 1. Cơ bản | print, input, biến, if/else, for/while, string, list, dict, set |
| 2. Logic | Nested if, loop nâng cao, pattern |
| 3. Functions | def, return, *args, **kwargs, lambda, recursion |
| 4. Data Structures | List, tuple, dict, set - methods & operations |
| 5. LeetCode | Search, Sort, Two Pointers, Sliding Window, Hashing, Stack, Matrix, Math, Bit |
| 6. Projects | OOP, File handling, Exception |

---

## 4. Các Patterns quan trọng

```python
# 1. Frequency Counter - Đếm
from collections import Counter
freq = Counter(arr)

# 2. Two Pointers - 2 con trỏ
left, right = 0, len(arr)-1

# 3. Sliding Window - cửa sổ trượt
for r in range(n):
    window_sum += arr[r]
    if r >= k: window_sum -= arr[r-k]

# 4. Hash - tra cứu nhanh
seen = {val: index for val, index in enumerate(arr)}

# 5. Stack/Queue - LIFO/FIFO
stack.append(x); stack.pop()
queue.append(x); queue.popleft()
```

---

## 5. Big O Summary

```
Tốt nhất → Xấu nhất:
O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2^n)
```

---

## 6. Code tổng hợp

```python
# 50 bài đã học! Ví dụ tổng hợp:
class Sol:
    def solve(self, arr):
        # Sử dụng nhiều kỹ thuật
        from collections import Counter
        freq = Counter(arr)  # Hash
        sorted_arr = sorted(arr)  # O(n log n)
        
        # Two pointers
        left, right = 0, len(arr)-1
        
        return result
```

---

## 7. Tiếp theo

Sau 50 bài cơ bản:
- **51-100**: Advanced Data Structures
- **101-200**: Advanced Algorithms  
- **201-500**: System Design
- **501-2000**: Real Projects

---

## 8. Practice Problems

### Problem 1: Valid Palindrome
```python
def is_palindrome(s):
    s = ''.join(c.lower() for c in s if c.isalnum())
    return s == s[::-1]
```

### Problem 2: Reverse String
```python
def reverse(s):
    return s[::-1]
```

### Problem 3: Two Sum
```python
def two_sum(nums, target):
    seen = {}
    for i, n in enumerate(nums):
        if target - n in seen:
            return [seen[target - n], i]
        seen[n] = i
```

### Problem 4: Max Subarray
```python
def max_sub(nums):
    max_sum = cur = nums[0]
    for n in nums[1:]:
        cur = max(n, cur + n)
        max_sum = max(max_sum, cur)
    return max_sum
```

### Problem 5: Climbing Stairs
```python
def climb(n):
    if n <= 2: return n
    a, b = 1, 2
    for _ in range(3, n+1):
        a, b = b, a + b
    return b
```

---

## 9. Congratulations!

**Bạn đã hoàn thành 50 bài Python cơ bản!**

```
┌─────────────────────────────────────┐
│  🎉 CHÚC MỪNG! 🎉                   │
│  Level: Python Beginner → Basic    │
│  XP: 500                            │
│  Skills: 50 topics                 │
└─────────────────────────────────────┘
```

**Tiếp theo:** Gõ "51" để tiếp tục nâng cao!

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 50 / 2000 |
| **Chapter** | Tổng hợp |
| **XP** | 500 |
| **Mức độ** | Basic Completed |