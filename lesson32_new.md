# Lesson 32 — Type Hints (Gợi ý kiểu)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 31 - Advanced file operations.

**Current Lesson:** Learning **type hints** - annotating function parameters and return types.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Basic type annotations
- Optional types
- Union types

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
from typing import List, Dict, Optional, Union

# Basic type hints
def greet(name: str) -> str:
    return f"Hello, {name}!"

def add(a: int, b: int) -> int:
    return a + b

print(greet("Minh"))
print(add(5, 3))

# List type
def process_list(items: List[int]) -> int:
    return sum(items)

# Dict type
def process_dict(data: Dict[str, int]) -> str:
    return f"Sum: {sum(data.values())}"

# Optional (may be None)
def find_user(name: Optional[str] = None) -> str:
    if name:
        return f"Found: {name}"
    return "User not found"

# Union (multiple types)
def parse(value: Union[int, str]) -> str:
    return str(value)

print(process_list([1, 2, 3]))
print(process_dict({"a": 1, "b": 2}))
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** def foo(x: int) -> str: means?
> **Answer:** Takes int, returns str

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Type annotated functions for calculator.

```python
def calculator(a: float, b: float, op: str) -> float:
    if op == "+": return a + b
    if op == "-": return a - b
    if op == "*": return a * b
    if op == "/" and b != 0: return a / b
    raise ValueError("Invalid operation")

print(calculator(10, 5, "+"))  # 15.0
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 32 / 2000 |
| **XP** | 320 |

Type **33** to continue