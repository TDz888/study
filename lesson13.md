# Bài 13 — String (Chuỗi ký tự)

---

## 1. Ôn tập
Bài 12 đã học `break` và `continue`. Giờ học **String** — kiểu dữ liệu văn bản.

---

## 2. Mục tiêu bài học
- Hiểu string là gì
- Biết cách tạo string
- Hiểu indexing (chỉ mục)
- Cắt string (slicing)

---

## 3. Code chính (CORE LESSON)

```python
# Tạo string
ten = "Minh"

# Indexing - Truy cập từng ký tự
print(ten[0])  # M
print(ten[1])  # i
print(ten[2])  # n
print(ten[3])  # h

# Index âm - Đếm từ cuối
print(ten[-1])  # h (ký tự cuối)
print(ten[-2])  # n

# Độ dài string
print(len(ten))  # 4
```

**Output:**
```
M
i
n
h
h
n
4
```

---

## 4. Slicing (Cắt string)

```python
text = "Hello Python"

# [start:end] - từ start đến end-1
print(text[0:5])   # Hello
print(text[6:12])  # Python

# [:end] - từ đầu đến end-1
print(text[:5])    # Hello

# [start:] - từ start đến cuối
print(text[6:])     # Python

# [start:end:step] - bước nhảy
print(text[0:12:2])  # HloPy (cách 1 ký tự)
print(text[::-1])     # nohtyP olleH (đảo ngược)
```

---

## 5. Trace luồng chạy

```
text = "Hello Python"
 0    1    2    3    4    5 6    7    8    9   10   11
 H    e    l    l    o    ␣    P    y    t    h    o    n
-12  -11  -10  -9   -8   -7   -6   -5   -4   -3   -2   -1

text[0:5] → "Hello"
text[6:12] → "Python"
text[::-1] → "nohtyP olleH"
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Index vượt ngoài
```python
text = "Hello"
print(text[10])  # LỖI! IndexError
```

---

### ❌ SAI THỨ 2 — Nhầm start và end trong slicing
```python
text = "Hello"
# Lấy "ell"
print(text[1:4])  # [1:4] = 1,2,3 (không phải 4)
```

---

### ❌ SAI THỨ 3 — Quên +1 cho index cuối
```python
text = "Hello"
# Muốn lấy "Hello"
print(text[0:4])  # "Hell" - thiếu!
print(text[0:5])  # "Hello" - đúng
```

---

## 7. Ghi nhớ nhanh

| Cú pháp | Ý nghĩa | Ví dụ |
|---------|---------|-------|
| `s[0]` | Ký tự đầu | `"Hello"[0]` = `"H"` |
| `s[-1]` | Ký tự cuối | `"Hello"[-1]` = `"o"` |
| `s[0:5]` | Cắt từ 0 đến 4 | `"Hello"[0:3]` = `"Hel"` |
| `len(s)` | Độ dài | `len("Hello")` = `5` |
| `s[::-1]` | Đảo ngược | `"Hello"[::-1]` = `"olleH"` |

**MẸO NHỚ:** Index bắt đầu từ 0. `s[0:5]` = từ 0 đến 4 (không phải 5).

---

## 8. Mini Test (3 câu)

**Câu 1:** `"Python"[0]` = ?
> Đáp án: `"P"`

**Câu 2:** `"Python"[-2]` = ?
> Đáp án: `"o"` (ký tự thứ 2 từ cuối)

**Câu 3:** `"Hello World"[0:5]` = ?
> Đáp án: `"Hello"`

---

## 9. LeetCode Practice

### Bài tập: Đảo ngược tên
**Yêu cầu:** Nhập tên, in ra tên đảo ngược

**Input:** `Minh`

**Output:** `hnim`

**✅ Đáp án:**
```python
ten = input()
print(ten[::-1])
```

---

## 10. Bonus Challenge

Kiểm tra chuỗi đối xứng (palindrome):
- "radar" đọc ngược cũng là "radar" → True
- "hello" → False

**Input:** `radar`

**Output:** `True`

**✅ Đáp án:**
```python
s = input()
if s == s[::-1]:
    print("True")
else:
    print("False")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 13 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 130 |
| **Mức độ** | Easy |