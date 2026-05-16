# Bài 49 — Complexities (Độ phức tạp)

---

## 1. Ôn tập
Bài 48 đã học Patterns. Giờ học về **Big O Notation** — đo độ phức tạp.

---

## 2. Mục tiêu bài học
- Hiểu Big O là gì
- Các loại complexity phổ biến
- Đánh giá code
- Tối ưu hóa

---

## 3. Các loại Complexity

| Big O | Tên | Ví dụ |
|-------|-----|-------|
| O(1) | Constant | array[index] |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Loop qua mảng |
| O(n log n) | Linearithmic | Sort (merge, quick) |
| O(n²) | Quadratic | Loop lồng nhau |
| O(2^n) | Exponential | Recursion không tối ưu |
| O(n!) | Factorial | Permutations |

---

## 4. Ví dụ từng loại

```python
# O(1) - Constant
def get_first(arr):
    return arr[0]

# O(n) - Linear
def find_max(arr):
    max_val = arr[0]
    for x in arr:
        if x > max_val:
            max_val = x
    return max_val

# O(n²) - Quadratic
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]

# O(log n) - Logarithmic
def binary_search(arr, target):
    left, right = 0, len(arr)-1
    while left <= right:
        mid = (left+right)//2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

---

## 5. Space Complexity

```python
# O(1) - Không tạo thêm
def sum(arr):
    total = 0  # 1 biến
    return total

# O(n) - Tạo mảng mới
def double(arr):
    return [x*2 for x in arr]

# O(n) - Tạo dictionary
def count(arr):
    freq = {}  # n phần tử
    return freq
```

---

## 6. Tối ưu hóa

| Đang | Thành | Giảm |
|-------|-------|------|
| O(n²) | O(n log n) | Sort trước |
| O(n) | O(1) | Dùng hash |
| O(n) | O(log n) | Binary search |

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Nhầm O(n) và O(n²)
```python
# O(n) - một vòng lặp
for x in arr:
    print(x)

# O(n²) - hai vòng lặp lồng
for x in arr:
    for y in arr:
        print(x, y)
```

---

### ❌ SAI THỨ 2 — Quên cắt bớt hằng số
```python
# O(2n) = O(n) - bỏ hằng số
for i in range(n):
    print(i)
for i in range(n):
    print(i)
```

---

### ❌ SAI THỨ 3 — Complexity phụ thuộc input
```python
# Best case, Average case, Worst case
# Thường lấy Worst case
```

---

## 8. Ghi nhớ nhanh

| Complexity | Tăng trưởng | Tốt/xấu |
|------------|-------------|---------|
| O(1) | Hằng số | Tốt nhất |
| O(log n) | Log | Tốt |
| O(n) | Tuyến tính | Tốt |
| O(n²) | Bình phương | Xấu |
| O(2^n) | Mũ | Rất xấu |

**MẸO NHỚ:** Big O = "lớn nhất" → đo tốc độ tăng khi input lớn.

---

## 9. Mini Test (3 câu)

**Câu 1:** loop for trong for = ?
> Đáp án: O(n²)

**Câu 2:** Hash lookup = ?
> Đáp án: O(1)

**Câu 3:** Binary search = ?
> Đáp án: O(log n)

---

## 10. LeetCode Practice

### Bài tập: Đánh giá complexity
**Yêu cầu:** Nhận xét complexity của code

**Code:**
```python
for i in range(n):
    for j in range(n):
        print(i, j)
```

**Output:** `O(n²)`

**✅ Đáp án:**
```
Vòng lặp lồng nhau → O(n * n) = O(n²)
```

---

## 11. Bonus Challenge

So sánh các thuật toán

| Thuật toán | Time | Space |
|------------|------|-------|
| Bubble Sort | O(n²) | O(1) |
| Merge Sort | O(n log n) | O(n) |
| Quick Sort | O(n²) worst, O(n log n) avg | O(log n) |
| Binary Search | O(log n) | O(1) |
| Hash Table | O(1) avg | O(n) |

**✅ Đáp án:**
```
- Sort nhỏ: Bubble Sort (đơn giản)
- Sort lớn: Merge Sort (n log n)
- Tìm kiếm: Binary Search (log n)
- Tra cứu nhanh: Hash Table (1)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 49 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 490 |
| **Mức độ** | Medium |