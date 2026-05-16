# Bài 11 — Vòng lặp While

---

## 1. Ôn tập
Bài 10 đã học `for` — vòng lặp với số lần biết trước. Giờ học `while` — lặp với điều kiện.

---

## 2. Mục tiêu bài học
- Hiểu `while` khác `for` thế nào
- Biết cách dùng `while` đúng
- Hiểu vòng lặp vô hạn
- Tránh lỗi thường gặp

---

## 3. Code chính (có comment)

```python
# Đếm ngược từ 5 đến 1
count = 5
while count > 0:
    print(count)
    count = count - 1

print("Boom!")

# Nhập cho đến khi đúng
password = ""
while password != "123456":
    password = input("Nhap mat khau: ")

print("Dang nhap thanh cong!")
```

**Output (ví dụ):**
```
5
4
3
2
1
Boom!
Nhap mat khau: 111
Nhap mat khau: 222
Nhap mat khau: 123456
Dang nhap thanh cong!
```

---

## 4. Trace chạy code

```
count = 5

Lần 1: count > 0 ? → True → print(5) → count = 4
Lần 2: count > 0 ? → True → print(4) → count = 3
Lần 3: count > 0 ? → True → print(3) → count = 2
Lần 4: count > 0 ? → True → print(2) → count = 1
Lần 5: count > 0 ? → True → print(1) → count = 0
Lần 6: count > 0 ? → False → DỪNG
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Vòng lặp vô hạn
```python
# LỖI! count không thay đổi → vòng lặp vô hạn
count = 5
while count > 0:
    print(count)
    # Quên: count = count - 1
```
**Vì sao sai:** Biến không thay đổi → vòng lặp không bao giờ dừng

**✅ Sửa:**
```python
count = 5
while count > 0:
    print(count)
    count = count - 1  # Cập nhật biến!
```

### ❌ Lỗi 2 — Quên dấu :
```python
while count > 0       # LỖI! Thiếu :
    print(count)
```

### ❌ Lỗi 3 — Điều kiện luôn True
```python
while True:  # Vòng lặp vô hạn!
    print("Hello")
# Cần break bên trong để thoát
```

---

## 6. Ghi nhớ nhanh

| Cú pháp | Ý nghĩa |
|---------|---------|
| `while điều_kiện:` | Lặp KHI điều kiện đúng |
| `count += 1` | Tăng biến (count = count + 1) |
| `count -= 1` | Giảm biến (count = count - 1) |

**CẢNH BÁO:** While cần điều kiện dừng, không thì treo máy!

**MẸO NHỚ:** For = biết trước, While = chưa biết (đợi đến khi đúng).

---

## 7. Mini test (3 câu)

**Câu 1:** Đoán kết quả:
```python
x = 0
while x < 3:
    print(x)
    x = x + 1
```
> Đáp án: `0 1 2`

**Câu 2:** Tại sao code này treo máy?
```python
x = 10
while x > 0:
    print(x)
    # x không thay đổi
```
> Đáp án: `x` luôn = 10 → vòng lặp vô hạn

**Câu 3:** Sửa để đếm 1 đến 5:
```python
x = 1
while x < 5:  # Thiếu gì?
    print(x)
    x = x + 1
```
> Đáp án: `while x <= 5:`

---

## 8. LeetCode practice

**Bài tập:** Máy tạo số ngẫu nhiên 1-10. Lặp đến khi đoán đúng.

**Input:** `7` (hoặc nhiều dòng)

**Output:** `Chuc mung ban da doan dung!`

**Khung code:**
```python
import random

so = random.randint(1, 10)

# Viết tiếp vào đây
```

**✅ Đáp án:**
```python
import random

so = random.randint(1, 10)

while True:
    guess = int(input())
    if guess == so:
        print("Chuc mung ban da doan dung!")
        break
    else:
        print("Sai roi, thu lai!")
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Viết chương trình tính tổng các số nhập vào cho đến khi nhập 0.

**Input:**
```
5
3
8
0
```

**Output:** `Tong = 16`

**✅ Đáp án:**
```python
tong = 0
while True:
    n = int(input())
    if n == 0:
        break
    tong = tong + n

print("Tong =", tong)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 11 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 110 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 11!** 

Gõ **12** để học tiếp Bài 12 (Break và Continue) →