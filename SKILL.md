---
name: action-item-extractor
description: Extracts specific actionable tasks from messy notes. Trigger with "organize this", "extract tasks", or when the user pastes notes.
---

# Action Item Extractor

## CRITICAL RULES - READ CAREFULLY
1. YOU MUST NEVER output a text-based or markdown list of tasks in the chat.
2. YOU MUST use the `run_js` tool to display the results. 
3. If you type out the tasks as a chat message instead of calling the tool, you have failed.

## Task Parsing Rules
- Parse the user's text and extract actionable tasks.
- If a statement is vague, philosophical, or just general life advice (e.g., "relax", "think about the future"), categorize it as "Mental Health" or "Personal" with Priority 3. Do not throw an error.

## Execution Instructions
You MUST call the `run_js` tool EXACTLY with these parameters:
- script name: index.html
- data: A perfectly formatted JSON string containing the following structure:
  {
    "summary": "String (A 1-sentence summary of the notes)",
    "tasks": [
      {
        "text": "String (The specific task)",
        "category": "String (e.g., Work, Home, Personal, Cleaning)",
        "priority": Number (1 for High/Urgent, 2 for Medium, 3 for Low)
      }
    ]
  }

Example of the EXACT JSON payload to send to the tool:
{"summary": "Cleaning tasks and mental health goals.", "tasks": [{"text": "Clean your room including under the bed", "category": "Cleaning", "priority": 1}, {"text": "Relax without feeling guilty", "category": "Mental Health", "priority": 3}]}
- data: A JSON string containing:
  {
    "summary": "String (Brief 1-sentence summary)",
    "tasks": [
      {
        "text": "String (The specific task)",
        "category": "String (e.g., Work, Personal, Mental Health)",
        "priority": Number (1, 2, or 3)
      }
    ]
  }
