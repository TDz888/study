# Bài 1 — Hello World! (Chào thế giới!)

---

## 1. Ôn tập
Chào mừng bạn đến với Python! Bài này là bắt đầu hoàn hảo để bạn viết dòng code đầu tiên.

---

## 2. Mục tiêu bài học
- Hiểu `print()` là gì và dùng để làm gì
- Biết cách xuất text ra màn hình
- Hiểu string (chuỗi ký tự) là gì
- Chạy được chương trình Python đầu tiên

---

## 3. Code chính (có comment)

```python
# Chương trình đầu tiên - In lời chào ra màn hình
print("Hello World!")
```

**Output:**
```
Hello World!
```

**Giải thích:**
- `print` = hàm in ra màn hình
- `()` = ngoặc tròn — nơi đặt dữ liệu cần in
- `" "` = dấu ngoặc kép — báo hiệu STRING (chuỗi ký tự)
- `Hello World!` = Text cần in ra

---

## 4. Trace chạy code

```
Máy tính đọc code
       ↓
Gặp print(...)
       ↓
Thấy dấu "" → Hiểu đây là STRING (văn bản)
       ↓
In nội dung bên trong ra màn hình
       ↓
Kết quả: Hello World!
```

---

## 5. Debug tư duy

### ❌ Lỗi 1 — Thiếu ngoặc kép
```python
print(Hello World!)  # LỖI!
```
**Vì sao sai:** Không có dấu "" → Python không biết đây là text

**✅ Sửa:**
```python
print("Hello World!")
```

### ❌ Lỗi 2 — Thiếu dấu ngoặc đóng
```python
print("Hello World!)  # LỖI!
```

**✅ Sửa:**
```python
print("Hello World!")
```

### ❌ Lỗi 3 — Ngoặc kép nhầm font (nháy cong)
```python
print(”Hello World!”)  # LỖI!
```

**✅ Sửa:**
```python
print("Hello World!")  # Dùng nháy thẳng
```

---

## 6. Ghi nhớ nhanh

| Thuật ngữ | Giải thích |
|-----------|------------|
| `print()` | Hàm in ra màn hình |
| `string` | Chuỗi ký tự (văn bản) |
| `" "` | Dấu báo hiệu string |
| `()` | Ngoặc tròn — chứa dữ liệu đầu vào |

**MẸO NHỚ:** `print` = máy in → in cái gì ra giấy thì cần cho vào máy. Python cần cho text vào ngoặc `" "` rồi `print()` mới in được.

---

## 7. Mini test (3 câu)

**Câu 1:** `print("Xin chào")` sẽ hiển thị gì?
> Đáp án: `Xin chào`

**Câu 2:** Tại sao code này LỖI?
```python
print(Xin chào)
```
> Đáp án: Thiếu dấu ngoặc kép `" "` — Python không biết đây là text

**Câu 3:** Sửa lỗi:
```python
print("Hello World!
```
> Đáp án: Thiếu dấu `"` đóng → `print("Hello World!")`

---

## 8. LeetCode practice

**Bài tập:** Viết chương trình in ra dòng: `Chao ban den voi Python`

**Input:** (không có input)

**Output:**
```
Chao ban den voi Python
```

**Khung code:**
```python
# Viết code vào đây
```

**Gợi ý:** Nhớ đặt text trong dấu `" "` và gọi `print()`

**✅ Đáp án:**
```python
print("Chao ban den voi Python")
```

---

## 9. Bonus (nếu học tốt)

**Thử thách:** Viết chương trình in ra **3 dòng**:
```
Toi la Python
Toi dang hoc print()
Den day di!
```

**✅ Đáp án:**
```python
print("Toi la Python")
print("Toi dang hoc print()")
print("Den day di!")
```

**Ghi nhớ:** Mỗi `print()` = 1 dòng mới

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 1 / 2000 |
| **Chapter** | 1 (Cơ bản) |
| **Level** | Beginner |
| **XP** | 10 (+10 XP khi hoàn thành) |

---

**🎉 Bạn đã hoàn thành Bài 1!** 

Gõ **2** để học tiếp Bài 2 (Biến - Variables) →