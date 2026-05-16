# Lesson 16 — String Methods (Phương thức String)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 15 - List methods for manipulating lists.

**Current Lesson:** Learning **string methods** - built-in functions for working with strings.

**Future Usefulness:** Text processing is everywhere - parsing, cleaning, formatting data.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Case methods: upper(), lower(), title(), strip()
- Search: find(), count(), startswith(), endswith()
- Replace: replace(), split(), join()

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
text = "  Hello World!  "

# Case
print(text.upper())     # "  HELLO WORLD!  "
print(text.lower())     # "  hello world!  "
print(text.strip())     # "Hello World!" (removes spaces)

# Search
print(text.find("World"))    # 7 (position)
print(text.count("l"))       # 3
print(text.startswith("  He"))  # True
print(text.endswith("!  "))     # True

# Modify
print(text.replace("World", "Python"))  # "  Hello Python!  "

# Split and Join
sentence = "apple,banana,cherry"
parts = sentence.split(",")  # ['apple','banana','cherry']
print("->".join(parts))      # "apple->banana->cherry"

# String formatting
name = "Minh"
age = 25
print(f"Name: {name}, Age: {age}")  # "Name: Minh, Age: 25"
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** What does "  hi  ".strip() return?
> **Answer:** "hi"

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Count words in a sentence.

```python
def count_words(sentence):
    return len(sentence.split())

print(count_words("Hello world Python"))  # 3
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 16 / 2000 |
| **XP** | 160 |

Type **17** to continue