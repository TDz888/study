# Bài 8 — Nested If (Điều kiện lồng nhau)

---

## 1. Ôn tập
Bài 7 đã học `elif` — kiểm tra nhiều điều kiện. Giờ học cách **lồng điều kiện**.

---

## 2. Mục tiêu bài học
- Hiểu nested if là gì
- Biết cách lồng điều kiện trong điều kiện
- Ứng dụng vào bài toán phân cấp
- Tránh lỗi khi dùng nested if

---

## 3. Code chính (có comment)

```python
# Kiểm tra tuổi và quyền bỏ phiếu
tuoi = 25
la_cong_dan = True

if tuoi >= 18:
    print("Du 18 tuoi")
    if la_cong_dan:
        print("Co quyen bo phieu")
    else:
        print("Khong phai cong dan")
else:
    print("Chua du 18 tuoi")
    print("Khong co quyen bo phieu")
```

**Output:**
```
Du 18 tuoi
Co quyen bo phieu
```

---

## 4. Trace chạy code

```
tuoi = 25, la_cong_dan = True

Bước 1: tuoi >= 18 ? → True (25 >= 18)
        → In "Du 18 tuoi"
        → Vào if bên trong

Bước 2: la_cong_dan ? → True
        → In "Co quyen bo phieu"
        → Kết thúc
```

**Sơ đồ:**
```
if tuoi >= 18:
    └── if la_cong_dan:  ← Lồng bên trong
    │       → "Co quyen bo phieu"
    └── else:
            → "Khong phai cong dan"
else:
    → "Chua du 18 tuoi"
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Thụt vào sai
```python
if tuoi >= 18:
    if la_cong_dan:
        print("Co quyen")  # OK
         print("Sai indent")  # LỖI!
```
**Vì sao sai:** Thụt vào phải đều 4 spaces

### ❌ Lỗi 2 — Lồng quá sâu
```python
if a:
    if b:
        if c:
            if d:  # Quá sâu, khó đọc
                print("...")
```
**Vì sao sai:** Khó đọc, nên dùng `elif` thay vì lồng quá 2-3 tầng

### ❌ Lỗi 3 — Điều kiện trùng lặp
```python
if x > 0:
    if x > 10:  # Thừa! Đã biết x > 0
        print("x > 10")
```
**Vì sao sai:** Điều kiện đã được kiểm tra ở trên

---

## 6. Ghi nhớ nhanh

| Khái niệm | Giải thích |
|-----------|------------|
| **Nested if** | If bên trong if — điều kiện trong điều kiện |
| **Indent** | Thụt vào 4 spaces — phải đúng |

**MẸO NHỚ:** Nested = lồng nhau như búp bê Nga. Mỗi lớp thụt vào 4 spaces.

---

## 7. Mini test (3 câu)

**Câu 1:** tuoi=15, co_bang= True → Output?
```python
if tuoi >= 18:
    if co_bang:
        print("Duoc thi")
    else:
        print("Chua thi")
else:
    print("Chua du tuoi")
```
> Đáp án: `Chua du tuoi`

**Câu 2:** Sửa lỗi indent:
```python
if x > 0:
if x > 10:  # Lỗi?
    print("x > 10")
```
> Đáp án: Thêm 4 spaces cho `if x > 10:`

**Câu 3:** x=12, y=5 → Output?
```python
if x > 10:
    print("A")
    if y > 10:
        print("B")
    else:
        print("C")
```
> Đáp án: `A` và `C`

---

## 8. LeetCode practice

**Bài tập:** Nhập điểm và số lần thi
- Điểm >= 5 → "Dat"
- Điểm < 5:
  - Lần thi 1 → "Thi lai"
  - Lần thi > 1 → "Hoc lai"

**Input:**
```
3
2
```

**Output:** `Hoc lai`

**Khung code:**
```python
diem = float(input())
lan_thi = int(input())
# Viết tiếp vào đây
```

**✅ Đáp án:**
```python
diem = float(input())
lan_thi = int(input())

if diem >= 5:
    print("Dat")
else:
    if lan_thi == 1:
        print("Thi lai")
    else:
        print("Hoc lai")
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Viết chương trình ATM đơn giản:
- Nhập số tiền
- Nếu < 100000 → "So tien khong hop le"
- Nếu >= 100000:
  - Nếu chia hết cho 50000 → "Rut duoc"
  - Nếu không → "So tien phai chia het cho 50000"

**Input:** `150000`

**Output:** `Rut duoc`

**✅ Đáp án:**
```python
so_tien = int(input())

if so_tien < 100000:
    print("So tien khong hop le")
else:
    if so_tien % 50000 == 0:
        print("Rut duoc")
    else:
        print("So tien phai chia het cho 50000")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 8 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 80 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 8!** 

Gõ **9** để học tiếp Bài 9 (And / Or / Not) →