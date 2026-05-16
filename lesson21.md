# Bài 21 — Dictionary (P1)

---

## 1. Ôn tập
Bài 20 đã học Tuple — dữ liệu không đổi. Giờ học **Dictionary** — dữ liệu theo cặp key-value.

---

## 2. Mục tiêu bài học
- Hiểu dictionary là gì
- Biết cách tạo và truy cập dict
- Hiểu key-value mapping
- Thêm/sửa/xóa trong dict

---

## 3. Code chính (CORE LESSON)

```python
# Tạo dictionary
student = {
    "name": "Minh",
    "age": 20,
    "grade": "A"
}

# Truy cập bằng key
print(student["name"])   # Minh
print(student["age"])    # 20

# Dùng get (an toàn hơn)
print(student.get("name"))      # Minh
print(student.get("address"))   # None (không lỗi)
print(student.get("address", "HN"))  # HN (mặc định)
```

**Output:**
```
Minh
20
Minh
None
HN
```

---

## 4. Thêm/Sửa/Xóa

```python
student = {"name": "Minh", "age": 20}

# Thêm
student["city"] = "Hanoi"
print(student)  # {'name': 'Minh', 'age': 20, 'city': 'Hanoi'}

# Sửa
student["age"] = 21
print(student)  # {'name': 'Minh', 'age': 21, 'city': 'Hanoi'}

# Xóa
del student["city"]
print(student)  # {'name': 'Minh', 'age': 21}

# Pop - Xóa và trả về giá trị
age = student.pop("age")
print(age, student)  # 21 {'name': 'Minh'}
```

---

## 5. Trace luồng chạy

```
student = {"name": "Minh", "age": 20}

student["name"] → Tìm key "name" → Trả về "Minh"
student["city"] = "Hanoi"
       ↓
Thêm cặp key-value mới
→ {"name": "Minh", "age": 20, "city": "Hanoi"}

del student["age"]
       ↓
Xóa cặp có key "age"
→ {"name": "Minh", "city": "Hanoi"}
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Key không tồn tại
```python
student = {"name": "Minh"}
print(student["age"])  # KeyError!
```
**Sửa:** Dùng `.get()` hoặc kiểm tra trước

---

### ❌ SAI THỨ 2 — Dùng list làm key
```python
# LỖI! Key phải là immutable
d = {[1,2]: "a"}  # TypeError

# Được
d = {(1,2): "a"}  # Tuple OK
```

---

### ❌ SAI THỨ 3 — Nhầm key và value
```python
d = {"a": 1, "b": 2}
# Key: "a", "b"
# Value: 1, 2
```

---

## 7. Ghi nhớ nhanh

| Thao tác | Cú pháp |
|----------|---------|
| Tạo | `d = {"a": 1, "b": 2}` |
| Truy cập | `d["a"]` |
| Get an toàn | `d.get("a", default)` |
| Thêm/Sửa | `d["c"] = 3` |
| Xóa | `del d["a"]` |
| Pop | `d.pop("a")` |

**MẸO NHỚ:** Dict = từ điển. Key = từ, Value = nghĩa. Tra "Minh" → tìm key → ra value.

---

## 8. Mini Test (3 câu)

**Câu 1:** `{"a": 1, "b": 2}["b"]` = ?
> Đáp án: `2`

**Câu 2:** Thêm "c": 3 vào `{"a": 1}`:
> Đáp án: `{"a": 1, "c": 3}`

**Câu 3:** Xóa key "a" khỏi dict:
> Đáp án: `del d["a"]` hoặc `d.pop("a")`

---

## 9. LeetCode Practice

### Bài tập: Đếm từ
**Yêu cầu:** Đếm số lần xuất hiện của mỗi từ

**Input:** `apple banana apple orange apple`

**Output:**
```
apple: 3
banana: 1
orange: 1
```

**✅ Đáp án:**
```python
words = input().split()
counts = {}
for word in words:
    counts[word] = counts.get(word, 0) + 1
for word, count in counts.items():
    print(f"{word}: {count}")
```

---

## 10. Bonus Challenge

Merge 2 dictionary

**Input:**
```
a 1 b 2
c 3 d 4
```

**Output:** `{'a': 1, 'b': 2, 'c': 3, 'd': 4}`

**✅ Đáp án:**
```python
d1 = dict(input().split())
d2 = dict(input().split())
d1.update(d2)
print(d1)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 21 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 210 |
| **Mức độ** | Easy |