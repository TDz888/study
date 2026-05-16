# Bài 34 — Classes và Objects (P1)

---

## 1. Ôn tập
Bài 33 đã học Exception. Giờ bắt đầu **OOP** — Lập trình hướng đối tượng.

---

## 2. Mục tiêu bài học
- Hiểu class là gì
- Hiểu object là gì
- Biết cách tạo class và object
- Hiểu attributes và methods

---

## 3. Code chính (CORE LESSON)

```python
# Định nghĩa class
class Xe:
    # Attributes (thuộc tính)
    ten = "Toyota"
    mau = "Do"
    
    # Methods (phương thức)
    def chay(self):
        print("Xe dang chay!")

# Tạo object
oto = Xe()

# Truy cập attributes
print(oto.ten)  # Toyota
print(oto.mau)  # Do

# Gọi methods
oto.chay()     # Xe dang chay!
```

**Output:**
```
Toyota
Do
Xe dang chay!
```

---

## 4. Constructor (init)

```python
class Nguoi:
    def __init__(self, ten, tuoi):
        self.ten = ten
        self.tuoi = tuoi
        
    def noi(self):
        print(f"Xin chao, toi la {self.ten}")

# Tạo object với dữ liệu
nguoi1 = Nguoi("Minh", 20)
nguoi2 = Nguoi("Lan", 18)

print(nguoi1.ten)  # Minh
nguoi1.noi()      # Xin chao, toi la Minh
```

**Output:**
```
Minh
Xin chao, toi la Minh
```

---

## 5. Trace luồng chạy

```
class Nguoi:
    def __init__(self, ten, tuoi):
        self.ten = ten
        self.tuoi = tuoi

nguoi1 = Nguoi("Minh", 20)
       ↓
__init__("Minh", 20) được gọi
       ↓
self.ten = "Minh" → lưu vào object
self.tuoi = 20 → lưu vào object
       ↓
nguoi1 là object với ten="Minh", tuoi=20
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Quên self trong methods
```python
class A:
    def say_hello():
        print("Hello")  # LỖI!

# Đúng
def say_hello(self):
    print("Hello")
```

---

### ❌ SAI THỨ 2 — Gọi hàm với lớp thay vì object
```python
class Xe:
    def chay(self):
        print("Chay")

# LỖI
Xe.chay()  # Thiếu self

# Đúng
oto = Xe()
oto.chay()
```

---

### ❌ SAI THỨ 3 — Gán giá trị cho biến global trong class
```python
x = 5  # Biến global

class Test:
    def set_x(self):
        x = 10  # Tạo biến local mới!
        
# Muốn gán vào biến global:
def set_x(self):
    global x
    x = 10
```

---

## 7. Ghi nhớ nhanh

| Khái niệm | Giải thích |
|-----------|------------|
| **Class** | Bản mẫu/khuôn mẫu |
| **Object** | Thực thể từ class |
| **__init__** | Hàm khởi tạo |
| **self** | Tham chiếu đến object hiện tại |
| **attribute** | Biến trong class |
| **method** | Hàm trong class |

**MẸO NHỚ:** Class = khuôn bánh, Object = chiếc bánh làm từ khuôn.

---

## 8. Mini Test (3 câu)

**Câu 1:** Đoán output:
```python
class A:
    x = 5
    
a = A()
print(a.x)
```
> Đáp án: `5`

**Câu 2:** __init__ dùng để làm gì?
> Đáp án: Khởi tạo object với giá trị ban đầu

**Câu 3:** self trong method là gì?
> Đáp án: Tham chiếu đến object đang thao tác

---

## 9. LeetCode Practice

### Bài tập: Class Hình chữ nhật
**Yêu cầu:** Tạo class HCN với:
- chiều dài, rộng trong __init__
- method diện tích()

**Input:** `5 3`

**Output:** `15`

**✅ Đáp án:**
```python
class HinhChuNhat:
    def __init__(self, dai, rong):
        self.dai = dai
        self.rong = rong
        
    def dien_tich(self):
        return self.dai * self.rong

d, r = map(int, input().split())
hcn = HinhChuNhat(d, r)
print(hcn.dien_tich())
```

---

## 10. Bonus Challenge

Thêm method chu_vi() vào class HCN

**Input:** `5 3`

**Output:**
```
Dien tich: 15
Chu vi: 16
```

**✅ Đáp án:**
```python
class HinhChuNhat:
    def __init__(self, dai, rong):
        self.dai = dai
        self.rong = rong
        
    def dien_tich(self):
        return self.dai * self.rong
    
    def chu_vi(self):
        return (self.dai + self.rong) * 2

d, r = map(int, input().split())
hcn = HinhChuNhat(d, r)
print(f"Dien tich: {hcn.dien_tich()}")
print(f"Chu vi: {hcn.chu_vi()}")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 34 / 2000 |
| **Chapter** | 6 (Projects) |
| **XP** | 340 |
| **Mức độ** | Medium |