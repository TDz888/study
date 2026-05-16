# Lesson 23 — More String Operations

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 16 - Basic string methods.

**Current Lesson:** More **advanced string operations**.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- String formatting with format()
- f-strings advanced
- is methods (isalpha, isdigit, etc.)
- String partitioning

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Format method
text = "Hello {}!"
print(text.format("World"))  # Hello World!

# Multiple placeholders
print("{} + {} = {}".format(2, 3, 5))

# Named placeholders
print("{name} is {age} years old".format(name="Minh", age=25))

# is methods
print("abc".isalpha())  # True
print("123".isdigit()) # True
print("abc123".isalnum()) # True
print("   ".isspace()) # True

# Partition
email = "user@example.com"
name, sep, domain = email.partition("@")
print(name, domain)  # user example.com

# zfill (padding)
print("42".zfill(5))  # 00042
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** "hello".isalpha() = ?
> **Answer:** True

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Validate email format.

```python
def is_valid_email(email):
    return "@" in email and "." in email.split("@")[1]

print(is_valid_email("test@example.com"))  # True
print(is_valid_email("invalid"))  # False
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 23 / 2000 |
| **XP** | 230 |

Type **24** to continue