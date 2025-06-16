# 📋 Meeting Notes Extractor

This project provides a Python utility that:

* Generates a **concise two-sentence summary** of a meeting transcript.
* Extracts a **list of action items**, each as a bullet point.
* Returns the result as a structured JSON object.

It uses:

* **LangChain** for prompt orchestration and LLM interaction.
* **Pydantic** to enforce a strict output schema.
* **OpenAI GPT-4** (or other compatible models).

---

## 🚀 Example

### Input:

```
Alice: We need to finalize the Q3 marketing plan by next Monday.
Bob: I'll send the initial draft by Thursday.
Alice: Also, let's schedule a follow-up meeting for Friday at 2 PM.
```

### Output:

```json
{
  "summary": "The team discussed finalizing the Q3 marketing plan by next Monday. Bob will send the initial draft by Thursday, and a follow-up meeting is scheduled for Friday at 2 PM.",
  "action_items": [
    "- Finalize the Q3 marketing plan by next Monday.",
    "- Bob to send the initial draft by Thursday.",
    "- Schedule a follow-up meeting for Friday at 2 PM."
  ]
}
```

---

## 📦 Installation

1️⃣ Install dependencies:

```bash
pip install openai langchain pydantic
```

2️⃣ Set your OpenAI API key:

```bash
export OPENAI_API_KEY=your-api-key-here
```

(or set it in the code)

---

## 💻 Usage

```python
from your_module import extract_meeting_notes

transcript = """
Alice: We need to finalize the Q3 marketing plan by next Monday.
Bob: I'll send the initial draft by Thursday.
Alice: Also, let's schedule a follow-up meeting for Friday at 2 PM.
"""

result = extract_meeting_notes(transcript)

import json
print(json.dumps(result, indent=2, ensure_ascii=False))
```

---

## ⚙️ Features

✅ Uses **LangChain’s PydanticOutputParser** to validate JSON structure.
✅ Automatic retry with stricter prompt if malformed output is detected.
✅ Strict schema:

```json
{
  "summary": "...",
  "action_items": ["...", "..."]
}
```

✅ Easily extendable (e.g. to FastAPI, LangSmith logging, agents).

---

## 📝 Project Structure

```
transcript_generator.ipynb  # Main logic
README.md                   # This file
```

---
