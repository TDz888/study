# Lesson 24 — More Dictionary Operations

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 8 - Dictionary basics.

**Current Lesson:** Advanced **dictionary operations**.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Dictionary comprehension
- Get with default
- Update and setdefault
- Nested dictionaries

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Get with default
d = {"a": 1}
print(d.get("b", 0))   # 0 (default if not found)
print(d.get("a", 0))   # 1

# setdefault - set if not exists
d.setdefault("c", 3)   # adds c=3
d.setdefault("a", 99)  # a exists, returns 1

# Update - merge dictionaries
d1 = {"a": 1}
d2 = {"b": 2}
d1.update(d2)
print(d1)  # {'a':1,'b':2}

# Dictionary comprehension
squares = {x: x**2 for x in range(5)}
print(squares)  # {0:0,1:1,2:4,3:9,4:16}

# Nested dictionaries
users = {
    "user1": {"name": "Minh", "email": "minh@test.com"},
    "user2": {"name": "Lan", "email": "lan@test.com"}
}
print(users["user1"]["name"])  # Minh
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** d.get("missing", "N/A") returns?
> **Answer:** "N/A"

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Invert a dictionary (keys become values).

```python
def invert(d):
    return {v: k for k, v in d.items()}

print(invert({"a": 1, "b": 2}))  # {1:'a', 2:'b'}
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 24 / 2000 |
| **XP** | 240 |

Type **25** to continue