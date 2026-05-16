# Lesson 31 — Working with Files (Advanced)

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 11 - Basic File I/O.

**Current Lesson:** Advanced **file operations** - JSON, CSV, binary files.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- JSON files (read/write)
- CSV files
- Binary files
- Path operations

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
import json
import csv
import os

# JSON - JavaScript Object Notation
data = {"name": "Minh", "age": 25, "skills": ["Python", "Java"]}

# Write JSON
with open("data.json", "w") as f:
    json.dump(data, f, indent=2)

# Read JSON
with open("data.json", "r") as f:
    loaded = json.load(f)
print(loaded)

# CSV - Comma Separated Values
# Write CSV
with open("users.csv", "w", newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["name", "age"])
    writer.writerow(["Minh", 25])
    writer.writerow(["Lan", 30])

# Read CSV
with open("users.csv", "r") as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)

# Path operations
print(os.path.exists("data.json"))  # True
print(os.path.getsize("data.json"))  # size in bytes
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** How to write dict to JSON file?
> **Answer:** json.dump(dict, file)

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Save and load user preferences.

```python
def save_prefs(prefs, filename="prefs.json"):
    with open(filename, "w") as f:
        json.dump(prefs, f)

def load_prefs(filename="prefs.json"):
    try:
        with open(filename, "r") as f:
            return json.load(f)
    except:
        return {}

prefs = {"theme": "dark", "volume": 50}
save_prefs(prefs)
loaded = load_prefs()
print(loaded)
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 31 / 2000 |
| **XP** | 310 |

Type **32** to continue