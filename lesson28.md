# Bài 28 — Scope (Phạm vi biến)

---

## 1. Ôn tập
Bài 27 đã học *args và **kwargs. Giờ học về **Scope** — phạm vi của biến.

---

## 2. Mục tiêu bài học
- Hiểu local scope và global scope
- Biết cách dùng `global` khi cần
- Tránh lỗi liên quan đến scope

---

## 3. Code chính (CORE LESSON)

```python
# Local scope - Biến trong hàm
def func():
    x = 10  # Biến local
    print(x)

func()
# print(x)  # LỖI! x không tồn tại bên ngoài

# Global scope - Biến ngoài hàm
y = 5

def func2():
    print(y)  # Có thể đọc biến global

func2()
```

**Output:**
```
10
5
```

---

## 4. Local và Global cùng tên

```python
x = "global"

def func():
    x = "local"  # Biến local, không ảnh hưởng global
    print(x)

print(x)  # global
func()    # local
print(x)  # global (không đổi)
```

**Output:**
```
global
local
global
```

---

## 5. Global keyword

```python
x = 5

def tang_x():
    global x  # Báo hiệu dùng biến global
    x = x + 1

print(x)  # 5
tang_x()
print(x)  # 6
```

---

## 6. Sơ đồ Scope

```
┌─────────────────────┐
│  Global Scope       │
│  x = 5              │
│  ┌───────────────┐  │
│  │ Local Scope   │  │
│  │ x = 10        │  │
│  │ (chỉ trong    │  │
│  │  hàm này)     │  │
│  └───────────────┘  │
└─────────────────────┘
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Gán biến trong hàm mà không khai báo
```python
x = 5

def func():
    x = x + 1  # LỖI! Local x chưa có giá trị

# Sửa 1: Dùng global
def func():
    global x
    x = x + 1

# Sửa 2: Return
def func(x):
    return x + 1

x = func(x)
```

---

### ❌ SAI THỨ 2 — Biến local không tồn tại ngoài hàm
```python
def func():
    local_var = 10

func()
print(local_var)  # NameError!
```

---

### ❌ SAI THỨ 3 — Dùng global không cần thiết
```python
# Bad practice - nên return thay vì global
def func():
    global result
    result = 10

# Good practice
def func():
    return 10

result = func()
```

---

## 8. Ghi nhớ nhanh

| Scope | Từ khóa | Tồn tại |
|-------|---------|---------|
| **Global** | Không có | Toàn bộ chương trình |
| **Local** | Trong def | Chỉ trong hàm |
| **global** | `global x` | Cho phép sửa global |

**MẸO NHỚ:** Local = phạm vi cục bộ (trong nhà), Global = toàn cầu (khắp nơi).

---

## 9. Mini Test (3 câu)

**Câu 1:** Output là gì?
```python
x = 1

def func():
    x = 2
    print(x)

print(x)
func()
```
> Đáp án: `1` và `2`

**Câu 2:** Sửa để hàm tăng x thêm 1:
```python
x = 5
def tang():
    global x
    x = x + 1
```

**Câu 3:** Biến trong hàm gọi là gì?
> Đáp án: Local variable

---

## 10. LeetCode Practice

### Bài tập: Đếm số lần gọi hàm
**Yêu cầu:** Đếm số lần gọi hàm `greet()`

**Gọi 3 lần greet()**

**Output:**
```
Lan 1
Lan 2
Lan 3
```

**✅ Đáp án:**
```python
count = 0

def greet():
    global count
    count += 1
    print(f"Lan {count}")

greet()
greet()
greet()
```

---

## 11. Bonus Challenge

Viết hàm với counter không dùng global (dùng closure)

**✅ Đáp án:**
```python
def make_counter():
    count = 0
    def counter():
        nonlocal count
        count += 1
        return count
    return counter

cnt = make_counter()
print(cnt())  # 1
print(cnt())  # 2
print(cnt())  # 3
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 28 / 2000 |
| **Chapter** | 3 (Functions) |
| **XP** | 280 |
| **Mức độ** | Medium |