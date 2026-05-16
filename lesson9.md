# Bài 9 — And / Or / Not

---

## 1. Ôn tập
Bài 8 đã học nested if. Giờ học cách **kết hợp điều kiện** với `and`, `or`, `not`.

---

## 2. Mục tiêu bài học
- Hiểu `and` — TẤT CẢ điều kiện phải đúng
- Hiểu `or` — ÍT NHẤT 1 điều kiện đúng
- Hiểu `not` — ĐẢO NGƯỢC kết quả
- Ứng dụng vào bài toán thực tế

---

## 3. Code chính (có comment)

```python
# AND - Tất cả phải đúng
x = 10
if x > 5 and x < 15:
    print("x nam trong khoang 5-15")

# OR - Ít nhất 1 đúng
tuoi = 17
if tuoi < 18 or tuoi > 60:
    print("Duoc giam gia")

# NOT - Đảo ngược
x = 5
if not x > 10:
    print("x khong lon hon 10")
```

**Output:**
```
x nam trong khoang 5-15
Duoc giam gia
x khong lon hon 10
```

---

## 4. Trace chạy code

**Bảng chân trị:**

### AND
| A | B | A and B |
|---|---|---------|
| True | True | True |
| True | False | False |
| False | True | False |
| False | False | False |

### OR
| A | B | A or B |
|---|---|-------|
| True | True | True |
| True | False | True |
| False | True | True |
| False | False | False |

### NOT
| A | not A |
|---|-------|
| True | False |
| False | True |

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Nhầm and và or
```python
# Sai - muốn xem xét cả 2 điều kiện
if x > 5 or x < 15:  # Luôn đúng!
    print("OK")

# Đúng - cả 2 phải đúng
if x > 5 and x < 15:
    print("OK")
```

### ❌ Lỗi 2 — Dùng | và & thay vì or và and
```python
# Sai - Python không hiểu
if x > 5 | x < 15:
    print("OK")

# Đúng
if x > 5 or x < 15:
    print("OK")
```

### ❌ Lỗi 3 — Quên đóng ngoặc với not
```python
if not (x > 10):  # Nên có ngoặc
    print("OK")
```

---

## 6. Ghi nhớ nhanh

| Toán tử | Ý nghĩa | Ghi nhớ |
|---------|---------|---------|
| `and` | VÀ — tất cả đúng | "A và B đều đúng" |
| `or` | HOẶC — ít nhất 1 đúng | "A hoặc B đúng" |
| `not` | KHÔNG — đảo ngược | "Không phải A" |

**MẸO NHỚ:**
- `and`: như đi qua 2 cổng, cổng nào khóa cũng không vào được
- `or`: như xin việc, chỉ cần 1 công ty nhận là được

---

## 7. Mini test (3 câu)

**Câu 1:** `True and False = ?`
> Đáp án: `False`

**Câu 2:** `True or False = ?`
> Đáp án: `True`

**Câu 3:** Đoán output:
```python
x = 5
if (x > 3) and (x < 10) and (x % 2 == 1):
    print("OK")
```
> Đáp án: `OK` (5 > 3, 5 < 10, 5 lẻ đều đúng)

---

## 8. LeetCode practice

**Bài tập:** Nhập 3 cạnh a, b, c. Kiểm tra:
- Cả 3 cạnh > 0
- a + b > c VÀ a + c > b VÀ b + c > a
→ "Tam giac hop le"

**Input:**
```
3
4
5
```

**Output:** `Tam giac hop le`

**Khung code:**
```python
a = float(input())
b = float(input())
c = float(input())
# Viết tiếp vào đây
```

**✅ Đáp án:**
```python
a = float(input())
b = float(input())
c = float(input())

if a > 0 and b > 0 and c > 0 and (a + b > c) and (a + c > b) and (b + c > a):
    print("Tam giac hop le")
else:
    print("Khong hop le")
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Viết chương trình kiểm tra đăng nhập:
- Tài khoản: "admin", Mật khẩu: "123456"
- Hoặc tài khoản: "user", Mật khẩu: "password"

**Input:**
```
admin
123456
```

**Output:** `Dang nhap thanh cong`

**✅ Đáp án:**
```python
user = input()
passw = input()

if (user == "admin" and passw == "123456") or (user == "user" and passw == "password"):
    print("Dang nhap thanh cong")
else:
    print("Dang nhap that bai")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 9 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 90 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 9!** 

Gõ **10** để học tiếp Bài 10 (Vòng lặp For) →