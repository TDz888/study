# Bài 14 — String Methods (P1)

---

## 1. Ôn tập
Bài 13 đã học indexing và slicing. Giờ học các **phương thức** xử lý string.

---

## 2. Mục tiêu bài học
- Hiểu method là gì
- Biết các method thường dùng: upper, lower, strip, replace
- Ứng dụng vào bài toán thực tế

---

## 3. Code chính (CORE LESSON)

```python
# Upper / Lower - Chuyển hoa/thường
text = "Hello Python"
print(text.upper())    # HELLO PYTHON
print(text.lower())    # hello python

# Strip - Xóa khoảng trắng đầu/cuối
text = "   Hello   "
print(text.strip())    # Hello

# Replace - Thay thế
text = "Hello World"
print(text.replace("World", "Python"))  # Hello Python

# Split - Tách chuỗi
text = "apple,banana,cherry"
fruits = text.split(",")
print(fruits)  # ['apple', 'banana', 'cherry']
```

**Output:**
```
HELLO PYTHON
hello python
Hello
Hello Python
['apple', 'banana', 'cherry']
```

---

## 4. Các Method khác

```python
# Count - Đếm số lần xuất hiện
text = "hello hello hello"
print(text.count("hello"))  # 3

# Find - Tìm vị trí (index)
text = "Hello Python"
print(text.find("Python"))  # 6

# Startswith / Endswith - Kiểm tra bắt đầu/kết thúc
text = "Hello.py"
print(text.startswith("Hello"))  # True
print(text.endswith(".py"))      # True

# Title - Viết hoa chữ cái đầu
text = "hello world"
print(text.title())  # Hello World
```

---

## 5. Trace luồng chạy

```
text = "   Hello World   "
text.strip()
       ↓
Xóa khoảng trắng đầu: "   Hello World   "
Xóa khoảng trắng cuối: "   Hello World"
Kết quả: "Hello World"

text.replace("World", "Python")
       ↓
Tìm "World" trong chuỗi
Thay thế bằng "Python"
Kết quả: "Hello Python"
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Quên dấu ngoặc ()
```python
text = "Hello"
print(text.upper)   # LỖI! Cần ()
print(text.upper())  # Đúng
```

---

### ❌ SAI THỨ 2 — Split sai ký tự
```python
text = "apple banana cherry"
# Phân tách bằng khoảng trắng
words = text.split(" ")  # OK
words = text.split()     # Cũng OK
```

---

### ❌ SAI THỨ 3 — Replace không lưu lại
```python
text = "Hello"
text.replace("Hello", "Hi")
print(text)  # "Hello" - KHÔNG thay đổi!
```
**GIẢI THÍCH:** String là immutable (không thay đổi được)

**✅ SỬA:**
```python
text = "Hello"
text = text.replace("Hello", "Hi")  # Gán lại
print(text)  # "Hi"
```

---

## 7. Ghi nhớ nhanh

| Method | Ý nghĩa |
|--------|---------|
| `.upper()` | Viết hoa |
| `.lower()` | Viết thường |
| `.strip()` | Xóa khoảng trắng 2 đầu |
| `.replace(a, b)` | Thay a bằng b |
| `.split(ký_tự)` | Tách chuỗi |
| `.count(ký_tự)` | Đếm số lần |
| `.find(ký_tự)` | Tìm vị trí |
| `.startswith(a)` | Bắt đầu bằng a? |
| `.endswith(a)` | Kết thúc bằng a? |

**MẸO NHỚ:** Method = hành động trên đối tượng. `text.upper()` = "biến text thành chữ HOA".

---

## 8. Mini Test (3 câu)

**Câu 1:** `"hello".upper()` = ?
> Đáp án: `"HELLO"`

**Câu 2:** `"  hello  ".strip()` = ?
> Đáp án: `"hello"`

**Câu 3:** `"hello".replace("l", "x")` = ?
> Đáp án: `"hexxo"`

---

## 9. LeetCode Practice

### Bài tập: Chuẩn hóa tên
**Yêu cầu:** Nhập tên, chuẩn hóa:
- Xóa khoảng trắng thừa
- Viết hoa chữ cái đầu

**Input:** `   john doe   `

**Output:** `John Doe`

**✅ Đáp án:**
```python
ten = input()
ten = ten.strip()
ten = ten.title()
print(ten)
```

---

## 10. Bonus Challenge

Đếm số từ trong câu:
- "Hello World" → 2 từ
- "Python is awesome" → 3 từ

**Input:** `Python is awesome`

**Output:** `3`

**✅ Đáp án:**
```python
cau = input()
tu = cau.split()
print(len(tu))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 14 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 140 |
| **Mức độ** | Easy |