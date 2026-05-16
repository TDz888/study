# Bài 40 — Two Pointers

---

## 1. Ôn tập
Bài 39 đã học Sort. Giờ học kỹ thuật **Two Pointers** — dùng 2 con trỏ.

---

## 2. Mục tiêu bài học
- Hiểu two pointers là gì
- Biết khi nào dùng
- Áp dụng vào bài toán cụ thể
- So sánh với approaches khác

---

## 3. Code chính (CORE LESSON)

```python
# Tìm cặp có tổng = target trong mảng đã sắp xếp
def two_sum(arr, target):
    left, right = 0, len(arr) - 1
    
    while left < right:
        current_sum = arr[left] + arr[right]
        
        if current_sum == target:
            return [left, right]
        elif current_sum < target:
            left += 1
        else:
            right -= 1
    
    return [-1, -1]

nums = [1, 2, 3, 4, 6]
print(two_sum(nums, 5))  # [1, 2] (2 + 4 = 6) → [1, 3] (3 + 4 = 7) → đợi tính lại
print(two_sum(nums, 5))  # [1, 3] vì 2+4=6>5 nên right--
```

**Output:**
```
[1, 3]
```

---

## 4. Remove Duplicates

```python
# Xóa phần tử trùng lặp trong mảng đã sắp xếp
def remove_duplicates(nums):
    if not nums:
        return 0
    
    slow = 0
    for fast in range(1, len(nums)):
        if nums[fast] != nums[slow]:
            slow += 1
            nums[slow] = nums[fast]
    
    return slow + 1

nums = [1, 1, 2, 2, 3, 4, 4]
print(remove_duplicates(nums))  # 4
print(nums[:4])  # [1, 2, 3, 4]
```

---

## 5. Trace luồng chạy

```
nums = [1, 2, 3, 4, 6], target = 5

left=0, right=4 → 1+6=7 > 5 → right=3
left=0, right=3 → 1+4=5 == target → return [0, 3]
```

---

## 6. Khi nào dùng Two Pointers

| Loại bài | Khi nào dùng |
|----------|--------------|
| Tìm cặp có tổng | Mảng đã sắp xếp |
| Xóa duplicates | Mảng đã sắp xếp |
| Container most water | Tìm max area |
| 3 sum | Tìm 3 số có tổng |

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Quên tăng/giảm pointers
```python
while left < right:
    # Quên cập nhật → vòng lặp vô hạn!
```

---

### ❌ SAI THỨ 2 — Condition sai
```python
while left < right:  # hoặc <= tùy bài
# Nhầm lẫn condition → sai kết quả
```

---

### ❌ SAI THỨ 3 — Dùng Two Pointers cho mảng chưa sắp xếp
```python
# Mảng chưa sắp xếp → two pointers có thể sai!
nums = [5, 2, 9, 1]
# sort trước khi dùng
```

---

## 8. Ghi nhớ nhanh

| Pattern | Mục đích |
|---------|----------|
| Left + Right | Tìm cặp tổng |
| Slow + Fast | Xóa duplicates |
| Expand + Contract | Container with most water |

**MẸO NHỚ:** Two Pointers = 2 người đi từ 2 phía → gặp nhau giữa đường.

---

## 9. Mini Test (3 câu)

**Câu 1:** Tìm [3, 4] trong [1,2,3,4]:
> Đáp án: left=0, right=3 → 1+4=5>3 → right=2 → 1+3=4 → found

**Câu 2:** Xóa duplicates [1,1,2]:
> Đáp án: 2 phần tử [1,2]

**Câu 3:** Ưu điểm two pointers?
> Đáp án: O(n) thay vì O(n²)

---

## 10. LeetCode Practice

### Bài tập: Tìm cặp có tổng = target
**Yêu cầu:** Tìm 2 số có tổng = target trong mảng đã sắp xếp

**Input:** 
```
9
1 2 3 4 5 6 7 8 9
```

**Output:** `3 7` (index)

**✅ Đáp án:**
```python
def two_sum(arr, target):
    left, right = 0, len(arr) - 1
    while left < right:
        if arr[left] + arr[right] == target:
            return left, right
        elif arr[left] + arr[right] < target:
            left += 1
        else:
            right -= 1

target = int(input())
arr = list(map(int, input().split()))
l, r = two_sum(arr, target)
print(l, r)
```

---

## 11. Bonus Challenge

Tìm 3 số có tổng = 0 (3 Sum)

**Input:** `[-1, 0, 1, 2, -1, -4]`

**Output:** `[[-1, -1, 2], [-1, 0, 1]]`

**✅ Đáp án:**
```python
def three_sum(nums):
    nums.sort()
    result = []
    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i-1]:
            continue
        left, right = i + 1, len(nums) - 1
        while left < right:
            s = nums[i] + nums[left] + nums[right]
            if s == 0:
                result.append([nums[i], nums[left], nums[right]])
                left += 1
                right -= 1
            elif s < 0:
                left += 1
            else:
                right -= 1
    return result

nums = list(map(int, input().split()))
print(three_sum(nums))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 40 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 400 |
| **Mức độ** | Hard |