# Bài 27 — *args và **kwargs

---

## 1. Ôn tập
Bài 26 đã học default parameters. Giờ học cách nhận **số lượng tham số linh hoạt**.

---

## 2. Mục tiêu bài học
- Hiểu `*args` — nhận nhiều positional arguments
- Hiểu `**kwargs` — nhận nhiều keyword arguments
- Biết cách dùng khi chưa biết trước số tham số

---

## 3. Code chính (CORE LESSON)

```python
# *args - Nhận nhiều positional arguments
def tinh_tong(*args):
    print(args)
    return sum(args)

print(tinh_tong(1, 2, 3))           # (1, 2, 3) → 6
print(tinh_tong(1, 2, 3, 4, 5))    # (1, 2, 3, 4, 5) → 15
```

**Output:**
```
(1, 2, 3)
6
(1, 2, 3, 4, 5)
15
```

---

## 4. **kwargs

```python
# **kwargs - Nhận nhiều keyword arguments
def in_thong_tin(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

in_thong_tin(name="Minh", age=20)
in_thong_tin(city="Hanoi", country="Vietnam")
```

**Output:**
```
name: Minh
age: 20
city: Hanoi
country: Vietnam
```

---

## 5. Kết hợp *args và **kwargs

```python
def func(*args, **kwargs):
    print("Args:", args)
    print("Kwargs:", kwargs)

func(1, 2, 3, name="Minh", age=20)
```

**Output:**
```
Args: (1, 2, 3)
Kwargs: {'name': 'Minh', 'age': 20}
```

---

## 6. Unpack khi gọi hàm

```python
# Unpack list thành args
nums = [1, 2, 3]
print(tinh_tong(*nums))  # 6

# Unpack dict thành kwargs
info = {"name": "Minh", "age": 20}
in_thong_tin(**info)
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Nhầm *args và **kwargs
```python
# *args = positional (vị trí)
# **kwargs = keyword (từ khóa)

# Sai
def func(**args):  # Không dùng được
    pass

# Đúng
def func(*args, **kwargs):
    pass
```

---

### ❌ SAI THỨ 2 — Đặt sau default parameter
```python
# LỖI
def func(a=1, *args):
    pass

# Đúng
def func(*args, a=1):
    pass
```

---

### ❌ SAI THỨ 3 — Quên unpack khi gọi
```python
nums = [1, 2, 3]
# Sai
tinh_tong(nums)  # (1, 2, 3) không cộng được

# Đúng
tinh_tong(*nums)  # Unpack → 1, 2, 3
```

---

## 8. Ghi nhớ nhanh

| Cú pháp | Nhận | Ví dụ |
|---------|------|-------|
| `*args` | Positional | `func(1, 2, 3)` |
| `**kwargs` | Keyword | `func(a=1, b=2)` |
| `*list` | Unpack list | `func(*[1,2,3])` |
| `**dict` | Unpack dict | `func(**{'a':1})` |

**MẸO NHỚ:** `*args` = argument (đối số), `**kwargs` = keyword arguments.

---

## 9. Mini Test (3 câu)

**Câu 1:** `sum(*[1,2,3])` = ?
> Đáp án: `6`

**Câu 2:** Viết hàm in tất cả args:
```python
def in_tat_ca(*args):
    for item in args:
        print(item)
```

**Câu 3:** Đoán output:
```python
def func(**kwargs):
    return kwargs.get("name", "Unknown")

print(func(name="Minh"))
```
> Đáp án: `Minh`

---

## 10. LeetCode Practice

### Bài tập: Hàm tìm max với nhiều số
**Yêu cầu:** Viết hàm `tim_max(*nums)` tìm số lớn nhất

**Input:** `5 3 9 1 7`

**Output:** `9`

**✅ Đáp án:**
```python
def tim_max(*nums):
    return max(nums)

nums = tuple(map(int, input().split()))
print(tim_max(*nums))
```

---

## 11. Bonus Challenge

Viết hàm merge dictionary với nhiều dict

**Input:**
```
a 1 b 2
c 3 d 4
```

**Output:** `{'a': 1, 'b': 2, 'c': 3, 'd': 4}`

**✅ Đáp án:**
```python
def merge_dicts(*dicts):
    result = {}
    for d in dicts:
        result.update(d)
    return result

d1 = dict(input().split())
d2 = dict(input().split())
print(merge_dicts(d1, d2))
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 27 / 2000 |
| **Chapter** | 3 (Functions) |
| **XP** | 270 |
| **Mức độ** | Medium |