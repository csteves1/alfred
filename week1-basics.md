# Week 1 — Python Basics
**Phase 1 | June**  
**Parallel to:** Data Structures course week 1-2

---

## What You're Learning This Week

The absolute fundamentals. No skipping. No shortcuts.  
Every concept this week appears directly in Alfred's codebase later.

---

## Concepts to Learn and Memorize

### 1. Variables and Data Types
```python
# The five types you'll use constantly
name = "Alfred"           # str — text
age = 28                  # int — whole numbers
battery = 87.5            # float — decimal numbers
is_active = True          # bool — True or False
nothing = None            # NoneType — absence of value
```
**Memorize:** You don't declare types in Python. Python figures it out.  
**Memorize:** Use f-strings for combining strings and variables.
```python
print(f"Battery level: {battery}%")
```

---

### 2. Lists and Dictionaries
These are the two most important data structures in Python. You will use them every single day.

```python
# List — ordered collection, use when order matters
commands = ["wake up", "play music", "check weather"]
commands.append("set timer")     # add to end
commands[0]                      # access by index — "wake up"
commands[-1]                     # last item — "set timer"
len(commands)                    # how many items — 4

# Dictionary — key/value pairs, use when you need to look things up
user = {
    "name": "Christopher",
    "age": 28,
    "location": "Myrtle Beach",
    "is_active": True
}
user["name"]                     # access by key — "Christopher"
user["city"] = "Charlotte"       # add new key
user.get("job", "unknown")       # safe access with default
```
**Memorize:** Lists use brackets [ ]. Dictionaries use braces { }.  
**Memorize:** Dictionary keys are almost always strings.

---

### 3. Loops
```python
# For loop — use when you know what you're looping over
for command in commands:
    print(f"Processing: {command}")

# While loop — use when you're waiting for a condition
battery = 100
while battery > 20:
    battery -= 10
    print(f"Battery: {battery}%")

# Loop with index when you need the position
for i, command in enumerate(commands):
    print(f"{i}: {command}")
```

---

### 4. Conditionals
```python
battery = 15

if battery < 20:
    print("Low battery — return to dock")
elif battery < 50:
    print("Battery getting low")
else:
    print("Battery OK")

# One line conditional (ternary)
status = "low" if battery < 20 else "ok"
```

---

### 5. String Methods You Need to Know
```python
message = "  Hello Alfred  "
message.strip()          # removes whitespace — "Hello Alfred"
message.lower()          # "  hello alfred  "
message.upper()          # "  HELLO ALFRED  "
message.split(" ")       # splits into list by space
"Alfred" in message      # True — checks if substring exists

sentence = "wake up alfred"
words = sentence.split(" ")    # ["wake", "up", "alfred"]
" ".join(words)                # back to "wake up alfred"
```

---

## This Week's Practice Scripts

Write each of these yourself. No copying. No AI writing it for you.  
If you get stuck for more than 15 minutes, look at the concept above, not AI.

### Exercise 1 — `user_profile.py`
Create a dictionary representing yourself with at least 6 keys (name, age, city, job, skills as a list, is_student as bool). Print each value using f-strings. Then add a new key and print the whole dictionary.

**Alfred connection:** Alfred stores user profiles exactly like this.

---

### Exercise 2 — `command_list.py`
Create a list of 5 things you might tell Alfred to do. Loop through the list and print each one numbered. Then add one more command to the end and print the total count.

**Alfred connection:** Alfred's command queue is a list.

---

### Exercise 3 — `battery_monitor.py`
Write a script that starts battery at 100. Use a while loop to drain it by a random amount each cycle (use Python's built-in `random.randint(1, 15)`). Print the battery level each cycle. When it drops below 20, print "Low battery warning" and stop the loop.

**Alfred connection:** This is literally Alfred's battery telemetry logic.

---

### Exercise 4 — `message_parser.py`
Ask the user to type a message using `input()`. Convert it to lowercase, strip whitespace, and split it into individual words. Print the word count. Check if the word "alfred" is in the message and print whether it was a direct command or not.

**Alfred connection:** This is how Alfred parses incoming voice commands.

---

### Exercise 5 — `user_profile_v2.py`
Expand Exercise 1. Ask the user to input their name and city using `input()`. Store the responses in your dictionary, replacing the hardcoded values. Print a formatted summary.

**Alfred connection:** Alfred collects and updates user data dynamically.

---

## Free Resources for This Week

1. [Python Official Tutorial — Sections 3 and 4](https://docs.python.org/3/tutorial/introduction.html)
2. [freeCodeCamp Python Course](https://www.youtube.com/watch?v=rfscVS0vtbw) — watch 0:00 to 1:30:00 this week
3. [W3Schools Python](https://www.w3schools.com/python/) — use as quick reference when you forget syntax

---

## End of Week Check

Before moving to Week 2, you should be able to:

- [ ] Create and access variables of all five types without looking it up
- [ ] Build a list and dictionary from scratch and access their values
- [ ] Write a for loop and a while loop without syntax errors
- [ ] Write an if/elif/else block correctly
- [ ] Use at least 5 string methods from memory
- [ ] Explain every line of all 5 exercises out loud

If you can't do all of these — repeat the exercises with different content before moving on.

---

## Commit This Week

Push at minimum:
- All 5 exercise scripts
- This README checked off with your completion date

Commit message format:
```
week1: complete all 5 basics exercises
```
