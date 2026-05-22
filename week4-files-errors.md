# Week 4 — File Handling and Error Management
**Phase 1 | Early July**

---

## What You're Learning This Week

Alfred needs to read and write data constantly — conversation logs, user profiles, configuration files. Error handling keeps Alfred running when something breaks instead of crashing entirely.

---

## Concepts to Memorize

### File Operations
```python
# Writing to a file
with open("conversation_log.txt", "w") as f:
    f.write("user: Hey Alfred\n")
    f.write("assistant: Good morning\n")

# Appending to a file — use "a" not "w" or you overwrite
with open("conversation_log.txt", "a") as f:
    f.write("user: What time is it?\n")

# Reading from a file
with open("conversation_log.txt", "r") as f:
    content = f.read()          # entire file as string
    
with open("conversation_log.txt", "r") as f:
    lines = f.readlines()       # list of lines

# JSON files — you'll use these constantly
import json

data = {"name": "Christopher", "age": 28}

# Write JSON
with open("user.json", "w") as f:
    json.dump(data, f, indent=2)

# Read JSON
with open("user.json", "r") as f:
    loaded = json.load(f)
    
print(loaded["name"])   # "Christopher"
```
**Memorize:** Always use `with open()` — it closes the file automatically.  
**Memorize:** "w" overwrites. "a" appends. "r" reads.

---

### Error Handling
```python
def read_user_profile(filepath):
    try:
        with open(filepath, "r") as f:
            return json.load(f)
    except FileNotFoundError:
        print(f"No profile found at {filepath}")
        return None
    except json.JSONDecodeError:
        print("Profile file is corrupted")
        return None
    except Exception as e:
        print(f"Unexpected error: {e}")
        return None
    finally:
        print("Attempted to read profile")  # always runs

# Custom exceptions
class AlfredNodeError(Exception):
    pass

class LLMConnectionError(AlfredNodeError):
    pass

def connect_to_llm(model):
    if model not in ["llama3", "gpt-4"]:
        raise LLMConnectionError(f"Unknown model: {model}")
```

---

## This Week's Exercises

### Exercise 1 — `conversation_saver.py`
Write functions to save and load conversation history as JSON. The save function takes a filename and list of message dictionaries. The load function returns the list or an empty list if file doesn't exist. Handle all errors gracefully.

### Exercise 2 — `config_manager.py`
Build a `ConfigManager` class that reads a JSON config file on init, provides a `get(key, default)` method, a `set(key, value)` method that saves back to file immediately, and handles missing file by creating a default config.

### Exercise 3 — `alfred_logger.py`
Build a logger that writes timestamped events to a .log text file. Each line should be formatted: `[2026-06-15 14:23:01] [brain-node] [INFO] Message routed to local model`. Use `datetime` module for timestamps.

### Exercise 4 — `safe_reader.py`
Write a function that reads any file type (txt or json) and returns content safely, with custom exceptions for file not found, permission error, and corrupt JSON specifically.

### Exercise 5 — `profile_persistence.py`
Combine your `UserProfile` class from Week 3 with JSON file saving. Add `save()` and `load()` class methods that persist the profile to disk and restore it.

---

## End of Week Check
- [ ] Read and write txt and JSON files from memory
- [ ] Write try/except/finally blocks correctly
- [ ] Create and raise custom exceptions
- [ ] Handle at least 3 specific exception types in one block

---
```
week4: file handling and error management exercises complete
```
