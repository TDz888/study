# Bài 7 — Elif (Nhiều điều kiện)

---

## 1. Ôn tập
Bài 6 đã học `if/else` — rẽ 2 nhánh. Giờ mở rộng ra nhiều nhánh với `elif`.

---

## 2. Mục tiêu bài học
- Hiểu `elif` là gì
- Biết cách dùng nhiều điều kiện liên tiếp
- Phân biệt `if/elif/else`
- Ứng dụng vào bài toán thực tế

---

## 3. Code chính (có comment)

```python
# Xếp loại điểm
diem = 8

if diem >= 9:
    print("Xuat sac")
elif diem >= 8:
    print("Gioi")
elif diem >= 6.5:
    print("Kha")
elif diem >= 5:
    print("Trung binh")
else:
    print("Yeu")
```

**Output:**
```
Gioi
```

---

## 4. Trace chạy code

```
diem = 8

Kiểm tra 1: diem >= 9 ? → 8 >= 9 → False (sai)
Kiểm tra 2: diem >= 8 ? → 8 >= 8 → True (đúng!)
→ In ra: "Gioi"
→ DỪNG, không kiểm tra tiếp
```

**Lưu ý quan trọng:** Nếu đúng 1 điều kiện → chỉ chạy code đó → KHÔNG kiểm tra tiếp.

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Điều kiện không theo thứ tự
```python
diem = 10

if diem >= 5:
    print("Dat")
elif diem >= 9:  # LỖI! Kiểm tra >= 5 trước
    print("Xuat sac")
```
**Vì sao sai:** Điều kiện lớn hơn phải kiểm tra trước

**✅ Sửa:**
```python
if diem >= 9:
    print("Xuat sac")
elif diem >= 5:
    print("Dat")
```

### ❌ Lỗi 2 — Thiếu else cuối
```python
if diem >= 9:
    print("Xuat sac")
elif diem >= 8:
    print("Gioi")
# Không có else → có thể không in gì
```

### ❌ Lỗi 3 — Nhầm elif và if riêng
```python
diem = 7

if diem >= 5:
    print("Dat")
if diem >= 8:    # Sai! Đây là if mới, không liên quan elif
    print("Gioi")
```

---

## 6. Ghi nhớ nhanh

| Từ khóa | Ý nghĩa |
|----------|---------|
| `if` | Điều kiện đầu tiên |
| `elif` | "Nếu không thì nếu..." — kiểm tra thêm |
| `else` | "Không thì" — khi tất cả sai |

**THỨ TỰ ĐÚNG:**
```
if điều_kiện_1:
    ...
elif điều_kiện_2:
    ...
elif điều_kiện_3:
    ...
else:
    ...
```

**MẸO NHỚ:** `elif` = "else if" = "nếu không thì nếu..."

---

## 7. Mini test (3 câu)

**Câu 1:** diem = 5.5 → Output?
```python
if diem >= 9:
    print("XS")
elif diem >= 8:
    print("G")
elif diem >= 6.5:
    print("K")
elif diem >= 5:
    print("TB")
else:
    print("Y")
```
> Đáp án: `TB`

**Câu 2:** Tại sao dùng elif thay vì nhiều if?
```python
# Nhiều if: kiểm tra TẤT CẢ điều kiện
# elif: dừng ngay khi đúng 1 điều kiện
```

**Câu 3:** diem = 10 → In gì?
> Đáp án: `XS`

---

## 8. LeetCode practice

**Bài tập:** Nhập nhiệt độ, phân loại:
- > 35°C → "Nong"
- 30-35°C → "Nong nhiet"
- 25-30°C → "Binh thuong"
- < 25°C → "Mat nguoi"

**Input:** `32`

**Output:** `Nong nhiet`

**Khung code:**
```python
nhiet_do = float(input())
# Viết tiếp vào đây
```

**✅ Đáp án:**
```python
nhiet_do = float(input())

if nhiet_do > 35:
    print("Nong")
elif nhiet_do >= 30:
    print("Nong nhiet")
elif nhiet_do >= 25:
    print("Binh thuong")
else:
    print("Mat nguoi")
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Viết chương trình tính cước taxi:
- 0-1km: 5000đ
- 1-5km: 4000đ/km
- 5-20km: 3000đ/km
- > 20km: 2000đ/km

**Input:** `3`

**Output:** `13000`

**✅ Đáp án:**
```python
km = float(input())

if km <= 1:
    tien = 5000
elif km <= 5:
    tien = 5000 + (km - 1) * 4000
elif km <= 20:
    tien = 5000 + 4 * 4000 + (km - 5) * 3000
else:
    tien = 5000 + 4 * 4000 + 15 * 3000 + (km - 20) * 2000

print(tien)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 7 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 70 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 7!** 

Gõ **8** để học tiếp Bài 8 (Nested If - Điều kiện lồng nhau) →