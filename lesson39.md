# Bài 39 — Sort (Sắp xếp)

---

## 1. Ôn tập
Bài 38 đã học Search. Giờ học các **thuật toán sắp xếp**.

---

## 2. Mục tiêu bài học
- Bubble Sort
- Selection Sort
- Insertion Sort
- Dùng sort có sẵn trong Python

---

## 3. Bubble Sort

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                # Hoán đổi
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr

nums = [64, 34, 25, 12, 22]
print(bubble_sort(nums))
```

**Output:**
```
[12, 22, 25, 34, 64]
```

**Trace:**
```
[64, 34, 25, 12, 22]
→ [34, 25, 12, 22, 64]
→ [25, 12, 22, 34, 64]
→ [12, 25, 22, 34, 64]
→ [12, 25, 22, 34, 64]
→ [12, 22, 25, 34, 64]
```

---

## 4. Selection Sort

```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_idx = i
        for j in range(i+1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        # Hoán đổi
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr
```

---

## 5. Python Sort có sẵn

```python
# sort() - sắp xếp tại chỗ
nums = [3, 1, 4, 1, 5]
nums.sort()
print(nums)  # [1, 1, 3, 4, 5]

# sorted() - trả về list mới
nums = [3, 1, 4]
sorted_nums = sorted(nums)
print(sorted_nums)  # [1, 3, 4]

# Sắp xếp giảm dần
nums.sort(reverse=True)
print(nums)  # [5, 4, 3, 1]
```

---

## 6. So sánh độ phức tạp

| Thuật toán | Best | Average | Worst |
|-----------|------|---------|-------|
| Bubble | O(n) | O(n²) | O(n²) |
| Selection | O(n²) | O(n²) | O(n²) |
| Python sort | O(n log n) | O(n log n) | O(n log n) |

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Sắp xếp dictionary
```python
d = {"b": 1, "a": 2}
# sort() không hoạt động trực tiếp
# Dùng sorted
sorted_items = sorted(d.items(), key=lambda x: x[1])
```

---

### ❌ SAI THỨ 2 — Gán sai
```python
nums = [3, 1, 2]
new_nums = nums.sort()  # LỖI! sort() trả về None
# Đúng
nums = [3, 1, 2]
nums.sort()
```

---

### ❌ SAI THỨ 3 — Sort tuple
```python
# Tuple không sort được tại chỗ
t = (3, 1, 2)
# t.sort() LỖI!

# Dùng sorted trả về list
sorted(t)  # [1, 2, 3]
```

---

## 8. Ghi nhớ nhanh

| Method | Ý nghĩa |
|--------|--------|
| `list.sort()` | Sắp xếp tại chỗ (in-place) |
| `sorted(list)` | Trả về list mới |
| `reverse=True` | Giảm dần |

**MẸO NHỚ:** sort() = sắp xếp tại chỗ. sorted() = tạo bản mới.

---

## 9. Mini Test (3 câu)

**Câu 1:** `[3, 1, 2].sort()` → ?
> Đáp án: `[1, 2, 3]`

**Câu 2:** sorted([3, 1, 2]) → ?
> Đáp án: Trả về `[1, 2, 3]`, không thay đổi gốc

**Câu 3:** sort(reverse=True) → ?
> Đáp án: Giảm dần

---

## 10. LeetCode Practice

### Bài tập: Sắp xếp danh sách sinh viên
**Yêu cầu:** Nhập tên và điểm, sắp xếp theo điểm giảm dần

**Input:**
```
3
An 85
Binh 90
Cuong 78
```

**Output:**
```
Binh 90
An 85
Cuong 78
```

**✅ Đáp án:**
```python
n = int(input())
students = []
for _ in range(n):
    ten, diem = input().split()
    students.append((ten, int(diem)))

students.sort(key=lambda x: x[1], reverse=True)
for ten, diem in students:
    print(ten, diem)
```

---

## 11. Bonus Challenge

Sắp xếp dict theo value

**Input:** `a 3 b 1 c 2`

**Output:** `b 1 c 2 a 3`

**✅ Đáp án:**
```python
pairs = input().split()
d = {pairs[i]: int(pairs[i+1]) for i in range(0, len(pairs), 2)}
sorted_d = sorted(d.items(), key=lambda x: x[1])
for k, v in sorted_d:
    print(k, v)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 39 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 390 |
| **Mức độ** | Medium |