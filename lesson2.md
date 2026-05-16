# Bài 2 — Biến (Variables)

---

## 1. Ôn tập
Bài 1 đã học `print()` — dùng để in text ra màn hình. Text cần đặt trong `" "`.

---

## 2. Mục tiêu bài học
- Hiểu **biến (variable)** là gì
- Biết cách tạo và sử dụng biến
- Hiểu **kiểu dữ liệu** cơ bản: string, int, float
- Dùng biến trong `print()`

---

## 3. Code chính (có comment)

```python
# Tạo biến và sử dụng
ten = "Minh"           # String - chuỗi ký tự
tuoi = 25              # Int - số nguyên
chieu_cao = 1.75       # Float - số thập phân

# In biến ra màn hình
print(ten)
print(tuoi)
print(chieu_cao)

# Kết hợp text và biến
print("Toi ten la", ten)
print("Toi", tuoi, "tuoi")
```

**Output:**
```
Minh
25
1.75
Toi ten la Minh
Toi 25 tuoi
```

---

## 4. Trace chạy code

```
Bước 1: ten = "Minh"
        → Tạo ô nhớ tên "ten", lưu giá trị "Minh"

Bước 2: tuoi = 25
        → Tạo ô nhớ tên "tuoi", lưu giá trị 25

Bước 3: print(ten)
        → Tìm ô nhớ "ten" → lấy giá trị "Minh" → in ra

Bước 4: print("Toi ten la", ten)
        → "Toi ten la" + "Minh" → In ra: Toi ten la Minh
```

**Biến đổi giá trị:**
```
ten: "" → "Minh"  (gán giá trị)
tuoi: "" → 25
chieu_cao: "" → 1.75
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Quên dấu `"` với string
```python
ten = Minh  # LỖI! String phải có ""
```
**Vì sao sai:** Text cần đặt trong ngoặc kép

**✅ Sửa:**
```python
ten = "Minh"
```

### ❌ Lỗi 2 — Đặt tên biến có khoảng trắng
```python
ten cua toi = "Minh"  # LỖI!
```
**Vì sao sai:** Tên biến không có khoảng trắng

**✅ Sửa:**
```python
ten_cua_toi = "Minh"
# hoặc
tenCuaToi = "Minh"
```

### ❌ Lỗi 3 — Gán sai kiểu dữ liệu
```python
tuoi = "25"   # Đây là STRING "25", không phải số 25
tuoi = 25     # Đây là số 25
```
**Vì sao sai:** `"25"` là text, `25` là số — khác nhau!

---

## 6. Ghi nhớ nhanh

| Thuật ngữ | Giải thích |
|-----------|------------|
| **variable** | Biến — nơi lưu dữ liệu |
| **assign** | Gán — đặt giá trị vào biến |
| **string** | Chuỗi ký tự — `"text"` |
| **int** | Số nguyên — 1, 2, 100 |
| **float** | Số thập phân — 1.5, 3.14 |

**MẸO NHỚ:** Biến = cái hộp có nhãn. `ten = "Minh"` = cái hộp tên "ten" chứa chữ "Minh".

---

## 7. Mini test (3 câu)

**Câu 1:** Đoán kết quả:
```python
x = 5
y = 10
print(x + y)
```
> Đáp án: `15`

**Câu 2:** Sửa lỗi:
```python
ho_ten = Nam
```
> Đáp án: `ho_ten = "Nam"` (thiếu "")

**Câu 3:** Có mấy loại số trong ví dụ này?
```python
a = 3
b = 3.5
c = "3"
```
> Đáp án: 3 loại — int (a), float (b), string (c)

---

## 8. LeetCode practice

**Bài tập:** Tạo 3 biến và in ra:
- `ho` = "Nguyen"
- `ten` = "An"
- `tuoi` = 20

**Input:** (không có input)

**Output:**
```
Nguyen
An
20
Nguyen An, 20 tuoi
```

**Khung code:**
```python
ho = "Nguyen"
ten = "An"
tuoi = 20
# Viết tiếp vào đây
```

**✅ Đáp án:**
```python
ho = "Nguyen"
ten = "An"
tuoi = 20

print(ho)
print(ten)
print(tuoi)
print(ho, ten, tuoi, "tuoi")
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Tính tổng của 2 số và in ra:
- Số thứ nhất: 15
- Số thứ hai: 27

**Output:**
```
Tong = 42
```

**✅ Đáp án:**
```python
so1 = 15
so2 = 27
tong = so1 + so2
print("Tong =", tong)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 2 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 20 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 2!** 

Gõ **3** để học tiếp Bài 3 (Toán tử - Operators) →