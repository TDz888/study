# Bài 17 — List Methods (P1)

---

## 1. Ôn tập
Bài 16 đã học tạo list, thêm/sửa/xóa. Giờ học các **phương thức** của list.

---

## 2. Mục tiêu bài học
- Học method: sort, reverse, count, index
- Biết cách sắp xếp list
- Tìm kiếm trong list

---

## 3. Code chính (có comment)

### Sort - Sắp xếp
```python
# Sort tăng dần
numbers = [3, 1, 4, 1, 5, 9, 2]
numbers.sort()
print(numbers)  # [1, 1, 2, 3, 4, 5, 9]

# Sort giảm dần
numbers.sort(reverse=True)
print(numbers)  # [9, 5, 4, 3, 2, 1, 1]
```

### Reverse - Đảo ngược
```python
numbers = [1, 2, 3]
numbers.reverse()
print(numbers)  # [3, 2, 1]
```

### Count và Index
```python
# Count - Đếm số lần xuất hiện
numbers = [1, 2, 2, 3, 2, 4]
print(numbers.count(2))  # 3

# Index - Tìm vị trí đầu tiên
fruits = ["apple", "banana", "cherry"]
print(fruits.index("banana"))  # 1
```

### Các method khác
```python
# Copy - Sao chép list (độc lập)
a = [1, 2, 3]
b = a.copy()
print(b)  # [1, 2, 3]

# Extend - Nối list
a = [1, 2]
b = [3, 4]
a.extend(b)
print(a)  # [1, 2, 3, 4]

# Clear - Xóa tất cả
a = [1, 2, 3]
a.clear()
print(a)  # []

# Pop - Xóa và trả về phần tử cuối
a = [1, 2, 3]
x = a.pop()
print(x, a)  # 3 [1, 2]
```

---

## 4. Trace chạy code

```
numbers = [3, 1, 4, 1, 5]
numbers.sort()
       ↓
So sánh từng cặp và hoán đổi vị trí
Sắp xếp từ nhỏ đến lớn
→ [1, 1, 3, 4, 5]
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Sort trả về None
```python
# LỖI! sort() thay đổi list, trả về None
a = [3, 1, 2]
b = a.sort()
print(b)  # None!

# ✅ Sửa
a = [3, 1, 2]
a.sort()
print(a)  # [1, 2, 3]
```

### ❌ Lỗi 2 — Sao chép sai cách
```python
# LỖI! Gán trực tiếp = cùng tham chiếu
a = [1, 2]
b = a
b[0] = 99
print(a)  # [99, 2] - a cũng đổi!

# ✅ Sửa
a = [1, 2]
b = a.copy()  # Hoặc b = a[:]
b[0] = 99
print(a)  # [1, 2] - a giữ nguyên
```

### ❌ Lỗi 3 — Index phần tử không tồn tại
```python
# LỖI! ValueError
fruits = ["apple", "banana"]
print(fruits.index("orange"))  # ValueError!

# ✅ Kiểm tra trước
if "orange" in fruits:
    print(fruits.index("orange"))
```

---

## 6. Ghi nhớ nhanh

| Method | Ý nghĩa |
|--------|---------|
| `.sort()` | Sắp xếp tăng dần |
| `.sort(reverse=True)` | Sắp xếp giảm dần |
| `.reverse()` | Đảo ngược |
| `.count(x)` | Đếm số lần xuất hiện |
| `.index(x)` | Vị trí của x (lỗi nếu không có) |
| `.copy()` | Sao chép list |
| `.extend(lst)` | Nối list |
| `.clear()` | Xóa tất cả |
| `.pop()` | Xóa và trả về cuối |

**MẸO NHỚ:** `.sort()` thay đổi list gốc, `sorted()` tạo list mới.

---

## 7. Mini test (3 câu)

**Câu 1:** `[3, 1, 2].sort()` → ?
> Đáp án: `[1, 2, 3]` (thay đổi trực tiếp)

**Câu 2:** `[1, 2, 3, 2].count(2)` = ?
> Đáp án: `2`

**Câu 3:** Sao chép list `[1, 2]` thành biến mới?
> Đáp án: `b = a.copy()` hoặc `b = a[:]`

---

## 8. LeetCode Practice

### Bài tập: Tìm max/min
**Yêu cầu:** Nhập 5 số, in số lớn nhất và nhỏ nhất

**Input:** `3 5 1 9 2`

**Output:**
```
Max: 9
Min: 1
```

**✅ Đáp án:**
```python
numbers = list(map(int, input().split()))
numbers.sort()
print("Max:", numbers[-1])
print("Min:", numbers[0])
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Xóa tất cả số chẵn trong list

**Input:** `[1, 2, 3, 4, 5, 6, 7, 8]`

**Output:** `[1, 3, 5, 7]`

**✅ Đáp án:**
```python
lst = [1, 2, 3, 4, 5, 6, 7, 8]
lst = [x for x in lst if x % 2 != 0]
print(lst)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 17 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 170 (+10 XP khi hoàn thành) |
| **Level** | Beginner |

---

**🎉 Bạn đã hoàn thành Bài 17!**

Gõ **18** để học tiếp Bài 18 (List Methods P2) →