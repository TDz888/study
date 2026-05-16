# Lesson 15 — List Methods (Phương thức List)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 7 - Learned lists basics: create, access, modify.

**Current Lesson:** Learning **list methods** - built-in functions to manipulate lists efficiently.

**Future Usefulness:** Lists are everywhere - methods make working with them much easier.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- append(), insert(), extend()
- remove(), pop(), clear()
- index(), count(), sort(), reverse()
- copy(), list()

-------------------------------------------------------------------------------
3. CONCEPT FOUNDATION
-------------------------------------------------------------------------------

### Adding Items
```python
lst = [1, 2, 3]
lst.append(4)      # [1,2,3,4] - add to end
lst.insert(1, 5)   # [1,5,2,3,4] - insert at index
lst.extend([7,8])  # [1,5,2,3,4,7,8] - add multiple
```

### Removing Items
```python
lst = [1, 2, 3, 2]
lst.remove(2)      # removes first 2 → [1,3,2]
lst.pop()         # removes last → [1,3]
lst.clear()       # removes all → []
```

### Other Methods
```python
lst = [3, 1, 2]
lst.sort()        # [1,2,3]
lst.reverse()     # [3,2,1]
lst.index(2)      # 1 (position of 2)
lst.count(3)     # 1 (how many 3s)
```

-------------------------------------------------------------------------------
4. MAIN CODE
-------------------------------------------------------------------------------

```python
# All methods demonstrated
numbers = [1, 2, 3]

# Add
numbers.append(4)
print("append(4):", numbers)  # [1,2,3,4]

numbers.insert(1, 99)
print("insert(1,99):", numbers)  # [1,99,2,3,4]

numbers.extend([5, 6])
print("extend:", numbers)  # [1,99,2,3,4,5,6]

# Remove
numbers.remove(99)
print("remove(99):", numbers)  # [1,2,3,4,5,6]

numbers.pop()
print("pop():", numbers)  # [1,2,3,4,5]

# Modify
numbers.sort()
print("sort():", numbers)  # [1,2,3,4,5]

numbers.reverse()
print("reverse():", numbers)  # [5,4,3,2,1]

# Info
print("index(3):", numbers.index(3))  # 2
print("count(5):", numbers.count(5))  # 1

# Copy
copied = numbers.copy()
print("copy:", copied)  # [5,4,3,2,1]
```

-------------------------------------------------------------------------------
5. MINI TEST
-------------------------------------------------------------------------------

**Question:** What is the output?
```python
lst = [3, 1, 2]
lst.sort()
print(lst)
```
> **Answer:** [1, 2, 3]

-------------------------------------------------------------------------------
6. BONUS CHALLENGE
-------------------------------------------------------------------------------

Remove all occurrences of a value from list.

```python
def remove_all(lst, value):
    while value in lst:
        lst.remove(value)
    return lst

print(remove_all([1,2,3,2,4,2], 2))  # [1,3,4]
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 15 / 2000 |
| **XP** | 150 |

Type **16** to continue