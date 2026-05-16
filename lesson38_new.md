# Lesson 38 — More on Classes

-------------------------------------------------------------------------------
1. TODAY'S MISSION
-------------------------------------------------------------------------------

Advanced class features: properties, class methods, static methods.

-------------------------------------------------------------------------------
2. MAIN CODE
-------------------------------------------------------------------------------

```python
class Rectangle:
    def __init__(self, width, height):
        self._width = width  # private
        self._height = height
    
    @property
    def width(self):
        return self._width
    
    @width.setter
    def width(self, value):
        if value > 0:
            self._width = value
    
    @classmethod
    def from_square(cls, side):
        return cls(side, side)
    
    @staticmethod
    def is_valid(w, h):
        return w > 0 and h > 0

r = Rectangle(10, 5)
print(r.width)  # 10
r.width = 20
print(r.width)  # 20

sq = Rectangle.from_square(5)
print(sq.width, sq.height)  # 5 5

print(Rectangle.is_valid(10, 5))  # True
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 38 / 2000 |
| **XP** | 380 |

Type **39** to continue