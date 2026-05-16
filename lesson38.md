# Bài 38 — Search (Tìm kiếm)

---

## 1. Ôn tập
Bài 37 đã học Magic Methods. Giờ học các **thuật toán tìm kiếm** cơ bản.

---

## 2. Mục tiêu bài học
- Linear Search (tìm tuyến tính)
- Binary Search (tìm nhị phân)
- So sánh 2 thuật toán
- Ứng dụng

---

## 3. Linear Search

```python
# Tìm kiếm tuyến tính
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1

# Test
nums = [4, 2, 7, 1, 9, 3]
print(linear_search(nums, 7))  # 2
print(linear_search(nums, 5))  # -1
```

**Output:**
```
2
-1
```

---

## 4. Binary Search

```python
# Tìm kiếm nhị phân (mảng đã sắp xếp)
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1

# Test
nums = [1, 3, 5, 7, 9, 11, 13]
print(binary_search(nums, 7))  # 3
print(binary_search(nums, 6))  # -1
```

**Output:**
```
3
-1
```

---

## 5. Trace luồng chạy Binary Search

```
arr = [1, 3, 5, 7, 9], target = 7

left=0, right=4, mid=2 → arr[2]=5 < 7 → left=3
left=3, right=4, mid=3 → arr[3]=7 == 7 → return 3
```

---

## 6. So sánh

| Thuật toán | Độ phức tạp | Yêu cầu |
|-----------|-------------|---------|
| Linear | O(n) | Không |
| Binary | O(log n) | Mảng đã sắp xếp |

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Binary search với mảng chưa sắp xếp
```python
# LỖI - mảng phải sắp xếp mới đúng!
nums = [5, 2, 8, 1]
binary_search(nums, 2)  # Kết quả có thể sai
```

---

### ❌ SAI THỨ 2 — Sai left/right boundary
```python
# Lỗi thường gặp
while left < right:  # Thay vì <=
    # Có thể bỏ sót phần tử cuối
```

---

### ❌ SAI THỨ 3 — mid tính sai với số âm
```python
# Python floor division OK
mid = (left + right) // 2  # Đúng
mid = (left + right) / 2   # Float!
```

---

## 8. Ghi nhớ nhanh

| Thuật toán | Độ phức tạp | Khi nào dùng |
|------------|-------------|--------------|
| Linear | O(n) | Mảng nhỏ, chưa sắp xếp |
| Binary | O(log n) | Mảng lớn, đã sắp xếp |

**MẸO NHỚ:** Binary = chia đôi → nhanh hơn nhiều.

---

## 9. Mini Test (3 câu)

**Câu 1:** Tìm 5 trong [1,2,3,4,5] với linear:
> Đáp án: index 4

**Câu 2:** Binary search yêu cầu gì?
> Đáp án: Mảng phải sắp xếp

**Câu 3:** Tìm 7 trong [1,3,5,7,9,11]:
> Đáp án: index 3

---

## 10. LeetCode Practice

### Bài tập: Tìm số trong mảng
**Yêu cầu:** Dùng binary search tìm số trong mảng đã sắp xếp

**Input:** 
```
7
1 3 5 7 9 11 13
```

**Output:** `3` (index của 7)

**✅ Đáp án:**
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

target = int(input())
arr = list(map(int, input().split()))
print(binary_search(arr, target))
```

---

## 11. Bonus Challenge

Tìm chỉ mục chèn (không cần chèn thật)

**Input:** `5 [1 3 5 7 9]`

**Output:** `2` (chỉ mục để chèn 5)

**✅ Đáp án:**
```python
def search_insert(nums, target):
    left, right = 0, len(nums)
    while left < right:
        mid = (left + right) // 2
        if nums[mid] < target:
            left = mid + 1
        else:
            right = mid
    return left

target = int(input())
nums = list(map(int, input().split()))
print(search_insert(nums, target))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 38 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 380 |
| **Mức độ** | Medium |