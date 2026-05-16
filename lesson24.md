# Bài 24 — Hàm (Functions) (P1)

---

## 1. Ôn tập
Bài 23 đã học Set. Giờ bắt đầu Chương 3 — **Functions** (Hàm).

---

## 2. Mục tiêu bài học
- Hiểu function là gì
- Biết cách định nghĩa hàm
- Hiểu parameter và argument
- Gọi hàm đúng cách

---

## 3. Code chính (CORE LESSON)

```python
# Định nghĩa hàm
def chao_hoi():
    print("Xin chao!")

# Gọi hàm
chao_hoi()
chao_hoi()
```

**Output:**
```
Xin chao!
Xin chao!
```

---

## 4. Hàm có parameter

```python
# Parameter - tham số
def chao_hoi(ten):
    print("Xin chao", ten)

# Argument - đối số
chao_hoi("Minh")   # Xin chao Minh
chao_hoi("Nam")    # Xin chao Nam
```

**Output:**
```
Xin chao Minh
Xin chao Nam
```

---

## 5. Hàm có nhiều parameter

```python
def cong(a, b):
    print(f"{a} + {b} = {a + b}")

cong(5, 3)      # 5 + 3 = 8
cong(10, 20)    # 10 + 20 = 30
```

**Output:**
```
5 + 3 = 8
10 + 20 = 30
```

---

## 6. Trace luồng chạy

```
def chao_hoi(ten):
    print("Xin chao", ten)

chao_hoi("Minh")
       ↓
a = "Minh" được gán cho parameter ten
       ↓
In ra: "Xin chao Minh"
       ↓
 Quay lại chỗ gọi
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Gọi hàm trước khi định nghĩa
```python
xin_chao()  # LỖI! Chưa định nghĩa

def xin_chao():
    print("Xin chao")
```

---

### ❌ SAI THỨ 2 — Sai số lượng argument
```python
def cong(a, b):
    print(a + b)

cong(5)       # LỖI! Thiếu argument
cong(5, 3, 2)  # LỖI! Thừa argument
```

---

### ❌ SAI THỨ 3 — Quên dấu ()
```python
def chao():
    print("Xin chao")

chao  # LỖI! Không gọi hàm
chao()  # Đúng
```

---

## 8. Ghi nhớ nhanh

| Khái niệm | Giải thích |
|-----------|------------|
| **Function** | Khối code có tên, dùng lại được |
| **def** | Từ khóa định nghĩa hàm |
| **Parameter** | Biến trong định nghĩa hàm |
| **Argument** | Giá trị truyền vào khi gọi |
| **Call** | Gọi hàm để chạy |

**MẸO NHỚ:** Function = công thức nấu ăn. Định nghĩa 1 lần, dùng nhiều lần.

---

## 9. Mini Test (3 câu)

**Câu 1:** Output là gì?
```python
def in_so(x):
    print(x)

in_so(5)
```
> Đáp án: `5`

**Câu 2:** Định nghĩa hàm tính bình phương:
```python
def binh_phuong(x):
    return x ** 2
```

**Câu 3:** Gọi hàm với argument 4:
> Đáp án: `binh_phuong(4)` → `16`

---

## 10. LeetCode Practice

### Bài tập: Hàm kiểm tra chẵn/lẻ
**Yêu cầu:** Viết hàm `kiem_tra_chan(n)`, trả về True nếu chẵn

**Input:** `8`

**Output:** `True`

**✅ Đáp án:**
```python
def kiem_tra_chan(n):
    return n % 2 == 0

n = int(input())
print(kiem_tra_chan(n))
```

---

## 11. Bonus Challenge

Viết hàm tính BMI:
- BMI = cân nặng / (chiều cao ^ 2)
- cân nặng: kg, chiều cao: m

**Input:** `70 1.75`

**Output:** `22.86`

**✅ Đáp án:**
```python
def tinh_bmi(can_nang, chieu_cao):
    return can_nang / (chieu_cao ** 2)

cn, cc = map(float, input().split())
print(f"{tinh_bmi(cn, cc):.2f}")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 24 / 2000 |
| **Chapter** | 3 (Functions) |
| **XP** | 240 |
| **Mức độ** | Easy |