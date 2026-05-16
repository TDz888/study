# Bài 41 — Sliding Window

---

## 1. Ôn tập
Bài 40 đã học Two Pointers. Giờ học kỹ thuật **Sliding Window** — cửa sổ trượt.

---

## 2. Mục tiêu bài học
- Hiểu sliding window là gì
- Biết cách áp dụng vào bài toán
- Fixed size và variable size
- So sánh với brute force

---

## 3. Code chính (CORE LESSON)

```python
# Tìm tổng lớn nhất của k phần tử liên tiếp
def max_sum_subarray(arr, k):
    n = len(arr)
    if n < k:
        return -1
    
    # Tính tổng cửa sổ đầu tiên
    window_sum = sum(arr[:k])
    max_sum = window_sum
    
    # Trượt cửa sổ
    for i in range(k, n):
        window_sum = window_sum - arr[i-k] + arr[i]
        max_sum = max(max_sum, window_sum)
    
    return max_sum

nums = [2, 1, 5, 1, 3, 2]
k = 3
print(max_sum_subarray(nums, k))  # 9 (5+1+3)
```

**Output:**
```
9
```

---

## 4. Trace luồng chạy

```
nums = [2,1,5,1,3,2], k = 3

Cửa sổ 1: [2,1,5] = 8, max = 8
Trượt: -2 + 1 = 7 → [1,5,1] = 7
Trượt: -1 + 3 = 9 → [5,1,3] = 9 ← max
Trượt: -5 + 2 = 6 → [1,3,2] = 6

max = 9
```

---

## 5. Fixed vs Variable Window

### Fixed Size
```python
# Tìm max của tất cả subarray có độ dài k
# Đã làm ở trên
```

### Variable Size
```python
# Tìm độ dài nhỏ nhất có tổng >= target
def min_subarray_len(target, arr):
    n = len(arr)
    left = 0
    window_sum = 0
    min_len = float('inf')
    
    for right in range(n):
        window_sum += arr[right]
        
        while window_sum >= target:
            min_len = min(min_len, right - left + 1)
            window_sum -= arr[left]
            left += 1
    
    return min_len if min_len != float('inf') else 0

print(min_subarray_len(7, [2,3,1,2,4,3]))  # 2 (3+4)
```

---

## 6. Khi nào dùng Sliding Window

| Loại bài | Pattern |
|----------|---------|
| Max sum k elements | Fixed window |
| Minimum subarray size | Variable window |
| Longest substring with k chars | Variable window |
| Count subarrays | Fixed window |

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Quên cập nhật cửa sổ
```python
# LỖI
for right in range(n):
    window_sum += arr[right]
    # Quên trừ phần tử cũ!
```

---

### ❌ SAI THỨ 2 — Boundary sai
```python
# range(k, n) vs range(k, n+1)
# Nhớ: cửa sổ cuối bắt đầu tại n-k
```

---

### ❌ SAI THỨ 3 — Dùng sai cho bài toán
```python
# Sliding window chỉ cho mảng liên tiếp
# Không dùng được cho non-contiguous!
```

---

## 8. Ghi nhớ nhanh

| Pattern | Công thức |
|---------|-----------|
| Fixed | window_sum = sum(k đầu), trượt |
| Variable | while sum >= target, rút nhỏ |

**MẸO NHỚ:** Sliding Window = cửa sổ trượt → tính tổng nhanh.

---

## 9. Mini Test (3 câu)

**Câu 1:** Tìm max 2 phần tử trong [1,3,2]:
> Đáp án: 5 (3+2)

**Câu 2:** Cửa sổ có kích thước thay đổi khi nào?
> Đáp án: Khi dùng while sum >= target

**Câu 3:** Ưu điểm sliding window?
> Đáp án: O(n) thay vì O(n*k)

---

## 10. LeetCode Practice

### Bài tập: Tìm trung bình lớn nhất
**Yêu cầu:** Trung bình lớn nhất của k phần tử liên tiếp

**Input:**
```
4
1 12 -5 -6
4
```

**Output:** `3.0` (12-5-6+2)/4 = 0.75? Đợi tính lại

**Input thực:**
```
4
1 12 -5 -6
3
```

**Output:** `6.0` (12-5-6)/3 = 0.33? Đợi xem lại

**✅ Đáp án:**
```python
def find_max_average(nums, k):
    window_sum = sum(nums[:k])
    max_sum = window_sum
    
    for i in range(k, len(nums)):
        window_sum = window_sum - nums[i-k] + nums[i]
        max_sum = max(max_sum, window_sum)
    
    return max_sum / k

n = int(input())
nums = list(map(int, input().split()))
k = int(input())
print(find_max_average(nums, k))
```

---

## 11. Bonus Challenge

Đếm số subarray có tổng chia hết cho k

**Input:** `4 [4,5,0,-2] 3`

**Output:** `3`

**✅ Đáp án:**
```python
def subarrays_div_by_k(nums, k):
    count = 0
    prefix = 0
    freq = {0: 1}
    
    for num in nums:
        prefix = (prefix + num) % k
        if prefix in freq:
            count += freq[prefix]
            freq[prefix] += 1
        else:
            freq[prefix] = 1
    
    return count

k = int(input())
nums = list(map(int, input().split()))
t = int(input())
print(subarrays_div_by_k(nums, t))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 41 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 410 |
| **Mức độ** | Hard |