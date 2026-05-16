# Bài 18 — For với List

---

## 1. Ôn tập
Bài 17 đã học list methods. Giờ học cách **duyệt list** bằng vòng lặp.

---

## 2. Mục tiêu bài học
- Biết cách duyệt list bằng for
- Dùng enumerate để lấy index
- Ứng dụng vào bài toán thực tế

---

## 3. Code chính (CORE LESSON)

```python
# Duyệt từng phần tử
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

print("---")

# Duyệt với index
for i, fruit in enumerate(fruits):
    print(f"{i}: {fruit}")

print("---")

# Duyệt với range
for i in range(len(fruits)):
    print(f"{i}: {fruits[i]}")
```

**Output:**
```
apple
banana
cherry
---
0: apple
1: banana
2: cherry
---
0: apple
1: banana
2: cherry
```

---

## 4. Trace luồng chạy

```
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    Lần 1: fruit = "apple" → print("apple")
    Lần 2: fruit = "banana" → print("banana")
    Lần 3: fruit = "cherry" → print("cherry")
    Hết phần tử → DỪNG
```

---

## 5. Vòng lặp lồng nhau

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

for row in matrix:
    for item in row:
        print(item, end=" ")
    print()
```

**Output:**
```
1 2 3 
4 5 6 
7 8 9 
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Sửa phần tử trong for
```python
fruits = ["apple", "banana"]
for fruit in fruits:
    fruit = "new"  # Không thay đổi list gốc!

# Đúng - dùng index
for i in range(len(fruits)):
    fruits[i] = "new"
```

---

### ❌ SAI THỨ 2 — Quên indent
```python
fruits = ["apple", "banana"]
for fruit in fruits:
print(fruit)  # Lỗi! Phải thụt vào
```

---

### ❌ SAI THỨ 3 — Dùng enumerate sai
```python
fruits = ["apple", "banana"]
for i in fruits:  # Sai - i là phần tử, không phải index
    print(i)

# Đúng
for i, fruit in enumerate(fruits):
    print(i, fruit)
```

---

## 7. Ghi nhớ nhanh

| Cú pháp | Ý nghĩa |
|---------|---------|
| `for x in lst:` | Duyệt từng phần tử |
| `for i, x in enumerate(lst):` | Duyệt với index |
| `for i in range(len(lst)):` | Duyệt với index (cách 2) |

**MẸO NHỚ:** `enumerate` = đánh số thứ tự (0, 1, 2...).

---

## 8. Mini Test (3 câu)

**Câu 1:** Đoán output:
```python
lst = [1, 2, 3]
for x in lst:
    print(x * 2)
```
> Đáp án: `2 4 6`

**Câu 2:** Dùng enumerate để in cả index và giá trị:
```python
for i, x in enumerate([10, 20, 30]):
    print(i, x)  # 0 10, 1 20, 2 30
```

**Câu 3:** In index của phần tử "b" trong `["a", "b", "c"]`:
> Đáp án: `1`

---

## 9. LeetCode Practice

### Bài tập: Tính tổng các số lẻ
**Yêu cầu:** Nhập list số, tính tổng các số lẻ

**Input:** `1 2 3 4 5`

**Output:** `9` (1+3+5)

**✅ Đáp án:**
```python
lst = list(map(int, input().split()))
tong = 0
for x in lst:
    if x % 2 != 0:
        tong += x
print(tong)
```

---

## 10. Bonus Challenge

Đếm số lần xuất hiện của mỗi phần tử

**Input:** `1 2 2 3 1 4 2`

**Output:**
```
1: 2
2: 3
3: 1
4: 1
```

**✅ Đáp án:**
```python
lst = list(map(int, input().split()))
for x in set(lst):
    print(f"{x}: {lst.count(x)}")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 18 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 180 |
| **Mức độ** | Easy |