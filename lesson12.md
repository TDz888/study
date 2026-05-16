# Bài 12 — Break và Continue

---

## 1. Ôn tập
Bài 11 đã học `while` — vòng lặp với điều kiện. Giờ học cách **điều khiển vòng lặp** với `break` và `continue`.

---

## 2. Mục tiêu bài học
- Hiểu `break` — THOÁT vòng lặp ngay
- Hiểu `continue` — BỎ QUA lượt hiện tại
- Biết khi nào dùng break/continue
- Tránh lỗi thường gặp

---

## 3. Code chính (CORE LESSON)

```python
# BREAK - Thoát ngay khi gặp điều kiện
print("Tim so dau tien lon hon 100:")
for i in range(50, 200):
    if i > 100:
        print("Tim thay:", i)
        break  # Thoát vòng for

# CONTINUE - Bỏ qua lượt này
print("\nIn so le nho hon 10:")
for i in range(1, 10):
    if i % 2 == 0:
        continue  # Bỏ qua số chẵn
    print(i)
```

**Output:**
```
Tim so dau tien lon hon 100:
Tim thay: 101

In so le nho hon 10:
1
3
5
7
9
```

---

## 4. Trace luồng chạy

### BREAK
```
range(50, 200):
i = 50 → 50 > 100? Không
i = 51 → Không
...
i = 101 → 101 > 100? Có! → break → DỪNG
```

### CONTINUE
```
i = 1 → 1 % 2 == 0? Không → print(1)
i = 2 → 2 % 2 == 0? Có → continue → BỎ QUA print
i = 3 → 3 % 2 == 0? Không → print(3)
...
```

---

## 5. So sánh Break vs Continue

| Từ khóa | Hành động | Vòng lặp |
|---------|-----------|----------|
| `break` | Thoát hẳn | Kết thúc hoàn toàn |
| `continue` | Bỏ qua lượt này | Quay lên lượt kế tiếp |

**Sơ đồ:**
```
BREAK:
for i in ...:
    if điều_kiện:
        break → ⬇️ DỪNG hẳn

CONTINUE:
for i in ...:
    if điều_kiện:
        continue → 🔄 Quay lên lượt kế tiếp
```

---

## 6. Debug Mentor Mode

### ❌ SAI THỨ 1 — Quên break trong while
```python
# Vòng lặp vô hạn!
while True:
    print("Hello")
    # Không có break
```

---

### ❌ SAI THỨ 2 — Dùng continue sai vị trí
```python
for i in range(10):
    continue  # Luôn bỏ qua mọi lượt!
    print(i)  # Không bao giờ chạy
```

---

### ❌ SAI THỨ 3 — Nhầm break và continue
```python
# Muốn bỏ qua số chẵn
for i in range(10):
    if i % 2 == 0:
        break  # LỖI! Thoát hẳn khi gặp số chẵn đầu tiên
    print(i)

# ĐÚNG
for i in range(10):
    if i % 2 == 0:
        continue  # Bỏ qua số chẵn, tiếp tục
    print(i)
```

---

## 7. Ghi nhớ nhanh

| Từ khóa | Nghĩa | Ví dụ |
|---------|-------|-------|
| `break` | Thoát | Đủ điều kiện → dừng |
| `continue` | Bỏ qua | Không đúng → bỏ lượt này |

**MẸO NHỚ:**
- `break`: như nhấn nút tắt máy → thoát ngay
- `continue`: như bỏ qua bài hát này → chơi bài kế tiếp

---

## 8. Mini Test (3 câu)

**Câu 1:** Output là gì?
```python
for i in range(5):
    if i == 3:
        break
    print(i)
```
> Đáp án: `0 1 2` (dừng ở i=3)

**Câu 2:** Output là gì?
```python
for i in range(5):
    if i == 3:
        continue
    print(i)
```
> Đáp án: `0 1 2 4` (bỏ qua i=3)

**Câu 3:** Tìm lỗi:
```python
x = 0
while x < 10:
    if x == 5:
        break
    print(x)
    x = x + 1
```
> Đáp án: `x = x + 1` phải nằm trong vòng lặp, trước break hoặc sau print

---

## 9. LeetCode Practice

### Bài tập: Tìm số nguyên tố đầu tiên
**Yêu cầu:** Tìm số nguyên tố đầu tiên trong khoảng 1-100

**Output:** `2` (2 là số nguyên tố đầu tiên)

**✅ Đáp án:**
```python
for n in range(1, 101):
    if n < 2:
        continue
    la_nguyen_to = True
    for i in range(2, n):
        if n % i == 0:
            la_nguyen_to = False
            break
    if la_nguyen_to:
        print(n)
        break
```

---

## 10. Bonus Challenge

In tất cả số từ 1-50, BỎ QUA:
- Số chia hết cho 5
- Số > 40

**Output:**
```
1
2
3
4
6
7
8
9
11
12
13
14
16
17
18
19
21
22
23
24
26
27
28
29
31
32
33
34
36
37
38
39
```

**✅ Đáp án:**
```python
for i in range(1, 51):
    if i > 40:
        break
    if i % 5 == 0:
        continue
    print(i)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 12 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **XP** | 120 |
| **Mức độ** | Medium |