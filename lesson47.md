# Bài 47 — Bit Manipulation

---

## 1. Ôn tập
Bài 46 đã học Math Problems. Giờ học **Bit Manipulation** — thao tác bit.

---

## 2. Mục tiêu bài học
- Các toán tử bit cơ bản
- AND, OR, XOR, NOT
- Left/Right shift
- Ứng dụng

---

## 3. Các toán tử Bit

```python
# AND (&) - cả 2 bit = 1 → 1
print(5 & 3)   # 101 & 011 = 001 = 1

# OR (|) - 1 trong 2 bit → 1
print(5 | 3)   # 101 | 011 = 111 = 7

# XOR (^) - khác nhau → 1
print(5 ^ 3)   # 101 ^ 011 = 110 = 6

# NOT (~) - đảo bit
print(~5)      # -6 (bù 2)
```

**Output:**
```
1
7
6
-6
```

---

## 4. Shift

```python
# Left shift (<<) - nhân 2^n
print(5 << 1)  # 10 (5*2)
print(5 << 2)  # 20 (5*4)

# Right shift (>>) - chia 2^n
print(10 >> 1)  # 5 (10/2)
print(10 >> 2)   # 2 (10/4)
```

---

## 5. Ứng dụng

### Kiểm tra bit thứ n
```python
def check_bit(n, i):
    return (n >> i) & 1

print(check_bit(5, 0))  # 1 (5=101)
print(check_bit(5, 1))  # 0
print(check_bit(5, 2))  # 1
```

### Đặt bit thứ n
```python
def set_bit(n, i):
    return n | (1 << i)

print(set_bit(4, 1))  # 6 (100 | 010 = 110)
```

### Xóa bit thứ n
```python
def clear_bit(n, i):
    return n & ~(1 << i)

print(clear_bit(6, 1))  # 4 (110 & ~010 = 110 & 101 = 100)
```

---

## 6. Số nhị phân

```python
# Chuyển đổi
print(bin(5))    # 0b101
print(int("101", 2))  # 5

# Format
print(format(5, '08b'))  # 00000101
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Nhầm & và and
```python
# & là bitwise, and là boolean
print(5 and 3)  # 3 (truthy)
print(5 & 3)    # 1 (bitwise)
```

---

### ❌ SAI THỨ 2 — Shift quá mức
```python
# 32-bit system: shift > 31 có thể sai
# Python OK nhưng nên cẩn thận
```

---

### ❌ SAI THỨ 3 — Xử lý số âm
```python
# Số âm dùng 2's complement
print(-5 & 0xFFFFFFFF)  # 4294967291
```

---

## 8. Ghi nhớ nhanh

| Toán tử | Ý nghĩa | Ví dụ |
|---------|--------|-------|
| `&` | AND | 1&1=1 |
| `\|` | OR | 1\|0=1 |
| `^` | XOR | 1^0=1 |
| `<<` | Left shift | n<<1 = n*2 |
| `>>` | Right shift | n>>1 = n/2 |

**MẸO NHỚ:** Bit = nhị phân, thao tác trên bit đơn vị.

---

## 9. Mini Test (3 câu)

**Câu 1:** 5 | 3 = ?
> Đáp án: `7`

**Câu 2:** 8 >> 1 = ?
> Đáp án: `4`

**Câu 3:** Bit thứ 2 của 5 (101)?
> Đáp án: `1`

---

## 10. LeetCode Practice

### Bài tập: Đếm bit 1
**Yêu cầu:** Đếm số bit 1 trong số nhị phân

**Input:** `11`

**Output:** `3` (1011)

**✅ Đáp án:**
```python
def count_bits(n):
    count = 0
    while n:
        n &= (n - 1)
        count += 1
    return count

print(count_bits(int(input())))
```

---

## 11. Bonus Challenge

Tìm số chỉ khác nhau một bit

**Input:** `5 4`

**Output:** `1` (5=101, 4=100, khác bit thứ 3)

**✅ Đáp án:**
```python
def hamming_distance(x, y):
    xor = x ^ y
    count = 0
    while xor:
        xor &= (xor - 1)
        count += 1
    return count

x, y = map(int, input().split())
print(hamming_distance(x, y))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 47 / 2000 |
| **Chapter** | 5 (LeetCode) |
| **XP** | 470 |
| **Mức độ** | Medium |