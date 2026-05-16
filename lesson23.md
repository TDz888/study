# Bài 23 — Set

---

## 1. Ôn tập
Bài 22 đã học dict methods. Giờ học **Set** — tập hợp các phần tử không trùng lặp.

---

## 2. Mục tiêu bài học
- Hiểu set là gì
- Biết cách tạo set
- Các phép toán tập hợp: union, intersection, difference
- Ứng dụng: loại bỏ trùng lặp

---

## 3. Code chính (CORE LESSON)

```python
# Tạo set
fruits = {"apple", "banana", "cherry"}
numbers = {1, 2, 3}

# Set không có thứ tự
print(fruits)  # {'cherry', 'banana', 'apple'}

# Không trùng lặp
s = {1, 2, 2, 3, 3, 3}
print(s)  # {1, 2, 3}

# Loại bỏ trùng lặp
nums = [1, 2, 2, 3, 1, 4, 3]
unique = set(nums)
print(unique)  # {1, 2, 3, 4}
```

**Output:**
```
{'cherry', 'banana', 'apple'}
{1, 2, 3}
{1, 2, 3, 4}
```

---

## 4. Các phép toán Set

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

# Union (hợp) - Tất cả
print(a | b)  # {1, 2, 3, 4, 5, 6}
print(a.union(b))

# Intersection (giao) - Chung
print(a & b)  # {3, 4}
print(a.intersection(b))

# Difference (hiệu) - Chỉ có trong a
print(a - b)  # {1, 2}
print(a.difference(b))

# Symmetric difference - Không chung
print(a ^ b)  # {1, 2, 5, 6}
```

---

## 5. Thêm/Xóa

```python
s = {1, 2, 3}

# Thêm
s.add(4)
print(s)  # {1, 2, 3, 4}

# Thêm nhiều
s.update([5, 6])
print(s)  # {1, 2, 3, 4, 5, 6}

# Xóa (báo lỗi nếu không tồn tại)
s.remove(1)
print(s)  # {2, 3, 4, 5, 6}

# Xóa (không báo lỗi)
s.discard(10)  # Không có 10 vẫn OK

# Pop - Xóa ngẫu nhiên 1 phần tử
x = s.pop()
print(x, s)
```

---

## 6. Trace luồng chạy

```
a = {1, 2, 3}
b = {2, 3, 4}

a | b (union)
       ↓
Gộp tất cả, loại bỏ trùng
→ {1, 2, 3, 4}

a & b (intersection)
       ↓
Lấy phần tử chung
→ {2, 3}
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Truy cập bằng index
```python
s = {1, 2, 3}
print(s[0])  # LỖI! Set không có index
```

---

### ❌ SAI THỨ 2 — Set không chứa list
```python
# LỖI! Set chỉ chứa immutable
s = {[1, 2]}  # TypeError

# Được
s = {(1, 2)}  # Tuple OK
```

---

### ❌ SAI THỨ 3 — Nhầm & và and
```python
# Sai
a & b  # Bitwise AND (số)

# Đúng cho set
a.intersection(b)
```

---

## 8. Ghi nhớ nhanh

| Phép toán | Ký hiệu | Method |
|-----------|---------|--------|
| Hợp | `\|` | `.union()` |
| Giao | `&` | `.intersection()` |
| Hiệu | `-` | `.difference()` |
| Xor | `^` | `.symmetric_difference()` |

**MẸO NHỚ:** Set = tập hợp. Không trùng lặp, không có thứ tự.

---

## 9. Mini Test (3 câu)

**Câu 1:** `{1, 2, 2, 3}` = ?
> Đáp án: `{1, 2, 3}` (loại trùng)

**Câu 2:** `{1, 2, 3} & {2, 3, 4}` = ?
> Đáp án: `{2, 3}`

**Câu 3:** `{1, 2} - {2, 3}` = ?
> Đáp án: `{1}`

---

## 10. LeetCode Practice

### Bài tập: Tìm phần tử chung
**Yêu cầu:** Nhập 2 list, in phần tử xuất hiện ở cả 2

**Input:**
```
1 2 3 4
3 4 5 6
```

**Output:** `3 4`

**✅ Đáp án:**
```python
set1 = set(map(int, input().split()))
set2 = set(map(int, input().split()))
common = set1 & set2
print(" ".join(map(str, sorted(common))))
```

---

## 11. Bonus Challenge

Tìm phần tử chỉ xuất hiện 1 lần trong cả 2 list

**Input:**
```
1 2 3 4
3 4 5 6
```

**Output:** `1 2 5 6`

**✅ Đáp án:**
```python
set1 = set(map(int, input().split()))
set2 = set(map(int, input().split()))
diff = set1 ^ set2
print(" ".join(map(str, sorted(diff))))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 23 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 230 |
| **Mức độ** | Medium |