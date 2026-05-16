# Bài 20 — Tuple

---

## 1. Ôn tập
Bài 19 đã học List Comprehension. Giờ học **Tuple** — kiểu dữ liệu giống list nhưng không thay đổi được.

---

## 2. Mục tiêu bài học
- Hiểu tuple là gì
- Biết cách tạo tuple
- Phân biệt tuple và list
- Ứng dụng tuple

---

## 3. Code chính (CORE LESSON)

```python
# Tạo tuple
colors = ("red", "green", "blue")
numbers = (1, 2, 3)
mixed = ("a", 1, True)

# Tuple 1 phần tử (cần dấu phẩy)
single = (5,)  # OK
not_tuple = (5)  # Đây là int, không phải tuple!

# Truy cập (giống list)
print(colors[0])   # red
print(colors[-1])  # blue

# Slicing
print(colors[0:2])  # ('red', 'green')

# Độ dài
print(len(colors))  # 3
```

**Output:**
```
red
blue
('red', 'green')
3
```

---

## 4. Tuple vs List

| Tuple | List |
|-------|------|
| `()` | `[]` |
| Không thay đổi được | Thay đổi được |
| Nhanh hơn | Chậm hơn |
| Dùng cho dữ liệu cố định | Dùng cho dữ liệu thay đổi |

```python
# Tuple không thể sửa
colors = ("red", "green", "blue")
# colors[0] = "yellow"  # LỖI! TypeError

# Nhưng có thể tạo tuple mới
colors = ("yellow", "green", "blue")
```

---

## 5. Các thao tác với Tuple

```python
# Count - Đếm
nums = (1, 2, 2, 3, 2)
print(nums.count(2))  # 3

# Index - Tìm vị trí
print(nums.index(3))  # 3

# unpack - Gán nhiều biến
a, b, c = (1, 2, 3)
print(a, b, c)  # 1 2 3

# Swap - Đổi chỗ
a, b = b, a  # Hoán đổi giá trị
```

---

## 6. Trace luồng chạy

```
colors = ("red", "green", "blue")

Unpacking:
a, b, c = colors
→ a = "red"
→ b = "green"
→ c = "blue"
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Tạo tuple 1 phần tử sai
```python
single = (5)   # LỖI! Đây là int
single = (5,)  # ĐÚNG! Cần dấu phẩy
```

---

### ❌ SAI THỨ 2 — Sửa tuple
```python
t = (1, 2, 3)
t[0] = 0  # LỖI! Tuple immutable
```

---

### ❌ SAI THỨ 3 — Nhầm () và []
```python
t = (1, 2, 3)  # Tuple
lst = [1, 2, 3]  # List
t.append(4)  # LỖI!
lst.append(4)  # OK
```

---

## 8. Ghi nhớ nhanh

| Đặc điểm | Tuple |
|----------|-------|
| Syntax | `(a, b, c)` |
| Thay đổi | Không (immutable) |
| Truy cập | `t[0]` |
| Unpack | `a, b = t` |
| Count | `t.count(x)` |
| Index | `t.index(x)` |

**MẸO NHỚ:** Tuple = "tuple" = nhóm → dữ liệu nhóm lại, không thay đổi (như tọa độ GPS).

---

## 9. Mini Test (3 câu)

**Câu 1:** `(1, 2, 3)[1]` = ?
> Đáp án: `2`

**Câu 2:** Tuple có thể thêm phần tử không?
> Đáp án: Không! Tuple immutable.

**Câu 3:** Unpack `("a", "b", "c")`:
```python
x, y, z = ("a", "b", "c")
# x="a", y="b", z="c"
```

---

## 10. LeetCode Practice

### Bài tập: Swap 2 biến
**Yêu cầu:** Nhập 2 số, đổi chỗ không dùng biến trung gian

**Input:** `3 5`

**Output:** `5 3`

**✅ Đáp án:**
```python
a, b = map(int, input().split())
a, b = b, a
print(a, b)
```

---

## 11. Bonus Challenge

Trả về nhiều giá trị từ function (sử dụng tuple)

**Input:** `5 3`

**Output:**
```
Hieu = 2
Thuong = 1
Du = 2
```

**✅ Đáp án:**
```python
def tinh(a, b):
    return a + b, a - b, a * b, a / b

x, y = map(int, input().split())
cong, tru, nhan, chia = tinh(x, y)
print(f"Hieu = {tru}")
print(f"Thuong = {nhan}")
print(f"Du = {int(chia)}")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 20 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 200 |
| **Mức độ** | Easy |