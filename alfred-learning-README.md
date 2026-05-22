# Alfred — AI Droid Project & Python Learning Path
**Author:** Christopher Steves  
**Goal:** Junior AI Application Developer | December 2026 Graduate  
**Target Role:** Generative AI / AI Application Developer — Charlotte, Atlanta, Southeast  

---

## What This Repository Is

This is not a collection of random practice exercises.  
Every script, every concept, every library learned here feeds directly into **Alfred** — a context-aware AI desktop droid assistant built on a local RAG pipeline, LLM routing, and MQTT event architecture.

By December 2026 this repository tells one coherent story:  
*Someone who learned to build real AI systems by actually building one.*

---

## Repository Structure

```
alfred-learning/
│
├── phase1-python-fundamentals/     # June - July | Pure Python, no AI libraries yet
│   ├── week1-basics/               # Syntax, variables, data types, loops
│   ├── week2-functions-and-logic/  # Functions, conditionals, problem solving
│   ├── week3-oop/                  # Classes and objects — how Alfred's modules are structured
│   ├── week4-files-and-errors/     # File I/O, error handling — conversation logging
│   ├── week5-apis-and-json/        # REST APIs, JSON — talking to LLMs
│   └── week6-capstone-mini-project/# Small working project using everything above
│
├── phase2-data-and-requests/       # August | Bridge between Python and AI libraries
│   ├── week7-pandas-and-data/      # Data manipulation — analyzing conversation history
│   ├── week8-http-and-rest/        # HTTP clients, headers, auth — production API calls
│   └── week9-capstone-mini-project/# CLI chatbot hitting a real LLM API
│
└── phase3-alfred-droid/            # September - December | Build Alfred
    ├── brain-node/                 # LLM routing, prompt engineering, Ollama integration
    ├── memory-rag-pipeline/        # LangChain, ChromaDB, embeddings, retrieval
    ├── audio-node/                 # TTS, STT, ElevenLabs integration
    ├── context-node/               # ActivityWatch API, PC context awareness
    └── mqtt-bus/                   # Eclipse Mosquitto, event-driven architecture
```

---

## The Three Phases

### Phase 1 — Pure Python Fundamentals
**June through July | Runs alongside Data Structures course**

No AI libraries. No LangChain. No shortcuts.  
This is where you build the foundation that makes Phase 3 actually yours.

**Rule:** Write it yourself first. Use AI only to understand why it broke, never to write it for you.

**Free Resources — in this order:**
1. [Python Official Tutorial](https://docs.python.org/3/tutorial/) — dry but accurate, do it first
2. [freeCodeCamp Python Full Course (YouTube)](https://www.youtube.com/watch?v=rfscVS0vtbw) — 4 hours, genuinely good, pause and code along
3. [Real Python](https://realpython.com) — free articles, project-based, use for specific topics
4. [W3Schools Python](https://www.w3schools.com/python/) — quick syntax reference, not a course
5. [Exercism.io Python Track](https://exercism.org/tracks/python) — free coding exercises with mentor feedback

**What to memorize in Phase 1:**
- Variable types: str, int, float, bool, list, dict, tuple
- Loop patterns: for, while, list comprehensions
- Function structure: def, parameters, return, default args
- Class structure: __init__, self, methods, inheritance basics
- Error handling: try, except, finally, raising exceptions
- File operations: open, read, write, with statements
- String methods: .split(), .join(), .strip(), .format(), f-strings

---

### Phase 2 — Data and Requests
**August | Bridge phase**

You can write Python. Now make it talk to the outside world.  
This is where Alfred's ability to call LLM APIs comes from.

**Free Resources:**
1. [Real Python — Requests Library](https://realpython.com/python-requests/) — essential
2. [Real Python — Working with JSON](https://realpython.com/python-json/)
3. [Pandas Official Getting Started](https://pandas.pydata.org/docs/getting_started/intro_tutorials/)
4. [freeCodeCamp APIs and Microservices (YouTube)](https://www.youtube.com/watch?v=GK4Pl-GmPHk)

**What to memorize in Phase 2:**
- requests.get(), requests.post(), response.json(), status codes
- JSON: json.loads(), json.dumps(), nested access
- Pandas: read_csv(), DataFrame basics, filtering, groupby
- Environment variables: os.environ, .env files, never hardcode API keys
- Basic auth patterns: headers, Bearer tokens

---

### Phase 3 — Build Alfred
**September through December | This is the capstone**

Every library you learn here gets learned by implementing it in Alfred directly.  
No separate practice — the project is the practice.

**Libraries in implementation order:**
1. **paho-mqtt** — MQTT message bus, Alfred's nervous system
2. **ollama** Python client — local LLM calls
3. **openai** Python SDK — cloud LLM fallback
4. **langchain** — RAG pipeline orchestration
5. **chromadb** — vector database for Alfred's memory
6. **fastapi** — internal API endpoints between nodes
7. **elevenlabs** — TTS for Alfred's voice
8. **opencv-python** — face detection for user recognition
9. **pyaudio / sounddevice** — audio input handling

**Free Resources for Phase 3:**
1. [LangChain Official Docs](https://python.langchain.com/docs/)
2. [ChromaDB Official Docs](https://docs.trychroma.com/)
3. [Ollama GitHub](https://github.com/ollama/ollama)
4. [FastAPI Official Tutorial](https://fastapi.tiangolo.com/tutorial/)
5. [Real Python — AsyncIO](https://realpython.com/async-io-python/)

---

## GitHub Commit Rules

**Do commit:**
- A finished working script, even if small
- A fixed bug with a note about what you learned
- A new module or feature added to Alfred

**Don't commit:**
- Code you can't explain line by line
- Broken code with no note about what's wrong
- AI-generated code you didn't read and understand

**Commit message format — keep it simple:**
```
week1: add list and dictionary practice scripts
week3: build Vehicle class with methods
phase2: script calling openweather API and parsing JSON response
alfred: brain-node LLM routing logic first draft
```

---

## The Interview Test

Before any code goes on your resume or gets discussed in an interview, pass this test:

**Can you explain every line out loud without looking at it?**

If yes — it's yours. Put it on GitHub. Talk about it confidently.  
If no — spend more time with it. You're not done yet.

---

## Milestone Targets

| Date | Milestone |
|------|-----------|
| End of June | Phase 1 weeks 1-3 complete, 20+ commits |
| End of July | Phase 1 complete, mini-project working, AI-103 study started |
| August 1 | Capstone proposal submitted to BenMessaoud |
| End of August | Phase 2 complete, CLI chatbot hitting real LLM API |
| End of September | Alfred MQTT bus and brain-node running locally |
| End of October | RAG pipeline working, Alfred remembers conversations |
| End of November | Alfred demo-able, HuggingFace deployment live |
| December | Capstone submitted, job applications active |

---

## What You're Building Toward

**Target Role:** Junior AI Application Developer / Generative AI Developer  
**Target Markets:** Charlotte NC, Atlanta GA, Nashville TN  
**Target Salary:** $65,000 - $78,000  
**Target Start Date:** January - March 2027  
**Odds with full execution:** 80-85%

The price of admission is genuine Python competency demonstrated through real code committed consistently over six months.

That's the deal. You agreed to it. Now build.
