# Bài 45 — Matrix (Ma trận)

---

## 1. Ôn tập
Bài 44 đã học Stack/Queue. Giờ học **Matrix** — cấu trúc 2D trong Python.

---

## 2. Mục tiêu bài học
- Tạo ma trận
- Truy cập phần tử
- Duyệt ma trận
- Các thao tác cơ bản

---

## 3. Tạo Matrix

```python
# Tạo ma trận 3x3
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Truy cập phần tử
print(matrix[0][0])  # 1
print(matrix[1][2])  # 6
print(matrix[2][1])  # 8
```

**Output:**
```
1
6
8
```

---

## 4. Duyệt Matrix

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

# Duyệt theo hàng
for row in matrix:
    for val in row:
        print(val, end=" ")
    print()
```

**Output:**
```
1 2 3 
4 5 6 
```

---

## 5. Tạo ma trận động

```python
# Tạo ma trận m x n
def create_matrix(m, n, default=0):
    return [[default for _ in range(n)] for _ in range(m)]

mat = create_matrix(3, 4)
print(len(mat))      # 3
print(len(mat[0]))   # 4

# Tạo ma trận có giá trị
mat2 = [[i * j for j in range(3)] for i in range(3)]
print(mat2)  # [[0,0,0], [0,1,2], [0,2,4]]
```

---

## 6. Các bài toán Matrix thường gặp

### Tìm đường chéo chính
```python
def diagonal_sum(matrix):
    n = len(matrix)
    total = 0
    for i in range(n):
        total += matrix[i][i]
    return total
```

### Xoay ma trận 90 độ
```python
def rotate(matrix):
    n = len(matrix)
    return [[matrix[n-1-j][i] for j in range(n)] for i in range(n)]
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Nhầm row/col
```python
# matrix[row][col]
# matrix[0][1] = row 0, col 1
```

---

### ❌ SAI THỨ 2 — Nhầm shape
```python
mat = [[1,2,3], [4,5,6]]
len(mat)      # 3 (số hàng)
len(mat[0])   # 3 (số cột)
```

---

### ❌ SAI THỨ 3 — Tạo ma trận sai cách
```python
# LỖI - tạo cùng một list!
mat = [[0] * 3] * 3
mat[0][0] = 1  # [[1,0,0], [1,0,0], [1,0,0]]

# ĐÚNG
mat = [[0 for _ in range(3)] for _ in range(3)]
```

---

## 8. Ghi nhớ nhanh

| Thao tác | Cú pháp |
|----------|---------|
| Tạo | `[[...], [...]]` |
| Truy cập | `matrix[r][c]` |
| Số hàng | `len(matrix)` |
| Số cột | `len(matrix[0])` |

**MẸO NHỚ:** Matrix = bảng 2D, hàng trước cột sau.

---

## 9. Mini Test (3 câu)

**Câu 1:** mat[0][1] = ?
> Đáp án: Hàng 0, cột 1

**Câu 2:** Shape của [[1,2],[3,4],[5,6]]?
> Đáp án: 3x2

**Câu 3:** Tổng đường chéo [[1,2],[3,4]]?
> Đáp án: 1 + 4 = 5

---

## 10. LeetCode Practice

### Bài tập: Tìm đường chéo chính
**Yêu cầu:** Tính tổng đường chéo chính ma trận vuông

**Input:**
```
3
1 2 3
4 5 6
7 8 9
```

**Output:** `15` (1+5+9)

**✅ Đáp án:**
```python
n = int(input())
matrix = [list(map(int, input().split())) for _ in range(n)]

total = 0
for i in range(n):
    total += matrix[i][i]
print(total)
```

---

## 11. Bonus Challenge

Xoay ma trận 90 độ theo chiều kim đồng hồ

**Input:**
```
1 2 3
4 5 6
7 8 9
```

**Output:**
```
7 4 1
8 5 2
9 6 3
```

**✅ Đáp án:**
```python
def rotate_90(matrix):
    n = len(matrix)
    return [[matrix[n-1-j][i] for j in range(n)] for i in range(n)]

matrix = [list(map(int, input().split())) for _ in range(len(matrix))]
result = rotate_90(matrix)
for row in result:
    print(*row)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 45 / 2000 |
| **Chapter** | 4 (Data Structures) |
| **XP** | 450 |
| **Mức độ** | Easy |