# Bài 30 — Recursion (Đệ quy)

---

## 1. Ôn tập
Bài 29 đã học Lambda. Giờ học **Recursion** — hàm gọi chính nó.

---

## 2. Mục tiêu bài học
- Hiểu đệ quy là gì
- Biết cách viết hàm đệ quy
- Hiểu base case và recursive case
- Tránh đệ quy vô hạn

---

## 3. Code chính (CORE LESSON)

```python
# Đếm ngược đệ quy
def dem_nguoc(n):
    if n <= 0:  # Base case - dừng
        print("Het!")
        return
    print(n)
    dem_nguoc(n - 1)  # Recursive case - gọi lại chính mình

dem_nguoc(5)
```

**Output:**
```
5
4
3
2
1
Het!
```

---

## 4. Cấu trúc đệ quy

```
Đệ quy gồm 2 phần:

1. BASE CASE (điểm dừng)
   → Khi này thì DỪNG, không gọi nữa

2. RECURSIVE CASE (gọi đệ quy)
   → Thu nhỏ bài toán
   → Gọi lại chính mình
```

**Ví dụ giai thừa:**
```python
# n! = n * (n-1)!
# 5! = 5 * 4 * 3 * 2 * 1 = 120

def giai_thua(n):
    if n <= 1:  # Base case
        return 1
    return n * giai_thua(n - 1)  # Recursive case

print(giai_thua(5))  # 120
```

---

## 5. Trace luồng chạy

```
giai_thua(5)
  = 5 * giai_thua(4)
  = 5 * 4 * giai_thua(3)
  = 5 * 4 * 3 * giai_thua(2)
  = 5 * 4 * 3 * 2 * giai_thua(1)
  = 5 * 4 * 3 * 2 * 1  (base case)
  = 120
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Không có base case
```python
def dem_nguoc(n):
    print(n)
    dem_nguoc(n - 1)  # Không dừng → vô hạn!

# Sửa - thêm base case
def dem_nguoc(n):
    if n <= 0:
        return
    print(n)
    dem_nguoc(n - 1)
```

---

### ❌ SAI THỨ 2 — Base case sai
```python
def giai_thua(n):
    if n == 0:  # Sửa thành <= 1
        return 1
    return n * giai_thua(n - 1)

print(giai_thua(1))  # 1 * giai_thua(0) = 1 * 1 = 1 ✓
print(giai_thua(0))  # 1 ✓
```

---

### ❌ SAI THỨ 3 — Đệ quy quá sâu
```python
# Gọi 10000 lần → RecursionError
def deep(n):
    if n <= 0:
        return
    return deep(n - 1)

deep(10000)  # LỖI!
```

---

## 7. Ghi nhớ nhanh

| Thành phần | Ý nghĩa |
|------------|---------|
| **Base case** | Điều kiện dừng |
| **Recursive case** | Gọi lại với bài toán nhỏ hơn |
| **Stack overflow** | Đệ quy quá sâu |

**MẸO NHỚ:** Đệ quy = lặp lại. Cần base case để dừng.

---

## 8. Mini Test (3 câu)

**Câu 1:** Đoán kết quả:
```python
def demo(n):
    if n <= 0:
        return
    print(n)
    demo(n - 1)

demo(3)
```
> Đáp án: `3 2 1`

**Câu 2:** `demo(0)` in gì?
> Đáp án: Không in gì (base case dừng ngay)

**Câu 3:** Giai thừa 4! = ?
> Đáp án: `24` (4×3×2×1)

---

## 9. LeetCode Practice

### Bài tập: Tính Fibonacci
**Yêu cầu:** Viết hàm đệ quy tính Fibonacci
- F(0) = 0
- F(1) = 1
- F(n) = F(n-1) + F(n-2)

**Input:** `10`

**Output:** `55`

**✅ Đáp án:**
```python
def fibonacci(n):
    if n <= 0:
        return 0
    if n == 1:
        return 1
    return fibonacci(n - 1) + fibonacci(n - 2)

n = int(input())
print(fibonacci(n))
```

---

## 10. Bonus Challenge

Đếm số chữ số của số nguyên bằng đệ quy

**Input:** `12345`

**Output:** `5`

**✅ Đáp án:**
```python
def dem_chu_so(n):
    if n < 10:
        return 1
    return 1 + dem_chu_so(n // 10)

n = int(input())
print(dem_chu_so(n))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 30 / 2000 |
| **Chapter** | 3 (Functions) |
| **XP** | 300 |
| **Mức độ** | Medium |