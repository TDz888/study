# Bài 3 — Toán Tử (Operators)

---

## 1. Ôn tập
Bài 2 đã học biến. Biến lưu dữ liệu, có thể dùng `print()` để in biến ra.

---

## 2. Mục tiêu bài học
- Biết các phép toán cơ bản: +, -, *, /
- Hiểu phép chia lấy dư (%) và chia lấy phần nguyên (//)
- Sử dụng toán tử gán: =, +=, -=
- Tính toán với biến

---

## 3. Code chính (có comment)

```python
# Các phép toán cơ bản
a = 10
b = 3

cong = a + b       # Cộng: 13
tru  = a - b       # Trừ: 7
nhan = a * b       # Nhân: 30
chia = a / b       # Chia: 3.333...

# Phép chia lấy phần nguyên
chia_nguyen = a // b   # 3

# Phép chia lấy dư
chia_du = a % b       # 1

# Lũy thừa
mu = a ** b          # 10^3 = 1000

print("Cong:", cong)
print("Tru:", tru)
print("Nhan:", nhan)
print("Chia:", chia)
print("Chia nguyen:", chia_nguyen)
print("Chia du:", chia_du)
print("Luy thua:", mu)
```

**Output:**
```
Cong: 13
Tru: 7
Nhan: 30
Chia: 3.3333333333333335
Chia nguyen: 3
Chia du: 1
Luy thua: 1000
```

---

## 4. Trace chạy code

```
a = 10, b = 3

cong = 10 + 3 → 13
tru  = 10 - 3 → 7
nhan = 10 * 3 → 30
chia = 10 / 3 → 3.333...

Chia lấy phần nguyên:
  10 // 3 = 3 (bỏ phần thập phân)

Chia lấy dư:
  10 % 3 = 1 (10 = 3*3 + 1, dư 1)
```

**MẸO chia dư (%):**
```
10 % 3 = 1  (vì 10 chia 3 được 3, dư 1)
15 % 4 = 3  (vì 15 chia 4 được 3, dư 3)
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Nhầm lẫn / và //
```python
print(10 / 3)   # Kết quả: 3.333... (số thập phân)
print(10 // 3)  # Kết quả: 3 (số nguyên)
```
**Vì sao sai:** `/` chia thập phân, `//` chia lấy phần nguyên

### ❌ Lỗi 2 — Nhầm lẫn % và /
```python
# % là chia lấy DƯ, không phải chia thường
print(10 % 3)   # 1 (dư)
print(10 / 3)   # 3.333... (chia thường)
```

### ❌ Lỗi 3 — Ép kiểu tự động
```python
a = 10
b = "3"
# print(a + b)  # LỖI! Không cộng được int + string
```

---

## 6. Ghi nhớ nhanh

| Toán tử | Ý nghĩa | Ví dụ | Kết quả |
|---------|---------|-------|---------|
| `+` | Cộng | `5 + 3` | `8` |
| `-` | Trừ | `5 - 3` | `2` |
| `*` | Nhân | `5 * 3` | `15` |
| `/` | Chia | `5 / 3` | `1.67` |
| `//` | Chia lấy nguyên | `5 // 3` | `1` |
| `%` | Chia lấy dư | `5 % 3` | `2` |
| `**` | Lũy thừa | `2 ** 3` | `8` |

**MẸO NHỚ:**
- `/` = chia thập phân (có phần dư)
- `//` = chia nguyên (bỏ phần dư)
- `%` = lấy phần dư thôi

---

## 7. Mini test (3 câu)

**Câu 1:** `17 % 5 = ?`
> Đáp án: `2` (17 chia 5 được 3, dư 2)

**Câu 2:** `17 // 5 = ?`
> Đáp án: `3` (17 chia 5 được 3, bỏ dư)

**Câu 3:** Tính: `2 ** 5`
> Đáp án: `32` (2 mũ 5 = 2×2×2×2×2)

---

## 8. LeetCode practice

**Bài tập:** Cho hình chữ nhật:
- Chiều dài: 15
- Chiều rộng: 8

Tính:
- Chu vi: (dài + rộng) × 2
- Diện tích: dài × rộng

**Input:** (không có input)

**Output:**
```
Chu vi: 46
Dien tich: 120
```

**Khung code:**
```python
dai = 15
rong = 8

# Tính chu vi và diện tích
```

**✅ Đáp án:**
```python
dai = 15
rong = 8

chu_vi = (dai + rong) * 2
dien_tich = dai * rong

print("Chu vi:", chu_vi)
print("Dien tich:", dien_tich)
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Kiểm tra số chẵn/lẻ:
- Số 42: chia 2 dư 0 → CHẴN
- Số 37: chia 2 dư 1 → LẺ

**Output:**
```
42 la so chan
37 la so le
```

**✅ Đáp án:**
```python
so1 = 42
so2 = 37

if so1 % 2 == 0:
    print(so1, "la so chan")
else:
    print(so1, "la so le")

if so2 % 2 == 0:
    print(so2, "la so chan")
else:
    print(so2, "la so le")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 3 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 30 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 3!** 

Gõ **4** để học tiếp Bài 4 (Input từ bàn phím) →