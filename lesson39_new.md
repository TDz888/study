# Lesson 39 — Magic Methods

-------------------------------------------------------------------------------
1. TODAY'S MISSION
-------------------------------------------------------------------------------

Special methods in classes: __str__, __repr__, __add__, __len__, etc.

-------------------------------------------------------------------------------
2. MAIN CODE
-------------------------------------------------------------------------------

```python
class Vector:
    def __init__(self, x, y):
        self.x, self.y = x, y
    
    def __str__(self):
        return f"Vector({self.x}, {self.y})"
    
    def __repr__(self):
        return f"Vector({self.x!r}, {self.y!r})"
    
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    
    def __len__(self):
        return 2
    
    def __getitem__(self, i):
        return [self.x, self.y][i]

v1 = Vector(1, 2)
v2 = Vector(3, 4)
print(v1 + v2)  # Vector(4, 6)
print(str(v1))  # Vector(1, 2)
print(v1[0])    # 1
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 39 / 2000 |
| **XP** | 390 |

Type **40** to continue