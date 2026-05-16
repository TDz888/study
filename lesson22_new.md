# Lesson 22 — Sets (Tập hợp)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 21 - Tuples (immutable sequences).

**Current Lesson:** Learning **sets** - unordered collections of unique elements.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Creating sets
- Adding/removing elements
- Set operations: union, intersection, difference

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Create
fruits = {"apple", "banana", "cherry"}
numbers = set([1, 2, 3, 2, 1])  # {1, 2, 3} (duplicates removed)
empty = set()

# Add/remove
fruits.add("orange")
fruits.remove("banana")
# fruits.remove("grape")  # Error if not exists
fruits.discard("grape")  # No error if not exists

# Operations
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

print(set1 | set2)   # {1,2,3,4,5,6} (union)
print(set1 & set2)   # {3,4} (intersection)
print(set1 - set2)   # {1,2} (difference)
print(set1 ^ set2)   # {1,2,5,6} (symmetric difference)

# Check membership
print("apple" in fruits)  # True
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** What does set([1,1,2,2,3]) produce?
> **Answer:** {1, 2, 3} (unique elements only)

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Find common elements between two lists.

```python
def common(l1, l2):
    return list(set(l1) & set(l2))

print(common([1,2,3,4], [3,4,5,6]))  # [3, 4]
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 22 / 2000 |
| **XP** | 220 |

Type **23** to continue