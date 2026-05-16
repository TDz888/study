# Bài 15 — String Methods (P2)

---

## 1. Ôn tập
Bài 14 đã học upper, lower, strip, replace, split. Giờ học thêm các method khác.

---

## 2. Mục tiêu bài học
- Học thêm các method: join, in, isdigit, isalpha
- Biết cách kiểm tra kiểu ký tự
- Ứng dụng vào validation

---

## 3. Code chính (CORE LESSON)

```python
# Join - Nối chuỗi
words = ["Python", "is", "awesome"]
print(" ".join(words))     # Python is awesome
print("-".join(words))    # Python-is-awesome

# In - Kiểm tra có trong chuỗi
text = "Hello Python"
print("Python" in text)    # True
print("Java" in text)      # False

# isdigit - Là số?
print("123".isdigit())     # True
print("abc".isdigit())     # False

# isalpha - Là chữ?
print("abc".isalpha())    # True
print("abc123".isalpha()) # False

# isalnum - Là chữ hoặc số?
print("abc123".isalnum())  # True
print("abc 123".isalnum()) # False
```

**Output:**
```
Python is awesome
Python-is-awesome
True
False
True
False
True
False
True
False
```

---

## 4. Các Method mở rộng

```python
# Center - Căn giữa
print("Hi".center(10, "-"))   # -----Hi----
print("Hi".center(10))        # "    Hi    "

# Ljust / Rjust - Căn trái/phải
print("Hi".ljust(10, "-"))    # Hi--------
print("Hi".rjust(10, "-"))    # --------Hi

# Zfill - Điền số 0
print("42".zfill(5))          # 00042
```

---

## 5. Trace luồng chạy

```
words = ["a", "b", "c"]
" ".join(words)
       ↓
Nối với " " (khoảng trắng) giữa các phần tử
→ "a b c"
```

```
"abc".isdigit()
       ↓
Kiểm tra tất cả ký tự có phải số 0-9?
→ "a" không phải số → False
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Nhầm in và ==
```python
text = "Hello Python"
# Sai - dùng ==
if text == "Python":
    print("Co Python")

# Đúng - dùng in
if "Python" in text:
    print("Co Python")
```

---

### ❌ SAI THỨ 2 — Join ngược
```python
words = ["a", "b", "c"]
# Sai - không hoạt động
result = words.join("-")

# Đúng - string.join(list)
result = "-".join(words)  # "a-b-c"
```

---

### ❌ SAI THỨ 3 — Isdigit với số âm
```python
print("-123".isdigit())  # False! Dấu - không phải số
```

---

## 7. Ghi nhớ nhanh

| Method | Ý nghĩa | Ví dụ |
|--------|---------|-------|
| `sep.join(list)` | Nối list bằng sep | `" ".join(["a","b"])` |
| `a in s` | Có a trong s? | `"a" in "abc"` → True |
| `.isdigit()` | Là số? | `"123"` → True |
| `.isalpha()` | Là chữ? | `"abc"` → True |
| `.isalnum()` | Là chữ/số? | `"abc123"` → True |
| `.center(n)` | Căn giữa | `"a".center(5)` → `" a  "` |

**MẸO NHỚ:** `in` = "có trong", `isdigit` = "là chữ số", `isalpha` = "là bảng chữ cái".

---

## 8. Mini Test (3 câu)

**Câu 1:** `"-"`join(["a","b","c"]) = ?
> Đáp án: `"a-b-c"`

**Câu 2:** `"123abc".isdigit()` = ?
> Đáp án: `False` (có chữ)

**Câu 3:** `"hello" in "hello world"` = ?
> Đáp án: `True`

---

## 9. LeetCode Practice

### Bài tập: Kiểm tra mật khẩu
**Yêu cầu:** Nhập mật khẩu, kiểm tra:
- Có ít nhất 8 ký tự
- Có cả chữ và số

**Input:** `Pass1234`

**Output:** `Mat khau hop le`

**Input:** `Pass`

**Output:** `Mat khau khong hop le`

**✅ Đáp án:**
```python
pw = input()
if len(pw) >= 8 and pw.isalnum():
    print("Mat khau hop le")
else:
    print("Mat khau khong hop le")
```

---

## 10. Bonus Challenge

Đếm số lần xuất hiện của mỗi chữ cái trong chuỗi (không phân biệt hoa thường)

**Input:** `Hello`

**Output:**
```
h: 1
e: 1
l: 2
o: 1
```

**✅ Đáp án:**
```python
s = input().lower()
for ch in set(s):
    if ch.isalpha():
        print(f"{ch}: {s.count(ch)}")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 15 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 150 |
| **Mức độ** | Easy |