# Week 3 — Object Oriented Programming
**Phase 1 | Late June**  
**Parallel to:** Data Structures course week 5-6

---

## What You're Learning This Week

Every node in Alfred is a class. The brain node is a class. The memory pipeline is a class. The battery monitor is a class. Understanding OOP is understanding how Alfred is actually structured.

---

## Concepts to Learn and Memorize

### 1. Classes and Objects
```python
class BatteryMonitor:
    # __init__ runs when you create an instance
    def __init__(self, max_voltage=4.2, warning_threshold=20):
        self.max_voltage = max_voltage
        self.warning_threshold = warning_threshold
        self.current_percentage = 100
        self.is_charging = False

    # Regular method — always takes self as first parameter
    def update(self, voltage):
        self.current_percentage = round((voltage / self.max_voltage) * 100, 1)

    def is_low(self):
        return self.current_percentage < self.warning_threshold

    def get_status(self):
        if self.is_charging:
            return f"Charging — {self.current_percentage}%"
        elif self.is_low():
            return f"LOW BATTERY — {self.current_percentage}%"
        else:
            return f"Battery OK — {self.current_percentage}%"

# Creating an instance
monitor = BatteryMonitor()
monitor.update(3.5)
print(monitor.get_status())   # "LOW BATTERY — 83.3%"... adjust thresholds
```
**Memorize:** `self` refers to the instance. Always first parameter in methods.  
**Memorize:** `__init__` is the constructor. Runs automatically when you create an object.

---

### 2. Inheritance
```python
class AlfredNode:
    """Base class for all Alfred nodes"""
    def __init__(self, node_name):
        self.node_name = node_name
        self.is_running = False

    def start(self):
        self.is_running = True
        print(f"[{self.node_name}] Starting...")

    def stop(self):
        self.is_running = False
        print(f"[{self.node_name}] Stopped.")

    def status(self):
        state = "running" if self.is_running else "stopped"
        return f"{self.node_name}: {state}"


class BrainNode(AlfredNode):
    """Inherits from AlfredNode, adds LLM routing"""
    def __init__(self):
        super().__init__("brain-node")   # calls parent __init__
        self.model = "llama3"
        self.message_count = 0

    def route_message(self, message):
        self.message_count += 1
        # routing logic goes here later
        return f"Routing to {self.model}: {message}"


brain = BrainNode()
brain.start()                          # inherited from AlfredNode
print(brain.route_message("hello"))    # BrainNode's own method
print(brain.status())                  # inherited from AlfredNode
```
**Memorize:** `super().__init__()` calls the parent class constructor.  
**Memorize:** Child classes inherit all parent methods automatically.

---

### 3. Dunder Methods (Magic Methods)
```python
class ConversationLog:
    def __init__(self):
        self.messages = []

    def add(self, role, content):
        self.messages.append({"role": role, "content": content})

    def __len__(self):
        return len(self.messages)       # enables len(log)

    def __str__(self):
        return f"ConversationLog with {len(self)} messages"   # enables print(log)

    def __repr__(self):
        return f"ConversationLog(messages={self.messages})"

log = ConversationLog()
log.add("user", "Hey Alfred")
log.add("assistant", "Good morning, Christopher")
print(len(log))    # 2
print(log)         # "ConversationLog with 2 messages"
```

---

### 4. Class vs Instance Variables
```python
class AlfredNode:
    node_count = 0   # class variable — shared across ALL instances

    def __init__(self, name):
        AlfredNode.node_count += 1
        self.name = name             # instance variable — unique to each instance
        self.id = AlfredNode.node_count

brain = AlfredNode("brain")
memory = AlfredNode("memory")
print(AlfredNode.node_count)   # 2 — shared
print(brain.id)                # 1 — unique
print(memory.id)               # 2 — unique
```

---

## This Week's Practice Scripts

### Exercise 1 — `alfred_node.py`
Build the `AlfredNode` base class from the example above. Add a `log_event(message)` method that appends timestamped messages to a list stored on the instance. Add a `get_logs()` method that returns all logs. Test it.

**Alfred connection:** This is literally Alfred's base node architecture.

---

### Exercise 2 — `brain_node.py`
Build a `BrainNode` class that inherits from `AlfredNode`. Add:
- A `model` attribute defaulting to "llama3"
- A `message_history` list
- A `route_message(message)` method that adds the message to history and returns whether it should go to local or cloud model (use a simple rule: if message contains "search" or "news" route to cloud, otherwise local)
- A `get_history()` method

**Alfred connection:** This is the skeleton of Alfred's actual brain node.

---

### Exercise 3 — `conversation_log.py`
Build a `ConversationLog` class with:
- A list of message dictionaries with role and content keys
- `add_message(role, content)` method
- `get_last_n(n)` method returning the last n messages
- `clear()` method
- `__len__` and `__str__` dunder methods
- `to_dict()` method returning the full list for passing to an LLM API later

**Alfred connection:** This feeds directly into Alfred's RAG pipeline context window management.

---

### Exercise 4 — `user_profile.py`
Build a `UserProfile` class with:
- name, face_id, last_seen attributes
- `update_last_seen()` method that stores current timestamp using `import time; time.time()`
- `is_authorized()` method — for now just return True if name is not "unknown"
- `__str__` dunder method

**Alfred connection:** Alfred's vision node creates UserProfile objects for each recognized face.

---

### Exercise 5 — `alfred_system.py`
Import your `BrainNode` and `ConversationLog` from the previous exercises. Create instances of both. Simulate a short conversation — add 3 messages to the log, route each through the brain node, print the routing decision and the log length after each message.

**Alfred connection:** This is your first multi-module Alfred simulation.

---

## Free Resources for This Week

1. [freeCodeCamp Python Course](https://www.youtube.com/watch?v=rfscVS0vtbw) — watch 3:00:00 to end
2. [Real Python — OOP in Python](https://realpython.com/python3-object-oriented-programming/)
3. [Real Python — Inheritance](https://realpython.com/inheritance-composition-python/)

---

## End of Week Check

- [ ] Write a class with __init__, instance variables, and methods from memory
- [ ] Create a child class using inheritance and super()
- [ ] Implement __len__ and __str__ dunder methods
- [ ] Explain the difference between class and instance variables
- [ ] Import a class from another file and use it
- [ ] Explain every line of all 5 exercises out loud

---

## Commit This Week

```
week3: complete OOP exercises — alfred node architecture skeleton
```
