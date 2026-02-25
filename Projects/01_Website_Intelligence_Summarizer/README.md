# Website Summarization with OpenAI 

This notebook documents my hands-on build of a simple LLM application: a **website summarizer** that fetches content from a public URL and generates a structured summary using OpenAI’s Chat Completions API.

The goal was to demonstrate practical LLM engineering fundamentals:
- environment setup
- secure API usage
- role-based prompt design
- message construction
- calling the model and parsing the response

---

## What I Built

**Input:** a website URL (example used: Front Line Advisory Group website)  
**Process:**
1. Fetch the visible website contents (`[redacted]_contents(url)`)
2. Construct a message payload in OpenAI's chat format (system + user)
3. Call the OpenAI Chat Completions API
4. Parse the response and display as Markdown

**Output:** a structured summary including:
- what the company does
- services and project examples
- acronyms explained (e.g., CIP, HUB)
- readable formatting with headings and bullet points

---

## Tools / Stack Used

- **Git + GitHub** (version control, project tracking)
- **PowerShell** (local setup + commands)
- **Cursor IDE** (project navigation + coding workflow)
- **Jupyter Notebook (.ipynb)** (experimentation + execution)
- **OpenAI Python SDK** (`openai.chat.completions.create`)
- **Prompt Engineering** (system + user prompts, structured output)

---

## What I Did (Step-by-Step)

### 1) Repo Setup
- Installed Git
- Cloned the course/project repository using HTTPS
- Opened the project locally (Projects folder)
- Opened the repo inside Cursor IDE

**Why this matters:**
- Git documents real work and progress  
- Cloning ensures I’m working from a consistent codebase  

---

### 2) API Setup (Securely)
- Generated an OpenAI API key
- Stored it locally as an environment variable / `.env` (not committed)

**Why the API key is secret:**
- Anyone with the key can spend credits from my account  
- Keys must never be hardcoded or pushed to GitHub  
- Proper secret handling is a production requirement  

---

### 3) Website Fetch + Summarization
- Pulled website content with `[redacted]_contents(url)`
- Built prompt + message payload using a `messages_for()` function
- Called the model using:

```python
response = openai.chat.completions.create(
    model="gpt-4.1-mini",
    messages=messages
)
```
## Parsed the model output using:
response.choices[0].message.content


## System message (behavior)
Defines how the assistant should behave (format, tone, structure, constraints).

## User message (task + input)
Provides the request and the website content.

### This structure is important because:
- it gives repeatable behavior
- it keeps instructions separate from the data
- it’s the standard format for production chat-based LLM applications
---

# Why the Message Format Looks Like This

OpenAI chat models expect a list of messages like:
```python
[
  {"role": "system", "content": "..."},
  {"role": "user", "content": "..."}
]
```

# Why I Used `messages_for()` (Modularity)

I created a helper function:
```python
def messages_for(website):
    return [
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": user_prompt + website}
    ]
```

### Why:
- keeps prompts reusable and clean
- makes it easy to summarize any website by swapping the input
- matches how LLM apps are structured in real projects (separation of prompt + runtime input)

---

# API Cost / Credits (What I Learned)

This notebook is not deployed publicly because:
- every run calls a paid API
- website text can be large → more tokens → higher cost

### Costs depend on:
- website length (tokens)
- model selection
- number of calls

### To control cost in real systems, you typically add:
- token limits
- chunking
- caching
- rate limiting

(Those are later-stage improvements. This notebook focuses on correct fundamentals.)

---

# Results (Example)

Example URL tested: https://www.walmart.com/

The model produced a structured summary including:
- company overview
- services breakdown
- project examples and scale
- acronyms explained
- practical interpretation for a first-time visitor

---

# Security Notes

✅ API keys are stored locally and not included in this repo  
✅ `.env` is not uploaded  
✅ No secrets are committed  

---
This isn’t “just a notebook.”

It demonstrates that I can:
- set up an AI dev environment cleanly
- securely use LLM APIs
- structure prompts for consistent output
- build small, working LLM applications end-to-end
- understand cost/security tradeoffs (API keys + tokens)

---

# Author

**Venkat Satya Uday Dhanush Karri**  
Focus: LLM systems, RAG, Agentic workflows, production AI engineering

---


