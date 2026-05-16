# Bài 31 — Modules và Import

---

## 1. Ôn tập
Bài 30 đã học Recursion. Giờ học cách **tổ chức code** với Modules.

---

## 2. Mục tiêu bài học
- Hiểu module là gì
- Biết cách import module
- Các cách import khác nhau
- Tạo module riêng

---

## 3. Code chính (CORE LESSON)

```python
# Import toàn bộ
import math

print(math.sqrt(16))  # 4.0
print(math.pi)        # 3.14159...
print(math.floor(3.7))  # 3
```

**Output:**
```
4.0
3.141592653589793
3
```

---

## 4. Các cách Import

```python
# Cách 1: Import toàn bộ
import math

# Cách 2: Import cụ thể
from math import sqrt, pi

# Cách 3: Import với alias
import math as m
from datetime import datetime as dt

# Cách 4: Import tất cả (không nên dùng)
from math import *
```

---

## 5. Các Module thường dùng

```python
# math - Toán học
import math
print(math.factorial(5))  # 120
print(math.pow(2, 3))     # 8.0

# random - Số ngẫu nhiên
import random
print(random.randint(1, 10))  # Số ngẫu nhiên 1-10
print(random.choice(["a", "b", "c"]))  # Chọn ngẫu nhiên

# datetime - Thời gian
import datetime
now = datetime.datetime.now()
print(now.year, now.month, now.day)
```

---

## 6. Tạo module riêng

```python
# file: mymodule.py
def chao(ten):
    return f"Xin chao {ten}"

def cong(a, b):
    return a + b

# -----------------
# sử dụng:
import mymodule

print(mymodule.chao("Minh"))  # Xin chao Minh
print(mymodule.cong(5, 3))    # 8
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Import không tồn tại
```python
import mathh  # LỖI! Thư viện không tồn tại
# Đúng: import math
```

---

### ❌ SAI THỨ 2 — Dùng hàm không import
```python
import math
# sqrt là của math
print(sqrt(16))  # LỖI! Phải math.sqrt(16)
```

---

### ❌ SAI THỨ 3 — Tên module trùng
```python
# file có tên trùng với thư viện
# import datetime  # LỖI! File datetime.py chặn thư viện
# Đặt tên khác: mydatetime.py
```

---

## 8. Ghi nhớ nhanh

| Cú pháp | Ý nghĩa |
|---------|---------|
| `import module` | Import toàn bộ |
| `from m import x` | Import cụ thể |
| `import m as alias` | Import với tên mới |
| `m.function()` | Gọi hàm từ module |

**MẸO NHỚ:** Module = thư viện. Import = mượn code người khác.

---

## 9. Mini Test (3 câu)

**Câu 1:** Import hàm sqrt từ math:
> Đáp án: `from math import sqrt`

**Câu 2:** Tính 2^10:
> Đáp án: `math.pow(2, 10)` hoặc `2 ** 10`

**Câu 3:** Số ngẫu nhiên 1-100:
> Đáp án: `random.randint(1, 100)`

---

## 10. LeetCode Practice

### Bài tập: Tính khoảng cách
**Yêu cầu:** Tính khoảng cách 2 điểm (x1, y1) và (x2, y2)
- Công thức: √((x2-x1)² + (y2-y1)²)

**Input:** `1 1 4 4`

**Output:** `4.242640687119285`

**✅ Đáp án:**
```python
import math

x1, y1, x2, y2 = map(int, input().split())
distance = math.sqrt((x2 - x1)**2 + (y2 - y1)**2)
print(distance)
```

---

## 11. Bonus Challenge

Tạo module tính toán và sử dụng

**✅ Đáp án:**
```python
# File calc.py
def phep_cong(a, b):
    return a + b

def phep_tru(a, b):
    return a - b

# Main
import calc
print(calc.phep_cong(10, 5))  # 15
print(calc.phep_tru(10, 5))   # 5
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 31 / 2000 |
| **Chapter** | 3 (Functions) |
| **XP** | 310 |
| **Mức độ** | Easy |