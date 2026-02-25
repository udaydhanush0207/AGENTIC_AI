# Website Intelligence Summarizer (LLM App)

## Overview
This project takes a public website URL, extracts the visible content, and uses an LLM to generate a structured summary designed for fast understanding.

It outputs:
- What the company does
- Core services
- Project examples (if available)
- Acronyms explained (CIP, HUB, etc.)
- Practical interpretation for a first-time visitor

## Architecture
**Input:** Website URL  
**Pipeline:**
1) Fetch website contents  
2) Build structured messages (system + user)  
3) Call Chat Completions API  
4) Parse response  
5) Render Markdown summary

**Output:** Structured, readable summary

## Key Engineering Concepts Demonstrated
- Role-based prompt design (system vs user)
- Modular message construction (`messages_for()`)
- JSON response parsing (`response.choices[0].message.content`)
- Clean separation of prompts and execution logic

## Setup
1) Create a virtual environment
2) Install dependencies
3) Add your API key

### Requirements
- Python 3.12+
- OpenAI-compatible API key

### Install
```bash
pip install -r requirements.txt
