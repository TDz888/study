# Bài 26 — Default Parameters

---

## 1. Ôn tập
Bài 25 đã học return. Giờ học cách **đặt giá trị mặc định** cho parameter.

---

## 2. Mục tiêu bài học
- Hiểu default parameter là gì
- Biết cách đặt giá trị mặc định
- Quy tắc đặt default parameter
- Ứng dụng thực tế

---

## 3. Code chính (CORE LESSON)

```python
# Hàm có default parameter
def xin_chao(ten="Ban"):
    print(f"Xin chao {ten}!")

xin_chao()        # Xin chao Ban!
xin_chao("Minh")  # Xin chao Minh!
```

**Output:**
```
Xin chao Ban!
Xin chao Minh!
```

---

## 4. Nhiều default parameter

```python
def dien_tich(dai, rong=10):
    return dai * rong

print(dien_tich(5))    # 50 (rong = 10 mặc định)
print(dien_tich(5, 3)) # 15 (rong = 3)
```

---

## 5. Default với các kiểu khác

```python
# Default là string
def gui_email(nguoi="everyone"):
    print(f"Email gui den {nguoi}")

# Default là số
def lap_phuong(x, mu=3):
    return x ** mu

print(lap_phuong(2))   # 8 (2^3)
print(lap_phuong(2, 4)) # 16 (2^4)

# Default là list (CẨN THẬN!)
def them_vao(item, danh_sach=[]):
    danh_sach.append(item)
    return danh_sach

print(them_vao("a"))      # ['a']
print(them_vao("b"))      # ['a', 'b']  ← Bug! list gốc bị thay đổi
```

---

## 6. Sửa lỗi list default

```python
# Cách đúng - dùng None
def them_vao(item, danh_sach=None):
    if danh_sach is None:
        danh_sach = []
    danh_sach.append(item)
    return danh_sach

print(them_vao("a"))  # ['a']
print(them_vao("b"))  # ['b'] ✓
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Default sau required
```python
# LỖI! Default phải đứng SAU
def func(a=1, b):  # SyntaxError
    pass

# Đúng
def func(b, a=1):
    pass
```

---

### ❌ SAI THỨ 2 — Default là list thay đổi
```python
# Bug phổ biến
def add(item, lst=[]):
    lst.append(item)
    return lst

# Fix
def add(item, lst=None):
    if lst is None:
        lst = []
    lst.append(item)
    return lst
```

---

### ❌ SAI THỨ 3 — Gán vào parameter
```python
def func(x=0):
    x = x + 1  # Không thay đổi default
    return x

print(func())  # 1
print(func())  # 1 (luôn là 1)
```

---

## 8. Ghi nhớ nhanh

| Quy tắc | Ví dụ |
|---------|-------|
| Default đứng SAU | `def f(a, b=1):` ✓ |
| Default đứng TRƯỚC | `def f(a=1, b):` ✗ |
| List default | `def f(lst=None):` |

**MẸO NHỚ:** Default = giá trị dự phòng. Luôn đặt ở cuối!

---

## 9. Mini Test (3 câu)

**Câu 1:** Đoán output:
```python
def chao(ten, loi="Xin chao"):
    print(f"{loi} {ten}")

chao("Minh")
```
> Đáp án: `Xin chao Minh`

**Câu 2:** Sửa lỗi:
```python
def ghi(noi_dung="Hello", file):
    print(noi_dung)
```
> Đáp án: `def ghi(file, noi_dung="Hello"):`

**Câu 3:** Giá trị mặc định của `pow(x, y=2)`:
> Đáp án: `y=2` → bình phương

---

## 10. LeetCode Practice

### Bài tập: Hàm lũy thừa với default
**Yêu cầu:** Viết hàm `mu(x, y=2)` trả về x^y

**Input:** `3`

**Output:** `9` (3^2)

**Input:** `3 3`

**Output:** `27` (3^3)

**✅ Đáp án:**
```python
def mu(x, y=2):
    return x ** y

args = input().split()
x = int(args[0])
y = int(args[1]) if len(args) > 1 else 2
print(mu(x, y))
```

---

## 11. Bonus Challenge

Viết hàm format name với title mặc định

**Input:** `Minh`

**Output:** `Mr. Minh`

**Input:** `Lan Miss`

**Output:** `Miss Lan`

**✅ Đáp án:**
```python
def format_name(ten, title="Mr."):
    return f"{title} {ten}"

s = input().split()
if len(s) == 1:
    print(format_name(s[0]))
else:
    print(format_name(s[1], s[0]))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 26 / 2000 |
| **Chapter** | 3 (Functions) |
| **XP** | 260 |
| **Mức độ** | Easy |