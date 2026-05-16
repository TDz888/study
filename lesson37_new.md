# Lesson 37 — Datetime Module

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 36 - Regular Expressions.

**Current Lesson:** Learning **datetime** - working with dates and times.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- datetime objects
- Formatting dates
- Timedelta calculations

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
from datetime import datetime, timedelta

# Current datetime
now = datetime.now()
print(now)  # 2024-01-15 12:30:45.123456

# Create specific datetime
dt = datetime(2024, 1, 15, 10, 30)
print(dt)

# Format
print(dt.strftime("%Y-%m-%d"))  # 2024-01-15
print(dt.strftime("%B %d, %Y"))  # January 15, 2024
print(dt.strftime("%H:%M"))      # 10:30

# Parse
parsed = datetime.strptime("2024-01-15", "%Y-%m-%d")
print(parsed)

# Timedelta
future = now + timedelta(days=30)
print(f"30 days from now: {future}")

# Date arithmetic
diff = datetime(2024, 3, 1) - datetime(2024, 1, 1)
print(f"Days: {diff.days}")  # 60
```

-------------------------------------------------------------------------------
4. BONUS CHALLENGE
-------------------------------------------------------------------------------

Days until birthday.

```python
from datetime import datetime

def days_until_birthday(month, day):
    today = datetime.now()
    bday = datetime(today.year, month, day)
    if bday < today:
        bday = datetime(today.year + 1, month, day)
    return (bday - today).days

print(days_until_birthday(12, 25))
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 37 / 2000 |
| **XP** | 370 |

Type **38** to continue