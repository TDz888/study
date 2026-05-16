# Bài 19 — List Comprehension

---

## 1. Ôn tập
Bài 18 đã học duyệt list bằng for. Giờ học cách **tạo list ngắn gọn** với comprehension.

---

## 2. Mục tiêu bài học
- Hiểu list comprehension là gì
- Biết cách viết ngắn gọn với `[expr for x in list]`
- Kết hợp với điều kiện

---

## 3. Code chính (CORE LESSON)

```python
# Cách thông thường
squares = []
for i in range(1, 6):
    squares.append(i ** 2)
print(squares)  # [1, 4, 9, 16, 25]

# List comprehension
squares = [i ** 2 for i in range(1, 6)]
print(squares)  # [1, 4, 9, 16, 25]
```

**Output:**
```
[1, 4, 9, 16, 25]
[1, 4, 9, 16, 25]
```

---

## 4. Các dạng Comprehension

```python
# Nhân đôi mỗi phần tử
nums = [1, 2, 3, 4, 5]
doubled = [x * 2 for x in nums]
print(doubled)  # [2, 4, 6, 8, 10]

# Lọc số chẵn
evens = [x for x in nums if x % 2 == 0]
print(evens)  # [2, 4]

# Lọc và biến đổi
upper = [s.upper() for s in ["hello", "world"]]
print(upper)  # ['HELLO', 'WORLD']
```

---

## 5. Cú pháp

```
[biểu_thức for phần_tử in list]
[biểu_thức for phần_tử in list if điều_kiện]
[biểu_thức if điều_kiện else biểu_thức for phần_tử in list]
```

**Ví dụ với if/else:**
```python
nums = [1, 2, 3, 4, 5]
result = ["chan" if x % 2 == 0 else "le" for x in nums]
print(result)  # ['le', 'chan', 'le', 'chan', 'le']
```

---

## 6. Trace luồng chạy

```
[x ** 2 for x in range(1, 4)]

Bước 1: x = 1 → 1 ** 2 = 1
Bước 2: x = 2 → 2 ** 2 = 4
Bước 3: x = 3 → 3 ** 2 = 9

Kết quả: [1, 4, 9]
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Quên []
```python
squares = x ** 2 for x in range(5)  # LỖI!
# Đúng
squares = [x ** 2 for x in range(5)]
```

---

### ❌ SAI THỨ 2 — Nhầm vị trí if
```python
# Sai - if ở cuối là lọc
nums = [x for x in range(10) if x % 2 == 0]  # Lọc số chẵn

# Đúng - if/else ở đầu là biến đổi
nums = [x if x > 5 else 0 for x in range(10)]  # Nếu > 5 giữ, không thì 0
```

---

### ❌ SAI THỨ 3 — Comprehension quá phức tạp
```python
# Đừng viết thế này!
result = [[x for x in range(y)] for y in range(3) if y > 0 if x % 2 == 0]
# Nên tách ra nhiều bước
```

---

## 8. Ghi nhớ nhanh

| Cú pháp | Kết quả |
|---------|---------|
| `[x*2 for x in lst]` | Nhân đôi |
| `[x for x in lst if x>0]` | Lọc |
| `[x if x>0 else 0 for x in lst]` | Lọc + thay thế |

**MẸO NHỚ:** `[x for x in list]` = "với mỗi x trong list, thêm x vào"

---

## 9. Mini Test (3 câu)

**Câu 1:** `[x**2 for x in [1,2,3]]` = ?
> Đáp án: `[1, 4, 9]`

**Câu 2:** `[x for x in [1,2,3,4] if x>2]` = ?
> Đáp án: `[3, 4]`

**Câu 3:** Viết comprehension lọc số âm:
```python
nums = [-1, 2, -3, 4]
positive = [x for x in nums if x > 0]  # [2, 4]
```

---

## 10. LeetCode Practice

### Bài tập: Bình phương số lẻ
**Yêu cầu:** Nhập list, trả về bình phương của các số lẻ

**Input:** `1 2 3 4 5`

**Output:** `[1, 9, 25]`

**✅ Đáp án:**
```python
nums = list(map(int, input().split()))
result = [x**2 for x in nums if x % 2 != 0]
print(result)
```

---

## 11. Bonus Challenge

Viết comprehension tạo bảng cửu chương 5
**Output:** `[5, 10, 15, 20, 25, 30, 35, 40, 45, 50]`

**✅ Đáp án:**
```python
result = [5 * i for i in range(1, 11)]
print(result)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 19 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 190 |
| **Mức độ** | Medium |