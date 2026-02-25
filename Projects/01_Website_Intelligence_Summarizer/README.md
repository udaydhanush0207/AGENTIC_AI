# Website Intelligence Summarizer (LLM Prototype)

## Overview
This project demonstrates a structured LLM pipeline that transforms a public website into a clean, structured business intelligence summary.

It uses OpenAI’s Chat Completions API to:

- Extract key company services
- Identify project examples
- Explain acronyms (CIP, HUB, etc.)
- Provide structured, readable Markdown output
- Present business context for first-time readers

This project is designed as a prototype LLM application and is not deployed publicly.

***

## Why This Project
The goal was to build a clean LLM-powered summarization workflow while practicing:

- Role-based prompt design (system vs user)
- Modular message construction
- API-based LLM interaction
- Structured Markdown output
- Real-world website data injection

***

## Architecture

### Input
- Public website URL

### Pipeline
1. Retrieve website contents
2. Construct structured prompt messages
3. Send to Chat Completions API
4. Parse structured JSON response
5. Render formatted Markdown output

### Output
- Executive summary
- Services breakdown
- Project scale
- Acronym explanation
- Practical interpretation

***

## Key Concepts Demonstrated
- System vs User prompt separation
- Controlled LLM behavior via instruction design
- Dynamic message construction (`messages_for()`)
- API response parsing
- Context injection
