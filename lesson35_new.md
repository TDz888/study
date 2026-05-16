# Lesson 35 — Iterators (Bộ lặp)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 34 - Generators.

**Current Lesson:** Understanding **iterators** - objects that can be iterated over.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Iterator protocol
- __iter__ and __next__
- Custom iterators

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Built-in iterators
lst = [1, 2, 3]
it = iter(lst)
print(next(it))  # 1
print(next(it))  # 2

# Custom iterator
class Counter:
    def __init__(self, limit):
        self.limit = limit
        self.current = 0
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current >= self.limit:
            raise StopIteration
        self.current += 1
        return self.current

for num in Counter(5):
    print(num, end=" ")
print()

# Range is iterator
r = range(5)
print(iter(r))  # <range_iterator>
print(next(r))  # 0
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** What methods make object iterable?
> **Answer:** __iter__ and __next__

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Create range-like iterator.

```python
class MyRange:
    def __init__(self, start, stop):
        self.current = start
        self.stop = stop
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current >= self.stop:
            raise StopIteration
        self.current += 1
        return self.current - 1

print(list(MyRange(3, 7)))  # [3,4,5,6]
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 35 / 2000 |
| **XP** | 350 |

Type **36** to continue