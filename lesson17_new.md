# Lesson 17 — While Loops Deep Dive

-------------------------------------------------------------------------------
1. KNOWLEDGE CONNECTION
-------------------------------------------------------------------------------

**Previous Lesson:** Lesson 6 - Basic while loops.

**Current Lesson:** Deeper understanding of while loops with practical examples.

-------------------------------------------------------------------------------
2. TODAY'S MISSION
-------------------------------------------------------------------------------

**What you'll learn:**
- Complex while conditions
- While True with break
- Input validation with while
- Infinite loop detection

-------------------------------------------------------------------------------
3. MAIN CODE
-------------------------------------------------------------------------------

```python
# Example 1: Countdown with while
print("=== Countdown ===")
count = 5
while count > 0:
    print(count)
    count -= 1
print("Liftoff!")

# Example 2: Input validation
print("\n=== Input Validation ===")
age = -1
while age < 0:
    try:
        age = int(input("Enter age (positive): "))
        if age < 0:
            print("Must be positive!")
    except ValueError:
        print("Invalid input!")
print(f"Valid age: {age}")

# Example 3: While True with break
print("\n=== Menu Loop ===")
while True:
    print("1. Add 2. View 3. Exit")
    choice = input("Choice: ")
    if choice == "3":
        print("Goodbye!")
        break
    print(f"Selected: {choice}")

# Example 4: Process list with while
print("\n=== Process List ===")
items = [1, 2, 3, 4, 5]
while items:
    item = items.pop(0)
    print(f"Processing: {item}")
```

-------------------------------------------------------------------------------
4. MINI TEST
-------------------------------------------------------------------------------

**Question:** How to stop infinite while True loop?
> **Answer:** Use break statement

-------------------------------------------------------------------------------
5. BONUS CHALLENGE
-------------------------------------------------------------------------------

Guessing game with limited attempts.

```python
import random
secret = random.randint(1, 10)
attempts = 3

while attempts > 0:
    guess = int(input("Guess (1-10): "))
    if guess == secret:
        print("You won!")
        break
    attempts -= 1
    print(f"Wrong! {attempts} attempts left")
else:
    print(f"Game over! Secret was {secret}")
```

---

## Progress

| Field | Value |
|-------|-------|
| **Lesson** | 17 / 2000 |
| **XP** | 170 |

Type **18** to continue