# Bài 44 — Stack và Queue

---

## 1. Ôn tập
Bài 43 đã học Hashing. Giờ học **Stack** và **Queue** — 2 cấu trúc dữ liệu cơ bản.

---

## 2. Mục tiêu bài học
- Hiểu Stack (LIFO)
- Hiểu Queue (FIFO)
- Dùng list/collections
- Ứng dụng

---

## 3. Stack (LIFO)

```python
# Stack - Last In First Out
stack = []

# Push - thêm vào
stack.append(1)  # [1]
stack.append(2)  # [1, 2]
stack.append(3)  # [1, 2, 3]

# Pop - lấy ra
print(stack.pop())   # 3
print(stack.pop())   # 2

print(stack)         # [1]
```

**Output:**
```
3
2
[1]
```

---

## 4. Queue (FIFO)

```python
from collections import deque

# Queue - First In First Out
queue = deque([1, 2, 3])

# Enqueue - thêm
queue.append(4)    # [1, 2, 3, 4]

# Dequeue - lấy
print(queue.popleft())  # 1
print(queue.popleft())  # 2

print(queue)            # [3, 4]
```

---

## 5. Ứng dụng Stack

### Valid Parentheses
```python
def is_valid(s):
    stack = []
    pairs = {')': '(', ']': '[', '}': '{'}
    
    for c in s:
        if c in '([{':
            stack.append(c)
        elif c in ')]}':
            if not stack or stack[-1] != pairs[c]:
                return False
            stack.pop()
    
    return len(stack) == 0

print(is_valid("()[]{}"))  # True
print(is_valid("(]"))       # False
```

---

## 6. Ứng dụng Queue

### BFS - Breadth First Search
```python
from collections import deque

# Duyệt cây/đồ thị theo chiều rộng
def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)
    
    while queue:
        node = queue.popleft()
        print(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

---

## 7. Debug Mentor Mode

### ❌ SAI THỨ 1 — Pop từ stack rỗng
```python
stack = []
stack.pop()  # LỖI! IndexError
# → Cần kiểm tra: if stack:
```

---

### ❌ SAI THỨ 2 — Nhầm LIFO và FIFO
```python
# Stack - vào sau ra trước
# Queue - vào trước ra trước
```

---

### ❌ SAI THỨ 3 — Dùng list thay vì deque
```python
# list.pop(0) = O(n)!
# deque.popleft() = O(1)
```

---

## 8. Ghi nhớ nhanh

| Cấu trúc | Từ khóa | Hoạt động |
|----------|----------|-----------|
| **Stack** | push/pop | LIFO |
| **Queue** | enqueue/dequeue | FIFO |

**MẸO NHỚ:** Stack = chồng đĩa, Queue = hàng đợi.

---

## 9. Mini Test (3 câu)

**Câu 1:** Stack sau: [1,2,3].pop() = ?
> Đáp án: `3` (ra trước)

**Câu 2:** Queue: [1,2,3].popleft() = ?
> Đáp án: `1` (ra trước)

**Câu 3:** Dùng gì cho BFS?
> Đáp án: Queue

---

## 10. LeetCode Practice

### Bài tập: Valid Parentheses
**Yêu cầu:** Kiểm tra dấu ngoặc hợp lệ

**Input:** `()[]{}`

**Output:** `True`

**Input:** `(]`

**Output:** `False`

**✅ Đáp án:**
```python
def is_valid(s):
    stack = []
    pairs = {')': '(', ']': '[', '}': '{'}
    
    for c in s:
        if c in '([{':
            stack.append(c)
        elif c in ')]}':
            if not stack or stack[-1] != pairs[c]:
                return False
            stack.pop()
    
    return len(stack) == 0

s = input()
print(is_valid(s))
```

---

## 11. Bonus Challenge

Tìm số lớn nhất trong mỗi cửa sổ trượt (Sliding Window Maximum)

**Input:** `7 [1 3 -1 -3 5 3 6 7] 3`

**Output:** `[3 3 5 5 6 7]`

**✅ Đáp án:**
```python
from collections import deque

def max_sliding_window(nums, k):
    result = []
    dq = deque()  # lưu indices
    
    for i in range(len(nums)):
        # Remove indices out of window
        while dq and dq[0] <= i - k:
            dq.popleft()
        
        # Remove indices of smaller elements
        while dq and nums[dq[-1]] < nums[i]:
            dq.pop()
        
        dq.append(i)
        
        if i >= k - 1:
            result.append(nums[dq[0]])
    
    return result

k = int(input())
nums = list(map(int, input().split()))
t = int(input())
result = max_sliding_window(nums, t)
print(result)
```

---

## Tiến độ

| Thông tin | Giá trị |
|-----------|---------|
| **Lesson** | 44 / 2000 |
| **Chapter** | 4 (Data Structures) |
| **XP** | 440 |
| **Mức độ** | Medium |