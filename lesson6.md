# Bài 6 — Câu lệnh If / Else

---

## 1. Ôn tập
Bài 5 đã học so sánh: `==, !=, >, <, >=, <=` và kết quả True/False.

---

## 2. Mục tiêu bài học
- Hiểu cấu trúc if/else
- Biết cách dùng if để rẽ nhánh
- Hiểu else là gì
- Thực hành với điều kiện thực tế

---

## 3. Code chính (có comment)

```python
# If - Nếu thỏa điều kiện thì làm
x = 10

if x > 5:
    print("x lon hon 5")

# If - Else: Nếu... thì... không thì...
x = 3

if x > 5:
    print("x lon hon 5")
else:
    print("x khong lon hon 5")
```

**Output:**
```
x lon hon 5
x khong lon hon 5
```

---

## 4. Trace chạy code

```
if x > 5:
    ↓
Kiểm tra: 3 > 5 ?
→ Sai (False)
→ Bỏ qua khối if, chạy else
→ In ra: "x khong lon hon 5"
```

**Quy tắc quan trọng:**
```
if ĐIỀU KIỆN:      ← Có dấu :
    code...       ← Thụt vào 4 spaces (TAB)
else:
    code...
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Quên dấu :
```python
if x > 5        # LỖI! Thiếu :
    print("x lon hon 5")
```
**Vì sao sai:** Python cần dấu `:` để báo hiệu bắt đầu khối code

**✅ Sửa:**
```python
if x > 5:
    print("x lon hon 5")
```

### ❌ Lỗi 2 — Thụt vào sai
```python
if x > 5:
print("x lon hon 5")  # LỖI! Phải thụt vào 4 spaces
```
**Vì sao sai:** Code trong if phải thụt vào 4 spaces

**✅ Sửa:**
```python
if x > 5:
    print("x lon hon 5")  # ✓ 4 spaces
```

### ❌ Lỗi 3 — Viết = thay vì ==
```python
if x = 5:   # LỖI! = là gán
    print("x bang 5")
```
**Vì sao sai:** `=` là gán giá trị, `==` là so sánh

**✅ Sửa:**
```python
if x == 5:  # == là so sánh
    print("x bang 5")
```

---

## 6. Ghi nhớ nhanh

| Cấu trúc | Ý nghĩa |
|----------|---------|
| `if điều_kiện:` | Nếu điều kiện đúng |
| `else:` | Không thì (khi if sai) |
| `:` | PHẢI có dấu 2 chấm |
| 4 spaces | PHẢI thụt vào trong if |

**MẸO NHỚ:** If = "Nếu", Else = "Không thì" — như 2 con đường rẽ nhánh.

---

## 7. Mini test (3 câu)

**Câu 1:** Đoán output:
```python
x = 7
if x > 10:
    print("A")
else:
    print("B")
```
> Đáp án: `B` (7 không lớn hơn 10)

**Câu 2:** Sửa lỗi thiếu dấu `:`
```python
if x == 5
    print("x bang 5")
```
> Đáp án: `if x == 5:`

**Câu 3:** Code này in gì?
```python
diem = 7
if diem >= 5:
    print("Do")
else:
    print("Truot")
```
> Đáp án: `Do`

---

## 8. LeetCode practice

**Bài tập:** Nhập 1 số, kiểm tra:
- Nếu chia 2 dư 0 → in "Chan"
- Nếu chia 2 dư 1 → in "Le"

**Input:** `8`

**Output:** `Chan`

**Input:** `7`

**Output:** `Le`

**Khung code:**
```python
n = int(input())
# Viết tiếp vào đây
```

**✅ Đáp án:**
```python
n = int(input())
if n % 2 == 0:
    print("Chan")
else:
    print("Le")
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Viết chương trình kiểm tra điểm:
- Điểm >= 8 → "Gioi"
- Điểm < 8 → "Chua Gioi"

**Input:** `9`

**Output:** `Gioi`

**✅ Đáp án:**
```python
diem = float(input())
if diem >= 8:
    print("Gioi")
else:
    print("Chua Gioi")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 6 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 60 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 6!** 

Gõ **7** để học tiếp Bài 7 (Elif - Nhiều điều kiện) →