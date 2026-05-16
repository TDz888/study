# Bài 4 — Input từ bàn phím

---

## 1. Ôn tập
Bài 3 đã học toán tử. Giờ ta học cách **nhận dữ liệu từ người dùng**.

---

## 2. Mục tiêu bài học
- Hiểu `input()` là gì
- Biết cách nhận text từ bàn phím
- Biết cách nhận số và chuyển đổi kiểu
- Kết hợp input + biến + print

---

## 3. Code chính (có comment)

```python
# Nhập tên
ten = input("Nhap ten cua ban: ")
print("Xin chao", ten)

# Nhập số tuổi
tuoi = input("Ban bao nhieu tuoi? ")
print("Ban", tuoi, "tuoi")
```

**Khi chạy:**
```
Nhap ten cua ban: Nam
Xin chao Nam
Ban bao nhieu tuoi? 20
Ban 20 tuoi
```

---

## 4. Trace chạy code

**Nhận số (QUAN TRỌNG!):**

```python
# input() luôn trả về STRING
# Muốn nhận số phải chuyển kiểu

tuoi = int(input("Nhap tuoi: "))
chieu_cao = float(input("Nhap chieu cao: "))

print("Tuoi:", tuoi)
print("Chieu cao:", chieu_cao)
```

**Khi chạy:**
```
Nhap tuoi: 25
Nhap chieu cao: 1.75
Tuoi: 25
Chieu cao: 1.75
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Không chuyển kiểu khi tính toán
```python
a = input("Nhap so a: ")
b = input("Nhap so b: ")
# print(a + b)  # LỖI! "5" + "3" = "53" (nối chuỗi)
```
**Vì sao sai:** input() trả về string, cần chuyển sang số

**✅ Sửa:**
```python
a = int(input("Nhap so a: "))
b = int(input("Nhap so b: "))
print(a + b)  # 8
```

### ❌ Lỗi 2 — Nhập float thành int
```python
chieu_cao = int(input("Nhap chieu cao: "))
# Nhập 1.75 → LỖI! "1.75" không chuyển được thành int
```
**Vì sao sai:** Dùng int cho số thập phân

**✅ Sửa:**
```python
chieu_cao = float(input("Nhap chieu cao: "))
```

### ❌ Lỗi 3 — Quên gán vào biến
```python
input("Nhap ten: ")  # LỖI! Dữ liệu bị mất
```
**Vì sao sai:** Không lưu vào biến thì mất dữ liệu

**✅ Sửa:**
```python
ten = input("Nhap ten: ")
```

---

## 6. Ghi nhớ nhanh

| Hàm | Ý nghĩa |
|-----|---------|
| `input()` | Nhận dữ liệu từ bàn phím |
| `input("text")` | Hiển thị text rồi chờ nhập |
| `int("5")` | Chuyển string "5" → số 5 |
| `float("1.5")` | Chuyển string "1.5" → số 1.5 |

**MẸO NHỚ:** `input()` = người nhập liệu → luôn trả về STRING → cần `int()` hoặc `float()` để tính toán.

---

## 7. Mini test (3 câu)

**Câu 1:** Đoán kết quả:
```python
a = int(input())
# Nhập: 10
print(a + 5)
```
> Đáp án: `15`

**Câu 2:** Sửa lỗi:
```python
a = input("Nhap so: ")
b = input("Nhap so: ")
print(a + b)  # Muốn in tổng
```
> Đáp án: `print(int(a) + int(b))`

**Câu 3:** Nhập 1.75 dùng hàm nào?
> Đáp án: `float(input())`

---

## 8. LeetCode practice

**Bài tập:** Nhập 2 số từ bàn phím, in ra tổng

**Input:**
```
5
3
```

**Output:**
```
Tong = 8
```

**Khung code:**
```python
# Viết code vào đây
```

**✅ Đáp án:**
```python
a = int(input())
b = int(input())
tong = a + b
print("Tong =", tong)
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Viết chương trình tính điểm trung bình:
- Nhập điểm Toán, Lý, Hóa
- Tính và in điểm trung bình

**Input:**
```
8
9
7
```

**Output:**
```
Diem trung binh = 8.0
```

**✅ Đáp án:**
```python
toan = float(input())
ly = float(input())
hoa = float(input())

trung_binh = (toan + ly + hoa) / 3
print("Diem trung binh =", trung_binh)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 4 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 40 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 4!** 

Gõ **5** để học tiếp Bài 5 (So sánh và Boolean) →