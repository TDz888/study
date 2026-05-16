# Lesson 36 — Regular Expressions (Biểu thức chính quy)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 35 - Iterators.

**Current Lesson:** Learning **regex** - pattern matching in strings.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- re module basics
- match, search, findall
- Pattern syntax
- Substitution

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
import re

# Basic patterns
text = "My email is test@example.com"

# search - find anywhere
match = re.search(r'\w+@\w+\.\w+', text)
print(match.group())  # test@example.com

# findall - find all matches
text = "Call 123-456-7890 or 987-654-3210"
phones = re.findall(r'\d{3}-\d{3}-\d{4}', text)
print(phones)  # ['123-456-7890', '987-654-3210']

# match - start of string
print(re.match(r'\d+', "123abc"))  # Match object

# split
print(re.split(r'\s+', "hello world"))  # ['hello','world']

# sub - replace
print(re.sub(r'\d', 'X', "123"))  # XXX

# Pattern symbols
# \d - digit
# \w - word character
# \s - whitespace
# . - any character
# * - zero or more
# + - one or more
# ? - optional

# With groups
match = re.match(r'(\d+)-(\d+)', "123-456")
print(match.group(1))  # 123
print(match.group(2))  # 456
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** What does \d+ match?
> **Answer:** One or more digits

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Extract all emails from text.

```python
text = "Contact us at support@example.com or sales@company.org"
emails = re.findall(r'[\w.-]+@[\w.-]+\.\w+', text)
print(emails)  # ['support@example.com', 'sales@company.org']
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 36 / 2000 |
| **XP** | 360 |

Type **37** to continue