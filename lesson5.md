# Bài 5 — So sánh và Boolean

---

## 1. Ôn tập
Bài 4 đã học `input()` để nhận dữ liệu. Giờ học cách **so sánh** dữ liệu.

---

## 2. Mục tiêu bài học
- Hiểu Boolean là gì (True / False)
- Biết các toán tử so sánh: ==, !=, >, <, >=, <=
- Phân biệt `=` và `==`
- Sử dụng so sánh trong điều kiện

---

## 3. Code chính (có comment)

```python
# Boolean - Giá trị đúng/sai
x = True   # Đúng
y = False  # Sai

print(True)
print(False)

# So sánh số
print(5 == 5)   # True (bằng)
print(5 != 3)   # True (không bằng)
print(5 > 3)    # True (lớn hơn)
print(5 < 3)    # False (nhỏ hơn)
print(5 >= 5)   # True (lớn hơn hoặc bằng)
print(5 <= 4)    # False (nhỏ hơn hoặc bằng)
```

**Output:**
```
True
False
True
True
True
False
True
False
```

---

## 4. Trace chạy code

```
5 == 5 → True (5 đúng bằng 5)
5 != 3 → True (5 đúng khác 3)
5 > 3  → True (5 đúng lớn hơn 3)
5 < 3  → False (5 không nhỏ hơn 3)

Lưu ý: = là GÁN, == là SO SÁNH
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Nhầm = và ==
```python
# Sai - đang gán, không phải so sánh
if x = 5:   # LỖI!
    print("x bang 5")

# Đúng - so sánh
if x == 5:
    print("x bang 5")
```

**Vì sao sai:** `=` là gán giá trị, `==` là so sánh

### ❌ Lỗi 2 — So sánh string sai
```python
print("hello" == "Hello")  # False (phân biệt hoa thường)
print("abc" == "abc")      # True
```

### ❌ Lỗi 3 — So sánh float
```python
print(0.1 + 0.2 == 0.3)  # False! (lỗi số thập phân)
# Nên dùng:
print(abs(0.1 + 0.2 - 0.3) < 0.0001)  # True
```

---

## 6. Ghi nhớ nhanh

| Toán tử | Ý nghĩa | Ví dụ |
|---------|---------|-------|
| `==` | Bằng | `5 == 5` → True |
| `!=` | Khác | `5 != 3` → True |
| `>` | Lớn hơn | `5 > 3` → True |
| `<` | Nhỏ hơn | `5 < 3` → False |
| `>=` | Lớn hơn hoặc bằng | `5 >= 5` → True |
| `<=` | Nhỏ hơn hoặc bằng | `5 <= 4` → False |

| Từ khóa | Ý nghĩa |
|----------|---------|
| `True` | Đúng (1) |
| `False` | Sai (0) |

**MẸO NHỚ:** `=` là GÁN (góc phải gán sang trái), `==` là SO SÁNH (so sánh 2 bên).

---

## 7. Mini test (3 câu)

**Câu 1:** `10 >= 10` cho kết quả gì?
> Đáp án: `True`

**Câu 2:** Sửa lỗi:
```python
if x = 10:
    print("x bang 10")
```
> Đáp án: `if x == 10:`

**Câu 3:** `5 != 5` cho kết quả gì?
> Đáp án: `False`

---

## 8. LeetCode practice

**Bài tập:** Nhập tuổi, kiểm tra có đủ 18 tuổi chưa

**Input:** `20`

**Output:**
```
Du tuoi
```

**Input:** `15`

**Output:**
```
Chua du tuoi
```

**Khung code:**
```python
tuoi = int(input())
# Viết tiếp vào đây
```

**✅ Đáp án:**
```python
tuoi = int(input())
if tuoi >= 18:
    print("Du tuoi")
else:
    print("Chua du tuoi")
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Kiểm tra số dương/âm/không:
- Nếu > 0 → "So duong"
- Nếu < 0 → "So am"
- Nếu = 0 → "So khong"

**Input:** `-5`

**Output:** `So am`

**✅ Đáp án:**
```python
n = int(input())
if n > 0:
    print("So duong")
elif n < 0:
    print("So am")
else:
    print("So khong")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 5 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 50 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 5!** 

Gõ **6** để học tiếp Bài 6 (Câu lệnh If / Else) →