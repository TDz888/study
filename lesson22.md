# Bài 22 — Dictionary (P2)

---

## 1. Ôn tập
Bài 21 đã học cách tạo và truy cập dict. Giờ học các **phương thức** của dictionary.

---

## 2. Mục tiêu bài học
- Học method: keys(), values(), items()
- Biết cách duyệt dictionary
- Sử dụng dict comprehension

---

## 3. Code chính (CORE LESSON)

```python
student = {"name": "Minh", "age": 20, "grade": "A"}

# Keys - Lấy tất cả key
print(student.keys())    # dict_keys(['name', 'age', 'grade'])

# Values - Lấy tất cả value
print(student.values())  # dict_values(['Minh', 20, 'A'])

# Items - Lấy cặp key-value
print(student.items())   # dict_items([('name', 'Minh'), ...])
```

**Output:**
```
dict_keys(['name', 'age', 'grade'])
dict_values(['Minh', 20, 'A'])
dict_items([('name', 'Minh'), ('age', 20), ('grade', 'A')])
```

---

## 4. Duyệt Dictionary

```python
student = {"name": "Minh", "age": 20, "grade": "A"}

# Duyệt keys
for key in student:
    print(key)

print("---")

# Duyệt keys + values
for key, value in student.items():
    print(f"{key}: {value}")
```

**Output:**
```
name
age
grade
---
name: Minh
age: 20
grade: A
```

---

## 5. Dict Comprehension

```python
# Tạo dict bình phương số từ 1-5
squares = {x: x**2 for x in range(1, 6)}
print(squares)  # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# Lọc dict
d = {"a": 1, "b": 2, "c": 3, "d": 4}
filtered = {k: v for k, v in d.items() if v > 2}
print(filtered)  # {'c': 3, 'd': 4}
```

---

## 6. Các Method khác

```python
# Copy - Sao chép
d1 = {"a": 1}
d2 = d1.copy()

# Update - Cập nhật từ dict khác
d1 = {"a": 1}
d2 = {"b": 2}
d1.update(d2)
print(d1)  # {'a': 1, 'b': 2}

# Clear - Xóa tất cả
d1.clear()
print(d1)  # {}

# in - Kiểm tra key có tồn tại
d = {"a": 1}
print("a" in d)   # True
print("b" in d)   # False
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Sửa dict khi duyệt
```python
d = {"a": 1, "b": 2}
for key in d:
    d[key] = 0  # Có thể lỗi trong một số trường hợp
```

---

### ❌ SAI THỨ 2 — Nhầm keys và values trong comprehension
```python
# Đúng: key trước, value sau
d = {x: x**2 for x in range(5)}

# Sai: ngược lại
d = {x**2: x for x in range(5)}  # Giá trị trùng!
```

---

### ❌ SAI THỨ 3 — Dùng list thay vì tuple trong items
```python
# Đúng
for key, value in d.items():
    print(key, value)

# Sai
for [key, value] in d.items():  # Không phá hủy tuple được
```

---

## 8. Ghi nhớ nhanh

| Method | Ý nghĩa |
|--------|--------|
| `.keys()` | Tất cả keys |
| `.values()` | Tất cả values |
| `.items()` | Cặp key-value |
| `.copy()` | Sao chép |
| `.update(d)` | Cập nhật từ d |
| `.clear()` | Xóa tất cả |
| `k in d` | Key có tồn tại? |

**MẸO NHỚ:** `.items()` trả về tuple → unpack được.

---

## 9. Mini Test (3 câu)

**Câu 1:** `{"a": 1}.keys()` → ?
> Đáp án: `dict_keys(['a'])`

**Câu 2:** `{x: x*2 for x in [1,2,3]}` = ?
> Đáp án: `{1: 2, 2: 4, 3: 6}`

**Câu 3:** Đếm giá trị > 2 trong `{1: 3, 2: 1, 3: 4}`:
> Đáp án: `2` (key "a" và "c")

---

## 10. LeetCode Practice

### Bài tập: Đảo key-value
**Yêu cầu:** Đảo ngược dict (value thành key, key thành value)

**Input:** `a 1 b 2 c 3`

**Output:** `{1: 'a', 2: 'b', 3: 'c'}`

**✅ Đáp án:**
```python
pairs = input().split()
d = {}
for i in range(0, len(pairs), 2):
    d[pairs[i+1]] = pairs[i]
print(d)
```

---

## 11. Bonus Challenge

Tìm key có value lớn nhất

**Input:** `a 5 b 10 c 3`

**Output:** `b`

**✅ Đáp án:**
```python
pairs = input().split()
d = {}
for i in range(0, len(pairs), 2):
    d[pairs[i]] = int(pairs[i+1])
max_key = max(d, key=d.get)
print(max_key)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 22 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 220 |
| **Mức độ** | Easy |