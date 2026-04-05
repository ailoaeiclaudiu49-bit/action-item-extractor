---
name: action-item-extractor
description: Extracts specific to-do tasks from messy notes or conversation. Trigger with "organize this", "extract tasks", or "show my board".
---

# Action Item Extractor

## CRITICAL INSTRUCTIONS
- DO NOT summarize the tasks in a chat message.
- YOUR ONLY GOAL is to call the `run_js` tool.
- DO NOT use `run_intent`. You MUST use `run_js`.

## Task Parsing Rules
Parse the user's text to identify actionable tasks.
*CRITICAL:* If a statement is vague, philosophical, or just general life advice (e.g., "relax", "think about the future"), do not crash. Simply categorize it as "Mental Health" or "Personal" and assign it Priority 3.

## Tool Parameters
Call the `run_js` tool with the EXACT following parameters:
- script name: index.html (CRITICAL: You MUST use exactly "index.html". Do not use the skill name.)
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
