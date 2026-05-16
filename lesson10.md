# Bài 10 — Vòng lặp For

---

## 1. Ôn tập
Bài 9 đã học `and`, `or`, `not` để kết hợp điều kiện. Giờ học **vòng lặp** — lặp lại code.

---

## 2. Mục tiêu bài học
- Hiểu vòng lặp là gì
- Biết cách dùng `for` với range
- Hiểu vòng lặp đếm
- Thực hành với các bài toán lặp

---

## 3. Code chính (có comment)

```python
# In số từ 1 đến 5
for i in range(1, 6):
    print(i)

print("---")

# In số chẵn từ 0 đến 10
for i in range(0, 11, 2):
    print(i)
```

**Output:**
```
1
2
3
4
5
---
0
2
4
6
8
10
```

---

## 4. Trace chạy code

```
range(1, 6) tạo: [1, 2, 3, 4, 5]

Vòng lặp:
i = 1 → print(1)
i = 2 → print(2)
i = 3 → print(3)
i = 4 → print(4)
i = 5 → print(5)
i = 6 → KHÔNG có trong range → DỪNG
```

**range(a, b, c):**
- `a`: bắt đầu (inclusive)
- `b`: kết thúc (exclusive)
- `c`: bước nhảy

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Nhầm range(a, b) và range(a, b + 1)
```python
# In 1 đến 5 - SAI
for i in range(1, 5):  # Chỉ in 1, 2, 3, 4
    print(i)

# ĐÚNG
for i in range(1, 6):  # In 1, 2, 3, 4, 5
    print(i)
```

### ❌ Lỗi 2 — Quên thụt vào
```python
for i in range(5):
print(i)  # LỖI! Phải thụt vào
```

### ❌ Lỗi 3 — range(5) bắt đầu từ 0
```python
for i in range(5):
    print(i)
# Output: 0, 1, 2, 3, 4 (bắt đầu từ 0)
```

---

## 6. Ghi nhớ nhanh

| Cú pháp | Kết quả |
|---------|---------|
| `range(5)` | 0, 1, 2, 3, 4 |
| `range(1, 5)` | 1, 2, 3, 4 |
| `range(0, 10, 2)` | 0, 2, 4, 6, 8 |
| `range(5, 0, -1)` | 5, 4, 3, 2, 1 |

**MẸO NHỚ:** `range(a, b)` = từ `a` đến `b-1`

---

## 7. Mini test (3 câu)

**Câu 1:** `range(3)` tạo ra gì?
> Đáp án: `[0, 1, 2]`

**Câu 2:** In số 5, 10, 15, 20 dùng range?
```python
for i in range(5, 25, 5):
    print(i)
```

**Câu 3:** Sửa để in 1 đến 10:
```python
for i in range(10):  # Lỗi?
    print(i + 1)
```
> Đáp án: `for i in range(1, 11):`

---

## 8. LeetCode practice

**Bài tập:** In bảng cửu chương 5

**Input:** (không có input)

**Output:**
```
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
5 x 4 = 20
5 x 5 = 25
5 x 6 = 30
5 x 7 = 35
5 x 8 = 40
5 x 9 = 45
5 x 10 = 50
```

**Khung code:**
```python
# Viết code vào đây
```

**✅ Đáp án:**
```python
for i in range(1, 11):
    print("5 x", i, "=", 5 * i)
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** In tam giác sao:
```
*
**
***
****
*****
```

**Khung code:**
```python
n = 5
# Viết tiếp vào đây
```

**✅ Đáp án:**
```python
n = 5
for i in range(1, n + 1):
    print("*" * i)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 10 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 100 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 10!** 

Gõ **11** để học tiếp Bài 11 (Vòng lặp While) →