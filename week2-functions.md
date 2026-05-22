# Week 2 — Functions and Logic
**Phase 1 | June**  
**Parallel to:** Data Structures course week 3-4

---

## What You're Learning This Week

Functions are how you stop repeating yourself and start building real systems.  
Every node in Alfred is a collection of functions. This week you learn to think in functions.

---

## Concepts to Learn and Memorize

### 1. Functions
```python
# Basic function
def greet_user(name):
    return f"Good morning, {name}"

result = greet_user("Christopher")
print(result)   # "Good morning, Christopher"

# Multiple parameters
def calculate_battery_percentage(voltage, max_voltage=4.2):
    percentage = (voltage / max_voltage) * 100
    return round(percentage, 1)

# Default parameters — max_voltage has a default of 4.2
print(calculate_battery_percentage(3.7))        # uses default
print(calculate_battery_percentage(3.7, 4.2))   # explicit
```
**Memorize:** Functions always start with `def`. Always return something or return None implicitly.  
**Memorize:** Default parameters go at the end of the parameter list.

---

### 2. Multiple Return Values
```python
def get_user_state(battery, hour):
    is_low_battery = battery < 20
    is_bedtime = hour >= 22 or hour < 6
    state = "sleeping" if is_bedtime else "active"
    return state, is_low_battery   # returns a tuple

state, low_battery = get_user_state(15, 23)
print(state)        # "sleeping"
print(low_battery)  # True
```

---

### 3. List Comprehensions
This is one of Python's most useful patterns. Learn it now.
```python
commands = ["wake up", "play music", "  check weather  ", "set timer"]

# Old way
cleaned = []
for command in commands:
    cleaned.append(command.strip())

# List comprehension — same thing, one line
cleaned = [command.strip() for command in commands]

# With condition — only keep commands over 7 characters
long_commands = [c for c in commands if len(c.strip()) > 7]
```

---

### 4. *args and **kwargs
You'll see these everywhere in AI libraries.
```python
# *args — accept any number of positional arguments
def log_events(*events):
    for event in events:
        print(f"[LOG] {event}")

log_events("user detected", "mic activated", "response generated")

# **kwargs — accept any number of keyword arguments
def create_user_profile(**details):
    return details   # returns a dictionary

profile = create_user_profile(name="Christopher", age=28, city="Myrtle Beach")
print(profile["name"])   # "Christopher"
```

---

### 5. Lambda Functions
Short anonymous functions used frequently in data processing.
```python
# Regular function
def double(x):
    return x * 2

# Lambda equivalent
double = lambda x: x * 2

# Common use — sorting a list of dictionaries
users = [{"name": "Alex", "age": 25}, {"name": "Chris", "age": 28}]
sorted_users = sorted(users, key=lambda u: u["age"])
```

---

## This Week's Practice Scripts

### Exercise 1 — `alfred_responses.py`
Write three functions:
- `get_greeting(hour)` — returns "Good morning", "Good afternoon", or "Good evening" based on the hour
- `get_battery_status(percentage)` — returns "Critical", "Low", "Normal", or "Full" based on ranges you define
- `format_response(greeting, name, battery_status)` — combines them into one string Alfred would say

Call all three and print the result.

**Alfred connection:** These are Alfred's response formatting utilities.

---

### Exercise 2 — `command_processor.py`
Write a function `process_commands(commands)` that takes a list of raw command strings and returns a cleaned list — stripped of whitespace, converted to lowercase, and filtered to remove any empty strings. Use a list comprehension.

Then write a second function `find_command(commands, keyword)` that returns all commands containing a specific keyword.

**Alfred connection:** This is Alfred's command preprocessing pipeline.

---

### Exercise 3 — `battery_calculator.py`
Write a function `estimate_runtime(battery_percentage, drain_rate_per_hour)` that returns how many hours and minutes of runtime remain. Return both values separately. Handle the edge case where battery is already at 0.

**Alfred connection:** Alfred's power management node uses exactly this logic.

---

### Exercise 4 — `event_logger.py`
Write a function `log_event(*args, **kwargs)` that accepts any number of events as positional args, and optional metadata as keyword args (like `severity="high"`, `source="brain-node"`). Print each event with its metadata formatted cleanly.

**Alfred connection:** Alfred's MQTT bus passes events exactly like this.

---

### Exercise 5 — `user_sorter.py`
Create a list of at least 4 dictionaries representing different users, each with a name, age, and last_seen timestamp (just use an integer like 1716000000 for now). Write a function that sorts them by last_seen using a lambda. Print the sorted result.

**Alfred connection:** Alfred's multi-user recognition node tracks and sorts users this way.

---

## Free Resources for This Week

1. [freeCodeCamp Python Course](https://www.youtube.com/watch?v=rfscVS0vtbw) — watch 1:30:00 to 3:00:00
2. [Real Python — Defining Functions](https://realpython.com/defining-your-own-python-function/)
3. [Real Python — List Comprehensions](https://realpython.com/list-comprehension-python/)

---

## End of Week Check

- [ ] Write a function with default parameters from memory
- [ ] Return multiple values from a function and unpack them
- [ ] Write a list comprehension with a condition
- [ ] Use *args and **kwargs correctly
- [ ] Write a lambda and use it in a sorted() call
- [ ] Explain every line of all 5 exercises out loud

---

## Commit This Week

```
week2: complete functions and logic exercises
```
