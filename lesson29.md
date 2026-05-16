# Bài 29 — Lambda Functions

---

## 1. Ôn tập
Bài 28 đã học Scope. Giờ học **Lambda** — hàm ẩn danh ngắn gọn.

---

## 2. Mục tiêu bài học
- Hiểu lambda là gì
- Biết cách viết hàm lambda
- Khi nào nên dùng lambda
- Kết hợp với map, filter, sorted

---

## 3. Code chính (CORE LESSON)

```python
# Hàm thông thường
def cong(a, b):
    return a + b

# Lambda tương đương
cong = lambda a, b: a + b

print(cong(5, 3))  # 8
```

**Output:**
```
8
```

---

## 4. Lambda không gán biến

```python
# Lambda dùng trực tiếp
print((lambda x: x ** 2)(5))  # 25

# Với map
nums = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x ** 2, nums))
print(squares)  # [1, 4, 9, 16, 25]
```

**Output:**
```
25
[1, 4, 9, 16, 25]
```

---

## 5. Lambda với filter

```python
nums = [1, 2, 3, 4, 5, 6]

# Lọc số chẵn
evens = list(filter(lambda x: x % 2 == 0, nums))
print(evens)  # [2, 4, 6]
```

---

## 6. Lambda với sorted

```python
students = [("Minh", 20), ("Lan", 18), ("An", 22)]

# Sắp xếp theo điểm (index 1)
sorted_by_age = sorted(students, key=lambda x: x[1])
print(sorted_by_age)
# [('Lan', 18), ('Minh', 20), ('An', 22)]
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Lambda phức tạp
```python
# Quá phức tạp cho lambda
result = (lambda a, b, c: ((a ** 2 + b ** 2 - c) ** 0.5) / (2 * a))(3, 4, 5)

# Nên dùng def
def tinh(a, b, c):
    return ((a ** 2 + b ** 2 - c) ** 0.5) / (2 * a)
```

---

### ❌ SAI THỨ 2 — Quên lambda là biểu thức
```python
# LỖI - Lambda chỉ có 1 dòng
lambda x: if x > 0: print("dung")

# Đúng
lambda x: print("dung") if x > 0 else print("sai")
```

---

### ❌ SAI THỨ 3 — Gán lambda cho biến rồi đổi tên
```python
add = lambda a, b: a + b
add(1, 2)  # OK

# Nên dùng def thay vì lambda khi có tên
def add(a, b):
    return a + b
```

---

## 8. Ghi nhớ nhanh

| Cú pháp | Ví dụ |
|---------|-------|
| `lambda x: expr` | `lambda x: x ** 2` |
| `lambda x, y: expr` | `lambda x, y: x + y` |
| `lambda x: expr1 if cond else expr2` | Với if/else |

**MẸO NHỚ:** Lambda = hàm ẩn danh, 1 dòng. Dùng cho map/filter/sorted.

---

## 9. Mini Test (3 câu)

**Câu 1:** `(lambda x: x * 2)(5)` = ?
> Đáp án: `10`

**Câu 2:** Viết lambda kiểm tra chẵn:
> Đáp án: `lambda x: x % 2 == 0`

**Câu 3:** `list(filter(lambda x: x > 2, [1, 3, 2, 4]))` = ?
> Đáp án: `[3, 4]`

---

## 10. LeetCode Practice

### Bài tập: Lambda với map
**Yêu cầu:** Nhập list số, nhân đôi mỗi số

**Input:** `1 2 3 4 5`

**Output:** `[2, 4, 6, 8, 10]`

**✅ Đáp án:**
```python
nums = list(map(int, input().split()))
result = list(map(lambda x: x * 2, nums))
print(result)
```

---

## 11. Bonus Challenge

Sắp xếp list string theo độ dài

**Input:** `hello world python is awesome`

**Output:** `['is', 'hello', 'world', 'python', 'awesome']`

**✅ Đáp án:**
```python
words = input().split()
sorted_words = sorted(words, key=lambda x: len(x))
print(sorted_words)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 29 / 2000 |
| **Chapter** | 3 (Functions) |
| **XP** | 290 |
| **Mức độ** | Medium |