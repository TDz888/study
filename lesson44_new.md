# Lesson 44 — Stack and Queue

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 43 - Hashing.

**Current Lesson:** Learning **Stack** and **Queue** — two fundamental data structures.

**Why This Matters:**
- Stack and Queue model real-world scenarios (stacks of plates, lines of people)
- Essential for many algorithms (DFS uses stack, BFS uses queue)
- Foundation for understanding more complex data structures

**Connection:**
```
Arrays → Lists → Stack (LIFO) / Queue (FIFO)
   ↓        ↓           ↓          ↓
Sequential  Index       Last First  First First
```

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll master today:**
- Stack (Last In, First Out) concept and operations
- Queue (First In, First Out) concept and operations
- When to use each data structure
- Real-world applications (parentheses validation, BFS)
- Python implementation with list and deque

**Real-world analogy:**
- **Stack:** Stack of plates — the last plate placed is the first one you pick up
- **Queue:** Line at a store — first person in line is served first

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### What is Stack?

A stack is like a pile of items where you can only:
- **Push:** Add item to top
- **Pop:** Remove item from top

```
Stack Visualization:

    ┌───────┐
    │   3   │  ← TOP (last added)
    ├───────┤
    │   2   │
    ├───────┤
    │   1   │
    ├───────┤
    │   0   │  ← BOTTOM (first added)
    └───────┘

Push 4: Adds 4 to top
Pop:    Removes 3 (the top element)
```

### What is Queue?

A queue is like a line where you can only:
- **Enqueue:** Add to back
- **Dequeue:** Remove from front

```
Queue Visualization:

FRONT → [0] [1] [2] [3] ← BACK
         ↑             ↑
       dequeue       enqueue
       (remove)      (add)
```

### Key Difference

```
Stack:  LIFO = Last In, First Out
        Last plate you put down is the first one you pick up

Queue:  FIFO = First In, First Out
        First person in line is served first
```

-------------------------------------------------------------------------------
4. TERMINOLOGY EXPLANATION
-------------------------------------------------------------------------------

| Term | Simple Meaning |
|------|----------------|
| **Stack** | Collection where items are added/removed from top only |
| **Queue** | Collection where items are added to back, removed from front |
| **Push** | Add item to stack (top) |
| **Pop** | Remove item from stack (top) |
| **Enqueue** | Add item to queue (back) |
| **Dequeue** | Remove item from queue (front) |
| **LIFO** | Last In, First Out — how stack works |
| **FIFO** | First In, First Out — how queue works |
| **Peek** | Look at top/front without removing |
| **Empty** | No items in the collection |

-------------------------------------------------------------------------------
5. MAIN CODE
-------------------------------------------------------------------------------

### 1. Stack Implementation

```python
# Stack using list
stack = []

# Push - add to top
stack.append(1)   # stack = [1]
stack.append(2)   # stack = [1, 2]
stack.append(3)   # stack = [1, 2, 3]

# Peek - look at top
print(stack[-1])  # 3 (doesn't remove)

# Pop - remove from top
print(stack.pop())   # 3, stack = [1, 2]
print(stack.pop())   # 2, stack = [1]
print(stack.pop())   # 1, stack = []

# Check if empty
if stack:
    print("Not empty")
else:
    print("Empty")

# Safe pop with check
stack = []
if stack:
    stack.pop()
else:
    print("Cannot pop from empty stack!")
```

### 2. Queue Implementation

```python
from collections import deque

# Create queue using deque (efficient!)
queue = deque()

# Enqueue - add to back
queue.append(1)   # queue = [1]
queue.append(2)   # queue = [1, 2]
queue.append(3)   # queue = [1, 2, 3]

# Peek - look at front
print(queue[0])   # 1 (doesn't remove)

# Dequeue - remove from front
print(queue.popleft())   # 1, queue = [2, 3]
print(queue.popleft())   # 2, queue = [3]
print(queue.popleft())   # 3, queue = []

# Initialize with values
queue = deque([1, 2, 3])
print(queue)  # deque([1, 2, 3])
```

### 3. Important: List vs Deque for Queue

```python
# ❌ WRONG - Using list for queue is slow!
queue = [1, 2, 3]
queue.pop(0)  # O(n)! Must shift all elements

# ✅ CORRECT - Use deque!
from collections import deque
queue = deque([1, 2, 3])
queue.popleft()  # O(1)! Just move pointer
```

### 4. Valid Parentheses (Stack Application)

```python
def is_valid(s):
    """
    Check if parentheses string is valid.
    Valid means: every opening has closing in correct order.
    
    Examples:
    - "()" → True
    - "()[]{}" → True
    - "(]" → False
    - "([)]" → False
    """
    stack = []
    pairs = {
        ')': '(',
        ']': '[',
        '}': '{'
    }
    
    for char in s:
        if char in '([{':
            # Opening bracket - push to stack
            stack.append(char)
        elif char in ')]}':
            # Closing bracket - check if matches
            if not stack or stack[-1] != pairs[char]:
                return False
            stack.pop()
    
    # Stack must be empty (all brackets matched)
    return len(stack) == 0


# Test
print(is_valid("()"))        # True
print(is_valid("()[]{}"))    # True
print(is_valid("(]"))        # False
print(is_valid("([)]"))      # False
print(is_valid("{[]}"))      # True
```

### 5. BFS using Queue

```python
from collections import deque

def bfs(graph, start):
    """
    Breadth-First Search using queue.
    Explores all neighbors at current depth before going deeper.
    """
    visited = set()  # Track visited nodes
    queue = deque([start])  # Start from start node
    visited.add(start)
    
    while queue:
        node = queue.popleft()
        print(f"Visiting: {node}")
        
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)


# Example graph (adjacency list)
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

bfs(graph, 'A')
# Output: A, B, C, D, E, F (level by level)
```

-------------------------------------------------------------------------------
6. EXECUTION TRACE
-------------------------------------------------------------------------------

### Trace: Valid Parentheses "{[()]}"

```
Input: "{[()]}"

Step 1: char='{'
  Is opening? → YES
  Push to stack → stack = ['{']

Step 2: char='['
  Is opening? → YES
  Push to stack → stack = ['{', '[']

Step 3: char='('
  Is opening? → YES
  Push to stack → stack = ['{', '[', '(']

Step 4: char=')'
  Is opening? → NO
  pairs[')'] = '('
  stack[-1] = '(' → MATCH!
  Pop → stack = ['{', '[']

Step 5: char=']'
  Is opening? → NO
  pairs[']'] = '['
  stack[-1] = '[' → MATCH!
  Pop → stack = ['{']

Step 6: char='}'
  Is opening? → NO
  pairs['}'] = '{'
  stack[-1] = '{' → MATCH!
  Pop → stack = []

Final: stack is empty → return True ✓
```

### Trace: BFS Traversal

```
Graph: A → [B, C]
       B → [A, D]
       C → [A, F]
       D → [B]
       F → [C]

Start: queue = ['A'], visited = {'A'}

Step 1: node='A'
  Dequeue → queue = []
  Visit A
  Add B → visited={'A','B'}, queue=['B']
  Add C → visited={'A','B','C'}, queue=['B','C']

Step 2: node='B'
  Dequeue → queue = ['C']
  Visit B
  Add D → visited={'A','B','C','D'}, queue=['C','D']
  E already visited

Step 3: node='C'
  Dequeue → queue = ['D']
  Visit C
  Add F → visited={'A','B','C','D','F'}, queue=['D','F']

Step 4: node='D'
  Dequeue → queue = ['F']
  Visit D (no new neighbors)

Step 5: node='F'
  Dequeue → queue = []
  Visit F (no new neighbors)

Result: A → B → C → D → F (breadth-first order)
```

### Stack Operations Trace

```
Operations: push(1), push(2), push(3), pop(), pop()

Step 1: push(1)
  stack = [1]

Step 2: push(2)
  stack = [1, 2]

Step 3: push(3)
  stack = [1, 2, 3]

Step 4: pop()
  Returns 3 (top element)
  stack = [1, 2]

Step 5: pop()
  Returns 2
  stack = [1]

Final: stack = [1]
```

-------------------------------------------------------------------------------
7. VISUAL THINKING MODE
-------------------------------------------------------------------------------

### Stack LIFO Visualization

```
Operations:
1. Push 1:    [1]
2. Push 2:  [1,2]
3. Push 3:  [1,2,3]
              ─┘ ← Top

Pop 1: Returns 3, stack = [1,2]
Pop 2: Returns 2, stack = [1]
Pop 3: Returns 1, stack = []

Last In (3) → First Out ✓
```

### Queue FIFO Visualization

```
Operations:
1. Enqueue 1:  [1]
2. Enqueue 2:  [1,2]
3. Enqueue 3:  [1,2,3]
              ↑
            Front

Dequeue 1: Returns 1, queue = [2,3]
Dequeue 2: Returns 2, queue = [3]
Dequeue 3: Returns 3, queue = []

First In (1) → First Out ✓
```

### Parentheses Matching

```
"{[()]}"

Stack at each step:

'{[' → matched '()', now '{['
  └── '[' → matched '[', now '{'
       └── '{' → matched '{', now []

All matched! ✓ Valid
```

```
"([)]"

Stack at each step:

'(' → matched ')', now '([]? Wait...'

'('
'[' → stack = ['(', '[']
')' → pairs[')'] = '('
       stack[-1] = '[' ✗ MISMATCH!

Invalid ✗
```

-------------------------------------------------------------------------------
8. DEBUG THINKING MODE
-------------------------------------------------------------------------------

### Common Mistake 1: Pop from Empty Stack

```python
# ❌ WRONG - Will crash!
stack = []
stack.pop()  # IndexError: pop from empty list

# ✅ CORRECT - Check first
stack = []
if stack:  # or: len(stack) > 0
    stack.pop()
else:
    print("Stack is empty!")

# Alternative: Try-except
try:
    stack.pop()
except IndexError:
    print("Stack is empty!")
```

**Why it happens:** Trying to remove from empty collection.

**Prevention:** Always check if stack/queue is non-empty before popping.

---

### Common Mistake 2: Confusing LIFO and FIFO

```python
# ❌ WRONG - Thinking stack works like queue
stack = [1, 2, 3]
print(stack.pop(0))  # Removes 1, not 3!

# ✅ CORRECT - Stack removes from END
stack = [1, 2, 3]
print(stack.pop())   # Returns 3

# For queue, use popleft() from deque
from collections import deque
queue = deque([1, 2, 3])
print(queue.popleft())  # Returns 1
```

**Why it happens:** list.pop() removes from end by default.

**Prevention:** Remember: stack = top at end, queue = front at beginning.

---

### Common Mistake 3: Using List for Queue Operations

```python
# ❌ WRONG - O(n) for popleft!
queue = [1, 2, 3]
queue.pop(0)  # O(n) - must shift all elements!

# ✅ CORRECT - Use deque!
from collections import deque
queue = deque([1, 2, 3])
queue.popleft()  # O(1) - just move pointer
```

**Why it happens:** List operations at beginning are slow.

**Prevention:** Use `deque` for queue, `list` for stack.

---

### Common Mistake 4: Not Handling All Cases in Parentheses

```python
# ❌ WRONG - Missing stack empty check
def is_valid(s):
    pairs = {')': '(', ']': '[', '}': '{'}
    for c in s:
        if c in '([{':
            stack.append(c)
        else:
            # What if stack is empty here?
            if stack[-1] != pairs[c]:  # CRASH if empty!
                return False
            stack.pop()
    return True

# ✅ CORRECT - Check stack first
def is_valid(s):
    pairs = {')': '(', ']': '[', '}': '{'}
    stack = []
    for c in s:
        if c in '([{':
            stack.append(c)
        else:
            if not stack or stack[-1] != pairs[c]:
                return False
            stack.pop()
    return len(stack) == 0
```

**Why it happens:** Closing bracket without opening = crash.

**Prevention:** Always check `not stack` before accessing `stack[-1]`.

-------------------------------------------------------------------------------
9. MEMORY REINFORCEMENT
-------------------------------------------------------------------------------

### Quick Reference

| Data Structure | Add | Remove | Use When |
|---------------|-----|--------|----------|
| **Stack** | append() | pop() | Need LIFO, backtracking |
| **Queue** | append() | popleft() | Need FIFO, level order |

### When to Use Stack

- Matching/validation (parentheses, tags)
- Undo operations
- Function call stack
- DFS traversal

### When to Use Queue

- Level-order traversal (BFS)
- Task scheduling
- Print queue
- Request handling

### Decision Tree

```
Need to process items in specific order?
│
├─ Last one added, first one out?
│   └─ Use Stack → append() + pop()
│
└─ First one added, first one out?
    └─ Use Queue → append() + popleft()
```

### Mnemonic

**"Latte" (Last In, First Out)**
- **L**ast → Stack
- **F**irst → Queue

**"FLIP"**
- **F**irst in, **L**ast out → Stack? No!
- Wait... **F**irst in, **F**irst out → Queue
- **L**ast in, **L**ast out → Actually... 
- **L**ast in, **F**irst out → Stack!

Let me fix that: **"LIFO = Stack, FIFO = Queue"**

-------------------------------------------------------------------------------
10. MINI TEST
-------------------------------------------------------------------------------

### Question 1: Concept Check

**What is the output of this code?**
```python
stack = [1, 2, 3]
stack.append(4)
stack.append(5)
print(stack.pop())
print(stack.pop())
```

> **Answer:** 5, then 4
> 
> Stack: [1,2,3,4,5]
> First pop() returns 5 (last added)
> Second pop() returns 4
> Stack is now [1,2,3]

---

### Question 2: Prediction

**What does `is_valid("([)]")` return?**

> **Answer:** False
> 
> The sequence is invalid because:
> - '(' opens
> - '[' opens  
> - ')' tries to close '[' - WRONG!
> - Should close '[' before '('

---

### Question 3: Problem Solving

**When should you use a queue instead of a stack?**

> **Answer:** When you need First-In-First-Out (FIFO) processing.
> 
> Examples:
> - Printing documents in order
> - BFS (Breadth-First Search)
> - Customer service queue
> - Any situation where order matters

-------------------------------------------------------------------------------
11. LEETCODE PRACTICE
-------------------------------------------------------------------------------

### Problem: Valid Parentheses

**Problem Statement:**
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:
1. Open brackets are closed by the same type of brackets.
2. Open brackets are closed in the correct order.
3. Every close bracket has a corresponding open bracket.

**Examples:**
```
Input: "()"
Output: true

Input: "()[]{}"
Output: true

Input: "(]"
Output: false

Input: "([)]"
Output: false
```

**Solution:**
```python
def is_valid(s):
    """
    Check if parentheses string is valid.
    
    Time: O(n)
    Space: O(n) worst case
    """
    stack = []
    pairs = {
        ')': '(',
        ']': '[',
        '}': '{'
    }
    
    for char in s:
        if char in '([{':
            # Opening bracket - push to stack
            stack.append(char)
        elif char in ')]}':
            # Closing bracket - must match top of stack
            if not stack or stack[-1] != pairs[char]:
                return False
            stack.pop()
    
    # All brackets must be matched (stack empty)
    return len(stack) == 0


# Read input
s = input()
print(is_valid(s))
```

-------------------------------------------------------------------------------
12. BONUS CHALLENGE
-------------------------------------------------------------------------------

### Challenge: Sliding Window Maximum

**Problem:**
Given an array `nums`, there is a sliding window of size `k` which moves from the left of the array to the right. You can only see the `k` numbers in the window. Return the max number in each window.

**Example:**
```
Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
Output: [3,3,5,5,6,7]
Explanation:
Window position                Max
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

**Solution using Monotonic Queue:**
```python
from collections import deque

def max_sliding_window(nums, k):
    """
    Find maximum in each sliding window.
    Uses monotonic decreasing deque for O(n) solution.
    
    Time: O(n)
    Space: O(k)
    """
    result = []
    dq = deque()  # Store indices, values decreasing
    
    for i in range(len(nums)):
        # Remove indices that are out of current window
        while dq and dq[0] <= i - k:
            dq.popleft()
        
        # Remove indices of smaller elements (they won't be max)
        while dq and nums[dq[-1]] < nums[i]:
            dq.pop()
        
        # Add current index
        dq.append(i)
        
        # Window is ready (i >= k-1 means we have k elements)
        if i >= k - 1:
            result.append(nums[dq[0]])  # Front is always max
    
    return result


# Read input
k = int(input())
nums = list(map(int, input().split()))
t = int(input())  # t is window size, k is also window size
# The problem uses k as window size, but test input gives k first

# Alternative with cleaner input handling
result = max_sliding_window(nums, k)
print(result)
```

**Why Monotonic Deque Works:**
```
Window: [1, 3, -1] → Max = 3
Deque (stores indices, decreasing values):
[3,-1] → indices 1,2 → values 3,-1
Max at front = 3 ✓

Slide to [3,-1,-3] → Max = 3
Remove index 0 (out of window)
Deque already: [3,-1] → Max still 3 ✓

Slide to [-1,-3,5] → Max = 5
Remove indices with smaller values than 5
Deque: [5] → Max = 5 ✓
```

-------------------------------------------------------------------------------
13. LESSON REFLECTION
-------------------------------------------------------------------------------

### What You Learned Today

1. **Stack (LIFO):** Last In, First Out — use `append()` and `pop()`
2. **Queue (FIFO):** First In, First Out — use `append()` and `popleft()`
3. **Valid Parentheses:** Classic stack problem
4. **BFS:** Uses queue for level-order traversal
5. **Deque:** Efficient for queue operations

### Key Takeaways

- Stack: append() + pop() (LIFO)
- Queue: append() + popleft() with deque (FIFO)
- Always check for empty before popping
- Use deque for O(1) queue operations

### Common Patterns

| Pattern | Data Structure |
|---------|---------------|
| Parentheses matching | Stack |
| Undo operations | Stack |
| BFS | Queue |
| DFS | Stack |
| Monotonic queue | Deque |

### Weak Points to Watch

- Forgetting to check for empty before popping
- Using list for queue (use deque instead)
- Not returning `len(stack) == 0` for valid parentheses

### Next Lesson Preview

**Lesson 45:** Tree and Binary Tree — Hierarchical data structures

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 44 / 2000 |
| **Chapter** | 4 (Data Structures) |
| **XP** | 440 |
| **Rank** | Builder |
| **Mastery** | Stack and Queue |
| **Weaknesses** | Remembering when to use list vs deque |
| **Recommended Focus** | Practice parentheses validation |
| **Suggested Review** | Lesson 43 (Hashing - used in BFS visited set) |
| **Next Lesson Readiness** | ✓ Ready for Trees |

---

**Type 45 to continue**