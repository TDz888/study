# Bài 37 — Magic Methods

---

## 1. Ôn tập
Bài 36 đã học Encapsulation. Giờ học **Magic Methods** — các method đặc biệt.

---

## 2. Mục tiêu bài học
- Hiểu magic methods là gì
- Biết các magic methods thường dùng
- Tự định nghĩa cho class
- Áp dụng vào thực tế

---

## 3. Code chính (CORE LESSON)

```python
class So:
    def __init__(self, gia_tri):
        self.gia_tri = gia_tri
    
    def __str__(self):  # str() gọi
        return f"So: {self.gia_tri}"
    
    def __repr__(self):  # repr() gọi
        return f"So({self.gia_tri})"
    
    def __add__(self, other):  # a + b
        return self.gia_tri + other.gia_tri
    
    def __len__(self):  # len()
        return 1

s = So(5)
print(str(s))     # So: 5
print(repr(s))    # So(5)
```

**Output:**
```
So: 5
So(5)
```

---

## 4. Các Magic Methods thường dùng

```python
class So:
    def __init__(self, x):
        self.x = x
    
    def __str__(self):
        return str(self.x)
    
    def __repr__(self):
        return f"So({self.x})"
    
    def __add__(self, other):      # +
        return So(self.x + other.x)
    
    def __sub__(self, other):      # -
        return So(self.x - other.x)
    
    def __mul__(self, other):      # *
        return So(self.x * other.x)
    
    def __eq__(self, other):       # ==
        return self.x == other.x
    
    def __lt__(self, other):       # <
        return self.x < other.x
    
    def __len__(self):
        return self.x

s1 = So(5)
s2 = So(3)
print(s1 + s2)  # So(8)
print(s1 == So(5))  # True
print(s1 < So(10))  # True
```

---

## 5. Trace luồng chạy

```
s1 = So(5)
s2 = So(3)

s1 + s2
       ↓
__add__(s1, s2)
       ↓
return So(5 + 3) = So(8)
       ↓
In ra: So(8)
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Quên tham số self và other
```python
def __add__(other):  # Thiếu self!
    return self.x + other.x
```

---

### ❌ SAI THỨ 2 — Trả về kiểu sai
```python
def __add__(self, other):
    # Nên trả về So (class) thay vì int
    return self.x + other.x  # In ra được nhưng không đúng pattern
```

---

### ❌ SAI THỨ 3 — Tất cả đều cần self
```python
def __str__(self):
    return f"{self.x}"  # Phải có self!
```

---

## 7. Ghi nhớ nhanh

| Magic Method | Khi nào gọi |
|--------------|-------------|
| `__init__` | Tạo object |
| `__str__` | print() hoặc str() |
| `__repr__` | repr() hoặc debugging |
| `__add__` | Toán tử + |
| `__eq__` | So sánh == |
| `__lt__` | So sánh < |
| `__len__` | len() |

**MẸO NHỚ:** Magic methods = "phép thuật" → tự định nghĩa toán tử.

---

## 8. Mini Test (3 câu)

**Câu 1:** Dùng __add__ để làm gì?
> Đáp án: Định nghĩa toán tử +

**Câu 2:** print(s) gọi method nào?
> Đáp án: `__str__`

**Câu 3:** len(obj) gọi method nào?
> Đáp án: `__len__`

---

## 9. LeetCode Practice

### Bài tập: Class PhanSo với cộng/trừ
**Yểu cầu:** Định nghĩa __add__ và __str__ cho PhanSo

**Input:** `1/2 + 3/4`

**Output:** `PhanSo(tu=10, mau=8)`

**✅ Đáp án:**
```python
class PhanSo:
    def __init__(self, tu, mau):
        self.tu = tu
        self.mau = mau
    
    def __str__(self):
        return f"PhanSo(tu={self.tu}, mau={self.mau})"
    
    def __add__(self, other):
        tu_moi = self.tu * other.mau + other.tu * self.mau
        mau_moi = self.mau * other.mau
        return PhanSo(tu_moi, mau_moi)

ps1 = PhanSo(1, 2)
ps2 = PhanSo(3, 4)
print(ps1 + ps2)
```

---

## 10. Bonus Challenge

So sánh 2 PhanSo (tu/mau)

**Input:** `1 2 vs 3 6`

**Output:** `Bang nhau` (1/2 = 3/6)

**✅ Đáp án:**
```python
class PhanSo:
    def __init__(self, tu, mau):
        self.tu = tu
        self.mau = mau
    
    def __eq__(self, other):
        return self.tu * other.mau == other.tu * self.mau

ps1 = PhanSo(1, 2)
ps2 = PhanSo(3, 6)
if ps1 == ps2:
    print("Bang nhau")
else:
    print("Khong bang")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 37 / 2000 |
| **Chapter** | 6 (Projects) |
| **XP** | 370 |
| **Mức độ** | Medium |