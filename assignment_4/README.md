# Simplified Agentic RAG System

This project builds a LangGraph-based agentic RAG pipeline that:

- Retrieves up to 5 relevant software best-practice snippets from a local JSON KB.
- Generates an initial LLM-based answer.
- Self-critiques the answer for completeness.
- If incomplete, retrieves 1 extra snippet and refines the answer.
- Outputs a citation-backed response.

## Requirements

- Python 3.10+
- `langchain`
- `langgraph`
- `chromadb`
- `openai`

## Run

1️⃣ Place `self_critique_loop_dataset.json` in the project folder  
2️⃣ Update your OpenAI API key (via environment)  
3️⃣ Run: The entire notebook through the end.

## Example

Enter your software best-practices question: What are best practices for debugging?

=== FINAL ANSWER ===
When debugging, start with a minimal reproducible test, use logging, and apply divide-and-conquer (debugging_guide.md). Also, consider pair debugging for complex issues (debug_tips.md).

=== CITED SOURCES ===
KB001: debugging_guide.md (updated 2024-01-10)
KB002: debug_tips.md (updated 2024-01-15)
