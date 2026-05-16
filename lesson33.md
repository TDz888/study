# Bài 33 — Exception Handling

---

## 1. Ôn tập
Bài 32 đã học File Handling. Giờ học cách **xử lý lỗi** với Exception.

---

## 2. Mục tiêu bài học
- Hiểu exception là gì
- Biết cách dùng try/except
- Xử lý nhiều loại lỗi
- Dùng finally

---

## 3. Code chính (CORE LESSON)

```python
# Try - Except cơ bản
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Khong chia duoc cho 0!")

# Try - Except - Else - Finally
try:
    f = open("test.txt", "r")
    content = f.read()
except FileNotFoundError:
    print("File khong ton tai!")
else:
    print("Doc thanh cong!")
finally:
    print("Luon chay cuoi cung")
```

**Output:**
```
Khong chia duoc cho 0!
```

---

## 4. Các loại Exception thường gặp

```python
# ZeroDivisionError - Chia cho 0
try:
    10 / 0
except ZeroDivisionError:
    print("Loi chia 0")

# ValueError - Giá trị không hợp lệ
try:
    int("abc")  # Không phải số
except ValueError:
    print("Loi gia tri")

# IndexError - Index không tồn tại
try:
    lst = [1, 2, 3]
    print(lst[10])
except IndexError:
    print("Loi index")

# TypeError - Sai kiểu
try:
    "abc" + 123
except TypeError:
    print("Loi kieu du lieu")
```

---

## 5. Trace luồng chạy

```
try:
    code có thể lỗi
       ↓ (nếu có lỗi)
except LoaiLoi:
    xử lý lỗi
       ↓
code tiếp theo
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Bắt quá rộng
```python
# Không nên - bắt tất cả lỗi
try:
    x = 10 / 0
except:
    print("Co loi")

# Nên - bắt cụ thể
except ZeroDivisionError:
    print("Loi chia 0")
```

---

### ❌ SAI THỨ 2 — Lỗi không bắt được
```python
# Muốn bắt ValueError nhưng code gây TypeError
try:
    int(None)  # TypeError, không phải ValueError
except ValueError:
    print("Day la ValueError")
# → Không bắt được!
```

---

### ❌ SAI THỨ 3 — Quên thứ tự except
```python
try:
    x = int("abc")
except Exception:  # Bắt tất cả
    print("Loi")
except ValueError:  # Không bao giờ chạy!
    print("ValueError")
# → Phải để specific trước, general sau
```

---

## 7. Ghi nhớ nhanh

| Từ khóa | Ý nghĩa |
|----------|---------|
| `try` | Thử code |
| `except` | Bắt lỗi |
| `else` | Chạy khi không có lỗi |
| `finally` | Luôn chạy |
| `raise` | Ném lỗi |

**MẸO NHỚ:** Try/Except = thử/bắt. Thử làm, bắt lỗi nếu có.

---

## 8. Mini Test (3 câu)

**Câu 1:** Output?
```python
try:
    print(5 / 0)
except:
    print("Loi")
```
> Đáp án: `"Loi"`

**Câu 2:** Bắt lỗi file không tồn tại:
> Đáp án: `except FileNotFoundError:`

**Câu 3:** Luôn chạy dù có lỗi:
> Đáp án: `finally:`

---

## 9. LeetCode Practice

### Bài tập: An toàn khi chia số
**Yêu cầu:** Nhập 2 số, chia an toàn (nếu lỗi in thông báo)

**Input:** `10 0`

**Output:** `Khong the chia cho 0`

**Input:** `10 2`

**Output:** `5`

**✅ Đáp án:**
```python
try:
    a, b = map(int, input().split())
    result = a / b
    print(result)
except ZeroDivisionError:
    print("Khong the chia cho 0")
except ValueError:
    print("Cu phap sai")
```

---

## 10. Bonus Challenge

Viết hàm kiểm tra số với try/except

**Input:** `12abc`

**Output:** `Khong phai so`

**Input:** `123`

**Output:** `123`

**✅ Đáp án:**
```python
def kiem_tra_so(s):
    try:
        return int(s)
    except ValueError:
        return "Khong phai so"

n = input()
result = kiem_tra_so(n)
if isinstance(result, int):
    print(result)
else:
    print(result)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 33 / 2000 |
| **Chapter** | 3 (Functions) |
| **XP** | 330 |
| **Mức độ** | Medium |