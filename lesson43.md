# Bài 43 — Hashing

---

## 1. Ôn tập
Bài 42 đã học String Algorithms. Giờ học **Hashing** — kỹ thuật băm.

---

## 2. Mục tiêu bài học
- Hiểu hash table là gì
- Dùng dictionary/set để hash
- Giải bài toán với O(1) lookup
- Ứng dụng thực tế

---

## 3. Hash Table cơ bản

```python
# Hash table = Dictionary trong Python
# O(1) cho insert, lookup, delete

# Ví dụ: Đếm tần suất
s = "hello"
freq = {}

for c in s:
    freq[c] = freq.get(c, 0) + 1

print(freq)  # {'h': 1, 'e': 1, 'l': 2, 'o': 1}
```

**Output:**
```
{'h': 1, 'e': 1, 'l': 2, 'o': 1}
```

---

## 4. Hash Set

```python
# Set = Hash Set
# Kiểm tra phần tử tồn tại trong O(1)

nums = [1, 2, 3, 2, 1, 4]
unique = set(nums)
print(unique)  # {1, 2, 3, 4}

# Kiểm tra nhanh
if 3 in unique:
    print("Co so 3")
```

---

## 5. Two Sum với Hash

```python
# Bài toán classic - Two Sum
def two_sum(nums, target):
    seen = {}  # {value: index}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    return []

nums = [2, 7, 11, 15]
print(two_sum(nums, 9))  # [0, 1]
```

**Trace:**
```
i=0, num=2 → complement=7 → 7 not in seen → seen[2]=0
i=1, num=7 → complement=2 → 2 in seen! → return [0, 1]
```

---

## 6. Ưu điểm Hashing

| Thao tác | Array | Hash Table |
|----------|-------|------------|
| Search | O(n) | O(1) |
| Insert | O(1) | O(1) |
| Delete | O(n) | O(1) |

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Hash collision (trùng hash)
```python
# Python tự xử lý - không cần lo
# Nhưng cần chọn hash function tốt
```

---

### ❌ SAI THỨ 2 — Dùng list cho large data
```python
# LỖI - O(n) search!
for x in big_list:
    if x == target: ...

# ĐÚNG - O(1) lookup
hash_set = set(big_list)
if target in hash_set: ...
```

---

### ❌ SAI THỨ 3 — Nhầm dict keys và values
```python
d = {"a": 1}
if "a" in d:     # Check key
if 1 in d.values():  # Check value
```

---

## 8. Ghi nhớ nhanh

| Cấu trúc | Độ phức tạp |
|----------|-------------|
| List lookup | O(n) |
| Set lookup | O(1) |
| Dict lookup | O(1) |

**MẸO NHỚ:** Hash = "băm" → tìm nhanh như tra từ điển.

---

## 9. Mini Test (3 câu)

**Câu 1:** Độ phức tạp tìm phần tử trong set?
> Đáp án: O(1)

**Câu 2:** Two sum dùng hash có độ phức tạp?
> Đáp án: O(n)

**Câu 3:** freq.get(c, 0) nghĩa là gì?
> Đáp án: Lấy giá trị, nếu không có trả về 0

---

## 10. LeetCode Practice

### Bài tập: Tìm số bị thiếu
**Yêu cầu:** Tìm số bị thiếu trong dãy 1-n

**Input:** `5 [1 2 4 5 5]`

**Output:** `3`

**✅ Đáp án:**
```python
n = int(input())
nums = list(map(int, input().split()))

# Dùng set
full = set(range(1, n + 1))
nums_set = set(nums)
missing = full - nums_set

print(list(missing)[0])
```

---

## 11. Bonus Challenge

Tìm phần tử xuất hiện nhiều nhất (majority element > n/2)

**Input:** `7 [2 2 1 1 1 2 2]`

**Output:** `2`

**✅ Đáp án:**
```python
from collections import Counter

def majority(nums):
    freq = Counter(nums)
    n = len(nums)
    for num, count in freq.items():
        if count > n // 2:
            return num
    return -1

nums = list(map(int, input().split()))
print(majority(nums))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 43 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 430 |
| **Mức độ** | Medium |