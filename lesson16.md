# Bài 16 — List (Danh sách)

---

## 1. Ôn tập
Bài 15 đã học string methods. Giờ học **List** — kiểu dữ liệu lưu nhiều giá trị.

---

## 2. Mục tiêu bài học
- Hiểu list là gì
- Biết cách tạo và truy cập list
- Hiểu indexing và slicing trong list
- Thêm/sửa/xóa phần tử

---

## 3. Code chính (có comment)

### Tạo và truy cập List
```python
# Tạo list
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4, 5]
mixed = ["hello", 123, 3.14, True]  # List chứa nhiều kiểu

# Truy cập phần tử (index bắt đầu từ 0)
print(fruits[0])   # apple - phần tử đầu tiên
print(fruits[1])   # banana
print(fruits[-1])  # cherry - phần tử cuối cùng
print(fruits[-2])  # banana - phần tử thứ 2 từ cuối

# Độ dài list
print(len(fruits))  # 3

# Slicing - lấy một phần của list
print(fruits[0:2])   # ['apple', 'banana'] - từ index 0 đến 1
print(fruits[1:])    # ['banana', 'cherry'] - từ index 1 đến cuối
print(fruits[:2])    # ['apple', 'banana'] - từ đầu đến index 1
```

### Thêm/Sửa/Xóa phần tử
```python
fruits = ["apple", "banana"]

# Thêm phần tử vào cuối
fruits.append("cherry")
print(fruits)  # ['apple', 'banana', 'cherry']

# Chèn vào vị trí chỉ định
fruits.insert(1, "orange")  # index 1, giá trị "orange"
print(fruits)  # ['apple', 'orange', 'banana', 'cherry']

# Sửa phần tử theo index
fruits[0] = "mango"
print(fruits)  # ['mango', 'orange', 'banana', 'cherry']

# Xóa theo giá trị (xóa phần tử đầu tiên tìm thấy)
fruits.remove("banana")
print(fruits)  # ['mango', 'orange', 'cherry']

# Xóa theo index
del fruits[0]
print(fruits)  # ['orange', 'cherry']

# Xóa và lấy giá trị (pop)
last = fruits.pop()
print(last)    # 'cherry'
print(fruits)  # ['orange']
```

---

## 4. Trace chạy code

```
fruits = ["apple", "banana", "cherry"]
  index:    0         1          2

fruits[0] → "apple"
fruits[1] → "banana"
fruits[2] → "cherry"

fruits.append("orange"):
→ Thêm "orange" vào cuối
→ ['apple', 'banana', 'cherry', 'orange']

fruits.insert(1, "mango"):
→ Chèn "mango" vào vị trí index 1
→ ['apple', 'mango', 'banana', 'cherry', 'orange']
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Index vượt ngoài
```python
# LỖI! List chỉ có 2 phần tử (index 0 và 1)
fruits = ["apple", "banana"]
print(fruits[2])  # IndexError: list index out of range
```

### ❌ Lỗi 2 — Nhầm remove và pop
```python
# remove(x) - xóa theo GIÁ TRỊ, xóa phần tử đầu tiên tìm thấy
fruits = ["apple", "banana", "apple"]
fruits.remove("apple")
print(fruits)  # ['banana', 'apple'] - chỉ xóa phần tử đầu tiên

# pop() - xóa và trả về phần tử CUỐI
fruits = ["apple", "banana"]
item = fruits.pop()
print(item)   # 'banana'
print(fruits) # ['apple']
```

### ❌ Lỗi 3 — Gán sai khi modify
```python
# List methods modify TRỰC TIẾP, không cần gán lại
fruits = ["apple"]
fruits.append("banana")
# KHÔNG cần: fruits = fruits.append("banana")

# Nhưng nếu dùng + hoặc slicing -> TẠO list mới
new_fruits = fruits + ["cherry"]  # Tạo list mới
```

---

## 6. Ghi nhớ nhanh

| Thao tác | Cú pháp | Ví dụ |
|----------|---------|-------|
| Tạo list | `lst = [a, b, c]` | `["a", "b"]` |
| Truy cập | `lst[index]` | `lst[0]` |
| Index âm | `lst[-1]` | Phần tử cuối |
| Thêm cuối | `lst.append(x)` | `["a"].append("b")` |
| Chèn | `lst.insert(i, x)` | `["a"].insert(1, "b")` |
| Xóa giá trị | `lst.remove(x)` | Xóa phần tử đầu tiên = x |
| Xóa index | `del lst[i]` | Xóa phần tử tại i |
| Pop | `lst.pop()` | Xóa và trả về cuối |
| Độ dài | `len(lst)` | Số phần tử |

**MẸO NHỚ:** List = cái túi chứa nhiều thứ. Thêm bằng `append`, lấy ra bằng index. Index âm = đếm từ cuối (-1 là cuối).

---

## 7. Mini test (3 câu)

**Câu 1:** `[1, 2, 3][1]` = ?
> Đáp án: `2` (phần tử tại index 1)

**Câu 2:** `[1, 2, 3].append(4)` → ?
> Đáp án: `[1, 2, 3, 4]` (thêm 4 vào cuối)

**Câu 3:** Xóa "b" khỏi `["a", "b", "c"]`:
> Đáp án: `["a", "c"]` (dùng `.remove("b")`)

---

## 8. LeetCode Practice

### Bài tập: Quản lý điểm
**Yêu cầu:** Nhập 3 điểm vào list, tính điểm trung bình

**Input:**
```
8
9
7
```

**Output:** `8.0`

**✅ Đáp án:**
```python
diem = []

# Nhập 3 điểm
diem.append(int(input()))
diem.append(int(input()))
diem.append(int(input()))

# Tính trung bình
trung_binh = sum(diem) / len(diem)
print(trung_binh)
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Xóa tất cả phần tử trùng lặp trong list

**Input:** `[1, 2, 2, 3, 1, 4, 3]`

**Output:** `[1, 2, 3, 4]` (giữ nguyên thứ tự xuất hiện)

**✅ Đáp án:**
```python
lst = [1, 2, 2, 3, 1, 4, 3]
seen = set()
result = []

for item in lst:
    if item not in seen:
        result.append(item)
        seen.add(item)

print(result)  # [1, 2, 3, 4]
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 16 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 160 (+10 XP khi hoàn thành) |
| **Level** | Beginner |

---

**🎉 Bạn đã hoàn thành Bài 16!**

Gõ **17** để học tiếp Bài 17 (List Methods) →