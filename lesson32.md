# Bài 32 — File Handling (Đọc/Ghi file)

---

## 1. Ôn tập
Bài 31 đã học Import. Giờ học cách **đọc/ghi file** trong Python.

---

## 2. Mục tiêu bài học
- Biết cách mở file
- Đọc nội dung file
- Ghi nội dung vào file
- Quản lý file an toàn với with

---

## 3. Code chính (CORE LESSON)

```python
# Ghi file
with open("test.txt", "w") as f:
    f.write("Hello\n")
    f.write("World")

# Đọc file
with open("test.txt", "r") as f:
    content = f.read()
    print(content)
```

**Output (file test.txt):**
```
Hello
World
```

---

## 4. Các mode mở file

| Mode | Ý nghĩa |
|------|---------|
| `"r"` | Đọc (mặc định) |
| `"w"` | Ghi (ghi đè) |
| `"a"` | Ghi thêm vào cuối |
| `"rb"` | Đọc nhị phân |
| `"wb"` | Ghi nhị phân |

---

## 5. Đọc file nhiều cách

```python
# Đọc toàn bộ
with open("test.txt", "r") as f:
    content = f.read()

# Đọc từng dòng
with open("test.txt", "r") as f:
    lines = f.readlines()
    # hoặc
    for line in f:
        print(line.strip())
```

---

## 6. Trace luồng chạy

```
open("test.txt", "w")
       ↓
Tạo/overwrite file test.txt
       ↓
f.write("Hello")
       ↓
Ghi "Hello" vào file
       ↓
Đóng file (với with)
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — File không tồn tại khi đọc
```python
with open("notexist.txt", "r") as f:  # LỖI! FileNotFoundError
```

---

### ❌ SAI THỨ 2 — Mode "w" xóa file cũ
```python
# File cũ bị xóa hoàn toàn!
with open("test.txt", "w") as f:
    f.write("new")
```

---

### ❌ SAI THỨ 3 — Quên close file
```python
# Không dùng with - phải close
f = open("test.txt", "r")
content = f.read()
f.close()  # Quan trọng!
```

---

## 8. Ghi nhớ nhanh

| Hàm | Ý nghĩa |
|-----|---------|
| `open("file", "r")` | Mở file đọc |
| `open("file", "w")` | Mở file ghi |
| `f.read()` | Đọc toàn bộ |
| `f.readline()` | Đọc 1 dòng |
| `f.write(s)` | Ghi chuỗi |
| `with` | Tự đóng file |

**MẸO NHỚ:** with = "với" → dùng xong tự đóng cửa.

---

## 9. Mini Test (3 câu)

**Câu 1:** Mode nào để ghi thêm vào cuối?
> Đáp án: `"a"` (append)

**Câu 2:** Đọc file và in từng dòng:
```python
with open("file.txt", "r") as f:
    for line in f:
        print(line.strip())
```

**Câu 3:** Lỗi khi file không tồn tại với mode "r"?
> Đáp án: `FileNotFoundError`

---

## 10. LeetCode Practice

### Bài tập: Đọc file và đếm dòng
**Yêu cầu:** Đọc file input.txt, đếm số dòng

**Nội dung file input.txt:**
```
Line 1
Line 2
Line 3
```

**Output:** `3`

**✅ Đáp án:**
```python
with open("input.txt", "r") as f:
    lines = f.readlines()
    print(len(lines))
```

---

## 11. Bonus Challenge

Ghi danh sách số vào file (mỗi số một dòng)

**Input:** `1 2 3 4 5`

**File output.txt:**
```
1
2
3
4
5
```

**✅ Đáp án:**
```python
nums = input().split()
with open("output.txt", "w") as f:
    for num in nums:
        f.write(num + "\n")
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 32 / 2000 |
| **Chapter** | 6 (Projects) |
| **XP** | 320 |
| **Mức độ** | Easy |