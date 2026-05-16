# Bài 36 — Encapsulation (Đóng gói)

---

## 1. Ôn tập
Bài 35 đã học Inheritance. Giờ học **Encapsulation** — bảo vệ dữ liệu.

---

## 2. Mục tiêu bài học
- Hiểu encapsulation là gì
- Biết cách dùng private attributes
- Dùng getters và setters
- Property decorators

---

## 3. Code chính (CORE LESSON)

```python
class Nguoi:
    def __init__(self, ten, tuoi):
        self.ten = ten
        self.__tuoi = tuoi  # Private - 2 dấu gạch
    
    def get_tuoi(self):
        return self.__tuoi
    
    def set_tuoi(self, gia_tri):
        if gia_tri > 0:
            self.__tuoi = gia_tri

ng = Nguoi("Minh", 20)
print(ng.ten)      # Minh
# print(ng.__tuoi)  # LỖI! Private
print(ng.get_tuoi())  # 20
ng.set_tuoi(21)
print(ng.get_tuoi())  # 21
```

---

## 4. Property Decorator

```python
class Nguoi:
    def __init__(self, ten):
        self.__ten = ten
    
    @property
    def ten(self):
        return self.__ten
    
    @ten.setter
    def ten(self, gia_tri):
        if gia_tri:
            self.__ten = gia_tri

ng = Nguoi("Minh")
print(ng.ten)    # Minh - dùng như attribute
ng.ten = "Lan"   # Gán bình thường
print(ng.ten)    # Lan
```

---

## 5. Trace luồng chạy

```
ng = Nguoi("Minh", 20)
       ↓
self.ten = "Minh"
self.__tuoi = 20 (__tuoi là private)
       ↓
ng.ten → Trả về "Minh"
ng.__tuoi → LỖI! (private)
ng.get_tuoi() → Trả về 20
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Nhầm _ và __
```python
class A:
    def __init__(self):
        self._x = 1    # Protected (khuyến khích)
        self.__y = 2   # Private (hạn chế truy cập)
```

---

### ❌ SAI THỨ 2 — Vẫn truy cập được private
```python
ng = Nguoi("Minh", 20)
# Python không hoàn toàn private
print(ng._Nguoi__tuoi)  # 20 (name mangling)
# → Không nên dùng cách này!
```

---

### ❌ SAI THỨ 3 — Không cần setter cho tất cả
```python
# Không nên cho phép sửa mọi thứ
class HoSo:
    def __init__(self, id):
        self.__id = id
    
    @property
    def id(self):
        return self.__id
    
    # Không có setter cho id (không cho sửa)
```

---

## 7. Ghi nhớ nhanh

| Quy ước | Ý nghĩa |
|---------|---------|
| `_x` | Protected (khuyến khích không dùng ngoài class) |
| `__x` | Private (hạn chế truy cập) |
| `@property` | Getter - lấy giá trị |
| `@name.setter` | Setter - gán giá trị |

**MẸO NHỚ:** Private = riêng tư. Không cho sửa trực tiếp, phải qua getter/setter.

---

## 8. Mini Test (3 câu)

**Câu 1:** Private attribute ký hiệu là gì?
> Đáp án: `__` (2 dấu gạch dưới)

**Câu 2:** Dùng property để làm gì?
> Đáp án: Đọc/gán như attribute nhưng có kiểm soát

**Câu 3:** Truy cập __x bên ngoài class?
> Đáp án: Lỗi! Phải qua getter

---

## 9. LeetCode Practice

### Bài tập: Class với private salary
**Yêu cầu:** Tạo class NhanVien với salary private, dùng getter/setter

**Input:** `5000`

**Output:** `5000`

**Input:** `-1000`

**Output:** `Luong khong hop le`

**✅ Đáp án:**
```python
class NhanVien:
    def __init__(self, salary):
        self.__salary = salary
    
    @property
    def salary(self):
        return self.__salary
    
    @salary.setter
    def salary(self, value):
        if value > 0:
            self.__salary = value
        else:
            print("Luong khong hop le")

nv = NhanVien(int(input()))
print(nv.salary)
nv.salary = -1000
```

---

## 10. Bonus Challenge

Tạo class BankAccount với:
- Private balance
- deposit() và withdraw() có kiểm tra

**✅ Đáp án:**
```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance
    
    @property
    def balance(self):
        return self.__balance
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            print(f"Da nap {amount}")
        else:
            print("So tien khong hop le")
    
    def withdraw(self, amount):
        if amount > 0 and amount <= self.__balance:
            self.__balance -= amount
            print(f"Da rut {amount}")
        else:
            print("Khong rut duoc")

acc = BankAccount(1000)
acc.deposit(500)
acc.withdraw(200)
print(acc.balance)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 36 / 2000 |
| **Chapter** | 6 (Projects) |
| **XP** | 360 |
| **Mức độ** | Medium |