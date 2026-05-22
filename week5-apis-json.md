# Week 5 — APIs and JSON
**Phase 1 | Mid July**

---

## What You're Learning This Week

This is the bridge to everything. Alfred calls LLM APIs constantly. Understanding how to make HTTP requests, handle JSON responses, and manage API keys is non-negotiable.

---

## Concepts to Memorize

### Making API Requests
```python
import requests
import os

# GET request — fetching data
response = requests.get("https://wttr.in/Charlotte?format=j1")
print(response.status_code)   # 200 means success
data = response.json()        # parse JSON response automatically

# POST request — sending data (how you call LLM APIs)
response = requests.post(
    "https://api.openai.com/v1/chat/completions",
    headers={
        "Authorization": f"Bearer {os.environ.get('OPENAI_API_KEY')}",
        "Content-Type": "application/json"
    },
    json={
        "model": "gpt-3.5-turbo",
        "messages": [{"role": "user", "content": "Hello"}]
    }
)

data = response.json()
reply = data["choices"][0]["message"]["content"]
```
**Memorize:** Never hardcode API keys. Always use environment variables.  
**Memorize:** `response.json()` parses JSON automatically. `response.text` is raw string.  
**Memorize:** Status codes — 200 OK, 400 bad request, 401 unauthorized, 500 server error.

---

### Environment Variables
```python
import os
from dotenv import load_dotenv   # pip install python-dotenv

load_dotenv()   # reads .env file

api_key = os.environ.get("OPENAI_API_KEY")
if not api_key:
    raise ValueError("OPENAI_API_KEY not set")
```

**.env file (never commit this to GitHub):**
```
OPENAI_API_KEY=sk-your-key-here
OLLAMA_HOST=http://localhost:11434
```

**.gitignore must contain:**
```
.env
```

---

### Navigating Nested JSON
```python
# API responses are often deeply nested
response_data = {
    "choices": [
        {
            "message": {
                "role": "assistant",
                "content": "Good morning, Christopher"
            },
            "finish_reason": "stop"
        }
    ],
    "usage": {
        "prompt_tokens": 10,
        "completion_tokens": 5
    }
}

# Access nested values
content = response_data["choices"][0]["message"]["content"]
tokens_used = response_data["usage"]["completion_tokens"]

# Safe access for optional fields
finish = response_data["choices"][0].get("finish_reason", "unknown")
```

---

## This Week's Exercises

### Exercise 1 — `weather_fetcher.py`
Call the free wttr.in API (no key needed) for your city. Parse the JSON and print the current temperature, weather description, and humidity in a clean format. Handle connection errors.

**Alfred connection:** Alfred's context node pulls environmental data exactly like this.

### Exercise 2 — `ollama_caller.py`
Install Ollama locally and pull llama3. Write a function `ask_ollama(prompt)` that posts to `http://localhost:11434/api/generate` and returns the response text. Handle the streaming response format Ollama uses.

**Alfred connection:** This is Alfred's local LLM call function.

### Exercise 3 — `api_key_manager.py`
Set up python-dotenv. Create a `.env` file with a fake API key. Write a function that loads it safely and raises a clear custom error if it's missing. Add `.env` to `.gitignore` and verify it won't be committed.

**Alfred connection:** Alfred's security layer for all API credentials.

### Exercise 4 — `llm_router.py`
Build on Exercise 2. Write a `route_prompt(prompt)` function that:
- If the prompt contains "search", "news", or "today" — print "Routing to cloud" and return a placeholder response
- Otherwise — calls your `ask_ollama()` function and returns the real response

**Alfred connection:** This is Alfred's brain node routing logic in its simplest form.

### Exercise 5 — `conversation_api.py`
Build a simple back-and-forth with Ollama that maintains message history. Each message you send should include the full conversation history so the model has context. Store history as a list of dictionaries. Loop until user types "quit".

**Alfred connection:** This is Alfred's conversation memory in its most basic form.

---

## End of Week Check
- [ ] Make GET and POST requests with headers and JSON body from memory
- [ ] Parse nested JSON responses correctly
- [ ] Use environment variables for API keys — never hardcode
- [ ] Handle request exceptions (ConnectionError, Timeout, HTTPError)
- [ ] Have a working Ollama conversation loop running locally

---

```
week5: api and json exercises complete — ollama conversation loop working
```
