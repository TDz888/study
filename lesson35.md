# Bài 35 — Classes và Objects (P2)

---

## 1. Ôn tập
Bài 34 đã học tạo class và object. Giờ học **kế thừa** trong OOP.

---

## 2. Mục tiêu bài học
- Hiểu kế thừa là gì
- Biết cách tạo class con kế thừa class cha
- Override methods
- Dùng super()

---

## 3. Code chính (CORE LESSON)

```python
# Class cha
class DongVat:
    def __init__(self, ten):
        self.ten = ten
        
    def an(self):
        print(f"{self.ten} dang an")

# Class con kế thừa
class Cho(DongVat):
    def sua(self):
        print(f"{self.ten} keu: Gau Gau!")

# Tạo object
cho1 = Cho("Buddy")
cho1.an()    # Từ class cha
cho1.sua()   # Từ class con
```

**Output:**
```
Buddy dang an
Buddy keu: Gau Gau!
```

---

## 4. Override (Ghi đè)

```python
class DongVat:
    def tieng_keu(self):
        print("Tieng keu")

class Meo(DongVat):
    def tieng_keu(self):  # Override
        print("Meo meo")

meo = Meo()
meo.tieng_keu()  # Meo meo (không phải Tieng keu)
```

---

## 5. Super() - Gọi từ class cha

```python
class Nguoi:
    def __init__(self, ten):
        self.ten = ten

class SinhVien(Nguoi):
    def __init__(self, ten, msv):
        super().__init__(ten)  # Gọi __init__ của class cha
        self.msv = msv

sv = SinhVien("Minh", "SV001")
print(sv.ten, sv.msv)  # Minh SV001
```

---

## 6. Multiple Inheritance

```python
class Cha:
    def say(self):
        print("Cha noi")

class Me:
    def say(self):
        print("Me noi")

class Con(Cha, Me):
    pass

c = Con()
c.say()  # "Cha noi" - ưu tiên Cha
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Không gọi super().__init__
```python
class Con(Cha):
    def __init__(self, a, b):
        self.a = a
        # Quên gọi Cha.__init__(b) → lỗi
```

---

### ❌ SAI THỨ 2 — Class con không kế thừa đủ
```python
# Cha có method an() nhưng Con không gọi được
# Vì không có kế thừa đúng cách
class Con(Cha):  # Cần extends Cha!
```

---

### ❌ SAI THỨ 3 — Override sai
```python
class A:
    def test(self):
        print("A")

class B(A):
    def test(self, x):  # Đây là OVERLOAD, không phải override
        print("B", x)
        
b = B()
b.test()  # LỖI! Cần truyền x
```

---

## 8. Ghi nhớ nhanh

| Khái niệm | Ý nghĩa |
|-----------|--------|
| **Inheritance** | Kế thừa từ class cha |
| **Override** | Ghi đè method của cha |
| **super()** | Gọi method của class cha |

**MẸO NHỚ:** Kế thừa = con thừa hưởng từ cha (gen, đặc điểm).

---

## 9. Mini Test (3 câu)

**Câu 1:** Class B kế thừa A, A có method x(). B dùng được không?
> Đáp án: Có, tất cả methods của A đều được kế thừa

**Câu 2:** Override để làm gì?
> Đáp án: Thay đổi hành vi của method cha

**Câu 3:** super().__init__() dùng để làm gì?
> Đáp án: Gọi hàm khởi tạo của class cha

---

## 10. LeetCode Practice

### Bài tập: Class NhanVien kế thừa ConNguoi
**Yêu cầu:** Tạo class NhanVien kế thừa từ class Nguoi

**Input:** `Minh 20 1000`

**Output:**
```
Ten: Minh, Tuoi: 20
Luong: 1000
```

**✅ Đáp án:**
```python
class Nguoi:
    def __init__(self, ten, tuoi):
        self.ten = ten
        self.tuoi = tuoi
    
    def info(self):
        print(f"Ten: {self.ten}, Tuoi: {self.tuoi}")

class NhanVien(Nguoi):
    def __init__(self, ten, tuoi, luong):
        super().__init__(ten, tuoi)
        self.luong = luong
    
    def info(self):
        super().info()
        print(f"Luong: {self.luong}")

ten, tuoi, luong = input().split()
nv = NhanVien(ten, int(tuoi), luong)
nv.info()
```

---

## 11. Bonus Challenge

Tạo class HCN và HinhVuong (kế thừa từ HCN)

**✅ Đáp án:**
```python
class HinhChuNhat:
    def __init__(self, dai, rong):
        self.dai = dai
        self.rong = rong
    
    def dien_tich(self):
        return self.dai * self.rong

class HinhVuong(HinhChuNhat):
    def __init__(self, canh):
        super().__init__(canh, canh)

hv = HinhVuong(5)
print(hv.dien_tich())  # 25
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 35 / 2000 |
| **Chapter** | 6 (Projects) |
| **XP** | 350 |
| **Mức độ** | Medium |