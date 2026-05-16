# Bài 25 — Return Statement

---

## 1. Ôn tập
Bài 24 đã học định nghĩa và gọi hàm. Giờ học **return** — trả kết quả từ hàm.

---

## 2. Mục tiêu bài học
- Hiểu return là gì
- Biết cách trả kết quả từ hàm
- Phân biệt print và return
- Ứng dụng return vào bài toán

---

## 3. Code chính (CORE LESSON)

```python
# Hàm có return
def cong(a, b):
    return a + b

ket_qua = cong(5, 3)
print(ket_qua)  # 8

# Dùng kết quả trong biểu thức
print(cong(5, 3) * 2)  # 16
```

**Output:**
```
8
16
```

---

## 4. Print vs Return

```python
# Print - chỉ hiển thị, không trả kết quả
def p_cong(a, b):
    print(a + b)

p_cong(5, 3)  # In ra: 8
ket_qua = p_cong(5, 3)  # ket_qua = None!

# Return - trả kết quả để dùng tiếp
def r_cong(a, b):
    return a + b

ket_qua = r_cong(5, 3)  # ket_qua = 8
```

---

## 5. Return nhiều giá trị

```python
def tinh(a, b):
    tong = a + b
    hieu = a - b
    return tong, hieu

ket_qua = tinh(10, 5)
print(ket_qua)  # (15, 5)

# Unpack
tong, hieu = tinh(10, 5)
print(f"Tong: {tong}, Hieu: {hieu}")
```

**Output:**
```
(15, 5)
Tong: 15, Hieu: 5
```

---

## 6. Trace luồng chạy

```
def cong(a, b):
    return a + b

ket_qua = cong(5, 3)
       ↓
a = 5, b = 3
       ↓
tinh a + b = 8
       ↓
return 8 → lưu vào ket_qua
       ↓
ket_qua = 8
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Quên return
```python
def cong(a, b):
    a + b  # LỖI! Quên return

ket_qua = cong(5, 3)
print(ket_qua)  # None
```

---

### ❌ SAI THỨ 2 — Nhầm print và return
```python
# Sai - muốn dùng kết quả
def tinh(a, b):
    print(a + b)  # Không trả kết quả

ket_qua = tinh(5, 3) + 10  # LỖI! None + 10
```

---

### ❌ SAI THỨ 3 — Return sau logic
```python
def kiem_tra(x):
    if x > 0:
        return True
    # Không return ở đây → có thể None

# Đúng - luôn có return
def kiem_tra(x):
    if x > 0:
        return True
    return False
```

---

## 8. Ghi nhớ nhanh

| Từ khóa | Hành động |
|----------|-----------|
| `print(x)` | Hiển thị x, KHÔNG trả kết quả |
| `return x` | Trả x ra bên ngoài, CÓ thể dùng tiếp |

**MẸO NHỚ:** `return` = gửi hàng về kho. `print` = đem hàng ra trưng bày.

---

## 9. Mini Test (3 câu)

**Câu 1:** Đoán kết quả:
```python
def tinh(x):
    return x * 2

ket_qua = tinh(5)
print(ket_qua)
```
> Đáp án: `10`

**Câu 2:** `tinh(5) + 3` = ?
> Đáp án: `13` (10 + 3)

**Câu 3:** `tinh(5)` in ra gì nếu dùng print thay vì return:
> Đáp án: `10` (hiển thị) nhưng không trả kết quả cho biến

---

## 10. LeetCode Practice

### Bài tập: Hàm tính diện tích hình chữ nhật
**Yêu cầu:** Viết hàm `dien_tich(dai, rong)` trả về diện tích

**Input:** `5 3`

**Output:** `15`

**✅ Đáp án:**
```python
def dien_tich(dai, rong):
    return dai * rong

d, r = map(int, input().split())
print(dien_tich(d, r))
```

---

## 11. Bonus Challenge

Viết hàm trả về cả diện tích và chu vi hình chữ nhật

**Input:** `5 3`

**Output:**
```
Dien tich: 15
Chu vi: 16
```

**✅ Đáp án:**
```python
def hinh_chu_nhat(dai, rong):
    dt = dai * rong
    cv = (dai + rong) * 2
    return dt, cv

d, r = map(int, input().split())
dt, cv = hinh_chu_nhat(d, r)
print(f"Dien tich: {dt}")
print(f"Chu vi: {cv}")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 25 / 2000 |
| **Chapter** | 3 (Functions) |
| **XP** | 250 |
| **Mức độ** | Easy |