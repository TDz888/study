# Bài 48 — Common Patterns

---

## 1. Ôn tập
Bài 47 đã học Bit Manipulation. Giờ học các **patterns thường gặp** trong lập trình.

---

## 2. Mục tiêu bài học
- Frequency counter
- Multiple pointers
- Sliding window
- Fast and slow pointers
- Divide and conquer

---

## 3. Frequency Counter

```python
# Đếm tần suất - O(n)
def find_duplicates(nums):
    freq = {}
    result = []
    for num in nums:
        if num in freq and freq[num] == 1:
            result.append(num)
        freq[num] = freq.get(num, 0) + 1
    return result

print(find_duplicates([1, 2, 3, 2, 1]))  # [2, 1]
```

---

## 4. Multiple Pointers

```python
# Tìm cặp có tổng = 0 trong mảng đã sắp xếp
def sum_zero(arr):
    left = 0
    right = len(arr) - 1
    result = []
    
    while left < right:
        s = arr[left] + arr[right]
        if s == 0:
            result.append([arr[left], arr[right]])
            left += 1
            right -= 1
        elif s < 0:
            left += 1
        else:
            right -= 1
    
    return result

print(sum_zero([-4, -3, -2, -1, 0, 1, 2, 3]))
```

---

## 5. Fast and Slow Pointers

```python
# Phát hiện cycle trong linked list
def has_cycle(head):
    slow = head
    fast = head
    
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    
    return False
```

---

## 6. Divide and Conquer

```python
# Binary Search - chia để trị
def binary_search(arr, target):
    if not arr:
        return -1
    
    mid = len(arr) // 2
    if arr[mid] == target:
        return mid
    elif arr[mid] > target:
        return binary_search(arr[:mid], target)
    else:
        return mid + 1 + binary_search(arr[mid+1:], target)

print(binary_search([1, 2, 3, 4, 5], 3))  # 2
```

---

## 7. So sánh Patterns

| Pattern | Độ phức tạp | Khi nào dùng |
|---------|-------------|--------------|
| Frequency Counter | O(n) | Đếm, tìm duplicates |
| Two Pointers | O(n) | Mảng đã sắp xếp |
| Sliding Window | O(n) | Subarray/substring |
| Fast/Slow | O(n) | Phát hiện cycle |
| Divide/Conquer | O(log n) | Binary search |

---

## 8. Debug Mentor Mode

### ❌ SAI THỨ 1 — Chọn sai pattern
```python
# Dùng two pointers cho mảng chưa sắp xếp → sai
# → Sort trước hoặc dùng hash
```

---

### ❌ SAI THỨ 2 — Infinite loop
```python
while left < right:
    if arr[left] + arr[right] == 0:
        left += 1  # Cần cả 2 cập nhật!
        right -= 1
```

---

## 9. Ghi nhớ nhanh

| Pattern | Dùng khi |
|---------|----------|
| Frequency Counter | Đếm, so sánh O(n) |
| Two Pointers | Mảng đã sort, tìm cặp |
| Sliding Window | Subarray liên tiếp |
| Fast/Slow | Linked list cycle |
| Divide/Conquer | Search trong không gian lớn |

---

## 10. LeetCode Practice

### Bài tập: Tìm số xuất hiện 2 lần
**Yêu cầu:** Tìm tất cả số xuất hiện 2 lần (không dùng extra space)

**Input:** `[4,3,2,7,8,2,3,1]`

**Output:** `[2, 3]`

**✅ Đáp án:**
```python
def find_duplicates(nums):
    result = []
    for num in nums:
        idx = abs(num) - 1
        if nums[idx] > 0:
            nums[idx] = -nums[idx]
        else:
            result.append(abs(num))
    return result

nums = list(map(int, input().split()))
print(find_duplicates(nums))
```

---

## 11. Bonus Challenge

Maximum subarray (Kadane's algorithm)

**Input:** `[-2,1,-3,4,-1,2,1,-5,4]`

**Output:** `6` (4,-1,2,1)

**✅ Đáp án:**
```python
def max_subarray(nums):
    max_sum = nums[0]
    current_sum = nums[0]
    
    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)
    
    return max_sum

nums = list(map(int, input().split()))
print(max_subarray(nums))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 48 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 480 |
| **Mức độ** | Hard |