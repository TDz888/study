# Lesson 26 — Map, Filter, Reduce

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 25 - Lambda functions.

**Current Lesson:** Deep dive into **map, filter, reduce** - functional programming tools.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- map() - transform each element
- filter() - keep matching elements
- reduce() - combine elements
- functools module

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
from functools import reduce

# map - transform
nums = [1, 2, 3, 4]
doubled = list(map(lambda x: x * 2, nums))
print(doubled)  # [2, 4, 6, 8]

# filter - select
evens = list(filter(lambda x: x % 2 == 0, nums))
print(evens)  # [2, 4]

# Chaining
result = list(map(lambda x: x**2, filter(lambda x: x > 2, nums)))
print(result)  # [9, 16] (3^2, 4^2)

# reduce - combine
total = reduce(lambda a, b: a + b, nums)
print(total)  # 10

# With initial value
max_val = reduce(lambda a, b: a if a > b else b, nums)
print(max_val)  # 4
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** reduce(lambda a,b: a+b, [1,2,3]) = ?
> **Answer:** 6

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Find product of list.

```python
from functools import reduce
product = reduce(lambda a, b: a * b, [1, 2, 3, 4])
print(product)  # 24
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 26 / 2000 |
| **XP** | 260 |

Type **27** to continue